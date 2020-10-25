# eclipse-jpf #

This is a plugin to launch JPF on selected application property files (*.jpf) from within Eclipse. This plugin is the Eclipse analog to netbeans-jpf. This plugin is minimal by design and serves mostly to start an external JPF process from within Eclipse.

To this end, the plugin adds a "Verify.." popup menu item for *.jpf files that are selected in the package explorer window. 

Depending on the selected application property file, output will appear either in the eclipse console view or a jpf-shell.

The site.properties location can be entered in the "JPF Preferences" pane within the normal Eclipse Preferences window. The default location is `$HOME/.jpf/site.properties`.
 

This project is *not* a normal JPF project, i.e. it does not follow the usual JPF directory structure and artifacts. This is an Eclipse plugin project that builds into a jar file (attached) that installs into Eclipse as a plugin. Of course that means you need an Eclipse installation that includes the Plugin Development Environment (PDE) in order to build this project.

### Installation ###
If you have installed eclipse, then just download jpf and import the files into eclipse and you are good to go.
Download the files from  https://github.com/javapathfinder/jpf-core/archive/master.zip
