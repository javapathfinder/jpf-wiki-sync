As of July 2018, we are migrating our build workflow to `Gradle`, and we will use it as our standard builder after merging the `Gradle` support to our main branch.
However, our existing `Ant` support is still available in the branch `java-8`.
In the following, we provide instructions for your, according to the builder you are using:

***
### Important
**Some Java releases (e.g., `jdk1.8.0_101`, `_102`, `_111`) do not include `sun.misc.JavaOISAccess`. This will cause compilation errors during the build execution. Consider building JPF with an updated Java version to avoid such errors.**
***

<details close>
<summary>Click here if you are using <b>Gradle</b>.</summary>

## Building JPF

### Using the command line

The JPF repository includes a Gradle wrapper that requires nothing except Java to execute. It ensures that all JPF developers and environments use the same builder to avoid any kind of configuration issue.

> If you are using Windows, consider the `gradlew.bat` script.

```{bash}
> cd jpf-core
> ./gradlew buildJars

...
BUILD SUCCESSFUL in 13s
16 actionable tasks: 16 executed
```

If you want to have some help about what build tasks are available, check the command `./gradlew tasks --all`.


### Within Eclipse

Eclipse comes with Gradle support by default since the Neon release. If you use an older version for some reason, consider installing the [Buildship Plugin](https://github.com/eclipse/buildship/blob/master/docs/user/Installation.md) for Gradle support.

To import the project into Eclipse, proceed with the following steps:

1. Start by generating Eclipse configuration files:

```{bash}
> ./gradlew eclipse

BUILD SUCCESSFUL in 0s
3 actionable tasks: 3 executed
```

2. Select **File > Import** on the drop-down menu
3. Select **Existing Gradle Project**
4. Choose the root project directory and click **Finish**

#### Handling "Access Restriction" errors in the workspace

After importing, you may face some *Access Restriction* errors. To get rid of them, proceed with the following steps:

1. In the **Package Explorer**, right-click on the project name and select **Properties** on the drop-down menu
2. Navigate to **Java Compiler > Errors/Warning** and expand **Deprecated and restricted API**
3. On **Forbidden Reference (access rules)**, select **Ignore** from the drop-down menu and click **Apply and Close**.
4. A pop-up may appear. Click ok to perform a full rebuild.

***
**We avoid adding IDE-related files on the repository as many of them are user-dependent and may change over different versions of the same IDE.**
***

### Within IntelliJ Idea

Importing `jpf-core` on IntelliJ should be straightforward due to its Gradle support.

1. Launch the **New Project** wizard. If no project is currently opened in IntelliJ IDEA, click **Import Project** on the welcome screen. Otherwise, select **File > New > Project** from **Existing Sources** from the main menu.
2. Choose the project root directory containing the build.gradle file. Click OK.
3. On the first page of the Import Project wizard, **in Import Project from External model, select Gradle** and click Next.
4. On the next page of the Import Project wizard, specify Gradle project settings:
  4.1. Check **Use auto-import**
  4.2. Check **Create separate module per source set
  4.3. Make sure that **Use default gradle wrapper (recommended)** is checked
5. Click Finish.

## Running JPF ##

### Using the command line ###

~~~~~~~~ {.bash}
> cd jpf-core
> java -jar build/RunJPF.jar src/examples/Racer.jpf
JavaPathfinder v5.0 - (C) 1999-2007 RIACS/NASA Ames Research Center
.....
====================================================== statistics
elapsed time:       0:00:00
states:             new=9, visited=1, backtracked=4, end=2
search:             maxDepth=5, constraints=0
choice generators:  thread=8, data=0
heap:               gc=8, new=291, free=32
instructions:       3112
max memory:         79MB
loaded code:        classes=73, methods=1010

====================================================== search finished: 1/12/10 2:30 PM
~~~~~~~~

</details>
<details close>
<summary>Click here if you are using <b>Ant</b> (<code>java-8</code> legacy branch).</summary>

## Building JPF ##

If you have cloned the project repositories you are interested in (which at least includes [jpf-core](../jpf-core/index)), you can build and test each of them by means of their included [Ant](http://ant.apache.org) `build.xml` scripts. Note that you have to install Ant and JUnit separately, e.g. following directions [here](../install/requirements).


### Using the command line ###

~~~~~~~~ {.bash}
> cd jpf-core
> ant test

... lots of output, at the end you should see something like:
BUILD SUCCESSFUL
Total time: 2 minutes 31 seconds
~~~~~~~~

### Within NetBeans ###

 1. run **File/Open Project..** from the application menu, entering the JPF project you just downloaded (e.g. "jpf-core")
 1. select the project that appears in our project pane (e.g. "jpf-core")
 1. run **Build** from the project context menu

### Within Eclipse ###

* Ensure that the `JAVA_HOME` environment variable points to the jdk1.6xxx directory. If it is empty or points to a JRE then errors such as **javac not found** maybe seen. If you do not want the system Java settings to point to jdk1.6xxx, you can also set project specific settings in eclipse.

* If you eclipse settings are set to **Build Automatically** then the project after being cloned will be built.

* To build a particular project in the Project menu select **Build Project**. All the dependencies for the project will be built automatically. 

#### Project Specific JDK settings within Eclipse ####
1. In Eclipse go to **Project** -> **Properties** 

2. Select **Builders**

3. Pick **Ant_Builder** -> click **Edit**

4. Click on the **JRE** tab

5. Select **Separate JRE** -> **Installed JREs**

6. On Windows and Unix-based systems pick JDK1.6xxx. If it is not listed under the installed JREs, click on **Add**, browse your file system to where JDK1.6xxx resides and select. On OSx systems pick the JVM 1.6.0. 


## Running JPF ##

### Using the command line ###


~~~~~~~~ {.bash}
> cd jpf-core
> java -jar build/RunJPF.jar src/examples/Racer.jpf
JavaPathfinder v5.0 - (C) 1999-2007 RIACS/NASA Ames Research Center
.....
====================================================== statistics
elapsed time:       0:00:00
states:             new=9, visited=1, backtracked=4, end=2
search:             maxDepth=5, constraints=0
choice generators:  thread=8, data=0
heap:               gc=8, new=291, free=32
instructions:       3112
max memory:         79MB
loaded code:        classes=73, methods=1010

====================================================== search finished: 1/12/10 2:30 PM
~~~~~~~~

### Using eclipse plugin ###

 1. Right click on a .jpf file. Examples can be found in the src\examples directory in jpf-core
 1. If the eclipse plugin is correctly installed, a Verify option will appear. 
 1. Select the Verify option and the verification process of the system specified in the .jpf file begins

Note that the Application.jpf file essentially replaces previous uses of eclipse launch configurations. The required element of a .jpf file is the `target=MAIN_CLASS` where `MAIN_CLASS` is the class containing main method of the system under test. Any other configurations that need to be specified can be added here. for example `listener=gov.nasa.jpf.tools.SearchMonitor`.   

Specify `classpath=PATH_TO_BIN_DIRECTORY` to add the class files for the program under test to JPF's class path.  Windows users will need to use the double-backslash notation in specifying paths in the .jpf file.  An example .jpf file for the Windows platform is included below for convenience:

~~~~~~~~ {.bash}
target=mutex.DekkerTestMain
report.console.property_violation=error,trace,snapshot
listener=gov.nasa.jpf.listener.EndlessLoopDetector
classpath=C:\\Users\\fred\\Documents\\ch02-mutex\\bin
sourcepath=C:\\Users\\fred\\Documents\\ch02-mutex\\src,C:\\Users\\Fred\\Documents\\ch02-mutex\\src-test
~~~~~~~~

The .jpf file not only indicates the `target` and `classpath`, but it also turns on error reporting with trace generation (`report.console.property_violation`) and configures the source path (`sourcepath`).  Note that multiple source directories are specified using the comma separator.

### Using eclipse Run Configuration ###

 1. Select a .jpf file by clicking on it in the Package Explorer
 1. Click **Run** -> **Run Configurations** -> **run-JPF-core**. It is important the correct .jpf file is selected when the configuration is run. 

#### Windows users ####
After a fresh install of jpf-core you may see the following when trying to use the Eclipse Run-jpf-core configuration:

~~~~~~~~
java.lang.NoClassDefFoundError: gov/nasa/jpf/Main
Caused by: java.lang.ClassNotFoundException: gov.nasa.jpf.Main
    at java.net.URLClassLoader$1.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
Exception in thread "main" 
~~~~~~~~

In this particular case, the error was generated after the initial build after the clone had completed.  To resolve the issue, **refresh the Eclipse workspace** (F5 or right click Refresh).  After the refresh, the Run-jpf-core configuration should work as described above.

</details>