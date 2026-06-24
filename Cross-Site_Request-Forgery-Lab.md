# SEED Labs: Cross Site Request Forgery

The objective of this lab was to gain hands-on experience with Cross-Site Request Forgery (CSRF) attacks and understand how they can be used to exploit authenticated user sessions. Through this lab, I learned how a CSRF attack occurs when a victim who is logged into a trusted website visits a malicious website that sends unauthorized HTTP requests on the victim's behalf. By completing the exercises, I explored how attackers can take advantage of a user's active session to perform actions without the user's knowledge or consent and gained a better understanding of the security mechanisms used to defend against these attacks.

## The Lab

 <img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/36d741c6-413d-4533-9595-760ada6754ee" />

For the Cross-Site-Request-Forgery Attack to begin we have to get the docker containers up and running to begin the lab. Afterwards we head towards the dummy site where we can test the attack by taking advantage of the trust the site has between its user and browser. By going to seed-server.com and logging into an account we get access to information about the login with a http header extension that shows us the information shared between the site and the browser. When we login as “Samy” and we check “Alice” account from the add friend page we get information about her account that we should not be able to get.
 
<img width="632" height="348" alt="image" src="https://github.com/user-attachments/assets/dd2940b7-10d8-4035-adba-75d60b2bdd2d" />
 
By knowing her Guid = 56 we can now use that to out advantage and change information about her profile that should’t be able to be swapped.
 
 <img width="974" height="162" alt="image" src="https://github.com/user-attachments/assets/d364a858-1a24-49db-8a53-9058df2d2cff" />


By running this line of code, we can run a http get request from another site to get access to Alice’s account when she is using that specific page. The addfriend site forces Alice to add Samy as a friend. 

<img width="973" height="198" alt="image" src="https://github.com/user-attachments/assets/d190fd1c-de98-47ba-b42b-47b9c29891b9" />

This same philosophy can be applied to the edit profile portion of the page. By using the same http header extension, we can find the “POST” action and that is meant to update pages to utilize for our gain.  

<img width="974" height="380" alt="image" src="https://github.com/user-attachments/assets/58b1c059-1a42-4289-942b-81d9808a794b" />

After using the information, we gained from the http header extension we can put the exact fields we want to edit (edit profile) and change it to what we want. After running the editprofile site, Alice’s empty profile page changes to the from the code above.

<img width="610" height="196" alt="image" src="https://github.com/user-attachments/assets/0242b579-7439-422c-a467-61f89395ac42" />

<img width="613" height="231" alt="image" src="https://github.com/user-attachments/assets/61c46093-a814-4ddd-bb76-3ea9fd713e9d" />

A way to counter CSRF attacks is by using an elgg based application which deals with generating, validating tokens and handling errors if a missing token is detected. 

<img width="974" height="91" alt="image" src="https://github.com/user-attachments/assets/495515b9-ea42-48d1-8f00-007bd9b07a28" />

We also need to comment out this section of the attack since it allowed the CSRF to work in the first place by disabling its countermeasures. So, when we have the elgg code running and try to maliciously add a friend to Alice’s account we get this error instead, successfully thwarting the CSRF attack.

 <img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/a4cb2990-5367-422c-9fdd-788c85d7a103" />

