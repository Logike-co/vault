#java #spring

---
https://github.com/lokeshgupta1981/Spring-Boot-Examples/blob/master/spring-boot-batch/src/main/java/com/howtodoinjava/demo/batch/jobs/csvToDb/job/CsvToDatabaseJob.java
https://github.com/spring-projects/spring-batch/blob/main/spring-batch-samples/src/main/java/org/springframework/batch/samples/mongodb/InsertionJobConfiguration.java
https://spring.academy/courses/building-a-batch-application-with-spring-batch/lessons/spring-batch-steps-reading-writing-data
---
# Prerequisites

In order to get the most out of this guide, you should have:

- Experience with Java
- Familiarity with Spring Framework and Spring Boot
- Basic knowledge of Docker and SQL
# Introduction

Batch processing is a method of processing large volumes of data simultaneously, instead of processing them individually, in real time (in that case, we could talk about stream processing). This approach is widely used in many industries, including finance, manufacturing, and telecommunications. Batch processing is often used for tasks that require the processing of large amounts of data, such as payroll processing or billing, as well as tasks that require time-consuming calculations or analysis. Batch applications are ephemeral, which means that once they've completed, they end.

This type of processing comes with a number of challenges, including, but not limited to:

- Handling large amounts of data efficiently
- Tolerance to human errors and hardware deficiencies
- Scalability

When it's time to provide a batch-based application for processing large amounts of data in a structured way, Spring Batch provides a robust and efficient solution.

![[Pasted image 20240521023840.png]]

The billing job is structured in the following steps:

- **File preparation step**: copies the file that contains the monthly usage for Spring Cellular's customers from a file server to a staging area.
- **File ingestion step**: ingests the file into a relational database table that contains the data used to generate the billing report.
- **Report generation step**: processes the billing information from the database table, and generates a flat file that contains data for the customers who have spent more than $150.00 USD.

# Spring Batch Framework

Spring Batch is a lightweight, comprehensive framework, designed to enable the development of robust batch applications that are vital for the daily operations of enterprise systems.

It provides all the necessary features that are essential for processing large volumes of data, including transaction management, job processing status, statistics, and fault-tolerance features. It also provides advanced scalability features that enable high-performance batch jobs through multi-threaded processing and data-partitioning techniques. You can use Spring Batch in both simple use cases (such as loading a file into a database), and complex, high-volume use cases (like moving data between databases, transforming it, and so on).

Spring Batch integrates seamlessly with other Spring technologies, making it an excellent choice for writing batch applications with Spring.

## Batch Domain Language

The key concepts of the Spring Batch domain model are represented in the following diagram:

![[Pasted image 20240521024758.png]]

A `Job` is an entity that encapsulates an entire batch process, that runs from start to finish without interruption. A `Job` has one or more steps. A `Step` is a unit of work that can be a simple task (such as copying a file or creating an archive), or an item-oriented task (such as exporting records from a relational database table to a file), in which case, it would have an `ItemReader`, an `ItemProcessor` (which is optional), and an `ItemWriter`.

A `Job` needs to be launched with a `JobLauncher`, and can be launched with a set of `JobParameter`s. Execution metadata about the currently running `Job` is stored in a `JobRepository`.

## Batch Domain Model

Spring Batch uses a robust and well-designed model for the batch processing domain. It provides a rich set of Java APIs with interfaces and classes that represent all of the key concepts of batch processing like `Job`, `Step`, `JobLauncher`, `JobRepository`, and more. We will use these APIs in this course.

While the batch domain model can be implemented with any persistence technology (like a relational database, a non-relational database, a graph database, etc), Spring Batch provides a relational model of the batch domain concepts with metadata tables that closely match the classes and interfaces in the Java API.

The following entity-relationship diagram presents the main metadata tables:

![[Pasted image 20240521044358.png]]

