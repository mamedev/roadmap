Official MAME roadmap
=====================

Website/Hosting
With help of Duke we have transferred git mirror to: https://github.com/mamedev/

Idea is that in period of one week we transfer to GITHUB as main repository. Due to that time, all existing members should create their account there and provide me email they used for register and as a link to their main page (like mine at : https://github.com/mmicko ). You can keep your email private in account. You will all get emails @mamedev.org before moving to github that you can add as additional one and we will map users on git repo to those emails.

Since I am aware that there are lot of people that are not experienced with GIT, good news is that there is possibility of using same repo as SVN. To try that out try to pull data from https://github.com/mamedev/mame/trunk

There is now https://github.com/mamedev/playground repo to play with. Use https://github.com/mamedev/playground/trunk with SVN client in oreder to play.

Idea for main site is to have full or at least changeable content on github repository as well, so each team member can add information on site, also each team member can have a blog and be able to update it as part of main site. It will all be much clearer when site is up and git repo for it available. Idea is to keep it using Bootstrap to have modern look and feel, also plan to add MAWS like content and search. For start site will just have same info as on current one just with more modern look, but then anyone from team can update. Also thing is that since it's separate repo it can have additional people involved that do not need to have main project repository access.

Would like to keep mametesters as is (maybe some "facelifting" to get better look, but no functional change), and would like to offer moving hosting to it on same server to Fujix as well, and he will continue running it as before. Idea is enable that main site is using data from mametesters database when showing data related to drivers, so we can track per driver changes in past and so on. Hopefully that can be very useful operation.

GITHUB should make our code submission much easier, since there are pull requests so anyone can send us request and we can then do code review and apply or deny patch. All is visible to people and in our source tree true author will be marked, and that is important too.

There were lot more ideas for improvement but I would like to stick now to this main major issues and then continue adding things.

For promotion purposes we will use : https://twitter.com/mamedev_org to announce any further release/ interesting change and so on.

Using GIT will make us push on master branch all things that are for release, and not putting beta code ( like I did in past :( ) allowing users to see half baked product. Should make project look more serious but still very open.



Distribution
============
Time for 0.155 is long passed, and I would like to release it soon, if possible during next week. Idea for future releases would be to make it monthly (for example every last Wednesday in month) that will make all people interested to be aware when to expect a release, and also give us good feedback about issues. Project is big one and I do not expect all things always to work, but we will try to keep bugs on lowest possible level.

Since for last 2 years we are doing things as one team and basically one project, and from most developers I got request that we should deliver combined binary as official one, I can only accept that. Thing is that MAME is well known brand and that all people recognize it in opposition to MESS, so would suggest delivering it as MAME that will just include things we have in MAME and MESS now. 



Mobile
======
For supporting multiple systems and also as extension to point 2 (Distribution) would like to introduce premake4 (well it's fork with additional support, called genie) ( https://github.com/bkaradzic/genie ) that is project generator that allows defining rules per platform/build system so creating gnu makefiles for Linux, Mingw, OSX, creating projects for VS2005 -VS2013 and any custom project derivate of gnu make, like Android, NACL, asmjs, and so on. It will take some time to define all rules and test this, but I can work this on separate branch in just my local repo (good thing using GIT) so it can be delivered when finished in total.

Since tool is based on lua, it's possible easy to define your own rules, so creating custom builds with just some drivers enabled will be possible. That should solve us some of serious problems we have and make mobile more visible.



Licensing
=========
We had a large discussion over this. Conclusion was that there were no conclusion. But still think there is a room to work this out.

One solution would be that we use BSD 3-Clause ( http://opensource.org/licenses/BSD-3-Clause ) for a core, and make drivers GPL-3.0 or GPL 2 ( http://opensource.org/licenses/gpl-3.0.html ). For core, there is small number of developers that are (as I am aware) all fine with BSD. For drivers I do not see any difference of using GPL or our own MAME License. There is still restriction for users can not use it unless they provide a source and it's viral so we can use their code as well and they need to keep same license. Sure futher discussion will be needed but make a note that our license is not recognized as one of Open Source licenses so we are NOT Open Source project and can't gain some free usage of other software for example and things provided by some companies (like Jira from Atlassian). Note that this is not final, just idea.


LUA
====
Lua have been added, and I admit I have not done much into improving it. Addition of LuaBridge ( https://github.com/vinniefalco/LuaBridge ) have made exposing of existing core capabilities much easier. Also I have been doing some work on using LUA pages over Mongoose ( https://github.com/cesanta/mongoose ) web server. So code that is inside of webengine will disappear and pages could return JSON data as well as generating HTML or anything else needed.



Plugins
=======
Would like to introduce plugin system that is LUA based for MAME. There were lot of ideas for additional MAME functionalities or bringing back some old (removed since they are not existing on real machine), and introducing some new things and giving freedom to users to add their own things. Whole cheat system can actually be done as LUA plugin, fully independant, on our side is to provide consistent API. Will elaborate this later, but think it's good way to get some users back by giving them highscore plugin, cheat plugin, autofire and similar things.



GUI/Video/OSD in total
======================
* SDL2 video should be 1st class citizen for MAME so we actually need to break OSD better and make video modular as well.
* Need to add more modern ways of communicating with hardware like XAudio2. 
* UI need to be multilanguage and externaly defined layouts so skins can be provided by 3rd party  adding a way to access usage instructions form mame itself

