Verifying performance of Jasig CAS with Apache JMeter 
=====================================================

Files supporting the blog entry 
http://www.kth.se/blogs/1337/2013/02/verifying-performance-of-jasig-cas-with-apache-jmeter/

This files are copies of files that we actually use, but modified for 
a more generic CAS configuration. They should work, but I've not verified
that they do after these modifications.


## Files ##

### GenericCasPerfTest.jmx ###

A JMeter test suite with basic tests for Jasig CAS. It tests user
authentication and simulates getting and validating service tickets. 
The service ticket used for this purpuse is the CAS service management
web app, since it is a service that is included in CAS itself. You
can easily adapt the suite to use some other service of your choice,
but remember to enable it in CAS if you use service validation.


### users.csv ###

A file containing a list of username, password pairs separated by a tab.


### localhost.properties ###

A property file with configuration for variables which the test suite uses, 
among these the name of the file containing the users mentioned above.
These properties are mapped to variables in the suite in the 'Test Plan', 
the first page of the suite in the JMeter gui.


## Running ##

Assuming all failes (including users.csv) Run the test suite with the command:

```
jmeter -p localhost.properties -t GenericCasPerfTest.jmx
```
