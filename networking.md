Today, we're going to learn a bit about how networks and the internet work!

Computers need to know how to reach each other on the internet.  How do you know where to find someone that you know?
* Phone Number
* Address

Computers also use addresses to locate one another.  Open up a command prompt (Start -> cmd) and type "ipconfig".  This 
will show you a bunch of information about how to find your computer!

```
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . : hsd1.pa.comcast.net.
   IPv6 Address. . . . . . . . . . . : 2601:4a:8200:9192:88c9:1925:5531:81ee
   IPv6 Address. . . . . . . . . . . : 2601:4a:8200:9192:e56a:7359:3b85:3b80
   Temporary IPv6 Address. . . . . . : 2601:4a:8200:9192:145d:8111:89b:a355
   Link-local IPv6 Address . . . . . : fe80::e56a:7359:3b85:3b80%19
   IPv4 Address. . . . . . . . . . . : 10.0.0.9
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::226:f3ff:fed4:ddf2%19
                                       10.0.0.1
```

The <b>IPv4 Address</b> is the local address of your computer.  All of the computers on a local network are behind a <b>router</b> that manages
connections to and from the local network.  So, nobody outside of the school could contact your computer directly.  They would have to go 
through the router, which has rules about what computers are allowed to be contacted!

The <b>IPv6 ADdress</b> is a new feature that is not currently in use by most systems.  There are a limited number of addresses in 
IPv4!  How many addresses are there?  Note that there are 4 numbers in use between 0 and 255 (256 options each). 
Answer: 256*256*256*256 = 4,294,967,296

Why is this a problem?  Well, there are 7.5 billion people on Earth and only 4.3 billion IPv4 addresses.  So, if everyone has a phone 
connected to the Internet, we'll run out of possible addresses quickly.  Obviously, not everyone has a phone or computer, but we need
to be prepared for people with multiple devices and upcoming use-cases like Internet-connected cameras, appliances, and cars.  How many
addresses are available on IPv6?  65,536^7 * 256 = 1.32x10^36 (Undecillion) 1 trillion * 1 trillion * 1 trillion

The <b>Subnet Mask</b> groups machines on the network and allows the networking hardware to quickly determine which machines are allowed
to do certain tasks.

The <b>Default Gateway</b> is the IP Address of the router or switch that connects this computer to the rest of the Internet.  At home,
you can put that address into a web-browser to change how your network works.

Next, we're going to learn about how to find another computer's IP Address.  We need an IP Address to do things like browse a website 
or connect to a server that runs a game.

In the command prompt, type:

```
ping www.google.com
```

After running the command, you should see output that looks something like this:

```
Pinging www.google.com [172.217.7.132] with 32 bytes of data:
Reply from 172.217.7.132: bytes=32 time=20ms TTL=54
Reply from 172.217.7.132: bytes=32 time=19ms TTL=54
Reply from 172.217.7.132: bytes=32 time=22ms TTL=54
Reply from 172.217.7.132: bytes=32 time=30ms TTL=54

Ping statistics for 172.217.7.132:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 19ms, Maximum = 30ms, Average = 22ms
```

<b>Pinging</b> a server checks to see if it's there.  It has the side-effect on our computers of showing us the 
IP Address of another computer.  Try another request to "drive.google.com".

```
ping drive.google.com
```

Which numbers have changed?

```
Pinging drive.google.com [172.217.10.46] with 32 bytes of data:
Reply from 172.217.10.46: bytes=32 time=19ms TTL=52
Reply from 172.217.10.46: bytes=32 time=24ms TTL=52
Reply from 172.217.10.46: bytes=32 time=21ms TTL=52
Reply from 172.217.10.46: bytes=32 time=17ms TTL=52

Ping statistics for 172.217.10.46:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 24ms, Average = 20ms
```

The first two numbers stayed the same.  Try another domain (e.g. www.seas.upenn.edu)

```
Pinging www.seas.upenn.edu [158.130.68.91] with 32 bytes of data:
Reply from 158.130.68.91: bytes=32 time=20ms TTL=49
Reply from 158.130.68.91: bytes=32 time=22ms TTL=49
Reply from 158.130.68.91: bytes=32 time=111ms TTL=49
Reply from 158.130.68.91: bytes=32 time=62ms TTL=49

Ping statistics for 158.130.68.91:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 20ms, Maximum = 111ms, Average = 53ms
```

What changed now?  So, how do we find the IP address of a website given it's name?

The Domain Name System (DNS) maps from the name of a computer to its address.  In the old days, there was a text file called "HOSTS.txt"
that stored all of the addresses on the Internet.  To get a new address, a person had to call a single person who managed the text
file and request a new name and address.  Now, we need something that scales better than a single person taking phone calls.

A DNS-lookup starts with the last part of the address first.  We discard anything after the "/" because that is the path to the
file we're trying to access.

So, for www.google.com, we first go to the <b>com</b> server.  The <b>com</b> server tells us the location of the <b>google</b> 
server.  Once we get to a <b>google</b> server, Google can further route our request to the <b>www</b> server, which is where
web pages are stored.

How would we route to www.seas.upenn.edu/delozier/index.html?

```
edu
upenn
seas
www
/delozier/index.html
```

Here is a map of all of the addresses in use on the internet:  http://cse1.net/recaps/img/6-map.png

It's important that DNS is <b>distributed</b>, meaning that it's spread across many computers that have the same information.
Why is this important?  If DNS was stored on one computer, how would you attack the Internet?

Once we get to the computer that we're trying to talk to, how does it know what we want?  For example, a computer is capable
of running a web server (for website pages), an ftp server (for storing files), and a chat server (for AIM or IRC).
The <b>www</b> in the address indicates the specific service that we're looking for.  Each computer has a set of <b>ports</b>
on which it can accept network connections.  Port numbers range from 0-9999.  Port numbers are one to one in that a computer
can only open a port for connection once (e.g. web pages and files cannot come from the same port).

Some common ports are 80 (HTTP) and 21 (FTP).  Most servers will use these numbers so that there is consistency across all 
servers.

Next, we'll look at how to get the contents of a website in Processing:

```
void setup(){

}
```
