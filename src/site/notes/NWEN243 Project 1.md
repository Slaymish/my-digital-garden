---
{"dg-publish":true,"permalink":"/nwen-243-project-1/"}
---


# Project 1

Contents: [[NWEN243 MOC\|NWEN243 MOC]]
Hamish Burke || 25-07-2023
***

## Q1

a) `eth0`
b) `12:14:96:6f:4f:b1`
c) `00010010 00010100 10010110 01101111 01001111 10110001`
d) 48 bits
e) `ff:ff:ff:ff:ff:ff`

![SCR-20230801-lxcz-2.png](/img/user/SCR-20230801-lxcz-2.png)

## Q2

a)

```
Public IPs: 44.210.142.241
Private IPs: 172.31.81.8
```

b)

```
fe80::1014:96ff:fe6f:4fb1
```

c)

```
32 bits
```

d)

```
00110100 00010111 10100111 00000001
```

e) 

```
1111111010000000 0000000000000000 0000000000000000 0000000000000000 0001000000010100 1001011011111111 1111111001101111 0100111110110001


128 bits
```

## Q3

![SCR-20230801-lxcz-2.png](/img/user/SCR-20230801-lxcz-2.png)

a)

```
172.31.81.8/20

The /20 means the first 20bits of the IP address is the network bits.

10101100 00011111 01010001 00001000 is the binary representation of the IP. 32 bits in total

So network = 10101100 00011111 0101
And host = 0001 00001000
```

b)

```
172.31.80.0 to 172.31.95.255
```

c) 

```
So 32-20 = 12
2^12 = 4096
4096 Total IP's
-2 for router and .0
= 4094 usable distinct IPs
```

## Q4

a)

```
Based on the CIDR notation which is /20, there are 20 network bits.
By setting all of these to 1, and the rest (the host bits) to 0, you get the netmask.


255.255.240.0
11111111111111111111000000000000
```

b)

![SCR-20230801-mgwj-2.png](/img/user/SCR-20230801-mgwj-2.png)

```
172.31.95.255
```

c) 

```
The broadcast address is the highest possible IP address.

This can be found by setting all of the host bits in IP address to 1.
You can use either CIDR notation or the netmask to find out how many bits are network bits. 

I converted the IP to binary:

10101100 00011111 01010001 00001000

Then set the host bits (last 12) to 1:
10101100 00011111 01011111 11111111

Convert to decimal:
172.31.95.255
```

## Q5

a)

![SCR-20230801-mjlm-2.png](/img/user/SCR-20230801-mjlm-2.png)

```
This is the only device on the LAN that I know about. The IP and MAC address are both the routers. Reachable means it is possible to send/recieve to.
```

b) 

![SCR-20230801-mjzd-2.png](/img/user/SCR-20230801-mjzd-2.png)

```
This shows that the default ip to route traffic to is 172.31.80.1. As shown in part(A), this is the router of the network this machine is on. Part A shows the MAC address of the router, which is important information so the sender and reciever knows if packets are designated for them.

'ip route list' shows what devices to route through, depending on the source IP. As theres only one other known device on the network, It is sending everything through 172.31.80.1. All of them use the eth0 wireless interface. 'proto dhcp' means that the route was obtained by DHCP. 'src 172.31.81.8' says what IP to use as source for packets sent from this machine. 'metric 100' is the cost assigned to the route. As they're all the same, this has no effect.
```

## Q6

a)

![SCR-20230801-mksh-2.png](/img/user/SCR-20230801-mksh-2.png)

```
IP1 = 172.253.122.136
```

b)

![SCR-20230801-mlnp-2.png](/img/user/SCR-20230801-mlnp-2.png)

```
IP2 = 142.250.74.142
```

c)

```
I took the average RTT

RTL_VM_IP1: 1.243ms
RTL_VM_IP2: 95.989ms
RTL_local_IP1: 91.646ms
RTL_local_IP2: 32.191ms
```

d)

