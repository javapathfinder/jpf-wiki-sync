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
        
  * [Developer guide](devel/index) -- what's under the hood
    * [Top-level design](devel/design)
    * Key mechanisms, such as 
        - [ChoiceGenerators](devel/choicegenerator)
        - [Partial order reduction](devel/partial_order_reduction)
        - [Slot and field attributes](devel/attributes)
    * Extension mechanisms, such as
        - [Listeners](devel/listener)
        - [Search Strategies](devel/design)
        - [Model Java Interface (MJI)](devel/mji)
        - [Bytecode Factories](devel/bytecode_factory)
    * Common utility infrastructures, such as
        - [Logging system](devel/logging)
        - [Reporting system](devel/report)
    * [Running JPF from within your application](devel/embedded)
    * [Writing JPF tests](devel/jpf_tests)
    * [Coding conventions](devel/coding_conventions)
    * [Hosting an Eclipse plugin update site](devel/eclipse_plugin_update) 
        
    ---
        
  * [JPF core project](jpf-core/index) -- description and link to jpf-core
    
    ---
      
  * [Related research and publications](papers/index)    

