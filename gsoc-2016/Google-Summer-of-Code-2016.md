The Java Pathfinder (JPF) team is applying to the [Google Summer of Code](https://developers.google.com/open-source/gsoc/) (GSoC) program for 2016. If you are new to the GSoC program, this is an annual global event where Google sponsors university students to write code for selected open source projects where each student is supported by an experienced mentor. Projects have about a three month scope, carry a relatively low administrative overhead, can be done remotely, and are generally fun.

## Java Pathfinder ##

The development of [Java Pathfinder (JPF)](http://babelfish.arc.nasa.gov/trac/jpf/wiki/WikiStart)  started at [NASA Ames Research Center](http://www.nasa.gov/centers/ames/home/index.html) in 1999. It became an open-source project in 2005, and it is now released under the [Apache license, 2.0](http://www.apache.org/licenses/LICENSE-2.0). JPF's infrastructure is refactored as a Java virtual machine (JVM), and itself is written in Java. JPF is applied directly on the code, and it can be used to verify any code that is compiled into bytecode.

JPF is a very flexible tool. It offers a highly configurable structure, and introduces numerous extension mechanisms which make it a suitable engine for many existing tools. JPF has been used for a variety of application domains and research topics such as verification of multi-threaded applications, graphical user interfaces, networking, and distributed applications. 

Today, JPF is a mature tool with hundreds of active users. It is used as both a research platform and a production tool. Although it has had major contributions from industry and research labs, the main user community is academic - there are contributors from more than 20 universities worldwide.

To learn more about JPF, refer to the [JPF Wiki](http://babelfish.arc.nasa.gov/trac/jpf/wiki).

## Interested Students - Contact Us ##

You can find some project ideas [here](wiki:projects/projects). If you are interested in a project that is not listed here but is relevant to JPF, we would love to hear about it. If you have any questions or suggestions regarding JPF and GSoC, email us at \<jpf.gsoc [at] gmail.com\>. Please be sure to describe your interests and background. The more we know about you, the better we will be able to answer you questions about JPF and its potential projects. Join our IRC channel #jpf on freenode to engage in a discussion about all things JPF.

## Timeline ##

| Date | Event |
| :------------- | ------------- |
| 02/29 | Announcement of accepted mentoring organizations |
| 03/14 - 03/25 | Student application period |
| 03/25 | Student application deadline |
| 04/22 | Accepted students announced by Google |
| 04/22 - 05/23 | Community bonding period |
| 05/23 | Official GSoC coding begins |
| 06/27 | Mid-term evaluations deadline |
| 08/23 | Official GSoC coding ends and student submit code samples |
| 08/29 | Final evaluations due |
| 08/30 | Final results of GSoC announced |

## Required Skills ##

JPF is written in Java, and it analyzes Java bytecode, so the minimum skill required is to be familiar with Java and have some development experience with Java (class projects or industry experience). At a minimum you should know there is more to it than just the language - it's the language, the libraries and the virtual machine/bytecodes. Not all projects require a deep understanding of Java or JPF though, please look at the project descriptions to determine which skills are most important.

JPF is a software verification tool. It is a customizable virtual machine that enables the development of various verification algorithms. It will be to your advantage if you are familiar with formal methods, software testing, or model checking. However, JPF is where research meets development, so for many projects it is not a show stopper. We are looking for students who are highly motivated, bright, willing to learn, and love to code.

JPF is a fairly complex system. The first step to start is to get JPF [running](http://babelfish.arc.nasa.gov/trac/jpf/wiki/user/run) and [configured](http://babelfish.arc.nasa.gov/trac/jpf/wiki/user/config). This in itself can be a steep learning curve. It also helps if you already know what [listeners](http://babelfish.arc.nasa.gov/trac/jpf/wiki/devel/listener), [bytecode factories](http://babelfish.arc.nasa.gov/trac/jpf/wiki/devel/bytecode_factory) and [native peers](http://babelfish.arc.nasa.gov/trac/jpf/wiki/devel/mji) are, but no worries - the mentors will help you there. One thing you have to look at, but what is now surprisingly simple is how to [set up JPF projects](http://babelfish.arc.nasa.gov/trac/jpf/wiki/devel/create_project).

## Applying for GSoC ##

You will need to submit a proposal to Google during the student application phase (03/14 - 03/25). Check out the [GSoC FAQ](https://developers.google.com/open-source/gsoc/faq) page for more information. 

## Additional Information
   * [Project Ideas](Google-Summer-of-Code-2016-Project-Ideas)
   * [Accepted Projects](Google-Summer-of-Code-2016-Accepted-Projects)