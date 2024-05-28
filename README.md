# Learning-Cybersecurity-Attack-and-Defence
Testing the resistance of cybersecurity attacks of a travel agency website, and demonstration on two versions of website, protected and unprotected.

/////The main goal of this project is to teach people how to protect their site from user data theft, XSS attacks, CSRF attacks, as well as selecting user passwords using the Bruteforce method for people without experience or people with a small amount of it./////

/////Install guide://///

To use our project you need to install: OpenServer
1) Main.no - unprotected version of the project
2) Main.security - protected version of the project

Just install two version of website, place it in the projects folder and configure data base.

1)areaweb - name of the DB to unsecured(Main.no) project
2)areaweb2 - name of the DB to secured(Main.security) project

If you want to change the name of the DB, you can you can go to config files(src/config.php) and and change it in DB_NAME const, and you should note that if DB name is changed in code it also should match in phpMyadmin DB name.

/////About protection://///

1)Hashing method

1. password_hash
Purpose: This function is used to create a password hash. The hashed password can then be stored in a database.
Usage: It takes the plain text password and a hashing algorithm as parameters and returns a hashed password.

2. password_verify
Purpose: This function is used to verify that a given plain text password matches a hashed password.
Usage: It takes the plain text password and the hashed password as parameters and returns true if they match, or false otherwise.

3. PASSWORD_DEFAULT
Purpose: This is a constant used to indicate that the default algorithm should be used when hashing a password. The default algorithm can change over time as new and stronger algorithms are added to PHP.
Usage: When using PASSWORD_DEFAULT, PHP will automatically choose the best available hashing algorithm.

2)Brute-force Defence

Step 1:
A database query is performed to get the number of login attempts for specific email data and the time of the last attempt for entering with this email.
Also It checks whether there is a record of login attempts for this email at all.

Step 2:
If the number of attempts is greater or equal to the maximum value, and the time of the last attempt to enter is less than the timeout expire time, an error message will be displayed.

Step 3:
If more time has passed than the timeout expire time, the attempt counter will reset to zero.

Step 4:
If a record of login attempts does not exist, this function will create it.

Step 5:
If the user with the specified email address is not found, the attempt counter is increased to one and an error message will be displayed.
Additionally If the password is incorrect, the attempt counter is also increased for entered email and an error message will be displayed.

Step 6:
Upon successful login, the attempt counter  resets to zero and the time of the last attempt will be updated.

3)Xss defence

The htmlspecialchars() function in PHP converts special characters into HTML entities. This means that the characters <, >, &, ' and " are replaced with their HTML codes, which prevents the execution of the code entered by the user as HTML or JavaScript.

When it comes to protecting a web application from XSS attacks, the main task is to make sure that any user input that is displayed on the page is safe. To do this, this function needs to escape all the data before displaying it on the page. In our example, we used the htmlspecialchars() function, which is an effective way of escaping.

4)Csrf  defence

Step 1: Generating a CSRF token
Each time a user loads a page with a form, a unique CSRF token is generated. This token is stored in the user's session and is used to verify the authenticity of requests coming from the form.

Step 2: Include the CSRF token in the form
Each form, which should be protected from CSRF attacks, now contains a hidden field in which the CSRF token is stored. This token is passed along with the form when it is submitted.

Step 3: Checking the CSRF token in the handler
When the form is submitted, the server checks whether the CSRF token matches the value stored in the user's session. If the tokens do not match, the request is rejected.

Result
Now, every time a user submits a password change form, the server checks the CSRF token. If the token is missing or does not match the value stored in the session, the request is rejected and the user sees an error message. This protects our site from CSRF attacks, since an attacker will not be able to forge a request on behalf of a user without knowledge of the CSRF token, which is generated for each session and is not transmitted to third-party sites.
