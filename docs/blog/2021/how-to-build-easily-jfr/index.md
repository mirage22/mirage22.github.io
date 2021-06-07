---
layout: default
---

## How to easily build JFR

Build Java Flight Recorder from the source-code is easier than it ever was. It is not required to read a documentation or running additional application. In this post we explore both way. The first is the traditional and the seconde is very neat script build script available for unix and windows systems. The post is meant
unix users.

In both cases we clone the GitHub JMC repository to JMC_FOLDER destination [link](https://github.com/openjdk/jmc)
```bash
$ git clone https://github.com/openjdk/jmc
```

### Using neat *build.sh* script 
The script build.sh is located in the root of JMC_FOLDER, It's very neat script. It allows not only 
to comfortably build all required dependencies but it allows to run appropriate version of JMC/JFR. 
It is not required to remember any of steps mentioned in the second build option. Let's explore the script
```bash

$ ./build.sh --help
usage: call ./build.sh with the following options:
   --test                      to run the tests
   --testUi                    to run the tests including UI tests
   --installCore               to install JMC core
   --packageJmc                to package JMC
   --packageAgent              to package Agent
   --clean                     to run maven clean
   --run                       to run JMC, once it is packaged
   --runAgentExample           to run Agent 'InstrumentMe' example, once it is packaged
   --runAgentConverterExample  to run Agent 'InstrumentMeConverter' example, once it is packaged
   --help                      to show this help dialog
```

The script allows to chain the command, on the background it start the required p2 repository and makes all 
required steps. You can build and run the JMC/JFR in one simple command:
```bash
$ build.sh --clean --installCore --packageJmc --run
```

### Building JFR by command line
The following steps are nicely described also in JMC official docs. 
Let's open two independent terminals and ensure 
that you have proper JDK version
```bash
$ java -version
openjdk version "11.0.2" 2018-10-16
```

*Terminal 1* : make available 3rd party dependencies through p2 local repository

```bash
cd <JMC_FOLDER> 
cd releng/third-party
mvn p2:site
mvn jetty:run
```
*Terminal 2* : install core and package JMC to executable app
```bash
$ pwd <JMC_FOLDER>
$ cd core
$ mvn clean install

$ cd ..
$ pwd <JMC_FOLDER>
$ mvn package
```

Now you are ready to run JMC/JFR from you local build, Mac OS X:

```bash
target/products/org.openjdk.jmc/macosx/cocoa/x86_64/JDK\ Mission\ Control.app/Contents/MacOS/jmc
```

### Summary
Building JMC/JFR becomes due to the neat build.sh script very simple and easy. The script has more 
functionalities, feel free to discover them...
Happy JMCing
