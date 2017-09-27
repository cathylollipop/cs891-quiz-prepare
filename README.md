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

## Quiz 2

* Functional programming has its roots in lambda calculus: 

	* Computations are treated as the evaluation of mathematical functions. The output of one function serves as the input to the next function.

	* Changing state & mutable data are discouraged/avoided. Instead, the focus is on "immutable" objects, i.e., objects whose state cannot change after they are constructed.

* In contrast, object-oriented programming employs "hierarchical data abstraction":

	* Components are based on stable class roles & relationships extensible via inheritance & dynamic binding, rather than by functions that correspond to algorithmic actions.

	* State is encapsulated by methods that perform imperative statements. This state is often mutable.

* Java 8's functional features help close the gap between a program's "domain intent" & its computations:

	* Domain intent defines "what"

	* Computations define "how"

* Java 8's object-oriented features help to structure a program's software architecture

	* Common classes provide a reusable foundation for extensibility

	* Subclasses entend the common classes to create various custom solutions

	* Java 8's FP features are most effective when used to simplify computations within the context of an OO software architecture, especially concurrent & parallel computations

* A lambda expression is an unnamed block of code (with optional parameters) that can be stored, passed around, & executed later.

* A method reference is a compact, easy-to-read handle for a method that already has a name:

	* reference to a static method: ContainingClass::stacticMethodName

	* reference to an instance method of a particular object: containingObject::instanceMethodName

	* reference to an instance method of an arbitrary object of an given type: ContainingType::methodName

	* reference to a constructor: ClassName::new

* A functional interface contains only one abstract method

* A functional interface is the type used for a parameter when a lambda expression or method reference is passed as an argument.

* A predicate performs a test that returns true or false:

```
public interface Predicate<T> { boolean test(T t); }
```

* A function applies a computation on 1 parameter & returns a result:

```
public interface Function<T, R> { R apply(T t); }
```

* A BiFunction applies a computation on 3 parameters & returns a result:

```
public interface BiFunction<T, U, R> { R apply(T t, U u); }
```

* A Consumer accepts a parameter & returns no results:

```
public interface Consumer<T> { void accept(T t); }
```

* A Supplier returns a value & takes no parameters:

```
public interface Supplier<T> { T get(); }
```

* A constructor reference is also a Supplier.

* A functional interface my also have default methods or static methods.

* "embarrassingly parallel" -- there are no data dependencies between worker threads

* Concurrency is a form of computing where threads can run simultaneously

	* Concurrency often used to offload work from main thread to background threads

	* Java threads interact with each other via shared objects and/or message passing

	* Key goal is to share resources safely & efficiently to avoid race conditions

* Parallelism is a form of computing that partitions tasks into sub-tasks that can run independently & whose partial results are combined
	
	* key goal is to efficiently -- partition tasks into sub-tasks & combine results

	* Parallelism works best when there's no shared mutable state between threads

* Foundational concurrency support:

	* Focus on basic multi-threading & synchronization primitives

	* Efficient, but low-level & very limited in capabilities

* Advanced concurrency support:

	* Focus on course-grained "task parallelism" whose computations can run concurrently

	* Feature-rich & optimized, but also tedious & error-prone to program

* Foundational parallelism support:
	
	* Focus on data parallelism that runs the same task on different data elements

	* Powerful & scalable, but tricky to program correctly

* Advanced parallelism support:

	* Focus on functional programming for data parallelism & asynchrony

	* Strikes an effective balance between productivity & performance

* Concurrency is about correctly and efficiently controlling access to shared resources

* Parallelism is about using additional resources to produce an answer faster

* Java 8 streams are an addition to the Java library that provide programs with several key benefits:

	* Manipulate flows of data in a declarative way

	* Enable transparent parallelization without the need to write any multi-threaded code

* A stream is a pipeline of aggregate operations that process a sequence of elements. A stream is created via a factory method

* An aggregate operation performs a behavior on each element in a stream

	* Ideally, a behavior's output in a stream depends only on its input arguments

	* Behaviors with side-effects likely incurrace conditions in parallel streams

* Streams enhance flexibility by forming a "processing pipeline" that chains multiple aggregate operations together

* A stream holds no non-transient storage

* Every stream works very similarly:

	* Starts with a source of data

	* Processes the data through a pipeline of intermediate operations

	* Finishes with a terminal operation that yields a non-stream result, e.g.

		* no value at all

		* a collection

		* a primitive value

* Each aggregate operation in a stream runs its behavior sequentially by default. A Java 8 parallel stream splits its elements into multiple chunks & uses a common fork-join pool to process the chunks independently

* An aggregate operation processes all elements in a stream:

	* map: applies the given function to the elements of the input stream & returns an output stream consisting of the results. (May change the type of the stream)

	* filter: Tests the given predicate against each element of the input stream & returns an output stream consisting only of the elements that match the predicate. (May reduce the number of elements in Stream)

	* collect: A terminal operation that uses a collector to perform a reduction on the elements of its input stream & returns the results of the reduction.

* Terminal operation will trigger intermediate operation processing.

* A spliterator is a new type of "splittable iterator" in Java 8
	
	* It can be used to traverse elements of a source

	* It can also partition all elements of a source

		* Mostly used with Java 8 parallel streams

* Collector defines an interface whose implementations can accumulate input elements in a mutable result container

* The Collector interface defines three generic types:

	* T - The type of objects available, e.g., Integer

	* A - The type of a mutable accumulator object for collection, e.g., ArrayList<T>

	* R - The type of a final result, e.g., ArrayList<T>

