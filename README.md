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