- `Job_Instance`: This table contains all information relevant to a job definition, such as the job name and its identification key.
- `Job_Execution`: This table holds all information relevant to the execution of a job, like the start time, end time, and status. Every time a job is run, a new row is inserted in this table.
- `Job_Execution_Context`: This table holds the execution context of a job. An execution context is a set of key/value pairs of runtime information that typically represents the state that must be retrieved after a failure.
- `Step_Execution`: This table holds all information relevant to the execution of a step, such as the start time, end time, item read count, and item write count. Every time a step is run, a new row is inserted in this table.
- `Step_Execution_Context`: This table holds the execution context of a step. This is similar to the table that holds the execution context of a job, but instead it stores the execution context of a step.
- `Job_Execution_Params`: This table contains the runtime parameters of a job execution.

## Spring Batch Architecture

Spring Batch is designed in a modular, extensible way. The following diagram shows the layered architecture that supports the ease of use of the framework for end users:

![[Pasted image 20240521044433.png]]

This layered architecture highlights three major high-level components:

- The `Application` layer: contains the batch job and custom code written by the developers of the batch application.
- The `Batch Core` layer: contains the core runtime classes provided by Spring Batch that are necessary to create and control batch jobs. It includes implementations for `Job` and `Step`, as well as common services like `JobLauncher` and `JobRepository`.
- The `Batch Infrastructure` layer: contains common item readers and writers provided by Spring Batch, plus base services such as the repeat and retry mechanisms, which are used both by application developers and the core framework itself.

As a Spring Batch developer, you typically use APIs provided by Spring Batch in the `Batch Infrastructure` and `Batch Core` modules to define your jobs and steps in the `Application` layer. Spring Batch provides a rich library of batch components that you can use out of the box (such as item readers, item writers, data partitioners, and more).

# What Is a Job?

A `Job` is an entity that encapsulates an entire batch process that runs from start to finish. It consists of a set of steps that run in a specific order. We'll cover steps in a future lesson. Here, we focus on what a `Job` is and how it is represented in Spring Batch.

A batch job in Spring Batch is represented by the `Job` interface provided by the `spring-batch-core` dependency:

```java
public interface Job {
    String getName();
    void execute(JobExecution execution);
}
```

At a fundamental level, the `Job` interface requires that implementations specify the `Job` name (the `getName()` method) and what the `Job` is supposed to do (the `execute` method).

The `execute` method gives a reference to a `JobExecution` object. The`JobExecution` represents the actual execution of the `Job` at runtime. It contains a number of runtime details, such as the start time, the end time, the execution status, and so on. This runtime information is stored by Spring Batch in a metadata repository, which we'll cover in the next section.

Note how the `execute` method isn't expected to throw any exception. Runtime exceptions should be handled by implementations, and added in the `JobExecution` object. Clients should inspect the `JobExecution` status to determine success or failure.

# Understanding Job Metadata

One of the key concepts in Spring Batch is the `JobRepository`. The `JobRepository` is where all metadata about jobs and steps is stored. A `JobRepository` could be a persistent store, or an in-memory store. A persistent store has the advantage of providing metadata even after a `Job` is finished, which could be used for post analysis or to restart a `Job` in the case of a failure. We'll cover `Job` restartability in a later lesson.

Spring Batch provides a JDBC implementation of the `JobRepository`, which stores batch metadata in a relational database. In a production-grade system, you need to create a few tables that Spring Batch uses to store its execution metadata. We've covered metadata tables in the previous Lab.

The `JobRepository` is what creates a `JobExecution` object when a `Job` is first launched. But, how are `Job`s launched? Let's look at that in the next section.

# Launching Jobs

Launching jobs in Spring Batch is done through the `JobLauncher` concept, which is represented by the following interface:

COPY

```java
public interface JobLauncher {

   JobExecution run(Job job, JobParameters jobParameters)
          throws
             JobExecutionAlreadyRunningException,
             JobRestartException,
             JobInstanceAlreadyCompleteException,
             JobParametersInvalidException;
}
```

