
#### Latest JPF News
*  23/01/2018 The JPF team is applying to the [GSoC](https://developers.google.com/open-source/gsoc/) program for 2018. To learn more, please visit the [JPF/GSoC](JPF-Google-Summer-of-Code-2018) page.
*  05/01/2017 JPF Workshop 2017 will be co-located with [ASE 2017](http://ase2017.org) in Champaign, IL. Please consider submitting a paper.
*  02/27/2017 JPF got accepted for [GSoC 2017](https://summerofcode.withgoogle.com/organizations/5314871315922944/). Please visit our [ideas page](https://jpf.byu.edu/gsoc17/projects/projects.html), and let us know if you have a topic in mind.
*  19/01/2017 The JPF team is applying to the [GSoC](https://developers.google.com/open-source/gsoc/) program for 2017. To learn more, please visit the [JPF/GSoC](https://jpf.byu.edu/gsoc17/) page.
*  06/01/2016 [JPF Workshop 2016](http://jpf.byu.edu/jpf-workshop-2016/) will be co-located with [FSE 2016](http://www.cs.ucdavis.edu/fse2016/) in Seattle, WA, on November 18, 2016. Please consider submitting a paper.
*  04/22/2016 JPF student proposals accepted for GSoC 2016 [announced](https://summerofcode.withgoogle.com/organizations/5791763432210432/#projects) - Congratulations to the students!
*  02/29/2016 JPF got accepted for [GSoC 2016](https://summerofcode.withgoogle.com/organizations/5791763432210432/). Please visit our [ideas page](https://jpf.byu.edu/gsoc16/projects/projects.html), and let us know if you would like to propose a project.


This is the main page for Java™ Pathfinder (JPF). JPF is an extensible software model checking framework for Java™ bytecode programs. The system was developed at the [NASA Ames Research Center](http://arc.nasa.gov), open sourced in 2005, and is freely available on this server under the [Apache-2.0 license](http://www.apache.org/licenses/LICENSE-2.0).


This page is our primary source of documentation, and is divided into the following sections.

   ---

  * [Introduction](Introduction) -- a brief introduction into model checking and JPF
    * [What is JPF?](What-is-JPF)
    * [Testing vs. Model Checking](Testing-vs.-Model-Checking)
         - [Random value example](Random-Example)
         - [Data race example](Race-Example)
    * [JPF key features](Classification)
    
    ---

  * [How to obtain and install JPF](How-to-install-JPF) -- everything to get it running on your machine
    - [System requirements](System-requirements)
    - Downloading [binary snapshots](Downloading-binary-snapshots) and [sources](Downloading-sources)
    - [Creating a site properties file](Creating-site-properties-file)
    - [Building, testing, and running](Build,-Test,-Run)
    - Installing the JPF plugins
         - [Eclipse](Eclipse-Plugin) 
         - [NetBeans](NetBeans-Plugin)
    
    ---
         
  * [How to use JPF](How-to-use-JPF) -- the user manual for JPF    
    - [Different applications of JPF](Different-applications-of-JPF)
    - [JPF's runtime components](Runtime-components-of-JPF)
    - [Starting JPF](Starting-JPF)
    - [Configuring JPF](Configuring-JPF)
    - [Understanding JPF output](Understanding-JPF-output)
    - [Using JPF's Verify API in the system under test](Verify-API-of-JPF)
    
    ---
        
  * [Developer guide](Developer-guide) -- what's under the hood
    * [Top-level design](Search-Strategies)
    * Key mechanisms, such as 
        - [ChoiceGenerators](ChoiceGenerators)
        - [Partial order reduction](Partial-Order-Reduction)
        - [Slot and field attributes](Slot-and-field-attributes)
    * Extension mechanisms, such as
        - [Listeners](Listeners)
        - [Search Strategies](Search-Strategies)
        - [Model Java Interface (MJI)](Model-Java-Interface)
        - [Bytecode Factories](Bytecode-Factories)
    * Common utility infrastructures, such as
        - [Logging system](Logging-system)
        - [Reporting system](Reporting-system)
    * [Running JPF from within your application](Running-JPF-from-application)
    * [Writing JPF tests](Writing-JPF-tests)
    * [Coding conventions](Coding-Convention)
    * [Hosting an Eclipse plugin update site](Host-Eclipse-plugin-update-site) 
        
    ---
        
  * [JPF core project](JPF-core) -- description and link to jpf-core
    
    ---
      
  * [Related research and publications](Related-publications)    

