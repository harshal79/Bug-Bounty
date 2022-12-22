- When looking for application server vulnerabilites following vulnerabilites should be considered :
1. Testing For Default Credentials
2. Testing For Default Content
3. Bug Bounty Of a Web-App using Dangerous HTTP methods
4. Test for proxy functionality 
5. Test for virtual hosting misconfiguration
6. Test for web server software bugs
7. Test for web-app firewall (WAF)

**1. Testing for default credentials** :
	- There is a web application using some open source or comercial software installed on server.
	- Server administrator jsut forgot to remove predefined authentication credentails and they haven't changed it.
	- Lets assume I have a cisco router and I haven't changed default credentails of that router and I connected administrative with web application ( i.e., any network administrator can login remotely) 
	- https://cirt.net/ (for deafault passwords)

**2. Test for default content** :
	- phpinfo.php
	- debug method
	- sample functionality desined to demonstrate certain common task
	- powerfull function left accessiable
	- server manuals | documents | license that may lead some other attack through that information

 **How To Find this vulnerability ?** (Critical File Found) :
 1. Go to your target website 
	 `For example : www.target.com`
2. Now add the identifier at teh end of the URL like :
	`www.target.com/idfn`
3. Now hit the enter and capture the request using burpsuite.
4. Send the request to intruder and click on clear.
5. Now select the idfn (identifier) and click on add.
6. Now go to payload section and select the option Runtime file and add the payload file.
7. Click on start attack and check for the Status - 200 which means file has been found.
8. Now check the file.
https://github.com/BeingN00b/Critical-File-Payloads/blob/main/payloads.txt

**3. Bug Bounty of a Web App using dangerous HTTP methods** :

>{
	 **HTTP Methods** :-
	_1) GET Method_ : used to retrieve data from a web server.
	_2) POST Method_ : used to send some data to the server.
	_3) DELETE Method_ : requests the server to delete a file at a location that is specified by the given URL.
	_4) OPTIONS Method_ : used to find out the HTTP methods and other options that are supported by a web server.
	_5) HEAD Method_ : used to retrieve only header information (no body is included).
	_6) PUT Method_ : used to store the enclosed entity on a server. (dengerous method)
	_7) TRACE Method_ : used to diagnose the communication.
	_8) CONNECT Method_ : used to create tunnel with the proxy
	}

	- Many ways to detect HTTP Methods
		1. BurpSuite (use OPTIONS --> as a method)
		2. curl -X OPTIONS -i 'http://target.com'
		3. RESTClient (extension)
	- Exploitation of dengerous Methods :
		- For example (Request):
			- PUT /dav/abc.txt HTTP/1.1
			........
			........
			........
			This a Message

		- Now the abc.txt file is created on the server using PUT Method.
		- Instead of PUT Method try using DELETE Method.

**3. Application server as proxy** :
	- Using GET Method give full url of the 3rd party website if in the response you see the content of 3rd party website, then there is a vulnerability.

		Example 1: GET http://3rdpartyweb.com/ HTTP/1.1
		Example 2: CONNECT 3rdpartyweb.com:80
		Response: HTTP/1.0 200 OK
		Connection Established 
		(Then there is a vulnerability)

**4. Web Server Software Bugs** :
	- Identify the services running on a server. (nmap is a good option)
	- Try finding if any exploit is available for that particular version of the service. (expoiltdb and searchsploit are good options)
	- Fire up the metasploit and use the expolit for that version.
	- Identify any known vulnerabilites in the web application using Nessus or Acunetix.
	- Use http://whois.arin.net to identify the range of IP address assinged to the perticular domain.
	- (Tip - If possible, consider performing a local installaiton of the software you are attacking, and carry out your own testing to find new vulnerabilities that have not been discovered or widely circulated)