The `run` method is designed to launch a given `Job` with a set of `JobParameters`. We'll cover job parameters in detail in a later lesson. For now, you can think of them as a collection of key/value pairs that are passed to the `Job` at runtime. There are two important aspects to understand here:

- It is expected that implementations of the `JobLauncher` interface obtain a valid `JobExecution` from the `JobRepository` and execute the `Job`.
- The run method throws different types of exceptions. We'll cover all of these exceptions in detail during the course.

You'll almost never have to implement the `JobLauncher` interface yourself, because Spring Batch provides an implementation that's ready to use. The following diagram shows how the `JobLauncher`, the `JobRepository` and the `Job` interact with each other.

![[Pasted image 20240521062244.png]]

Batch jobs are typically launched in one of two ways:

- From the command line interface
- From within a web container

In this course, we'll only cover launching jobs from the command line. Please refer to the further resources links for more details about how to launch jobs from within a web container.

## What Are Job Instances?

A `Job` might be defined once, but it'll likely run many times, commonly on a set schedule. In Spring Batch, a `Job` is the generic definition of a batch process specified by a developer. This generic definition must be parametrized to create actual instances of a `Job`, which are called `JobInstance`s.

A `JobInstance` is a unique parametrization of a `Job` definition. For example, imagine a batch process that needs to be executed once at the end of each day, or when a certain file is present. In the once-per-day scenario, we can use Spring Batch to create an `EndOfDay` `Job` for that. There would be a single `EndOfDay` `Job` definition, but multiple instances of that same `Job`, one per day. Each instance would process the data of a particular day, and might have a different outcome (success or failure) from other instances. Therefore, each individual instance of the `Job` must be tracked separately.

A `JobInstance` is distinct from other `JobInstance`s by a specific parameter, or a set of parameters. For example, a parameter named `schedule.date` would specify a specific day. Such a parameter is called a `JobParameter`. `JobParameter`s are what distinguish one `JobInstance` from another. The following diagram shows how `JobParameter`s define `JobInstance`s:

![[Pasted image 20240521071435.png]]

## What Do Job Instances and Job Parameters Represent?

`JobInstance`s are distinct from each other by distinct `JobParameter`s. Those parameters usually represent the data intended to be processed by a given `JobInstance`. For example, in the case of the `EndOfDay` `Job`, the `schedule.date` `JobParameter` for January 1st defines the `JobInstance` that will process the data of January 1st. The `schedule.date` `JobParameter` for January 2nd defines the `JobInstance` that will process the data of January 2nd, and so forth.

While it is not required for `Job` parameters to represent the data to be processed, this is a good hint - and a good practice - to correctly design `JobInstance`s. Designing `JobInstance`s to represent the data to be processed is easier to configure, to test, and to think about, in case of failure.

The definition of a `JobInstance` itself has absolutely no bearing on the data to be loaded. It is entirely up to the `Job` implementation to determine how data is loaded, based on `JobParameter`s. Here are a few examples of `JobParameter`s, and how they represent the data to be processed by the corresponding `JobInstance`:

- A specific date: In this case, we would have a `JobInstance` per date.
- A specific file: In this case, we would have a `JobInstance` per file.
- A specific range of records in a relational database table: In this case, we would have a `JobInstance` per range.
- And more.

For our course, the `BillingJob` for Spring Cellular consumes a flat file as input, which is a good candidate to be passed as a `JobParameter` to our `Job`. This is what we'll see in the upcoming Lab of this lesson.

## [](https://spring.academy/courses/building-a-batch-application-with-spring-batch/lessons/spring-batch-understanding-job-instances#how-do-job-instances-relate-to-job-executions)How Do Job Instances Relate to Job Executions?

A `JobExecution` refers to the technical concept of a single _attempt_ to run a `JobInstance`. As seen in the previous lesson, a `JobExecution` may end in a success or failure. In the case of the `EndOfDay` `Job`, if the January 1st run fails the first time and is run again the next day, it is still the January 1st run. Therefore, each `JobInstance` can have multiple `JobExecution`s.