```
The difference in the round trip time is likely because of the location of the VM/local computers in relation to the youtube server. IP1 is closer to the VM while IP2 in closer to the 'local' machine. The dns server they retrieved the IP from would have given them the closed server to them.
```

## Q7

a)

![SCR-20230801-ncta-2.png](/img/user/SCR-20230801-ncta-2.png)

b)

![SCR-20230801-nfvv-2.png](/img/user/SCR-20230801-nfvv-2.png)

c) 

```
Same:
- Hop 23 & hop 25 (IP1)


As shown in the above two traceroutes, my computer and the AWS machine didn't share any common links to IP1. This isn't very suprising as the location of my computer and the AWS instance is very different, so the path to get to the IP is likley to be different. If I ran it a few more times, I may find similar nodes for the last couple hops of the traceroute, at that is nearer to the end sever location. 
```

## Alt Q7

![SCR-20230813-pbsz-2 1.png](/img/user/SCR-20230813-pbsz-2%201.png)

a)

```
The first packet is an ARP Request, sent from the machine with an IP of 172.31.80.1. It's asking for the MAC address associated with 172.31.81.8. 

The second packet is a reply to that request. It gives the MAC address that IP address has.
```

b)

```
Each entry in an ARP table has a TTL. This is the amount of time before that information expires and needs updating. Its likely asking the same ARP query whenever the current ARP cache expires.
```

c)

```
By looking at the timestamps, the time difference between consecutive ARP requests is approximately 29.4629.46 seconds
```

## Q8

a)
![SCR-20230813-pyha-2.png](/img/user/SCR-20230813-pyha-2.png)

b)
![SCR-20230813-pxyk-2.png](/img/user/SCR-20230813-pxyk-2.png)

c) 

```
As shown in the above two traceroutes, there aren't any hops that have the exact same IP. This is because when I tried to run the traceroute on [www.wgtn.ac.nz](http://www.wgtn.ac.nz/), a lot of the nodes closer to the destination didn't send the ICMP Time Exceeded packet, which I need to see their IP. There may (and it is quite likely) be some nodes that would overlap, as I'm assuming the servers for both are located in approximately the same space.
```

## Q9

![SCR-20230805-skbz-2.png](/img/user/SCR-20230805-skbz-2.png)

![SCR-20230805-skgk-2.png](/img/user/SCR-20230805-skgk-2.png)

```
I did a traceroute from the aws instance ecs.vuw.ac.nz. I repeated this and shown above, even the first hop is different (as well as others [eg 2,3 etc]). This shows the multiplicity of paths available between any two nodes.

The second time I ran it, it actully took fewer hops as well, from 21 to 19. This shows how it must have found a more efficent route to get there.
```

## Q10

![SCR-20230805-smfp-2.png](/img/user/SCR-20230805-smfp-2.png)

a) identify each packet, for each, specify: who is sending to who, and what its purpose is

```
tcpdump: listening on eth0, link-type ENlOMB (Ethernet), snapshot length 262144 bytes

09:18:40.146326 IP (tos 0x0, ttl 64, id 34387, offset 0, flags [none], proto UDP (17), length 71)
	172.31.81.8.46514 > 172.31.0.2.53: 4419+ [lau] A? www.wgtn.ac.nz. (43)

09:18:40.146455 IP (tos 0x0, ttl 64, id 26273, offset 0, flags [none], proto UDP (17), length 71)
	172.31.81.8.36508 > 172.31.0.2.53: 6971+ [lau] AAAA? www.wgtn.ac.nz. (43)

09:18:40.149695 IP (tos 0x0, ttl 255, id 30180, offset 0, flags [none], proto UDP (17), length 135)
	172.31.0.2.53 > 172.31.81.8.46514: 4419 4/0/1 www.wgtn.ac.nz. A 151.101.66.49, www.wgtn.ac.nz. A 151.101.130.49, www.wgtn.ac.nz 151.101.194.49, www.wgtn.ac.nz. A 151.101.2.49 (107)

09:18:40.173928 IP (tos 0x0, ttl 255, id 30181, offset 0, flags [none], proto UDP (17), length 155)
	172.31.0.2.53 > 172.31.81.8.36508: 6971 0/1/1 (127)
```

