- No matter the type of CSRF protection deployed, you can always try two things 
	1) _Clickjacking_
	2) _Changing the request method_

**1) Clickjacking :-**
	Exploiting clickjacking on the same endpoint bypasses all CSRF protection. Because technically, the request is indeed originating from the legitimate site. If the page where the vulnerable endpoint is located on is vulnerable to clickjacking, all CSRF protection will be rendered irrelevent and you will be able to achieve the same results as a CSRF attack on the endpoint.

**2) Change the request method :-**
	Another thing worth trying is changing the request method of the request. If the sensitive request that you would like to forge is sent via the POST method, try converting the request to a GET request. And if the action is done via a GET, try converting it into a POST. The application might still execute the action and the same protection mechanism is often not in place.

		For example, this request:                                                 
		POST /change_password                                                      
		POST body:new_password = test123                                        
		Can be rewritten as:                                                         
		GET /change_password?new_password=test123

##### CSRF Protection via Tokens : 
Just because a site is using CSRF tokens does not mean that it is validating them properly.
Here are few things to bypass CSRF protection via tokens -

**1) Delete the token param or send a blank token :-**
	Not sending a token works fairly often because of this common application logic mistake: applications sometimes only check the validity of the token if the token exists, or if the token parameter is not blank. In this case, sending a request without the token, or a blank vlaue as the token may be all you need to bypass the protection.
	
		For example, if a legitimate request looks like this:

		"
		POST /change_password
		POST body:
		new_password=test123 &csrf_tok=871caef0757a4ac9691aceb9aab8b65b
		"
		
		Try this:
		
		"
		POST /change_password
		POST body:
		new_password=test123
		"
		
		Or, this:
		"
		POST /change_password
		POST body:
		new_password=test123 &csrf_tok=
		"

##### 2) Use another session's CSRF token :-
The application might only be checking if the token is valid or not, and not checking if it belongs to the current user. If that's the case, you can simply hard code your own CSRF token into the payload!

Let's say victim's token is **871caef0757a4ac9691aceb9aad8b65b**, and yours is **YOUR_TOKEN**. You can obtain your own CSRF token easily but not the victim's token.
Try to bypass the CSRF protection by providing your own token in the place of the legitimate token.

		In other words, instead of sending this:

		"
		POST /change_password
		POST body:
		new_password=test123 &csrf_tok=871caef0757a4ac9691aceb9aad8b65b
		"

		Send this:
		"
		POST /change_password
		POST body:
		new_password=test123 &csrf_tok=YOUR_TOKEN
		"

### CSRF :
- Is used in HTML forms (not AJAX)
- Produced in backend while rendering HTML form.
- We can not set request header in HTML forms directly, so we have to send it via form input as a hidden field.

### X-CSRF-Token :
- It is added to the request HTTP header for AJAX requests.
- To use it, we can put the csrf value in a <meta> tag while rendering the HTML, then in front end we can get the value from that <meta> tag and send it to backend.
















































