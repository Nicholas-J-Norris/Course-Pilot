## Localization 

-----------------
### Q.: What do I have to do to make localization for my language?

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
### Q.: I see a characters garbage instead of my translated labels after localization is done. What's wrong?

A.: Make sure that your file is in proper UTF-8 encoding (see above).

-----------------
### Q.: I still see the english labels after localization is done.

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


### [Back to FAQ](https://github.com/Nicholas-J-Norris/Course-Pilot/blob/main/FAQ.md)