```
Packets 1-2 are DNS queries from client -> DNS server

	The first is requesting the A records for the address, the second is requesting the AAAA records for the adderss. A records resolve to IPv4 and AAAA resolve to IPv6.

Packets 3-4 are DNS responses from DNS server -> client

	Packet 3 responds with the A records, which are IPv4 addresses of IP addresses. 
```

b)

```
All packets are sent/recieved using UDP protocol. This is an apropirate protocol for querying DNS records as you are generally just receiving a few records. This is something where you don't need a synchronous connection.
```

## Q11

![q11.png](/img/user/q11.png)

a) 

```
Packet 1:
	The source IP is 172.31.81.8 (which is our VMs IP)
	The dest IP is 151.101.66.49 (which is the DNS server)

Packet 2:
	Source IP = 151.101.66.49 (which is the DNS server)
	Dest IP = 172.31.81.8 (which is our VMs IP)
 
Packet 3:
	The source IP is 172.31.81.8 (which is our VMs IP)
	The dest IP is 151.101.66.49 (which is the DNS server)
```

b)

```
Packet 1:
	Source port = 56056
	Dest port = 443

Packet 2:
	Source port = 443
	Dest port = 56056
 
Packet 3:
	Source port = 56056
	Dest port = 443
```

c)

```
Packet 1:
	Flags = S (SYN)
 
Packet 2:
	Flags = S. (SYN)

Packet 3:
	Flags = ACK 
```

d)

```
Packet 1: 
This packet is sent from our VM to the server. It is used to tell the other server which sequence number they should accept. This is the initial connection request.

Packet 2: 
This packet is sent from the server to our VM. Same as the first packet, except this one is to tell our VM what sequence number our computer should accept from the server. This is the initial connection response from the server.

Packet 3: 
This packet is used to acknowledge the packet(s) sent from the server that were successfully received by our VM.
```

## Q12

```
The first sequence number sent by both computers (first two packets) are chosen at random. Once the connection is established, they are incremented based on the number of bytes of data being sent. This ensures ordered delivery.

The acknowledgment number shows the expected sequence number for the next recieved segement. When packets are successfully recieved, the acknowledgment number is set the the NEXT expected sequence number, which lets the sender confirm the packets have been delivered.
```

## Q13

![q13.png](/img/user/q13.png)

## Q14

![q14.png](/img/user/q14.png)

```java
import java.io.*;
import java.net.*;

public class SimpleWebServer {
	public static void main(String[] args){
		int port = 8080;
		try {
			ServerSocket serverSocket = new ServerSocket(port);
			System.out.println("Sever running  at http://localhost:" + port);

			while(true){
				Socket clientSocket = serverSocket.accept();
				System.out.println("Connection from " + clientSocket.getInetAddress());
				handleRequest(clientSocket);
				System.out.println("Served");
				clientSocket.close();
			}
		} catch (IOException e){
			e.printStackTrace();
		}
	}

	private static void handleRequest(Socket clientSocket) throws IOException {
    		InputStream inputStream = clientSocket.getInputStream();
   		BufferedReader reader = new BufferedReader(new InputStreamReader(inputStream));

    		// Read the first line of the HTTP request (Request Line)
    		String requestLine = reader.readLine();

   	 	// Read and parse the HTTP headers
    		String headerLine;
		String publicIP = null;
    		while ((headerLine = reader.readLine()) != null && !headerLine.isEmpty()) {
        		if (headerLine.startsWith("X-Real-IP:")) {
            			publicIP = headerLine.substring("X-Real-IP:".length()).trim();
        		}
    		}

    		OutputStream outputStream = clientSocket.getOutputStream();
    		PrintWriter out = new PrintWriter(outputStream, true);

    		out.println("HTTP/1.1 200 OK");
    		out.println("Content-Type: text/html");
    		out.println();

    		out.println("<!DOCTYPE html>");
    		out.println("<html>");
   	 	out.println("<head>");
    		out.println("<title>Hello World!!</title>");
    		out.println("</head>");
    		out.println("<body>");
		out.println("<h1>Hello World!!</h1>");
    		out.println("<h2>I'm Hamish Burke!</h2>");

    		if (publicIP != null && !publicIP.isEmpty()) {
		        out.println("<p>Public IP (X-Real-IP): " + publicIP + "</p>");
		} else {
		        out.println("<p>Public IP: " + clientSocket.getInetAddress().getHostAddress() + "</p>");
		}

    		out.println("</body>");
    		out.println("</html>");

    		out.close();
	}
}
```

