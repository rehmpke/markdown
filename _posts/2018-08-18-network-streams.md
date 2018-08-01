---
layout: "post"
title: "Network Streams Learning"
date: "2018-08-18 08:58"
---

# Network Streams Learning

TCP vs. UDP
TCP gives feedback along the way is more popular.

UDP is used for video streaming and audio streams more.

## Netcat

AWK

This is an interesting way to interact with ports on a system.

Type

	$ nc -lp - 1024

hit return.

That begins netcat listening on port 1024 on your network system.

Nothing really happens other than we see the prompt. Basically netcat is listening and waiting for us to make a request. we can use the http: verbs GET, POST, HEAD, and PUT

HTTP

	$ nc www.rogerehmpke.com 80
	GET /Pages/Home.aspx HTTP/1.0
	Host: www.rogerehmpke.com
	
or

	$ nc rogerehmpke.com 
	GET / HTTP/1.0
	Host: rogerehmpke.com
	

## Curl 

Curl is a slightly easier method of getting http content.

	$ curl -s https://rogerehmpke.com
	
to get any url or add the -I flag to get a header

	$ curl -Is https://rogerehmpke.com
	