* The Collector interface has five methods:
	
	* supplier() - returns a Supplier instance that generates an empty accumulator, e.g., `return ArrayList::new`

	* accumulator() - returns a function that adds a new element to an existing accumulator, e.g., `return ArrayList::add`

	* combiner() - returns a function that merges two accumulators together, e.g., `return (List<T> one, List<T> another) -> { one.addAll(another); return one;};`

	* finisher() - returns a function that converts an accumulator to final result type, e.g., `return Function.identity()`

	* charactersitics() - provides a stream with additional information used for internal optimizations, e.g., UNORDERED, INDENTIFY_FINISH, CONCURRENT

## Quiz 3

* Pros of SearchWithSequentialStreams:
	
	* Streams use "internal" iterators versus "external" iterators used by collections

	* pipeline is declarative since it's a series of transformations performed by aggregate operations

	* focus on "what" operations to perform, rather than on "how" they're implemented

	* lambda functions without side-effects make it easier to reson about behavior & enables optimization

* Cons of SearchWithSequentialStreams

	* slower than using sequential loops (add overthead)

* Common factory methods for creating streams

	* from a java collection: Collection.stream() / parallelStream()

		* a call to parallel() can appear anywhere in a stream & will have same effect as parallelStream()

	* from an array: Arrays.stream(arr)

	* from a static factory method: Stream.of(arr)

	* (sequential only)Stream.iterate(new BigIntegerp[] {BigInteger.ONE, BigInteger.ONE}, f -> new BigInteger[]{f[1], f[0].add(f[i])}).map(f -> f[0]).limit(100).forEach(...)

	* BufferedReader.lines() obtains lines of a file

	* Files.lines()

	* Random.ints(0,100).limit(50).forEach(...)

	* Stream.generate(TreeMap<Long, String>::new).limit(100).collect(toList());

* Advantages of internal iterators over external iterators:
	
	* improved code readability

	* transparent optimizations

	* fewer bugs

* Advantages of external iterators over internal iterators:

	* More control over iteration steps

	* Multiple active iterators

* A Java 8 stream is an implementation of the POSA1 pipes & filter pattern -> divide an app's tasks into multiple self-contained data processing steps & connect these steps via intermediate data buffers to form a data processing pipeline

* other common implementations of pipes & filters: 
	
	* a pipeline in UNIX command-line shells

	* System V STREAMS

* Java I/O streams are different from Java 8 streams

* collection vs. streams:
	
	* a collection is an in-memory data structure that can store, retrieve, & manipulate groups of elements

	* a stream is a fixed data structure that processes elements on-demand

	* various factory methods can convert collections to streams & vice versa

* Java 8 adds two new concurrency & parallelism frameworks related to functional programming

	* parallel streams:

		* partitions a stream into multiple substreams that run independently & combine into a "reduced" result

		* chunks of data in the substreams can be mapped to multiple threads(&cores)

	* completable futures

		* supports dependent actions that trigger upon completion of async operations

		* Async operations can run concurrently in thread pools

	* these frameworks often eliminate the use of synchronization or explicit threading when developing concurrent/parallel apps!

	* both fameworks use the fork-join pool framework by default

		* employs work-stealing to accelerate performance on multi-core processors

* A java 8 parallel stream splits its elements into multiple chuncks & uses a thread pool to process these chunks independently
	
	* this splitting & thread pool are often invisible to programmers

	* the order in which chunks are processed is likely non-deterministic, i.e., programmers often have little/no control over how chunks are processed

	* the results of the processing are likely deterministic

	* when a stream executes sequentially all of its aggregate operations run in a single thread

	* when a stream executes in parallel, it is partitioned into multiple substream "chunks" that run in a common fork-join pool

	* the same aggregate operations can be used for sequential & parallel streams

		* Java 8 streams can thus treat parallelism as an optimization & leverage all available cores!

		* Naturally, behaviors run by thes aggregate operations must be designed carefully to avoid accessing unsynchronized shared state..

* A Java 8 parallel stream implements a "map/reduce" variant optimized for multi-core processors

	* It's actually more like the "split-apply-combine" data anlysis strategy.

* Splite-apply-combine workflow:
	
	* split - recursively partition a data source into independent "chunks"

		* spliterators are defined to partition collections in Java 8

		* you can also define custom spliterators

		* parallel streams perform better on data sources that can be split efficiently & evenly

	* apply - process chunks independently in a pool of threads

		* programmer have some control over how many threads are in the pool

	* combine - join partial results into a single result

		* performed by terminal operations like collect() & reduce()

* Java 8 parallel streams framework assumes behaviors don't incur race conditions, parallel streams should therefore avoid operations with side-effects, e.g.:
	
	* stateful lambda expressions

	* interference w/the data source

* Java 8 lambda expressions & method references containing no shared state are useful for parallel streams since they needn't be explicitly synchronized

* a parallel program always does more work than a non-parallel program
	
	* it needs to partition the problem

	* it needs to perform processing

	* it needs to combine the results

* Java 8 parallel streams are thus useful in some (but not all) conditions, e.g.,
	
	* when behaviors have certain properties:

		* independent

		* computationally expensive

		* applied to many elements of data sources

		* if there are multiple cores

	* the "NQ" model: N is the # of data items to process per thread, Q quantifies how CPU-intensive the processing is.

* when not to use Java 8 parallel streams:
	
	* the source is expensive to split or splits unevenly

	* the startup cost of parallelism overwhelm the amount of data

	* combining partial results is costly

	* a Java 8 feature doesn't enable sufficient exploitable parallelism

	* there aren't many/any cores