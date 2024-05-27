<h1>Client</h1>

<h2>Description</h2>
Let's hack the Securnet admin account!

![index page](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/client/1.png)


<h3>Test the webapp</h3>
Firstly I tested to login with admin admin

![test1](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/client/2.png)

Maybe this could be a case of XSS, so then I inspected the page to see if there was any scripts in plaintext for me.

![script](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/client/3.png)

And there it was, the script that verified the login.
Now it's time to undo do find the flag.

<h3>Code breakdown</h3>

So this script basically checks the user and password

To verify the user it checks if in the username is equal to the sha-256 hash. In this case the username is 'admin' as said in the challenge description.

```
if (sha256(username) === "8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918") {
```

To verify the password it converts the specified unicode values into characters which gives the value <strong>a98781de7e7357236c73c5ae7311cbdb</strong>

```
if (password === String.fromCharCode(97, 57, 56, 55, 56, 49, 100, 101, 55, 101, 55, 51, 53, 55, 50, 51, 54, 99, 55, 51, 99, 53, 97, 101, 55, 51, 49, 49, 99, 98, 100, 98)) {
```

Then after verifying the inputs it constructs the flag by concatenating the string "flag{" (made here String.fromCharCode(102, 108, 97, 103, 123)) with the password and then closing the bracets with "String.fromCharCode(125)". If the username and password are right the flag will be shown on an alert box.

```
var flag = String.fromCharCode(102, 108, 97, 103, 123) + password + String.fromCharCode(125);
alert(flag);
console.log(flag);
```


<h3>Solving</h3>

So after analyzing the code we have the username "8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918" and the password "a98781de7e7357236c73c5ae7311cbdb"

Since the password is a SHA-256 string you just need to go to a online decrypter like this


![decrypt](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/client/4.png)


With that we know the user and passowrd, now just need to test the credentials and retrieve the flag :)

![flag](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/client/5.png)

And that's it ::D
