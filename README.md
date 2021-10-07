# D N S
### What happens when you enter www.example.com

Recently in an interview I was asked to describe the process of what happens when you enter www.google.com into a browser. I wanted to share my answer as I hear DNS being mentioned more and more in the news when applications like Slack or Facebook goes down. The inside joke being "It's always DNS". So what is it and how does it work?

DNS stands for Domain Name System and is how your browser converts a domain name to an IP address. Domain names, IP addresses, what’s all that? Well you can think of these like contacts in your phone. The domain name being the name of the contact and the IP address being the contact’s phone number. You call someone using their phone number but you would never memorize all the numbers for all of your contacts. Well it’s the same here, we communicate on the internet using IP addresses. IP addresses are 4 numbers between 0 and 255 separated by a period, for example 1.2.3.4. As humans we would never be able to memorize all the IP addresses for all the websites we like to visit. It would be too much. This is where DNS comes in. 

DNS resolves domain names to the IP addresses of the servers we want to communicate with. When you go to google.com and land on the homepage, it may seem like a simple process but a lot is happening in the background. The internet works on client-server communication. Our browser can act as a client requesting the google.com webpage and one of google’s servers serves us that content. Our browser makes the request to the server by going to the server's IP address and the server responds to our IP address. Just like your phone when you press on a contact and the phone calls the phone number. Going to google.com (google’s domain name) the browser goes to the correct IP address.

At the time of writing this a quick look at https://www.internetlivestats.com/total-number-of-websites/ showed that there are currently over 1.8 billion websites online right. Seems like a lot of contacts to save in your phone. This number is constantly growing too. This is where the system part of the Domain Name System comes into place. This is how it works,

We start by entering www.example.com into our browser. Our browser itself doesn’t translate this into an IP address nor does it know where to find the corresponding IP address. Instead it passes along this to a DNS resolver. The resolver will work on our behalf (still on the client side) to resolve the IP address.

Before we continue, let’s discuss what we entered into our browser. “www.example.com” is actually “www.example.com.” (note the period) this is referred to as a fully qualified domain name and it breaks down as follows,
“.” = root domain 
“com” = top level domain
“example” = 2nd level domain
“www” = 3rd level domain 
It breaks down in a hierarchical system where each level is separated by a period with the final period referring to the root domain. This will help the DNS resolver query for our requested webpage.  

First our DNS resolver looks at the “.” and knows this is the root domain therefore it will query the root name servers. There are 13 root name servers. Why 13? Well remember the 1.8 billion websites. That would be way too much for one place. Not to mention it would be a single point of failure and would be against the distributed nature of the internet. These root name servers break up this giant number and is out first point of call for this DNS Resolution. Our DNS resolver queries the root name server asking “do you know the IP address for www.example.com.?”. The root name server won’t know the IP address for our query however it will recognize the “.com”. It will give us the IP address for the “.com” name servers.


From https://www.iana.org/domains/root/servers 

.com is known as a top level domain. It is the highest place in the DNS system (after the root) and “example” is actually a subdomain of “.com”


![](./walkTheTreeGif.png)