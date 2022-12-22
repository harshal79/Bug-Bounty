###### Tool
1. SubBrute 
	https://github.com/TheRook/subbrute.git
	`Use: ./subbrute.py target.com > subdomain.txt`
	`Use(for subdomains of subdomains): ./subbrute.py -c 100 -t subdomains.txt > newsubdomains.txt`
2. altdns (subdomains of subdomains)
	https://github.com/infosec-au/altdns.git
	`Use: ./altdns.py -i subdomains.txt -o output -w words.txt -r -s output.txt -t 100`
3. httpstatus.io(website)
	Check status codes, response headers, and redirect chains.
4. Sublist3r (works with python3)
	https://github.com/aboul3la/Sublist3r.git
5. Aquatone
	This tool can list subdomains and check for subdomain takeover and scan a large port range too.
	https://github.com/michenriksen/aquatone.git

+ Before you start looking for vulnerabilities, it's essential to know what your target is using as a technology to work:
	+ _Do they use a WAF like CloudFront or CloudFlare ?_
	+ _Do they use a CMS like Wordpress, Drupal or Joomla ?_
	+ _Do they use a framework like AngularJS or CakePHP ?_
	+ _What's the version of Apache ?_
	+ _Do they use template engine like Jinja2 or Smarty ?_
	``"It's better if you have the version"``

 >For example: Your target hava a profile page where you can control input (like name or address) which is reflected on a public page. If you know the framework version, you can possibally try XSS PayLoads or others payloads !
 >
 >If your target use a tmeplate engine like Smarty, check the version and try template injection!

+ To get these information about a target, use a plugin called **Wappalyzer**.

###### Google Dorks:
Use Google Dorks like follow:
	_site:target.com --www_
	_site:target.com intitle:"test" -support_
	_site:target.com ext:php | ext:html_
	_site:subdomain.target.com_
	_site:target.com inurl:auth_
	_site:target.com inurl:dev_

###### Shodan.io (search engine for Internet-connected devices):
It's like Google but for servers, IoT and all devices which can be connected to Internet.
	Here are the basic search filters you can use:
		1) _country_: find devices in a particular country
		2) _geo_: you can pass it coordinates
		3) _hostname_: find values that match the hostname
		4) _net_: serach based on an IP or /x CIDR
		5) _os_: search based on operating system
		6) _port_: find particular ports that are open
		7) _before/after_:  find results within a timeframe

##### The pefect worddlist for Bug Bounty:
SecLists : 
	Include usernames, passwords, URLs, sensitive data patterns, fuzzing payloads, web shells, and many more.
	Lists all common extension like .php, .asp, .txt, .bak, .old, .conf, .config ... and lots of interesting filename, payloads and fuzzing lists.
	https://github.com/danielmiessler/SecLists.git

##### Tools for content discovery
- Dirsearch : https://github.com/maurosoria/dirsearch.git
- Dirb : Pre-installed in Kali

###### Finding hidden GET & POST parameters :
 - Sometimes developers "hide" parameters in GET or POST queries, and sometimes it can be interesting to try to find these parameters and inject payloads into them.
 - For this use tool called **Arjun**. 
 - https://github.com/s0md3v/Arjun.git

##### Burp Suite :
 With BurpSuite, you have a good option to list and find **.JS** scripts. Export all JS scripts to a file.
+ **Tool**
	+ Relative-url-extractor : 
		This python script tries to extract URLs endpoints stored in JS scripts. 
		https://github.com/jobertabma/relative-url-extractor.git
	-  Virtual Host Discovery :
		This script help you find Vhost behind a target. 
		Many targets have a **Vhost** like _"admin"_ or _"beta"_ that are not properly protected !
		https://github.com/jobertabma/virtual-host-discovery.git
