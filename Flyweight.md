#FLYWEIGHT PATTERN

##PROBLEM
You need a lot of copies of an object
##Examples
*List of users
*Game objects
*Posts in a social app like Twitter

##What is it?
*A flyweight is a shared object that can be used in multiple contexts simultaneously.
*Instead of recreating instances, instances are re-used or shared
*A Dictionary of objects where entries are added to dictionary, if not present , and reused if already there.
*This can be used only for read-only objects like posts on a timeline or obstacles in a game.

##Usage
Objects which can be globally used like user object can be loaded at login from the database and can be shared throughout the time of the session. Only drawback is if any changes are made to entity which is represented by 	the shared object after it has been created will not be propagated. So there must be some methodology to refresh the cache. 
Also any entity sharing the flyweight object can edit it and changes will be propagated throughout the session.
##Example
###UserList
*Application have lots and lots of users
*Users are use throughout the session.
We need to create user only when used
####User class
*Has a user name and other attributes
*Also has a list of followers which may be heavy
####UserFactory class
*Purpose is to supply users as needed
*This will be having an internal user dictionary
####GetUser method of UserFactory class-
This would return the reference to the user if it is present in the dictionary and if not found in the dictionary it will query the database and fetch the user and store it in the dictionary as well as return a reference to it as requested. This is lazy loading of user to create only when necessary.

