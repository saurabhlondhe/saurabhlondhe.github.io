---
layout: post
title:  "IRC Bot in Python"
date:   2018-10-24
desc: "A Chat bot over IRC written in python"
keywords: "bot,python,irc,internet relay chat"
categories: [Project,Python,Linux]
tags: [open source,python, Chat Bot,irc]
icon: icon-python
---
![IRC #demobot](https://img.shields.io/badge/freenode-%23demobot-green.svg)
### IRC (Internet Relay Chat)
IRC is a communication medium where peoples talk on the same topic over the world. There are hundreds of channels hosted on IRC. There are client programs who provide a GUI which is easy to log on and chat. IRC servers do use the same socket server-client architecture for communication.  So we are going to design bots in python using socket programming.

### What Python can do?
Python having great library collections and easy to understand. Like other languages, Python have socket module through which we can communicate to the servers. Socket create communication between two entities. python is good for ML so designing bot using Python is easy.

---

### Python Basics

```python
import socket           # import socket

irc = socket.socket(socket.AF_INET, socket.SOCK_STREAM)         # create socket object

irc.connect((server, int(PORT)))            # server(ip of server) and port number

irc.send("text")        # sends a message to server

print(irc.recv(2048))       # receive a message from server
```


### IRC basics
-   IRC - Internet Relay Chat
-   irc port : ```6667```
-   *irc server : ```chat.freenode.net```
-   *channel : #demobotin
    -   is a network where we can do communication with others
-   *nickname : botname

join irc channel [here](https://webchat.freenode.net/?channels=%23demobot) before starting
```sh
PRIVMSG <channel-name> <user-name> <msg> #sends private messege to channel
```

## Starting with code. . .
-   importing modules
    -   sys
    -   socket
    ```python
    import sys
    import socket
    ```

-   Initialization
    ```python
    channel = "#demobot"
    server = "chat.freenode.net"
    botnick = "hello_bot"
    NAME = "Love Python"
    port = 6667
    ```

-   connecting to server by creating socket connection
    ```python
    irc=socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    irc.connect((server,port))
    print("connected")
    ```

-   send user name to server
    ```python
    irc.send("USER " + botnick + " " + botnick + " " + botnick + " :"+NAME+"\n")
    ```

-   send nick name to server
    ```python
    irc.send("USER " + botnick + " " + botnick + " " + botnick + " :"+NAME+"\n")
    ```

-   joining channel
    ```python
    irc.send("JOIN " + channel + "\n")
    ```

-   reply with greetings
    ```python
    hi_greet=["hi","hi!","hey","hey!","hello","hello!"]

    irc.send("PRIVMSG "+channel+" :"+user_name+", "+hi_greet[random.randint(0, 5)]+" \n")
    ```

---
### Source code :-
```python
import platform
import random
import socket
import sys

reload(sys)
sys.setdefaultencoding('utf8')


channel = '#demobot'
server = "chat.freenode.net"
botnick = hello_bot
PORT = 6667
sentUser = False
sentNick = False
hi_greet=["hi","hi!","hey","hey!","hello","hello!"]
irc = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
print "\nConnecting to:" + server
irc.connect((server, int(PORT)))
print ("done")

try:
    while 1:
        text = irc.recv(2048)
        if len(text) > 0:
            print text
        else:
            continue
#----------------------YOUR CODE WILL GO FROM HERE -----------------------
        msg=text.lower().split(":")[-1]
        user_name=text.split("!")[0][1:]
        print ("name:"+user_name)
        if msg.strip() in hi_greet:
            print("send pong")
            irc.send("PRIVMSG "+channel+" :"+user_name+", "+hi_greet[random.randint(0, 5)]+" \n")
            print("success")
#-------------------------------TO HERE ----------------------------------
        if text.find("PING") != -1:
            irc.send("PONG " + text.split()[1] + "\n")
            print("in ping")

        if sentUser == False:
            irc.send("USER " + botnick + " " + botnick + " " + botnick + " :"+NAME+"\n")
            sentUser = True
            print("set user name")
            continue

        if sentUser and sentNick == False:
            irc.send("NICK " + botnick + "\n")
            sentNick = True
            print("nick")
            continue

        if text.find("255 " + botnick) != -1:
            irc.send("JOIN " + channel + "\n")

        if text.find(":!host") != -1:
            irc.send("PRIVMSG " + channel + " :" + str(platform.platform()) + "\n")

except KeyboardInterrupt:
    irc.send("QUIT :I have to go for now!\n")
    print "\n"
    sys.exit()
```

---
***NOTE :***
code will work with python2

---

