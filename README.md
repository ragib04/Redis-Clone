 ![enter image description here](https://img.shields.io/badge/python-3.8-blue.svg)
# Redis-Clone
This is a prototype for Redis with some basic functionalities. Itan be used like any REST API. 
### Table of Contents
 <details>
   <summary>Click to expand!</summary>

   ##### Redis-Clone
   1. Usage
   2. Overview
   3. Functions Implemented
      * GET()
      * SET()
      * EXPIRE()
      * ZADD()
      * ZRANGE()
      * ZRANK()
      * DELETE()
      * ZREVRANK()
      * ZREVRANGE()
      * TTL()
      * PING()
   4. Questions
 </details>
 
### Usage
 To use the app the dependency mentioned in the requirements.txt must be satisfed. 
Once the dependency has been satisfied app.py can directly be executed via any CLI. 

    python3 app.py
The server will then be live on [http://localhost:5000/](http://localhost:5000/)

### **Overview**
This prototype is an attempt to give Redis like functionalities. 11 different Redis functions have been implemented in this prototype. The most difficult part in this prototype was to attain persistence. 
#### Persistence
This was a major problem that aroused during the development of the project. This problem is solved in a very Novel way in this prototype. 
This problem is solved by logging. Here is the algorithm that was used to solve this problem:

1. A local txt file is created that will log all the queries that can alter the database(Ex: SET, DELETE, EXPIRE). A snapshot of a log file is shown below. 

![enter image description here](https://github.com/tcd97/Redis-Clone/blob/master/src/test/log_file.png)

2. Once the server is stopped then the complete database is erased(State Lost). But when the server is live again then first all the queries present in the log are executed to gain the lost state. 

Thus persistence is achieved in this way. 
This technique is used by Redis and is called Logging. 
Another method called Snapshotting is also used by Redis on demand of the user. This is not implemented here due to lack of time. 
Logging has some disadvantages which is discussed in Questions section

