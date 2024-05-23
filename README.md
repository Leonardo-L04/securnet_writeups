<h2>Description</h2>
I just made an Epoch to Human Readable time converter!

Check it out!

[print1]


<h3>Test the webapp</h3>
Firstly I tested what the webapp did.

[print2]
[print3]

Looks like I does what the name says :D

<h3>Exploiting</h3>
After knowing what it was doing I tried to run sqli and xss payloads. But I was unsuccessfull. 
All I got that was new was a new error code :')

[print4]

Then after trying to run fuzzing tools and analyzing the website with burpsuite, I went back to read the challenge.
That's when I searched for the word "Epoch". Since my main language is not english I had to search it and I found this:

[print5]

[print6]

C o m m a n d I n j e c t i o n

Then basically just used a valid input like "123" and then piped ls into it

[print7]