The relation between the concepts of `Job`, `JobInstance`, `JobParameters`, and `JobExecution` is summarized in the following diagram:

![[Pasted image 20240521071632.png]]

Here's a concrete example of the lifecycle of a `JobInstance` in the case of the `EndOfDay` `Job`:

![[Pasted image 20240521071654.png]]

In this example, the first execution attempt of `Job Instance 1` fails, so another execution is run and succeeds. This leads to two `JobExecution`s for the same `JobInstance`. For `Job Instance 2` however, the first execution attempt succeeds, therefore there is no need to launch a second execution.

In Spring Batch, a `JobInstance` is not considered to be complete unless a `JobExecution` completes successfully. A `JobInstance` that is complete can't be restarted again. This is a design choice to prevent accidental re-processing of the same data for batch `Job`s that are not idempotent.

## [](https://spring.academy/courses/building-a-batch-application-with-spring-batch/lessons/spring-batch-understanding-job-instances#the-different-types-of-job-parameters)The Different Types of Job Parameters

`JobParameter`s are typically used to distinguish one `JobInstance` from another. In other words, they are used to _identify_ a specific `JobInstance`.

Not all parameters can be used to identify `Job` instances. For example, if the `EndOfDay` `Job` takes another parameter - say, `file.format`) - that represents the format of the output file (CSV, XML, and others), this parameter does not really represent the data to process, so, it could be excluded from the process of identifying the `Job` instances.

This is where non-identifying `JobParameter`s come into play. In Spring Batch, `JobParameter`s can be either identifying or non-identifying. An identifying `JobParameter` contributes to the identification of `JobInstance`, while a non-identifying one doesn't. By default, `JobParameter`s are identifying, and Spring Batch provides APIs to specify whether a `JobParameter` is identifying or not.

In the example of the `EndOfDay` `Job`, the parameters can be defined in the following table:

|Job parameter|Identifying?|Example|
|---|---|---|
|schedule.date|Yes|2023-01-01|
|file.format|No|csv|

Now the question is: Why is this important, and how is it used in Spring Batch? Identifying `JobParameter`s play a crucial role in the case of failure. In a production environment, where hundreds of `Job` instances are running, and one of them fails, we need a way to identify which instance has failed. This is where identifying `Job` parameters are key. When a `JobExecution` for a given `JobInstance` fails, launching the same job with the _same_ set of identifying `JobParameter`s will create a new `JobExecution` (ie a new attempt) for the _same_ `JobInstance`.

## What Is a Step?

In everyday life we often talk about taking steps. A step down the path. A step in the right direction. Stepping up to the task.

Spring Batch has steps, too. A `Step` is a domain object that encapsulates an independent, sequential phase of a batch `Job`. It contains all of the information necessary to define a unit of work in a batch `Job`.

A `Step` in Spring Batch is represented by the `Step` interface provided by the `spring-batch-core` dependency:

COPY

```java
public interface Step {

  String getName();

  void execute(StepExecution stepExecution) throws JobInterruptedException;
}
```

Similar to the `Job` interface, the `Step` interface requires, at a fundamental level, an implementation to specify the step name (the `getName()` method) and what the step is supposed to do (the `execute` method).

The `execute` method provides a reference to a `StepExecution` object. The `StepExecution` represents the actual execution of the step at runtime. It contains a number of runtime details, such as the start time, the end time, the execution status, and so on. This runtime information is stored by Spring Batch in the metadata repository, similar to the `JobExecution`, as we have seen previously.

The `execute` method is designed to throw a `JobInterruptedException` if the job should be interrupted at that particular step.

## What Are the Different Types of Steps?

While it's possible to implement the `Step` interface manually to define the logic of a step, Spring Batch provides different implementations for common use cases. All these implementations derive from the base `AbstractStep` class that provides the common requirements such as setting the start time, end time of a step, updating the exit status of the step, persisting the step's metadata in the job repository, etc.

The most commonly used `Step` types are the following:

