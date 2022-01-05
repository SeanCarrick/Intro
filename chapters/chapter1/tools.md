# Tools
This chapter *should be* short and sweet, because I'm just going to talk briefly about the tools that ship with the Java JDK. The way we are going to look at these tools is one-by-one, in alphabetic order (the same as they show up in your JDK installation directory's `bin` directory):

| Tool | Name and Purpose/Use |
| :--: | :---------- |
| `jaotc` | a java static compiler which **produces native code for compiled java methods**. It uses Graal as the code-generating backend and `libelf` for generating `.so` AOT library. The tool is part of java installation and can be used the same way as `javac`. |
| `jar` | A JAR (Java ARchive) is a package file format typically used to **aggregate many Java class files and associated metadata and resources (text, images, etc.) into on file to distribute application software or libraries on the Java Platform**. |
| `jarsigner` | The `jarsigner` tool has two purposes: **To sign Java ARchive (JAR) files**. To verify the signatures and integrity of signed JAR files. |
| `java` | This is the program that launches the Java Virtual Machine (JVM) and executes the main method in the main class of a Java program. It interprets the compiled byte code into the machine language for the platform on which it is executed. |
| `javac` | Reads source files that contain module, package, and type declarations written in the Java programming language, and compiles them into class files that run on the JVM. The `javac` command can also process annotations in java source files and classes. |
| `javadoc` | Used for **generating API documentation in HTML format from JavaDoc comments**  in source code files. |
| `javap` | Tool used to **get the information of any class or interface**. The `javap` command (also known as the *Java Disassembler*) desassembles one or more class files. |
| `jcmd` | A utility used to **send diagnostic command requests to the JVM**, where these requests are useful for controlling *Java Flight Recordings*, troubleshoot, and diagnose JVM and Java applications. |
| `jconsole` | A JMX-compliant graphical tool **for monitoring a JVM**. It can monitor both local and remote JVMs. It can also monitor and manage an application. |
| `jdb` | The Java Debugger (JDB) is a **tool for Java classes to debug a program at the command line**. It implements the *Java Platform Debugger Architecture*. It helps in detecting and fixing bugs in a Java program using the *Java Debug Interface* (JDI). |
| `jdeprscan` | This tool is a **static analysis tool** provided by the JDK that scans a JAR file or some other aggregation of class files for uses of deprecated API elements. |
| `jdeps` | A Java Class Dependency Analyzer tool, which is a command line tool **to show the package-level or class-level dependencies of given Java class files**. |
| `jfr` | *Java Flight Recorder* (JFR) is a **tool for collecting diagnostic and profiling data about a running Java application**. It is integrated into the JVM and causes almost no performance overhead, so it can be used even in heavily loaded production environments. |
| `jhsdb` | A tool used to **attach to a Java process or to launch a postmortem debugger to analyze the content of a core dump from a crashed JVM**. |
| `jimage` | This is a special file format used to **store class and resource files of multiple Java modules to support custom Java Runtime Environment** (JRE). One and only one JIMAGE file is used for each JRE to store all built-in Java modules. |
| `jinfo` | Used to **generate Java configuration information for a specified Java process**.| 
| `jjs` | Stands for *Java JavaScript*. The command can be used to **run scripts in files or scripts entered on the command line** in interactive mode. It can also be used to execute shell scripts. |
| `jlink` | A tool that **generates a custom Java runtime image** that contains only the platform modules that are required for a given application. Such a runtime image acts exactly like the JRE, but contains only the modules we picked and the dependencies they need to function. |
| `jmap` | A command line utility that is included in Linux:registered: (but not Windows:registered:) releases of the JDK. This utility **prints memory-related statistics for a running JVM or core file**. If `jmap` is used without any command line options, then it prints the list of shared objects loaded. |
| `jmod` | A tool that is intended for **modules that have native libraries or other configuration files** or for modules that you intend to link, with the `jlink` too, to a runtime image. The JMOD file format lets you aggregate files other than `.class` files, metadata, and resources. |
| `jps` | Lists the **instrumental HotSpot JVMs** on the target system. The tool is limited to reporting information on JVMs for which it has the access permissions. |
| `jrunscript` | Used to **run a command line script shell that supports interactive and batch modes**. |
| `jshell` | An **interactive tool for learning the Java programming language and prototyping Java code**. JShell is a Read-Evaluate-Print-Loop (REPL), which evaluates declarations, statements, and expressions as they are entered and immediately shows the results. |
| `jstack` | This command **prints Java stack traces of Java threads for a specified Java process**. For each Java frame, the full class name, method name, byte code index (BCI), and line number, when available, are printed. C++ mangled names aren't demangled. |
| `jstat` | Uses the built-in instrumentation in the Java HotSpot VM **to provide information about performance and resource consumption of running applications**. The tool can be used when diagnosing performance issues, and in particular issues related to heap sizing and garbage collection. |
| `jstatd` | This is an RMI server application that **monitors for the creation and termination of instrumented Java HotSpot VMs** and provides an interface to enable remote monitoring tools to attach to JVMs that are running on the local host. |
| `keytool` | A key and certificate management utility. It **allows users to administer their own public/private key pairs and associated certificates for use in self-authentication** (where the user authenticates him/herself to other users/services) or data integrity and authentication services, using digital signatures. |
| `pack200` | A Java application that **transforms a JAR file into a compressed pack200 file** using the Java gzip compressor. The pack200 files are highly compressed files that can be directly deployed, saving bandwidth and reducing download time. |
| `rmic` | Compiler used **to generate stub and skeleton class files** using the **Java Remote Method Protocol** (JRMP) and stub and tie class files (IIOP protocol) for remote objects. The `rmic` compiler generates *Object Management Group* (OMG) Interface Definition Language (IDL). |
| `rmid` | Used **to start the activation system daemon that enables objects to be registered and activated in a JVM**. |
| `rmiregistry` | Used to **get a registry operating on the local host or local host and port**. |
| `serialver` | Used to **return the `serialVersionUID` for one or more classes in a form suitable for copying into an evolving class**. |
| `unpack200` | Opposite of `pack200`: transforms a packed file into a JAR file for web deployment. |

That's a lot of tools! While you won't use a lot of these tools, at least this page will be here for your reference if you decide to try them out.