# INSTALLATION AND RUNNING

-----------------
### Q.: I am neither under Windows nor KDE. Can I work with Course Pilot?

A.: Yes. However, you will not have the System tray icon feature available, so 
you will need to run Course Pilot repeatedly each time to restore it from hidden 
mode. Also you will not see that Course Pilot is started hidden (except for 
in the processes list). Because of this inconvenience, we do not recommend 
to use hidden mode when the systray icon is unavailable (do not select "Hide" 
for minimizing and closing actions in Preferences).

-----------------
### Q.: Why I should start Course Pilot from its installation directory?

A.: This is because Course Pilot startup script uses relative paths for finding
dependency libraries. If you prefer to have a portable script to run it from
anywhere, you can replace the relative paths in the script by absolute ones.

-----------------
### Q.: May I be sure that my data and preferences will not be lost after reinstalling or upgrading Course Pilot?

A.: Yes. All data (diaries, tasks, events etc.) and preferences are stored 
separately from the installation directory and will be unchanged even if you 
completely remove the Course Pilot from your machine. After reinstalling or 
upgrading the application, you should have the same workspace as in the previous 
installation.  

-----------------
### Q.: Where Course Pilot stores my data and preferences? How to backup them or remove them after uninstalling the application?

A.: This is a directory named ".memoranda" under the path defined by "user.home" 
java system property: 

    - On Win2K and WinXP it is usually 
      "C:\Documents and Settings\{USERNAME}\.memoranda"      
      
    - On WinNT and Win95/98/Me it is usually 
      "C:\WINNT\PROFILES\{USERNAME}\.memoranda", or
      "C:\WINDOWS\PROFILES\{USERNAME}\.memoranda"
      
    - On Linux it is usually "/home/{USERNAME}/.memoranda" ("~/.memoranda")
    
    NOTE that if you were the Course Pilot user when it was called "jNotes2", your
    directory is still named as ".jnotes2", not ".memoranda".
    
To make a complete backup copy of all Course Pilot projects, events and 
application preferences, simply make a copy of this directory. Similarly, to 
remove them after uninstall, remove this directory.

-----------------
### Q.: Can multiple users work with the Course Pilot on the same machine?

A.: Yes. Due to separate user's directories (see the section above), each
user have his own separate environment where the Course Pilot stores his projects 
data and preferences.

-----------------
### Q.: Can I have two or more Course Pilot applications started at once?

A.: No. Every time when you launch Course Pilot, it checks if it is not already 
started. If started, it will not run a new process, but will try to restore a 
window (if it was in the "hidden mode") or put the window to top (if it is 
already opened). 

-----------------
### Q.: I get alarm notifications from my local firewall when Course Pilot starts.

A.: The Course Pilot uses by default a socket connection on the local port 19432 to 
be sure that it is not already started. The firewalls and other security 
software may react to this connection, so you need to configure it to allow   
trusted connections on this port for Course Pilot.

-----------------
### Q.: I get java.net.BindException when Course Pilot starts.

A.: Probably it is a rare case when the Course Pilot port is already 
used by another application. You need to change the port number (see below).

-----------------
### Q.: How to change the default port number for Course Pilot?

A.: Open the "memoranda.properties" file in your Course Pilot user directory and 
add a line: 

	PORT_NUMBER=n

, where n is any unused port number. 

-----------------
### Q.: Can I disable port listening at all?

A.: Yes, but it will allow to start more than one instances of Course Pilot. Open 
the "memoranda.properties" file in your Course Pilot user directory and add a line: 

	CHECK_IF_ALREADY_STARTED = NO

Note that this is a debug/troubleshooting mode and it is not recommended as a
normal everyday way of using Course Pilot.

### [Back to FAQ](https://github.com/Nicholas-J-Norris/Course-Pilot/blob/main/FAQ.md)
