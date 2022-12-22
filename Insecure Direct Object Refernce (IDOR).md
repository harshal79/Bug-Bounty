+ Insecure Direct Object Reference (IDOR) occurs when an application provides direct access to the object based on the user-supplied input. As a result of this vulnerability, attackers can bypass authorization and access resoures in the system directly.

	``For example - Database Records or file.``

+ IDOR allow attackers to bypass authorization and access resources directly by modifying the value of a parameter used to direct an object. 

+ Such resources can be database entries belonging to other users, files in the system, and more.

+ This is caused by the fact the application takes user-supplied input and uses it to retrieve an object without performing sufficient authorization checks.

##### Hackerone Reports 
+ https://hackerone.com/reports/390346
+ https://hackerone.com/reports/227522
+ https://hackerone.com/reports/287789
+ https://hackerone.com/reports/264919























