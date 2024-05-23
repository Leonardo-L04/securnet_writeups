<h1>Time Converter</h1>

<h2>Description</h2>
I just made an Epoch to Human Readable time converter!

Check it out!

![index page](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/1.png)


<h3>Test the webapp</h3>
Firstly I tested what the webapp did.

![test1](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/2.png)
![test2](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/3.png)

Looks like I does what the name says :D

<h3>Exploiting</h3>
After knowing what it was doing I tried to run sqli and xss payloads. But I was unsuccessfull. 
All I got that was new was a new error code :')

![example](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/4.png)

Then after trying to run fuzzing tools and analyzing the website with burpsuite, I went back to read the challenge.
That's when I searched for the word "Epoch". Since my main language is not english I had to search it and I found this:

![print5](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/5.png)

![print6](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/6.png)

<h3><strong>✨ C o m m a n d  I n j e c t i o n ✨</strong></h3>

Then basically just used a valid input like "123" and then piped ls into it

![flag](https://github.com/Leonardo-L04/securnet_writeups/blob/main/img/7.png)
