# SEED Labs SQL injection Attack Lab 
SQL injection is a code injection technique that exploits the vulnerabilities in the interface between web applications and database servers. The vulnerability is present when user's inputs are not correctly checked within the web applications before being sent to the back-end database servers. Many web applications take inputs from users, and then use these inputs to construct SQL queries, so the web applications can get information from the database. Web applications also use SQL queries to store information in the database. These are common practices in the development of web applications. When SQL queries are not carefully constructed, SQL injection vulnerabilities can occur. The SQL injection attack is one of the most common attacks on web applications.

## The Attack

This lab has us experimenting with SQL injection attack that interferes with queries that web application is trying to make with its database, allowing us to modify data beyond its intended purpose.
 
 <img width="975" height="343" alt="image" src="https://github.com/user-attachments/assets/8848eec1-1bab-4b2a-983c-f92705a7da06" />

To start we start up them dockers and gain access to the database from the terminal allowing us to see the information of its users and other various details. The lab has us get accustomed with some of the commands in SQL before continuing with the attack.  

 <img width="350" height="339" alt="image" src="https://github.com/user-attachments/assets/b5e5aac6-2e4c-4a29-aa3b-fbfc33eda10a" />

<img width="698" height="258" alt="image" src="https://github.com/user-attachments/assets/47ed2b24-7d6f-41c8-89b8-c69e43452a73" />

From there we are out able to see what type of info Alice has from her salary to SSN and id, with this information we can try to see if we can manipulate those columns to what we want.

<img width="944" height="136" alt="image" src="https://github.com/user-attachments/assets/bb12e333-69c4-47be-95bf-6e7fc34cd586" />

We head over to the site where the information is being sent to the database and from there, we attempt our SQL injection attack through the username to gain access to the admins account. By using the # symbol we comment out the rest of the query effectively only making the system check for the username and bypass the password validation.

  <img width="792" height="356" alt="image" src="https://github.com/user-attachments/assets/79c77be5-1b5b-443b-9be3-aa372acde412" />

In the admin profile we can see the information of all the users which are currently in the database. After proceeding with this we log out of the admin account and enter Alice’s account in an attempt to change information like her salary to something that fits her better. 

<img width="974" height="260" alt="image" src="https://github.com/user-attachments/assets/b7640bd8-cbac-4268-927b-b4227c6fa994" />

In the same way we accessed the admin account we do with Alice and like that we are in her account. We head over to her edit profile page and that’s where the real magic is able to happen. 

<img width="500" height="140" alt="image" src="https://github.com/user-attachments/assets/3a234f88-4dbc-485e-9829-bf1e775d4848" />

By making a SQL query to change her salary from 20000 to 30000, and point the change to her id (which is 1) we are able to comment out the rest of the query allowing us to bypass the authentication process of an information change.   

<img width="419" height="382" alt="image" src="https://github.com/user-attachments/assets/12e2a918-948f-4731-9d89-07389d598968" />

<img width="974" height="230" alt="image" src="https://github.com/user-attachments/assets/94606158-8533-47d7-b302-e89192ab13fd" />

The next part of the lab has us changing Boby salary to 1 but I like Boby’s name so I switched from 30000 to 40000 using the same method as the one we used with Alice.   

<img width="974" height="154" alt="image" src="https://github.com/user-attachments/assets/a4fb0f31-404b-4f4c-9eb6-37038d358f3c" />

<img width="704" height="42" alt="image" src="https://github.com/user-attachments/assets/786962fd-8a42-427d-912f-cd946e447ab3" />

Continuing from that section we were tasked with changing his password to something simple like “pwd”. Just like the previous section instead of targeting the salary column, we target the password column and follow the same steps as before to apply the attack  

<img width="974" height="108" alt="image" src="https://github.com/user-attachments/assets/fdccc1e4-9c43-4d2b-a369-86c79abb6b67" />

<img width="974" height="18" alt="image" src="https://github.com/user-attachments/assets/dc51c463-597e-4db3-a4bc-2563706fc67b" />

Now we learn how to defend against a SQL injection attack by modifying the script to properly sanitize inputs from the user to have it so when an attacker gains access to an attacker, they are unable to obtain any information on that page. 

<img width="974" height="330" alt="image" src="https://github.com/user-attachments/assets/8ad7776b-5213-4496-9e96-70cc83c5086d" />

<img width="735" height="356" alt="image" src="https://github.com/user-attachments/assets/7d097499-f2e2-44d5-b4f6-c6df201eec50" />

<img width="974" height="357" alt="image" src="https://github.com/user-attachments/assets/cb1fe857-daee-4c8f-8737-b22d94f26cc2" />

The way the code is setup in the original inception of the code leads to vulnerabilities because the query is directly inserting user input into the query string. We add the line of code from the screenshot below to prepare the SQL query with placeholders instead of directly taking in the user input. The database compiles ahead of time and treats everything after “?” inserted as data only. 

<img width="974" height="359" alt="image" src="https://github.com/user-attachments/assets/feb76d15-1daf-4126-aae1-e1d2a4fe8a3f" />

So now when the attacker enters the account all he sees is information slots are empty .
