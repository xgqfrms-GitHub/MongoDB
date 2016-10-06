# MongoDB : Store Data in MongoDB 

[https://www.freecodecamp.com/challenges/store-data-in-mongodb](https://www.freecodecamp.com/challenges/store-data-in-mongodb) 

[https://ide.c9.io/xgqfrms/mongodb](https://ide.c9.io/xgqfrms/mongodb)  



## Install learnyoumongo with this command: 

```sh
$ npm install learnyoumongo
``` 


## Install MongoDB with this command: 

```sh
$ sudo apt-get install mongodb-org
``` 


## Set up your mongod alias by following the directions at: 
[Setting Up MongoDB](https://community.c9.io/t/setting-up-mongodb/1717)

```sh
$ sudo apt-get install -y mongodb-org

$ mkdir data
$ echo 'mongod --bind_ip=$IP --dbpath=data --nojournal --rest "$@"' > mongod
$ chmod a+x mongod

$ ./mongod
``` 

>MongoDB parameters used:
--dbpath=data - Because it defaults to /var/db (which isn't accessible)
--nojournal - Because mongodb usually pre-allocates 2 GB journal file (which exceeds Cloud9 disk space quota)
--bind_ip=$IP - Because you can't bind to 0.0.0.0
--rest - Runs on default port 28017

```sh
$ mongo
``` 
































































     ,-----.,--.                  ,--. ,---.   ,--.,------.  ,------.
    '  .--./|  | ,---. ,--.,--. ,-|  || o   \  |  ||  .-.  \ |  .---'
    |  |    |  || .-. ||  ||  |' .-. |`..'  |  |  ||  |  \  :|  `--, 
    '  '--'\|  |' '-' ''  ''  '\ `-' | .'  /   |  ||  '--'  /|  `---.
     `-----'`--' `---'  `----'  `---'  `--'    `--'`-------' `------'
    ----------------------------------------------------------------- 


Welcome to your Node.js project on Cloud9 IDE!

This chat example showcases how to use `socket.io` with a static `express` server.

## Running the server

1) Open `server.js` and start the app by clicking on the "Run" button in the top menu.

2) Alternatively you can launch the app from the Terminal:

    $ node server.js

Once the server is running, open the project in the shape of 'https://projectname-username.c9.io/'. As you enter your name, watch the Users list (on the left) update. Once you press Enter or Send, the message is shared with all connected clients.

