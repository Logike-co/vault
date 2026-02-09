
+ formato codigo fuente editor es .drn

Bootstrap the project:
+ Despues de generar un proyecto por spring initalizr
1. Select the following options:
    
    - Project: Maven
    - Language: Java
    - Spring Boot: The latest 3.0.X version
2. Enter the following values next to the corresponding Project Metadata fields:
    
    - Group: `example`
    - Artifact: `billing-job`
    - Name: `Billing Job`
    - Description: `Billing job for Spring Cellular`
    - Package name: `example.billingjob`
    - Packaging: `Jar`
    - Java: `17`
    
![[Pasted image 20240521053755.png]]
The project is structured as follows:

- `src/main/java/example/billingjob/BillingJobApplication.java`: The main class of the Spring Boot application. It contains the `main` method and has the `@SpringBootApplication` annotation.
- `src/test/java/example/billingjob/BillingJobApplicationTests.java`: This class contains the tests of our application.
- `src/main/resources/application.properties`: Contains the configuration properties of the application. It is empty for the moment.

+ TODO: debe existir un drakon initalizr, el cual debe estar a la raiz del scr, puede ser drn con la misma estructura del sistema, para que sea una imagen del src.
+ ? clase por diagrama ?
+ ? los archivos de configuracion como pom.xml y properties, como se diagramarian ?

+ Una vez se cree la estructura de las clases basicas, se puede añadir opcion crear arquitectura limpia hexagonal. asi se añaden clases de java y drakon.

* el IDE puede ser un plugin a intelliJ para que sea añadido 
*  puede ser un aplicativo vaadin
* ? para la parte grafica como se deberia diseñar en drakon UI?


