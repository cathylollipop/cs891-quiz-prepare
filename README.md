# cs891-quiz-prepare

## Quiz 1

* Java 8 is a "hybrid" that combines the object-oriented & functional paradigms

	* Object-oriented programming is an "imperative" paradigm -> imperative programming focuses on describing how a program operates via statements that change its state

	* Functional programming is a "declarative" paradigm -> declarative programming focuses on "what" computations to perform, not "how" to compute them.

		* fluent interface: lines.stream().filter(line -> !omit.equals(line)).collect(toList()) -> cascading method calls. Extremely easy to make code parallelized.

* Java was originally an object-oriented programming language.

	* Java apps were organized in terms of structural elements such as classes, interfaces and packages.

* An object is an instance of a class that performs certain operations and interacts with other objects.
	
	* An object in Java resides in a memory location of a computer

	* It consists of

		* state - represented via data fields

		* behavior - represented via methods

	* Objects often correspond to real-world entites

* Many non-objecty oriented programming languages organized apps in terms of functional elements such as actions and logic. Object-oriented Java programs also perform actions and contain logic. However, these functional elements are not main focus in the object-oriented parts of java.

* Java supports key object-oriented concepts: 

	* Data & control abstractions

	* Inheritance

	* Polymorphism

* Abstractions:
	
	* data abstractions: data abstraction separates abstract properties of a data type from the concrete details of its implementation. Abstract properties (APIs) are the only thing that visible to the clients who want to use this data type. Changes in the underlying implementation should not affect client code.

	* control abstractions: if-else, switch, loops.

* Data abstration:
	
	* Java supports data abstraction via Abstract Data Types (ADTs), which define:

		* a set of data value(s)

		* operations on these value(s)

	* At the heart of data abstraction is encapsulation

		* hides ADT internal representation so apps can only access public operations

* Classes & Interfaces:
	
	* Java classes -> blueprint of objects, consists of fields (store state) and methods (define behaviors).

	* Java interfaces define a contract specifying methods that classes implementing the interface provide

	* Java interfaces provide a subset of the features provided by Java classes: Java <= 7 interfaces have no method implementations, only method signatures

	* interfaces cannot be instantiated, must be implemented by a class

	* class defines the interfaces methods and any necessary fields

* Java generics enabled passing ADTs as prameters when defining classes, interfaces and methods

	* Generics eleminate unnecessary code duplication

	* Ensure compile-time type safety when operating on different ADTs

* packages -> classes and interfaces can be grouped into packages, e.g. java.lang, java.util, java,io

* Java's garbage collector automatically reclaims & recycles memory that is not in use by a program

* Java exception handling separates "normal" app execution from "anomalous" app execution

* Inheritance in Java is specified via "extends" key word
	
	* it allows a subclass to inherit all non-private fields & methods from a super class

* All java classes inherit from the java.lang.Object super class:
	
	* defines methods that can be used by all non-primitive types

	* java.lang.Object defines .equals(): operator== returns true if two objects have the same memory address, .equals(), on the other hand, compares actual content of two objects

* Three purpose of subclass methods:

	* to augment the subclass API -- stack subclass inherits fields & methods from Vector super class --- for free!

	* to implement subclass methods -- stack implement push() method using addElement() method from Vector class

	* to override super class methods in subclass with same signatures -- to take advantage of polymorphism

* Polymorphism enables transparent customization of methods inherited from a super class

* Polymorphism & inheritance are essential to the "open/closed principle"
	
	* a class should be open for extension but closed for modification

	* the "open/closed principle" can be applied in conjunction with patterns to enable extensions without modifying existing classes or apps

	* subclasses defined in accordance with the open/closed principle can define their own custom behaviors that are more suitable for a particular use case while still resuing structure & functionality from super class

* Polymorphism in Java occurs when a reference to a super class is used to refer to an object of a subclass
	
	* subclass methods can override super class methods

* Polymorphism is implemented by the Java compiler & JVM

	* Dynamically dispatched methods correspond to an object's subclass, dynamic dispatching is also known as "virtual method invocation"

	* Each Java class typically has a virtual table (vtable) that contains addresses of dynamically dispatched methods

	* Each Java object contains a pointer to the vtable (vptr) of its class, the JVM uses the vptr to locate & dynamically dispatch a virtual method

	* Java also supports static method dispatching, where a method implementation is selected at compile-time: Java private, final, static methods

* JCF is a unified architecture for representing & manipulating collections
	
	* a collection is an object that represents a group of objects

	* Collections can be accessed & manipulated independently of their representation

* JCF benefits:
	
	* reduces programming effort: providing data structures & algorithms so developers don't need to write them

	* enable interoperability: gives a common way to pass collections

	* increase performance

	* reduce effort designing & learning new APIs

	* foster software reuse: providing standard interfaces for collections & algorithms that manipulate them

* iterate through collections:

	* for loop

	* for each loop

	* iterable

	* forEach() method