---
## Hashnode
slug: networking-part-4
domain: hashnode.hudater.dev
subtitle: "cURL: The Internet, Stripped of Its UI"
enableToc: true
saveAsDraft: false

# Cover Image URL of the post
# String | Optional
# Note: You must upload the image to Hashnode's CDN, before you can use it here.
# Ex: https://cdn.hashnode.com/res/hashnode/image/upload/v1681132538878/itnaYF1h-.png
# - To upload, Login to Hashnode and go to https://hashnode.com/uploader
#   Use the URL that is generated after the upload.
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768907490094/TEkoHSA4S.jpg?auto=format

## Jekyll
title: "cURL: The Internet, Stripped of Its UI (4/6)"
layout: post
date: 2026-01-29 06:30:00 +0530
categories: [chaicode, networking-series]
comments: true
pin: false
# tags: [servers, proxmox, homelab, hybrid cloud, architecture diagram]
tags:
  - networks
  - dns
  - chaicode
image:
  path: "https://res.cloudinary.com/djsasyvfl/image/upload/v1769649785/57f2e71e-4011-4c68-a5ef-dc2891620429.png"
  alt: "cURL Flow"
---

> You click Email at hudater.dev to offer me a Job
> 
> Mail client opens
> 
> But what if I told you that button is just a very polite wrapper around a command-line tool?

Well it's not exactly cURL under the hood but the principle remains the same: a client sends a request, and a server sends back a response.


What you triggered with that button click is exactly what cURL does but the good, ol' CLI way: **a request and a response**

This simple, UNIX-like interaction of request-response is what makes cURL all that useful for us.

### Terms

We should clarify some terms before starting with cURL.

1. **Client**

    - A client is anything that makes a request.
    - Examples
        - GUI Browser like Chrome
        - cURL
    - If something is asking for data, it’s the client.

2. **Server**

    - A server is the machine (or program) that responds to requests.
    - Examples:
        - A website backend
        - An API service

3. **Request**

    - A request is the message sent from client to a server.
    - It usually includes:
        - What you want
        - Where you want it from
        - Sometimes extra info (headers, authentication)
    - Example request: “GET /users”

4. **Response**

    - A response is what the server sends back upon a request
    - It contains:
        - A status code (success or failure)
        - Data (HTML, JSON, etc.)
    - Example response: {"username": "Hudater"}

5. **API (Application Programming Interface)**

    - An API is basically a server endpoint meant for programs, not humans.
    - Instead of giving you a webpage, it gives you data.
    - Data can be in format like:
        - JSON
        - XML
        - Plain text
    - Meant for programs to consume, not humans

6. **Protocol**

    - A protocol is a set of rules for communication.

7. **HTTP (HyperText Transfer Protocol)**

    - HTTP is the basic communication language of the web.
    - It defines rules for how requests and responses work:

8. **HTTPS**

    - HTTPS is just HTTP, but encrypted and secure.
    - The “S” stands for Secure

9. **URL (Uniform Resource Locator)**

    - A URL is the address of something on the internet.
    - Example: https://hudater.dev

10. **Status Codes**

    - When a server responds, it includes a number showing what happened
    - Some common Status Codes:
        - 200 - OK (success)
        - 404 - Not Found
        - 500 - Server error

### cURL Explainer

At its core, cURL is a tool to transfer data using URLs.

cURL supports multiple protocols but one we will use here is `HTTP` and `HTTPS`. It’s like the networking part of a browser minus the GUI.

### Why cURL

We need cURL because it gives the most direct way to communicate with servers.

It shows the server’s response as-is, including the raw output and important details like HTTP status codes. This makes cURL extremely useful for testing and debugging applications without relying on a browser or frontend.

cURL is especially common when working with APIs, where the goal is to send requests and receive data directly, usually in formats like JSON.

### cURLing away

Let's try cURLing my links webpage

```bash
curl https://hudater.dev
```

