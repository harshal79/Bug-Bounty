A pre-defined session cookie is planted into the victim's browser. So after the victim logs into a website, they will use the same session cookie that the attacker already knows, and thus the attacker-owned cookie is now authenticated and can be exploited.

### Case 1 :- 

+ Browser 1 (same application) ---------> Copy cookie before login
+ Browser 2 (same application) ---------> Try to login with that copied cookie
+ Browser 1 (same application) ---------> Refresh the browser or try to login with same cookie -------> if you will be logged in then there is a session fixation

### Case 2 :- 

+ Browser 1 (same application) ---------> Login First ----> Copy Cookie 
+ Browser 2 (same application) ---------> Import copied cookie ----> If you will be logged in then there is a session fixation

### Case 3 :-

+  Browser 1 (same application) ---------> Login First ---> Copy Cookie ---> Logout
+  Browser 2 (same application) ---------> Login using copied cookie ---> If you will be logged in then there is a session fixation

### How to Test Session Fixation?

- Session-ID same pre and post login. 
	* Step 1 - Visit login page. Go to cookie editor extension which is already installed in web browser and edit cookies. Copy Session-ID.
	* Step 2 - Login inot application. Again, visit cookie editor. Copy cookie.
	* Step 3 - If both cookies are same then report the issue.

### Recommendation : -

- The first focus on the sesssion token itself. Create a new session token, associate the new session token with the existing session, disassociate the old session token, pass the new session token to the client.

- The second foucs on the entire session. Create a news sesssion, copy all the of the session data from the old session to the new session, destory the old session, pass the token associated with the new session to the  client. 
