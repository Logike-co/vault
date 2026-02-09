[[Introducing Generics]]
Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces and methods. Much like the more familiar formal parameters used in method declarations, type parameters provide a way for you to re-use the same code with different inputs.

[[Type Inference]]
Type inference is a Java compiler's ability to look at each method invocation and corresponding declaration to determine the type argument (or arguments) that make the invocation applicable.

[[Wildcards]]
In generic code, the question mark (?), called the wildcard, represents an unknown type. The following section discuss wildcards in more detail, including upper bounded wildcards, lower bounded wildcards, and wildcard capture.

[[Type Erasure]]
Type erasure ensures that no new classes are created for parameterized types; consequently, generics incur no runtime overhead.

[[Restriction on Generics]]
Restrictions on using Generics.