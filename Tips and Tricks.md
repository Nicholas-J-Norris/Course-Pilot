# Tips and Tricks

* Note that this FAQ section describes some hacks and undocumented features    
* which we cannot recommend as a common practice when working with Course Pilot.   
* **Use them at your own risk.**   
* Note also that any of these backdoors may become unavailable in any further 
* release without notice. 

------------------
### Q.: Can I modify default text style properties in the Notes Editor?

A.: You can override default editor CSS by setting the "USER_CSS" key in the 
"${memoranda_user_dir}/memoranda.properties" file. Provide an absolute path to 
your custom CSS file there. You can also hack the embedded "default.css"
file at "net/sf/memoranda/ui/resources/css" path.It contains CSS style rules for 
displaying various HTML elements in the editor. Note that CSS support is limited
by restricted subset of CSS1 properties only.

------------------
### Q.: Can I change the default "Course Pilot user dir" location?

A.: There are "MEMORANDA_HOME" property key which overrides the default location
of a directory for storing the projects data (see "Where the Course Pilot stores my
data and preferences?"). It can be useful if you want to share one environment 
between various users on the same machine, or if you have multiple accounts.

Note that the location of "memoranda.properties" file is constant and doesn't
depend on this property (it is always in your "${user.home}/.memoranda" 
directory).


### [Back to FAQ](https://github.com/Nicholas-J-Norris/Course-Pilot/blob/main/FAQ.md)