## Q15

![lastquestion.png](/img/user/lastquestion.png)

```java
import java.io.*;
import java.net.*;

public class SimpleWebServer {
    private static final String API_KEY = "...";

    public static void main(String[] args) {
        int port = 8080;
        try {
            ServerSocket serverSocket = new ServerSocket(port);
            System.out.println("Server running at http://localhost:" + port);

            while (true) {
                Socket clientSocket = serverSocket.accept();
                System.out.println("Connection from " + clientSocket.getInetAddress());
                handleRequest(clientSocket);
                System.out.println("Served");
                clientSocket.close();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private static void handleRequest(Socket clientSocket) throws IOException {
        InputStream inputStream = clientSocket.getInputStream();
        BufferedReader reader = new BufferedReader(new InputStreamReader(inputStream));

        // Read the first line of the HTTP request (Request Line)
        String requestLine = reader.readLine();

        // Read and parse the HTTP headers
        String headerLine;
        String publicIP = null;
        while ((headerLine = reader.readLine()) != null && !headerLine.isEmpty()) {
            if (headerLine.startsWith("X-Real-IP:")) {
                publicIP = headerLine.substring("X-Real-IP:".length()).trim();
            }
        }

        OutputStream outputStream = clientSocket.getOutputStream();
        PrintWriter out = new PrintWriter(outputStream, true);

        out.println("HTTP/1.1 200 OK");
        out.println("Content-Type: text/html");
        out.println();

        out.println("<!DOCTYPE html>");
        out.println("<html>");
        out.println("<head>");
        out.println("<title>Hello World!!</title>");
        out.println("</head>");
        out.println("<body>");
        out.println("<h1>Hello World!!</h1>");
        out.println("<h2>I'm Hamish Burke!</h2>");

        if (publicIP != null && !publicIP.isEmpty()) {
            String geoLocation = getGeoLocation(API_KEY, publicIP);
            if (geoLocation != null) {
                out.println("<p>Public IP (X-Real-IP): " + publicIP + "</p>");
                out.println("<p>" + geoLocation + "</p>");
            } else {
                out.println("<p>Failed to fetch geolocation information</p>");
            }
        }

        out.println("</body>");
        out.println("</html>");
        out.close();
    }

    private static String getGeoLocation(String apiKey, String ipAddress) {
        try {
            String url = "api.ipgeolocation.io";
            int port = 80; // HTTPS uses port 443

            Socket socket = new Socket(url, port);
            PrintWriter pw = new PrintWriter(socket.getOutputStream(), true);

            pw.println("GET /ipgeo?apiKey=" + apiKey + "&ip=" + ipAddress + " HTTP/1.1");
            pw.println("Host: " + url);
            pw.println("Connection: close"); // To close the connection after receiving the response
            pw.println();
            pw.flush();

            BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            StringBuilder response = new StringBuilder();
            String line;

            while ((line = br.readLine()) != null) {
                response.append(line);
            }

            br.close();
            socket.close();

            return response.toString(); 
        } catch (IOException e) {
            e.printStackTrace();
            return null; 
        }
    }
}

```