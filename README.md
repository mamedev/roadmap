Official MAME roadmap
=====================

Website/Hosting
===============
As you are all aware our site is quite old-style looking, also we have lot of things distributed on various places and it's hard to switch some responsibilities to team-members or to add new member in team due to need of involvement of 3-4 persons to finish the job. Also users are not aware on first site where to find needed information or how to contact us.

Was do lot of thinking and trying to find solution that will cover all our needs, and managed to get something :) 


Distribution
============
Also on main site we will need to update for unofficial sources for Linux and OSX distributions or we can even provide our own if someone is willing to take care of that.

For Windows releases I would like to create NSIS installation package together with web updater, so application can be updated automatically once it is installed. For now I can just make a NSIS package that will install MAME and help user set up rom/sample folders. (Similar that QMC2 have on 1st start-up).

Mobile
======
Lack of mobile presence is a problematic pointed by lot of developers as well. Thing is that we need a proper way to port application to mobile devices and SDL2 work was part of it. Also BGFX integration that I am working on is supporting Android and iOS as official targets and therefore we can use it for that as well.

It's not that simple task and it would require us as well to try to find some more Android/iOS developers to help on this as well. Hopefully when there is some progress they will apply themselves.

New developers
==============
We should encourage new developers to join. Think GITHUB should help us, since that way they will see they are recognized, they will appear as contributors in our tree with links to their account that feels better for them. I am aware young developers are maybe not much interested in old arcades and computers, but there are still some people out there willing to work. I planned of adding Join Us page on new site, with knowledge requirements that are of interest to us, including gui programming, lua scripting, automated testing, QT and more and not just C/C++.

