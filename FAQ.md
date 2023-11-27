
# The Course Pilot FAQ

-----------------
## [Installation and Running](https://github.com/Nicholas-J-Norris/Course-Pilot/blob/main/Installation%20and%20Running.md)			
-----------------
Q.: I am neither under Windows nor KDE. Can I work with Course Pilot?

A.: Yes. However, you will not have the System tray icon feature available, so 
you will need to run Course Pilot repeatedly each time to restore it from hidden 
mode. Also you will not see that Course Pilot is started hidden (except for 
in the processes list). Because of this inconvenience, we do not recommend 
to use hidden mode when the systray icon is unavailable (do not select "Hide" 
for minimizing and closing actions in Preferences).

-----------------
Q.: Why I should start Course Pilot from its installation directory?

A.: This is because Course Pilot startup script uses relative paths for finding
dependency libraries. If you prefer to have a portable script to run it from
anywhere, you can replace the relative paths in the script by absolute ones.

-----------------
Q.: May I be sure that my data and preferences will not be lost after 
reinstalling or upgrading Course Pilot?

A.: Yes. All data (diaries, tasks, events etc.) and preferences are stored 
separately from the installation directory and will be unchanged even if you 
completely remove the Course Pilot from your machine. After reinstalling or 
upgrading the application, you should have the same workspace as in the previous 
installation.  

-----------------
Q.: Where Course Pilot stores my data and preferences? How to backup them or
remove them after uninstalling the application?

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
Q.: Can multiple users work with the Course Pilot on the same machine?

A.: Yes. Due to separate user's directories (see the section above), each
user have his own separate environment where the Course Pilot stores his projects 
data and preferences.

-----------------
Q.: Can I have two or more Course Pilot applications started at once?

A.: No. Every time when you launch Course Pilot, it checks if it is not already 
started. If started, it will not run a new process, but will try to restore a 
window (if it was in the "hidden mode") or put the window to top (if it is 
already opened). 

-----------------
Q.: I get alarm notifications from my local firewall when Course Pilot starts.

A.: The Course Pilot uses by default a socket connection on the local port 19432 to 
be sure that it is not already started. The firewalls and other security 
software may react to this connection, so you need to configure it to allow   
trusted connections on this port for Course Pilot.

-----------------
Q.: I get java.net.BindException when Course Pilot starts.

A.: Probably it is a rare case when the Course Pilot port is already 
used by another application. You need to change the port number (see below).

-----------------
Q.: How to change the default port number for Course Pilot?

A.: Open the "memoranda.properties" file in your Course Pilot user directory and 
add a line: 

	PORT_NUMBER=n

, where n is any unused port number. 

-----------------
Q.: Can I disable port listening at all?

A.: Yes, but it will allow to start more than one instances of Course Pilot. Open 
the "memoranda.properties" file in your Course Pilot user directory and add a line: 

	CHECK_IF_ALREADY_STARTED = NO

Note that this is a debug/troubleshooting mode and it is not recommended as a
normal everyday way of using Course Pilot.
	

## [Localization](https://github.com/Nicholas-J-Norris/Course-Pilot/blob/main/Localization.md)

-----------------
Q.: What do I have to do to make localization for my language?

A.: 1) Find the "messages_patterns.properties" file in the 
       "src/net/sf/memoranda/util/localmessages" directory of the source 
       distribution. With binary distro, you can unpack the 
       "build/memoranda.jar" to find this file (with any unzip utility). 
    2) Open this file with your favorite text editor. Note that if your 
       language uses non-Latin1 characters, your editor must be 
       Unicode-enabled. 
    3) Translate the labels and insert your translations after the "=" signs.
    4) Save your file as "messages_**.properties" where "**" is two letters of 
       your language code. Use UTF-8 encoding for your file if you've used 
       additional characters.
    5) Rebuild the Course Pilot or zip the "memoranda.jar" back.
    6) Run the Course Pilot (check if the "Enable localization" option of the 
       Preferences dialog is turned on) and test your labels.

         ... and (optionally),
    7) Send us your file for including it into distribution.
    
    You can also put your file into some external location and add the line into
    the memoranda.properties file:
    
    LOCALES_DIR = /path/to/your/dir
    
    The "memoranda.properties" file located in your memoranda user directory 
    (see "Where Course Pilot stores my data and preferences?" above).
    
-----------------
Q.: I see a characters garbage instead of my translated labels after 
    localization is done. What's wrong?

A.: Make sure that your file is in proper UTF-8 encoding (see above).

-----------------
Q.: I still see the english labels after localization is done.

A.: 1) Check if the "Enable localization" option in the Preferences dialog is 
       turned on. Note that you need to restart the Course Pilot after you've 
       changed this option.
    2) Make sure that you used the proper language code in your file name. 
       It must be equals to the value of the "user.language" Java system 
       property on your machine. If this property is not set for your language,
       check your system locale settings.
    3) Make sure that your new file is in the 
       "net/sf/memoranda/util/localmessages" directory of "build/memoranda.jar"
       and it has the proper file name syntax (see above).


                                TIPS AND TRICKS

* Note that this FAQ section describes some hacks and undocumented features    
* which we cannot recommend as a common practice of working with Course Pilot.   
* Use them on your own risk and don't complain if something goes wrong :-)     
* Note also that any of these backdoors can get unavailable in any further 
* release without notice. 

------------------
Q.: Can I modify default text style properties in the Notes Editor?

A.: You can override default editor CSS by setting the "USER_CSS" key in the 
"${memoranda_user_dir}/memoranda.properties" file. Provide an absolute path to 
your custom CSS file there. You can also hack the embedded "default.css"
file at "net/sf/memoranda/ui/resources/css" path.It contains CSS style rules for 
displaying various HTML elements in the editor. Note that CSS support is limited
by restricted subset of CSS1 properties only.

------------------
Q.: Can I change the default "Course Pilot user dir" location?

A.: There are "MEMORANDA_HOME" property key which overrides the default location
of a directory for storing the projects data (see "Where the Course Pilot stores my
data and preferences?"). It can be useful if you want to share one environment 
between various users on the same machine, or if you have multiple accounts.

Note that the location of "memoranda.properties" file is constant and doesn't
depend on this property (it is always in your "${user.home}/.memoranda" 
directory).

------------------
LITTLE TRICKS WITH STICKERS:
An unobvious but amusing feature of the Stickers is that you can use HTML tags 
in the sticker's text. So, you can change a font and color or even place images 
right into the stickers. 



                                    MAC OS X
----------------
Some MacOS X users report that they experienced problems with Kunststoff L&F on
their platform. So, we recommend to change the L&F settings either to 'System'
or 'Java default'.    
  
 
================================================================================
$Id: FAQ.txt,v 1.8 2007/04/06 21:21:21 alexeya Exp $
