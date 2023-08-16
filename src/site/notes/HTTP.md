---
{"dg-publish":true,"permalink":"/http/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-08-2023
***

# Hyper-Text Transfer Protocol

> [!Hyper-Text]
> Basically just `<a href="example.com">this</a>`

- Links in documents
- A system that allows you to jump between text documents in a **non-linear** way
- Follows a [[Client-Server Paradigm\|Client-Server Paradigm]]

## Features

- **Text-orientated** protocol
- Just **request/response** protocol
- HTTP is stateless
	- Message itself has to carry any states it needs (cookies)
- Can return with different [[HTTP Status Codes\|HTTP Status Codes]]
- [[HTML\|HTML]] is **not** a protocol, its a *markup language*

HTTP v1:
- For each request, had to create a **new** [[TCP (transmission control protocol)\|TCP (transmission control protocol)]] connection

HTTP v1.1:
- Persistent connections
- Can exchange multiple messages/responses on the [[TCP (transmission control protocol)\|TCP (transmission control protocol)]]

### Request Operations

- GET
	- **Doesn't have body**
	- Retrieve document by URL
- HEAD
	- Retrieve metainformation about a document
- POST
	- Can have a body
	- Give information to the server
- PUT
	- Can have a body
	- Store document under specified URL
- DELETE
- TRACE
- CONNECT

> [!PUT vs POST]
> If you POST multiple time, will create multiple entries
> PUT will only create 1 entry
> Unlike PUT, POST is **not** 'idempotent'

### Form

`<CRLF>` is the **carriage-return+line-feed** characters (**new-line**)
- Basically just `\n`

```
START_LINE <CRLF>
MESSAGE_HEADER <CRLF>
<CRLF>
MESSAGE_BODY <CRLF>
```

#### Start Line

- Indicates whether its a request or response

```
GET https://www.example.com/ HTTP/1.1
```

- Request operation is a **Get**
- The URL is the requested resource
- HTTP version is 1.1

#### Message Header

- Contains Key,value pairs for operating parameters of the HTTP request
- Eg: user agent, accepted content types etc

#### Message Body

- **Optional**
- Used in methods like POST and PUT
- **Not in GET**

#### URL Structure

```
https://video.doepud.co.uk:80/anatomy-of-a-url?docid=10
```

- `http` = protocol
- `video` = Subdomain
- `doepud.co.uk` = domain name
- `anatomy-of-a-url` = path
- `:80` = port 
- `?` = query
- `docid=10` = parameters