Need to define coding style acceptable for contributing code (something like : https://www.kernel.org/doc/Documentation/CodingStyle )


GUI/Video/OSD in total
======================
As told, already started adding BGFX library, that also contain NanoVG library that makes nice GUI creation easier. Also there is NanoSVG providing easy usage of SVG which can help with loading custom things for GUI, including parts of layout. Thing is VG is of Vector Graphics so it means that all is written in one vector space and scaled on screen so there are no issues drawing it on different resolutions. This part will require some time that is for sure, but first we need to upgrade our video output and make this part possible to develop. Note that BGFX as lib can use SDL2/OpenGL, DX9 and DX11, it supports various platforms ( more info at https://github.com/bkaradzic/bgfx )

* We would need to add audio support for inputs and for 5.1 or more outputs.
* externaly defined layouts so skins can be provided by 3rd party  adding a way to access usage instructions form mame itself
* separate rendering and window handling

On desktop platforms users are more to use GUI then start emu from command line or use internal gui of ours. There are two ways. We can make internal gui fancy (including menu bar) and go that way, or stick with QT as way of providing UI for us. Both have their pros and cons. Thing is that if we move to unique output lib and use nanovg and nanosvg, we can even do a nice portable debugger on it and remove need for it, but it's not going to be easy in any of two cases. So for now I would leave options open. Monitor emulation multi-platform (BGFX should enable this with portable shaders).



Debugger
========
We currenly have 3 debuggers. They are made modular so you can have windows native and QT one on Windows, or QT and OSX native on OSX and QT only on Linux. Thing is that this makes development changes on debugger slower since you need to update 3 versions and you can try max 2 on Win and OSX and just 1 on Linux. Idea would be to make QT version more robust and performant on Windows as well so we can move to one debugger. We would anyway need to include QT in our future builds (for Windows) since asll tools that need interface shell be done using QT (like imgtool gui).

For new features we would need something like palette and tilemap viewer added to debugger. We can also add some custom views per driver, but I would like to keep that as plugins so they are not inside driver code, but defined by external lua scripts.

Address watch window separated, with type conversion, was one of interesting ideas of things to be added. Also ability to add labels to addresses could be of great help while developing. Those that are OS specific (for computers) we can even hold in external files and distribute on some way, so when debugging pc software you are aware that it's accessing bios info for floppy selection for example. Lot of work but for start we need to distribute a way of doing it and if it's usefull we should get more external input on this for specific platforms.

Some fancy views, like logic analyzers view for discrete logic devices and pin states of devices we emulate. 



Testing
=======
Built in regression test (like we had in MAMEUI) would be great for smoke-testing of big changes, idea is just to start driver wait few sec and close it. It should show you crashes if there are some. LUA scripts for testing drivers/software items could be very usefull, but first all things available in core must be visible by LUA itself, that will make this kind of testing then possible.



Save States/INP
===============
Save states can be very usefull for debugging as well as INP files. We need a way to make system more robust on changes of core components and to warn users if some of old save states is not possible to be used any more. Also it would be nice to separate it internaly and use ZIP containers for storing data in it, that way we will have more control of check process. We need more thinking on this specially how to detect changes in data stored by device state saving.

Rewind and re-recording support for INP would be nice features to add to our code.



IPS Soft patching
=================
Support for this would be great, enabling users to select patches that will do some translations and so on. This can be even done on similar as for softlists to list patches that shoul at least help us test games that are on languages we do not speak, or enable playing some of 1000 variatons of KOF or similar games avalialable now only in HBMAME. 



Softlists
=========
Adding custom softlist support can be usefull for users that wish to have their collection of software that are not good-dumps or they are homebrew software.



Networking/IPC
==============
Networking is currently used only by MESS drivers, and things are working on correct way. Think we should make network builds 1st class citizens and made it default one (with option to be disabled and not vice-versa). Two-way IPC is thing that should help us better integrate with other applications. Idea for this is to be portable as much as possible. There are some variants like on http://qt-project.org/doc/qt-4.8/ipc.html but I would like to have solution without QT if possible so we can port it to mobile systems that will not have debugger and anything else using QT.



Layout
======
Current layout system works fine for small number of items. Would like to suggest moving to SVG as standard way of defining vector graphics and use it for internal purposes. We would still need an editor (in QT for example) so it should be possible to create layout for some games or machines without knowing much of how our internals work.



Emulation improvements in general
=================================
We need to list of all deprecated code in our core to be able to work on that. There are still lot of things that are duplicated or beeing done on few different ways, some devices still duplicated implementations, or like sound cores still in lot of separated files with quite 1990 look with static variables and so on. Need to take care of cassette image format handling there are modern and legacy and 90% is legacy there. MCFG_SCREEN_VBLANK_TIME is also one of things we need to take care of.

Problem on some big core changes is that we actually never anounced them on list to other developers, or for that some other means were used (shoutbox or IRC). Thing is that with using GIT we can now work on our GIT repo copy, share that with others but still code is not on main repo, and that will prevent imature code comming to main branch too early, and also it's easy to get feedback from other developers about some approach.

Performance is our big issue. I know that accuracy is always on 1st place, but we need to think of users as well. There is no use of system if it's running on 10% of speed on most modern computer. I am against hacking things, so we should not make speed by cheathing, but changes like new memory system and more work on LLVM integration. To be honest I do not have much knowledge for that task and would like if OG and anyone else interested can come with some more ideas.

We need to be more close to hardware, so RESET and IRQ pins should be used as such, making emulation as close to real hardware. No reset pin = no F3 button working. Other things that can go pin level should go in that direction.

Our sound cores should go to cycle-accurate where we can. 


Multiple machines
=================
Thing that we should work on is support for multiple machines running at once and communicate. If we add IPC mechanism to communicate with other instance of MAME, we should use same mechanism to provide internal communication as well, that way we need less testing and speed impact is small. Also we need to provide some devices like we have terminal and teleprinter to be connected on same way to machines, so we can easy move from terminal simulator to vt100 driver for example.



Slot improvements
=================
Support for multiple interface devices is needed. Some cards have few busses supported, and one of simple examples is SCSI cd-rom with audio. We should add ability for CPU's to also be slots, so we can change CPU type/speed where applicable. PCI should be properly redone as slot device, including controllers using it enabling us to emulate modern arcade and pc systems.

RAM device as slot device can be good way to go as well.

Multiple keyboards support can be very usefull when we have two machines running at once, or we have terminal connected to PC, so we need a way of telling on which one we are typing now.

Also joysticks, dipswitches should act as devices, and in case of joystics slot devices.



Mainframe and minicomputers
===========================
Few years ago we got approval from Bob Supnik author of SIMH to convert cpu cores to our system. We did not do much meanwhile, but think we should try to work on these machines as well, specially VAX and PDP11 since those could get us quite nice user base and make project look much more serious.