- `TaskletStep`: Designed for simple tasks (like copying a file or creating an archive), or item-oriented tasks (like reading a file or a database table).
- `PartitionedStep`: Designed to process the input data set in partitions.
- `FlowStep`: Useful for logically grouping steps into flows.
- `JobStep`: Similar to a `FlowStep` but actually creates and launches a separate job execution for the steps in the specified flow. This is useful for creating a complex flow of jobs and sub-jobs.

The following diagram explains the hierarchy and relation between these different types of `Steps`.

![[Pasted image 20240522234518.png]]

## The `TaskletStep`

The [`TaskletStep`](https://docs.spring.io/spring-batch/docs/5.0.4/reference/html/step.html#taskletStep "Spring Batch Tasklet Step") is an implementation of the `Step` interface based on the concept of a `Tasklet`. A `Tasklet` represents a unit of work that the Step should do when invoked. The `Tasklet` interface is defined as follows:

COPY

```java
@FunctionalInterface
public interface Tasklet {

  @Nullable
  RepeatStatus execute(StepContribution contribution, ChunkContext chunkContext) throws Exception;
}
```

The `execute` method of this functional interface is designed to contain one iteration of the business logic of a `TaskletStep`. There are a few key elements to understand:

- The return type of the `execute` method is of type `RepeatStatus`. This is an enumeration that's used to signal to the framework that work has been completed (`RepeatStatus.FINISHED`), or not completed yet (`RepeatStatus.CONTINUABLE`). In that latter case, the `TaskletStep` re-invokes that `Tasklet` again.
- Each iteration of the `Tasklet` is executed in the scope of a database transaction. This way, Spring Batch saves the work that has been done during the iteration in the persistent job repository. That way, the step can resume where it left off, in case of failure. For this reason, the `TaskletStep` requires a `PlatformTransactionManager` to manage the transaction of the `Tasklet`. We'll address this in the Lab for this lesson.
- The `execute` method provides a reference to a `StepContribution` object, which represents the contribution of this `Tasklet` to the step (for example how many items were read, written, or otherwise processed) and a reference to a `ChunkContext` object, which is a bag of key/value pairs that provide detail about the execution context of the `Tasklet`.
- The `execute` method is designed to throw an exception if any error occurs during the processing, in which case, the step will be marked as failed.

Spring Batch provides several implementations of the `Tasklet` interface for common use cases:

- `ChunkOrientedTasklet`: Designed for item-oriented data sets, like a flat file or database table. We'll explain this implementation in more detail, and use it in the Labs of this course.
- `SystemCommandTasklet`: Lets you invoke an Operating System command within the `Tasklet`. We won't use this implementation in this course, but you can refer to the "References" section for more information about how to use it.
- Others. See the [Spring Batch Reference documentation](https://docs.spring.io/spring-batch/reference/index.html) for details.

We'll explore these concepts in more detail in future lessons. All you need to understand for now is the different types of Steps and what comprises them.

## Using Steps To Define the Job Execution Flow

As we said, you'll rarely have to implement the `Job` interface manually, like we did in the previous lessons (which we did deliberately, for learning purposes). In fact, Spring Batch provides the `AbstractJob` class that lets you define your job as a flow of steps. This class has two variations:

- `SimpleJob`: For sequential execution of steps.
- `FlowJob`: For complex step flows, including conditional branching and parallel execution.

In this course, you'll learn how to use the `SimpleJob` variation. For more information about `FlowJob`, see the "Condition Flows" and "Parallel Flows" references in the "Links" section of this lesson.

## [](https://spring.academy/courses/building-a-batch-application-with-spring-batch/lessons/spring-batch-steps-using-steps#the-simplejob)The `SimpleJob`

The `SimpleJob` class is designed to compose a job as a sequence of steps. A step should be completed successfully in order for the next step in the sequence to start. If a step fails, the job is immediately terminated and subsequent steps are not executed. You can create a sequential flow of steps by using the `JobBuilder` API. Here's an example with two steps:

COPY

```java
@Bean
public Job myJob(JobRepository jobRepository, Step step1, Step step2) {
  return new JobBuilder("job", jobRepository)
    .start(step1)
    .next(step2)
    .build();
}
```

In this example, the job (`myJob`) is defined as a sequence of two steps, `step1` and `step2`. The job starts with `step1` and moves to `step2` only if `step1` completes successfully. If `step1` fails, the job is terminated, and `step2` won't be executed. Our `BillingJob` for Spring Cellular is defined as a sequence of three steps, and we'll define it in a similar manner in the Lab for this lesson.

In the previous example, we pass steps as parameters to the `myJob` bean definition method. But, how are these steps defined, and how are they created? This is what we'll see in the next section.

## [](https://spring.academy/courses/building-a-batch-application-with-spring-batch/lessons/spring-batch-steps-using-steps#how-to-create-steps)How To Create Steps?

Similar to the `JobBuilder` API, Spring Batch provides the `StepBuilder` API to let you create different types of steps. All step types share some common properties (like the step name, the job repository to report metadata to, and others), but each step type has its own specific properties. For this reason, Spring Batch provides a specific builder for each step type (`TaskletStepBuilder`, `PartitionedStepBuilder`, and others).

You shouldn't worry about how to create those specific builders, as Spring Batch guides you to using the corresponding one depending on the type of step you are creating. The main entry point to create steps is the `StepBuilder` API. Here's an example that creates a `TaskletStep`:

COPY

```java
@Bean
public Step taskletStep(JobRepository jobRepository, Tasklet tasklet, PlatformTransactionManager transactionManager) {
  return new StepBuilder("step1", jobRepository)
    .tasklet(tasklet, transactionManager)
    .build();
}
```

In this example, we define the step as a Spring bean. The `StepBuilder` accepts the step name and the job repository to report metadata to at construction time, as those are common to all step types.

After that, we call the `StepBuilder.tasklet` method, which will use a `TaskletStepBuilder` to further define specific properties of the `TaskletStep`, mainly the `Tasklet` to execute as part of the step and the transaction manager to use for transactions. Note how we did not use the `TaskletStepBuilder` directly.

The pattern is similar if, for instance, you want to create a partitioned step. Here's an example to create a `PartitionedStep`:

COPY

```java
@Bean
public Step partitionedtStep(JobRepository jobRepository, Partitioner partitioner) {
  return new StepBuilder("step1", jobRepository)
    .partitioner("worker", partitioner)
    .build();
}
```

In the same way that we've created a `TaskletStep` in our lab, we'll use the main entry point (the `StepBuilder`) by passing the common properties to it in the constructor (that is, the step name and job repository), then call `StepBulider.partitioner` to further configure the partitioned step with its specific attributes (the `partitioner` in this case). The `Partitioner` is beyond the scope of this lesson and course. We'll use it here only as an example, to show the difference between step type specific attributes. Note that we didn't use the `PartitionedStepBuilder`, instead we used the `StepBuilder` directly.

##   Understanding Step Metadata

Similar to job-level metadata, which is stored in the `BATCH_JOB_EXECUTION` table, Spring Batch stores step-level metadata in the `BATCH_STEP_EXECUTION` table. This includes the start time of the step, its end time, its execution status, and other details. We'll see an example of this step-level metadata in the lab for this course.

Another similarity with the job level is the execution context. Each step has an execution context, which is nothing more than a set of key/value pairs to store runtime information about the execution of the step. This includes the step type, the tasklet type if the step is a `TaskletStep`, and other details. The context might also record the progress of a step, like item read count, item write count, and other metrics. These key/value pairs can be used to restart a step where it left off, in case of failure.

By default, a successful step is not re-executed when restarting a failed job instance. However, in some situations, even a successful step should be re-executed when re-attempting a job instance. Spring Batch makes that possible through the `StepBuilder.allowStartIfComplete` parameter. You can also limit the number of times a step is restarted by using the `StepBuilder.startLimit` parameter.