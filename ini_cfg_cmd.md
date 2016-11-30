#INI files vs CFG files vs command line parameters

In current code there is lot of mixing what is INI value and what should be CFG value.
Also we have lot of command line parameters and not all should be there for sure.

Idea is to clean this up, and put things in proper places only.

* 1st unadored option at command line present machine to be started
* 2nd can be used for software name to be used
* commands that are handled by clifront.cpp should be exposed over commandline
* image devices mounting should be exposed to command line as now
* slot devices should be defined as configuration, adding new command line option as well for loading configuration 
* configuration for driver should contain slot configuration, ram size, dip-switch settings for each devices inside
* controller configuration should be stored in separate configuration files (as in distribution ctrl files)
* config for sound_manager ???
* config for render contains view settting ???
* config for network contains mac address ???
* config for image contains image_directories ???
* config for crosshairs ???
* config for bookkeeping, contains coin counters???
* config for laserdisc_device , overlay config ???


 
