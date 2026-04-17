Web Server
  Contributors
    Holten Bradley
    Mohamed Suliman
    Rishab Ambekar

----------------- How to -----------------

This web server is developed in C. It will need to be ran on Linux machines or Ubuntu for windows and apple machines. 

https://ubuntu.com/desktop/wsl

Follow this link to download and run Ubuntu for Windows (Windows Subsystem for Linux). Also, make sure to download git on your computer. https://git-scm.com/install/


You should be able to clone this repository, navigate to the project in your terminal, and run with the following commands.
$ git clone https://github.com/holten-bradley/webServer
$ cd webServer
$ ./web_server 9000 ./testing 5 5 50 50

Then, in a new terminal, you will use wget to query the server and fetch the URL.

$ wget http://127.0.0.1:9000/image/jpg/29.jpg

This project also has folders of URLs to fetch multiple with the same command.

$ wget -i <path-to-urls>/urls -O results

If you can not get the path, right-click on the URLs or bigurls file and select properties to get the absolute path.


----------------- Editor's Notes -----------------

Below is our class submission for this project. It does not have a lot of explanation, so I will add that now.
This works like any other web server. Requests are made to a server and fetched from the World Wide Web.
This particular server uses a cache and multi-threading to fetch these URLs faster. This means our most recent searches will stick around in our short-term memory so that we can retrieve them faster than long-term memory.
The cache also helps us to navigate our long-term memory faster. We can search based on these short-term memory locations instead of starting from the beginning.

Since this is written in C, we are handling memory allocation. 
In most languages, this is done for us. In this project, we want to make sure we have full control of our memory to organize it and keep fetches optimized.

The multi-threading is also handled manually. We have worker threads and dispatcher threads. 
Dispatcher threads listen to the client and queue requests, and the worker threads go grab from the queue, process the request, and deliver it to the client.

The difficult part of creating a web server is thread management. We need to avoid deadlocks. 
Deadlocks are threads that are waiting on one another to finish their task. Neither can finish while the other is waiting on their current task.
To avoid these server-crashing events, we lock threads manually. We will lock any new requests once a dispatcher is talking with a client, and/or worker threads as they are searching through memory.


This was all very interesting to learn and develop. It challenged us to think in terms of computing and memory layouts instead of having object oriented coding languages complete it for us.

----------------- Class Submission -----------------

CSCI-4061 Fall 2022 - Project #3 Group 99

Mohamed Suliman (sulim016)

Holten Bradley (bradl515)

Rishab Ambekar (ambek006)


We have developed a server.c which can be run linked with the given util files through ./web_server using the make file. 
This server will use the local port to start the server and recieve requests through that port. 
It will then save all requests that have been fufilled in a file, wget-log. 
All requests are handled by the dispatcher which then sends the request to the worker who handles the url to get said connection.

To run the file: ./webserver port path num_dispatcher num_workers queue_length cache_size
See /testing/how_to_test for more details

Then, use wget in a seperate terminal to send requests to the port in which web_server was run.

This must be run on a linux 64 machine.
This was run on Linux csel-kh4250-15 5.15.0-56-generic #62~20.04.1-Ubuntu SMP Tue Nov 22 21:24:20 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
Through the University of Minnesota.
