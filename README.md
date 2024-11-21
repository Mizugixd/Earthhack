
Navigation Menu

Code
Issues
Pull requests
This repository has been archived by the owner on Mar 5, 2023. It is now read-only.
Utility mod and proxy server for 1.12.2

3arthqu4ke.github.io/3arthh4ck/
License
 MIT license
 214 stars
 54 forks
 11 watching
 4 Branches
 21 Tags
 Activity
Public archive repository
3arthqu4ke/3arthh4ck
Folders and files
Name	
Latest commit
3arthqu4ke
3arthqu4ke
last year
History
.github
2 years ago
docs
2 years ago
gradle/wrapper
3 years ago
src/main
last year
.gitignore
2 years ago
Dockerfile
2 years ago
LICENSE
2 years ago
README.md
last year
build.gradle
2 years ago
gradle.properties
3 years ago
gradlew
3 years ago
gradlew.bat
3 years ago
jitpack.yml
2 years ago
pingbypass.properties
2 years ago
settings.gradle
2 years ago
version.py
2 years ago
Repository files navigation
README
MIT license
⚠️ This is an outdated and archived 1.12.2 client. More and more servers are updating to newer versions. Any new PingBypass I release will be found here.

3arthh4ck
CodeFactor GitHub All Releases Docker Image Size (latest by date) Lines of code Repo size Build

3arthh4ck is Minecraft 1.12.2 utility mod for anarchy PvP. With the 1.7.0 release it also takes over the role of the now outdated PingBypass Server and Client. To install it just drop the jar into your forge mods folder. By default, any message prefixed with a + will be handled as command, e.g. +toggle clickgui, to open the gui. Because of bloat I decided to hide some of the more complicated Settings by default. You can find those by using the Settings module.

Proxy/PingBypass
Image of a PingBypass server
3arthh4ck can be used as a Proxy server. With ping being such an important factor in crystal PvP this allows you to play on servers far away from where you are without the disadvantage of high ping. This proxy can, opposed to the old PingBypass, stay connected to a server, allowing to join through it at a later point. This can for example be used to wait out 2b2t's queue system.

To set up the 3arthh4ck proxy you need a server, I personally started out using GCP's free trial. The location of that server should be as close as possible to the one you want to play on. That server should have an Ip and port which are reachable from the outside. The game will run on that server. Keep in mind that no matter which account you use on your client, the Minecraft account on the server will always be used when you play.

Setup with docker
Install docker on your server.

Run docker pull 3arthqu4ke/pingbypass.

Run docker run -i -t -p <ip>:<port>:25565 3arthqu4ke/pingbypass.

You should now be in the shell of the docker container.

Login to your Minecraft account via hmc login <email>, then enter your account password.

Launch the PingBypass server with hmc launch 1 -id --jvm -Dpb.password=<some password>.

You are now done with the server. Use the commands from the HMC-Specifics to stop the game. Or just stop the container.

On your own PC just install 3arthh4ck by using its Installer or dropping it inside your mods folder.

In the MultiPlayer Menus top right corner you will see a book and a PingBypass button. Use PingBypass button to toggle it on and off and the book to enter the server's connection details, also the password you used in step 6.

You can add the PingBypass server like a normal Minecraft server, this will make it look like in the picture above. When the PingBypass button is toggled on you will join any server you click through the PingBypass proxy.

There is two sets of modules, one accessible through the PB-Gui module. These modules have separate configs and represent the ones on the proxy server.

Manual Setup with HeadlessMc
This is just what the docker container already automates.

Install Java 8 on the server

Create a folder where your game will run.

Inside that folder create two directories: mods and earthhack

Put the 3arthh4ck jar and the HMC-Specifics-1.12.2 jar inside the mods folder.

Inside the earthhack directory create a file called pingbypass.properties filled with the following:

pb.server=true
pb.password=<password for your pingbypass proxy>
pb.ip=<the aforementioned ip (definitely not 127.0.0.1)>
pb.port=<the aforementioned port>
Download HeadlessMc and run its jar once.

This should create a file called HeadlessMC/config.properties. Edit that file and add:

hmc.gamedir=<the directory created in step 2.>
hmc.java.versions=<the directory where the java binary is located, e.g. /usr/bin/java>
hmc.invert.jndi.flag=true
hmc.invert.lookup.flag=true
hmc.invert.lwjgl.flag=true
hmc.invert.pauls.flag=true
Run HeadlessMc again:

Login to your Microsoft account with login <email>, then enter your password.
Run download 1.12.2., then forge 1.12.2.
List the downloaded versions with versions -refresh.
Launch the game with launch <id of the forge version> -id.
You are now done with the server. Just follow the steps after 7. in the docker setup.
