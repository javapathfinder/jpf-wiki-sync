# Project Ideas

Please note that this list is not exclusive. If you have other ideas and topics related to JPF, please let us know on \<jpf.gsoc [at] gmail.com\> or the [JPF Google group](https://groups.google.com/forum/#!forum/java-pathfinder).

### JPF Infrastructure

* [Automatic Delegation of Method Calls in JPF](#automatic-delegation-of-method-calls-in-jpf) <Nastaran>

* [Visualization of Execution Traces](#visualization-of-execution-traces) <Franck>
 
* [Dynamic State Matching](#dynamic-state-matching) <Pavel>

* [Extending JPF Inspector](#extending-jpf-inspector) <Pavel>


### JPF Application Domains

* [Model Checking Distributed Java Applications](#model-checking-distributed-java-applications) <Nastaran>

* [Model Checking Distributed Applications With Blocking Sockets](#model-checking-distributed-applications-with-blocking-sockets) <Nastaran>

* [Verification of Multi Agent Systems](#verification-of-multi-agent-systems) <Franco><Neha> 

* [Verification of Actor-based Systems](#verification-of-actor-based-systems) <Nastaran>


### Symbolic Execution

* [Improving JDart](#improving-jdart) <Kasper>

* [Handling Native Calls in the Context of Symbolic Execution](#handling-native-calls-in-the-context-of-symbolic-execution) <Corina><Nastaran>

* [Probabilistic Programming Environment](#probabilistic-programming-environment) <Willem> 

* [Fingerprinting for Programs](#fingerprinting-for-programs) <Willem>

* [Probabilistic Symbolic Program Repair](#probabilistic-symbolic-program-repair) <Willem>

* [Heap Generation for Automatic Test](#heap-generation-for-automatic-test) <Eric><Neha><Oksana>

### Concolic Execution

* [Concolic Execution for Android Apps](#concolic-execution-for-android-apps) <Kasper>

### JPF Extensions and External Systems Interfacing

* [Evaluating jpf-psyco](#evaluating-jpf-psyco) <Kasper>

* [PSYCO for Reactive Systems](#psyco-for-reactive-systems) <Falk><Teme>

* [Improving the jpf-reliability Extension](#improving-the-jpf-reliability-extension) <Kasper><Corina>

### Environment and Test Case Generation

* [Environment and Test Case Generation for Specific Domains](#environment-generation-for-specific-domains) <Oksana>

* [Environment and Test Case Generation for Symbolic Execution](#environment-generation-for-symbolic-execution) <Oksana>


### Projects Descriptions

#### Automatic Delegation of Method Calls in JPF
[jpf-nhandler](https://bitbucket.org/nastaran/jpf-nhandler) is a JPF extension that provides automatic, on-demand delegation of calls in JPF. It allows for executing some parts of code directly on the host JVM. One of its main components is a translator that converts classes and objects between the JPF and JVM environments. More detailes about the tool can be found in this [paper](http://dl.acm.org/citation.cfm?id=2632363).

The goal of this project is to improve the tool functionalities in various ways: 

* Adding a functionality that allows for creating native peer methods (which execute on the host JVM) with nondeterministic return values. 
* Avoiding a call from being delegated more than once - this can be achieved via a cache layer that records the effects of a delegated method call. If JPF encounters the same call later, the cached effects is reflected in JPF. 
* Providing a lazy update strategy - the jpf-nhandler converter has a map which associates JPF objects to their JVM representations created by the converter. By default, this maps is cleared after a native call is handled. jpf-nhandler can be configured to not clear the map to avoid recreating JVM objects. However, in this setting, if JPF modifies an object that is stored in the map, the JPF object and its JVM counterpart may get out of sync. This discrepancy can be addressed using a lazy update strategy.

#### Visualization of Execution Traces
JPF is able to find notorious concurrency bugs such as deadlocks. Although finding bugs is one of the major strengths of JPF, providing feedback to the programmer is one of its main weaknesses. For example, for a deadlock JPF provides the programmer at which line each thread is stuck. Although this is of some use, what is much more valuable is to report how each thread got to that point.

A few extensions to JPF have recently been developed to provide some functionality to trace the executions of the threads. In this project, we will develop an  extension of JPF to trace the execution of the threads and to provide feedback to the programmer.

#### Dynamic State Matching 
Design and implement user-friendly support (API) for dynamically changing what elements of the program state are considered for state matching. Use existing concepts of JPF API (listeners, annotations, dynamic serializer) when possible. Customize the state storage mechanism of JPF.
It will be used to dynamically select elements of the concrete program state that will be ignored in state matching at the end of a given transition, or, more generally, to construct abstractions of the program state on-the-fly during the state space traversal.
An additional goal is to implement support for dynamically defining custom elements of the program state (abstract values, a set of predicates with truth values) that will be also considered in state matching.
It should be possible to turn on/off such custom elements of the program state dynamically.

#### Extending JPF Inspector
[JPF Inspector](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-inspector) is a tool for inspection and control of JPF execution that works like a debugger. This project aims to make the codebase up-to-date with the current version of JPF core which is compatible with Java 8, do some refactoring, and implement new features. The list of features that would be really useful includes command-line interface (batch processing) and support for symbolic values (printing, breakpoints). Another goal would be to improve extensibility of the tool.

#### Model Checking Distributed Java Applications
The techniques used to model check distributed Java applications can be divided into two main categories: 

1. The centralization approach - the entire distributed application is captured within a single process, and the model checker is able to verify all the communicating processes. 

2. The cache-based approach - the model checker verifies only one process, and the rest of the processes run outside of the model checker. A cache layer is used to keep the external processes in synchronization with the process under test. 

The extensions, [jpf-nas](http://babelfish.arc.nasa.gov/hg/jpf/jpf-nas) and [net-iocache](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/net-iocache), allow for verifying distributed systems. jpf-nas is based on the centralization technique, and net-iocache applies the cache-based technique. The goal of this project is to integrate jpf-nas with net-iocache to obtain a tool that combines centralization with the cache-based technique. That is, it centralizes some processes of the distributed application under test within the model checker while the rest of the processes are running outside of the model checker.

#### Model Checking Distributed Applications With Blocking Sockets
[jpf-nas](http://babelfish.arc.nasa.gov/hg/jpf/jpf-nas) is an extension of JPF that provides support for model checking distributed multithreaded Java applications. It relies on the multiprocess support included in the [JPF core](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-core) which provides basic functionality to verify the bytecode of distributed applications. jpf-nas supports interprocess communication via TCP sockets by modeling the Java networking package java.net. This tool can handle simple multi-client server applications. Some examples can be found in the jpf-nas distribution (at jpf-nas/src/examples/). The goal of this project is to extend the communication model supported by the tool towards an existing open source Java library/framework used to create multi-client server applications, such as [NanoHttpd](https://github.com/NanoHttpd/nanohttpd) and [QuickServer](http://www.quickserver.org/).

#### Verification of Multi Agent Systems
The goal of this project is to develop techniques that analyze key properties in multi-agent systems. The [jpf-mas](http://dl.acm.org/citation.cfm?id=2485058) extension will initially provide the ability to generate the reachable state space of Brahms models. The reachable state space can then be encoded into input for a variety of model checkers such as SPIN, NuSMV and PRISM, thereby enabling the verification of LTL, CTL and PCTL properties. The project will also need to investigate how to generate the set of reachable states for other kinds of models, such as Jason models, and how to compose reachable states of different modelling languages both at run-time and off-line.

#### Verification of Actor-based Systems
The goal of this project is verifying actor-based systems using the model checking technique. This can be achieved through extending the [jpf-actor](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-actor) extension of JPF. jpf-actor is a framework that can be used to systematically test actor programs that compile to bytecode. It requires making the codebase of jpf-actor up-to-date with the current version of [jpf-core](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-core) which is compatible with Java 8. It also includes extending the project towards an actor-based Scala library, called [Akka](http://akka.io).

#### Improving JDart
[JDart](https://github.com/psycopaths/jdart) is an open-source, dynamic symbolic analysis framework built on Java PathFinder. It has been applied to industrial scale software, including complex NASA systems. We have many ideas for improving JDart and welcome additional ideas too:

1. Integrate ways of generating more informative reports of the analysis results. For example, the constraints tree resulting from the analysis can be visualized (possibly interactively), which would be very helpful for program comprehension and debugging. 
2. Add more exploration strategies to JDart. In particular, new exploration heuristics could be interesting, e.g., for targeted concolic execution. It could also combine other static analyses, such as, program slicing, where the computed slice can be used to constrain the exploration. 
3. [JConstraints](https://github.com/psycopaths/jconstraints) is a solver abstraction layer used by JDart to interact transparently with SMT solvers. JConstraints has support for some solvers, e.g., Z3 and SMTinterpol. Often, however, one needs to select a solver that is best suited for the constraints generated (e.g., linear, non-linear). It could be very useful adding additional solvers to JDart based on JConstraints and evaluate them to understand better their applicability. This could also comprise adding a general interface to solvers that support the SMTLib format.
4. JDart supports various (fixed-size) symbolic data structures, e.g., arrays and HashMap. It would be interesting to improve this, in particular with symbolic array indexes and support for unbounded data structures possibly with Lazy Initialization.

#### Handling Native Calls in the Context of Symbolic Execution
The goal of this project is to handle native calls in the context of symbolic execution by generating native peers and associating them with native methods on-the-fly. For the native peers we need concrete values to be used as input parameters for automatically generated native peers methods. The idea is to first solve the constraints obtained with symbolic execution and use those solutions as input parameters. This can be accomplished by enhancing [jpf-symbc](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-symbc) to use the [jpf-nhandler](https://bitbucket.org/nastaran/jpf-nhandler) extension of JPF.

#### Probabilistic Programming Environment

The goal of the project is to build a simple probabilistic programming language with an execution environment. For a quick intro to Probabilistic Programming see [here](http://adriansampson.net/notes/5d3mpq5r6ab0/). An example of a probabilistic programming environment can be also found [here](http://webppl.org/). The novelty of this project lies in that we will combine sampling approaches with precise model counting (where it is applicable) to do the probabilistic inference; current systems only use sampling. We will build the system on top of the [Symbolic PathFinder (SPF)](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-symbc) tool suite where all the model counting facilities already exist. The base language for the system will be Java and a small prototype already exist that just need to be extended.

#### Fingerprinting for Programs

The goal of this project is to build a system that given a piece of code can build a fingerprint for the code that can be compared to other programs. One possible application is plagiarism detection or clone detection. We will constraint ourselves to Java code that can be symbolically executed by the [Symbolic Pathfinder (SPF)](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-symbc) tool and where constraints can be handled by [Green](https://github.com/green-solver/green-solver). The approach will rely on extracting conditions for output and to then compare these against others. The conditions we will use are path conditions from executing the code symbolically with SPF and we will use Green to put the conditions into a canonical form etc.

#### Probabilistic Symbolic Program Repair

The goal of this project is to do program repair where the repairs are picked according to how well they fix the program. Mostly program repair research has focussed on fixing the program just so that it passes the tests that are currently failing, we would instead look at how close the fixed program can get to an oracle program. The context would be cases where we have the oracle, for example in coding contents such as CodeHunt or online courses.  The notion of distance will be using percentage of inputs that give the correct results and the fixes we will consider are simple syntactic changes. We will use [Symbolic PathFinder (SPF)](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-symbc) for the symbolic execution and [Green](https://github.com/green-solver/green-solver) for model counting to allow us to determine the number of inputs that flow down each path in the code. More details on Probabilistic Symbolic Execution can be found in the following two papers:

* [Probabilistic symbolic execution](http://dl.acm.org/citation.cfm?doid=2338965.2336773)
* [Statistical symbolic execution with informed sampling](http://dl.acm.org/citation.cfm?doid=2635868.2635899)

#### Heap Generation for Automatic Test

This project looks to use a fully symbolic heap to follow specific paths in a unit under test and at the end of the path create a concrete heap for that path. The concrete heap is created by automatically generating a sequence of API calls on the various objects in the heap to create the same structure as the symbolic heap that followed the specific path. The interested student will have a background in automatic test generation, symbolic heaps (including generalized symbolic execution), and a strong foundation in SMT solvers. The primary thrust of the project focusses on creating a generalized heap solver tool that includes the ability to reconstruct heap structures using public interfaces on objects (i.e., finding the correct sequence of public method calls and constructors to create a specific heap structure). Should be lots of fun with many challenges.

#### Concolic Execution for Android Apps
[JDart](https://github.com/psycopaths/jdart) is an open-source, dynamic symbolic analysis framework built on Java PathFinder. It has been applied to industrial scale software, including complex NASA systems. This project seeks to extend this capability to Android applications by supporting the Dalvik instruction set, e.g., by using [jpf-pathdroid](http://babelfish.arc.nasa.gov/hg/jpf/jpf-pathdroid).

#### Evaluating jpf-psyco
[jpf-psyco](https://github.com/psycopaths/psyco) is an open-source tool built on JPF for generating temporal component interfaces. A temporal interface is expressed as a finite-state automaton over the public methods of the component and captures safe ordering relationships of method invocations. jpf-psyco relies on a combination of symbolic execution and automata learning for generating interfaces. This project seeks to evaluate jpf-psyco with new examples (e.g. reactive systems) and experimenting with other learning algorithms.

#### PSYCO for Reactive Systems
PSYCO is a JPF extension, [jpf-psyco](https://github.com/psycopaths/psyco), that generates interfaces of reactive components. The current version of PSYCO combines active automata learning and dynamic symbolic execution to achieve this goal. Since it is based on active automata learning, PSYCO cannot decide termination in many cases and runs to the exhaustion of a manually set time limit.

The goal of the project is to add a new analysis to PSYCO that can extends PSYCO to (a) decide termination in more cases, and (b) enables PSYCO to check properties on reactive components. 

The main idea is to use the symbolic summary of a component (this is 
already computed in PSYCO by dynamic symbolic execution) as a basis 
for symbolic search, i.e., unrolling the transition system of the component
to some finite depth. There are multiple ways of doing this that allow for 
deciding when your exploration reaches a fixed-point: This can be done 
using term rewriting and quantifier elimination or OBDDs. 

#### Improving the jpf-reliability Extension
[jpf-reliability]( http://dl.acm.org/citation.cfm?id=2643011) is a probabilistic software analysis tool for programs with probabilistic and nondeterministic behavior. It synthesizes schedulers, i.e. resolutions of nondeterminism, that maximizes (or conversely minimizes) the probability of a property being satisfied. It features various algorithms for sampling execution paths. Sampling is highly parallelizable, and this project seeks to design and implement a distributed infrastructure that fits into the framework of jpf-reliability. Other improvements can also be experimented with, e.g., state pruning algorithms and other algorithms for sampling paths.

#### Environment Generation for Specific Domains
When model checking applications belonging to specific domains (e.g., Swing, Android), 
JPF users have to provide application environment, consisting of test drivers and models 
for libraries that are too complex for JPF to run. The goal of this project is to evaluate the
existing (or provide new) semi-automated support for generation of test drivers and library 
models/stubs based on the results of domain-specific static analysis, specifications, run-time 
information, or other suitable techniques. Once generated, such drivers and stubs can 
be used to verify applications belonging to specific domains using appropriate jpf 
extensions (e.g., [jpf-awt](http://babelfish.arc.nasa.gov/trac/jpf/wiki/projects/jpf-awt), [jpf-android](https://bitbucket.org/heila/jpf-android)). The project can be implemented on top of 
[OCSEGen](http://ti.arc.nasa.gov/publications/8752/download) or another suitable tool.

#### Environment Generation for Symbolic Execution
When using Symbolic PathFinder (SPF), one needs to supply application environment, consisting of 
test drivers and models/stubs for libraries that are too complex for SPF to handle.
The goal of this project is to evaluate the existing (or provide new) semi-automated support 
for generation of test drivers and library  models/stubs, containing symbolic values, based on 
the results of domain-specific static analysis, specifications, run-time information, or other 
suitable techniques. Once generated, such drivers and stubs can be used to verify applications 
using SPF. The project can be implemented on top of [OCSEGen](http://ti.arc.nasa.gov/publications/8752/download) or another suitable tool.