![cURL webpage](https://res.cloudinary.com/djsasyvfl/image/upload/v1769644423/curl_first_ntci3t.png)
_cURL Webpage_

This command sends a simple HTTP GET request to the server and prints the response directly in your terminal.

In the response screenshot, we can see we get pure HTML back which would be rendered if we sent the request via a GUI Web Browser

#### Verbose

That wasn't very useful for debugging. Let's try the `-v` flag which will enable verbose output mode showing us more information about the connection, request and response


```bash
curl -v https://hudater.dev
```

![cURL verbose Header](https://res.cloudinary.com/djsasyvfl/image/upload/v1769644810/curl_verbose_header_x8oqvl.png)
_cURL verbose Header_

![cURL verbose Footer](https://res.cloudinary.com/djsasyvfl/image/upload/v1769644808/curl_verbose_footer_phj1cj.png)
_cURL verbose Footer_

If you executed this cURL command, you would be able to see:

- DNS Lookup
- TCP Connection (handshake)
- HTTP Request being made
- Response Status Code
- Response Headers

#### Specifying HTTP Verbs

The default behavior when running cURL is to perform a GET operation but we can specify operation verb using:

```bash
curl --request HTTP_VERB_HERE URL_HERE
```

or

```bash
curl -X HTTP_VERB_HERE URL_HERE
```

#### GET

Let's do a GET operation on an API from [FreeApi.app](https://freeapi.app/){:target="_blank"}

```bash
curl -X GET https://api.freeapi.app/api/v1/public/randomjokes/joke/random
```

![cURL GET Response](https://res.cloudinary.com/djsasyvfl/image/upload/v1769646215/curl_api_get_jakc4q.png)
_cURL GET Response_

#### POST without Parameters

The POST method is used to send data to the server.

It is a simple write operation.

Once the POST request has been made, the server can process the data.

Let's do a POST operation on the Kitchen Sink API Endpoint from [FreeApi.app](https://freeapi.app/){:target="_blank"}

```bash
curl -X POST https://api.freeapi.app/api/v1/kitchen-sink/http-methods/post
```

![cURL POST Response](https://res.cloudinary.com/djsasyvfl/image/upload/v1769646867/curl_api_post_d1nnpa.png)
_cURL POST Response_

Since this is just a Kitchen Sink Endpoint, meaning it's just there to practice and sends back 200 response code upon receiving POST request

#### POST with Parameters

Let's do a POST request to `Register user` API endpoint, again from [FreeApi.app](https://freeapi.app/){:target="_blank"}

```bash
curl -X POST https://api.freeapi.app/api/v1/users/register
```

![cURL POST Fail](https://res.cloudinary.com/djsasyvfl/image/upload/v1769647381/curl_api_post_fail_param_lnderr.png)
_cURL POST Fail_

In the response, we get Status Code 422 which means the request has Unprocessable Content.

From the [API documentation](https://freeapi.hashnode.space/api-guide/apireference/registerUser){:target="_blank"}, we can see that we need to provide certain data with the request.

Now we will do a POST request with correct data

```bash
curl --request POST \
  --url https://api.freeapi.app/api/v1/users/register \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "email": "user.email@domain.com",
  "password": "test@123",
  "role": "ADMIN",
  "username": "doejohn"
}'
```

![cURL POST Success](https://res.cloudinary.com/djsasyvfl/image/upload/v1769647953/curl_api_post_success_e47sco.png)
_cURL POST Success_

This time we get Status Code 2XX which means the request was successful!

This command has some extra flags, here is an explanation:


| Flag                                      | Meaning                                                    |
|-------------------------------------------|------------------------------------------------------------|
| --header 'accept: application/json'       | Tells the server to send back data in JSON Format          |
| --header 'content-type: application/json' | Tells the server you are sending data in JSON Format       |
| --data '{"key" : "value"}'                | This is the data you are sending                           |

### Common Pitfalls

Beginners are bound to make mistakes, most we can do is beware!

Here are some common mistakes to avoid:

1. Mixing up lowercase and uppercase Flags
    - For example: `-X` is equivalent to `--request` while `-x` is used to specify proxy to use

2. Sending data without specifying data format
    - This could cause Failed method call, make sure to specify your sent data format

3. Not Using Quotes Around Data
    - Improper quotes would cause data to be interpreted as shell commands, watch out!


### Visualization

Here is a diagram explaining Browser flow

![Browser Interaction](https://res.cloudinary.com/djsasyvfl/image/upload/v1769649941/701f649d-7a21-4943-9faa-c2122391480f.png)
_Browser Interaction_


And another one explaining cURL flow

![cURL Interaction](https://res.cloudinary.com/djsasyvfl/image/upload/v1769649785/57f2e71e-4011-4c68-a5ef-dc2891620429.png)
_cURL Interaction_

### Conclusion

Now we understand what cURL is, how to make requests using cURL and much more.

In the next blog, we might be doing some handshakes ;)

