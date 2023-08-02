# NWEN Server.c

![[assignment03.pdf]]

```
Server Program Specifications 
1. The program should accept one command line argument. Excluding the program name, the argument should specify the port number that the program will use. The program should immediately terminate with a return value of -1 if the argument is not specified. The program should also immediately terminate with a return value of -1 if the specified port number is less than 1024. 

2. Initiate the required socket operations to create and bind a socket. 

3. Listen for TCP clients at the port specified in the command line. (During testing, you may need to use a "random” port number to avoid conflicts with other students running tests on the same server.) 

4. When a client successfully establishes a connection with the server, send a HELLO message back to the client . 

5. Wait for a message from the client. 

6. Perform the following based on the message received from the client: 
	(a) If the message has the contents BYE (case-insensitive), close the connection to the client and go back to step 3. 
	(b) If the message has the contents GET (case-insensitive) followed by a file name (example: GET file.txt), open the file as text file for reading. The file should be located in the same directory as the server program. If the opening is successful, send the following back to the client: 
	SERVER 200 OK\n \n (Contents of file)\n \n \n 

	You must follow this format strictly. Note that there is a single empty line (a newline) after SERVER 200 OK and two empty lines (two newlines) after the contents of the file. If the opening is not successful, send the following back to the client: SERVER 404 Not Found\n For any other error encountered (e.g., no file name is specified in the GET message), send the following back to the client: 3 NWEN 241 2023T1 (Weeks 6–7 Topics) Assignment 3 SERVER 500 Get Error\n 
	
	(c) If the message has the contents PUT (case-insensitive) followed by a file name (example: PUT file.txt), open the file as text file for writing (if the file exists, existing contents must be emptied). The file should be located in the same directory as the server program. Write every message received from the client to the file. Upon receipt of two consecutive empty lines (just newlines), close the file. The last two consecutive empty lines should also be written into the file. After successfully closing the file, send the following back to the client: 
SERVER 201 Created\n For any other error encountered (e.g., failure to open file), send the following back to the client: SERVER 501 Put Error\n For other messages, send the following back to the client: SERVER 502 Command Error\n

```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

#define BUFFER_SIZE 1024

void error(const char *msg) {
    perror(msg);
    exit(-1);
}

int main(int argc, char *argv[]) {
    int sockfd, newsockfd, portno;
    socklen_t clilen;
    char buffer[BUFFER_SIZE];
    struct sockaddr_in serv_addr, cli_addr;
    int n;

    if (argc != 2 || (portno = atoi(argv[1])) <= 1024) {
        error("Invalid arguments.");
    }

    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    
    if (sockfd < 0) 
        error("Error opening socket.");
        
    bzero((char *) &serv_addr, sizeof(serv_addr));
    
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_addr.s_addr = INADDR_ANY;
    serv_addr.sin_port = htons(portno);

    if (bind(sockfd, (struct sockaddr *) &serv_addr,
              sizeof(serv_addr)) < 0) 
        error("Error on binding.");
        
	  listen(sockfd, 5);
	  clilen = sizeof(cli_addr);

	  while(1) {
		    newsockfd = accept(sockfd,
		                 (struct sockaddr *) &cli_addr,
		                 &clilen);

		    if (newsockfd < 0)
		    	error("Error on accept.");

		    bzero(buffer, BUFFER_SIZE);
		    strcpy(buffer,"HELLO");
		    
		    n = write(newsockfd, buffer, strlen(buffer));
		    
		    if (n < 0)
		    	error("Error writing to socket.");

	      // Your code for handling client messages here.

	      close(newsockfd);

	  }

    close(sockfd);
    return 0; 
}
```
> [!failure]- Failure 
>   Error: There is another generation process
>   
>   - plugin:obsidian-textgenerator-plugin:56949 TextGenerator.eval
>     plugin:obsidian-textgenerator-plugin:56949:31
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>   - plugin:obsidian-textgenerator-plugin:62 __async
>     plugin:obsidian-textgenerator-plugin:62:10
>   
>   - plugin:obsidian-textgenerator-plugin:56935 TextGenerator.generate
>     plugin:obsidian-textgenerator-plugin:56935:12
>   
>   - plugin:obsidian-textgenerator-plugin:58440 AutoSuggest.eval
>     plugin:obsidian-textgenerator-plugin:58440:52
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>  

> [!failure]- Failure 
>   Error: There is another generation process
>   
>   - plugin:obsidian-textgenerator-plugin:56949 TextGenerator.eval
>     plugin:obsidian-textgenerator-plugin:56949:31
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>   - plugin:obsidian-textgenerator-plugin:62 __async
>     plugin:obsidian-textgenerator-plugin:62:10
>   
>   - plugin:obsidian-textgenerator-plugin:56935 TextGenerator.generate
>     plugin:obsidian-textgenerator-plugin:56935:12
>   
>   - plugin:obsidian-textgenerator-plugin:58440 AutoSuggest.eval
>     plugin:obsidian-textgenerator-plugin:58440:52
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>  
