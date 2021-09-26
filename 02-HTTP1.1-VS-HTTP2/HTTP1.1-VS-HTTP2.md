# Difference between HTTP/1.1 VS HTTP/2

Let me start from the era where things get to look for some improvement in internet world, In 1990s HTTP was a simple protocol for a simple job – transporting documents from a web server to your computer as efficiently as possible. This is because the web was simple, made up of documents and a spattering of images that were no sweat for the hardware of the time to make it happen to the user view.

HTTP which stands for Hypertext Transfer Protocol for transferring 'hypertext' documents. HTTP is the method computers and servers use to request and send information, for example when someone navigates to wikipedia.com from their browser, their browser sends an HTTP request to the wikipedia servers for the content that appears on the page. Then, wikipedia servers send HTTP responses with the text, images, and formatting that the browser displays to the user. These were simple documents/files comprising mostly text and a few images, marked up with HTML to add formatting and links to other hypertext documents/files. By 1996 the HTTP/1.0 specification was adopted. This version was simple for the needs of the mid-90s web usage by the users – make a connection, download a file, close the connection, and repeat for each file needed to display a web page. It's like make 3 TCP connections for downloading a single file

By the end of 90s things began to change, the web is rapidly changing, people started buying and selling things over the internet that leads to necessitating the security, in addition to images people started watching videos, uploading them, editing the documents, sending animated gif's from their browsers, ikt makes the HTTP/1 slow for these new test cases.

Then HTTP/1.1 came to overcome all these problems, with added security features, features to imrpove the speed and efficiency of the web servers which helps to power the 'hypermedia' web version, this version is still in use on the web, now a new version HTTP/2 was created and in existence from 2015. HTTP/2 is much faster and more efficient than HTTP/1.1. One of the ways in which HTTP/2 is faster is in how it prioritizes content during the loading process.

## The Transition from HTTP/1.1 to HTTP/2

Google was working on it’s own replacement for HTTP/1.1 since the early 2010s, called SPDY. This protocol used the existing infrastructure built for HTTP/1.1, but modified how the requests worked over the infrastructure. SPDY used 'multiplexing' to download multiple resources/files efficiently over a single TCP connection, and could be 'back-ported' to existing applications. In 2015, w3 officially adopted the HTTP/2 specification based on SPDY, and all major browsers began supporting the protocol.

## How HTTP/2 becomes faster than HTTP/1.1?

Modern websites function much more like applications, with a constant two-way stream of data being an essential part of their functionality. For example, when you’re typing something in a Google Docs, every keystroke sends data to google’s servers and then the google’s servers process that data, and then send updates back to your browser with the text you’ve typed, along with other helpful information like suggestions, the last edit status of the document etc. If it is over HTTP/1.1 where we have the 3-way TCP connections for each of our keypress would initiate a new connection to the server, to send each character you typed over the wire. Then, your browser would have to constantly 'ping' google’s server to see if the status of the document changed, to add the character to the screen. That’s a boatload of connections and it takes more time. But in case of HTTP/2 it’s essentially a constant two-way stream over a single connection google’s server is always listening for data coming from your browser and your browser is always listening for data to come back from google. There’s no more send data, wait for response, update the screen, send more data, wait for a response, etc. Instead, everything happens in real-time. In this way, a web page like a Google Doc can update itself so frequently as to feel like a native application on your computer ex: Microsoft Word where you can see then instant changes.

![http](https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/http2.jpg)

## What is prioritization?

Coming to topic prioritization as we have discussed earlier, prioritization refers to the order in which pieces of content are loaded, if a user visits a news website and navigates to an article. Should the photo at the top of the article load first? Should the text of the article load first? Should the banner ads load first?

Prioritization affects a webpage's load time. For example in certain resources, like large JavaScript files, may block the rest of the page from loading if they have to load first. More of the page can load at once if these render-blocking resources load last. In addition the order in which these page resources load affects how the user perceives page load time. If only behind-the-scenes content like CSS file or content the user can't see immediately like banner ads at the bottom of the page loads first, the user will think the page is not loading at all. If the content that's most important to the user loads first, such as the image at the top of the page, then the user will perceive/thinks the page as loading faster. In HTTP/2, developers have hands-on, detailed control over prioritization, HTTP/2 offers a feature called weighted prioritization. This allows developers to decide which page resources will load first every time. In HTTP/2 when a client makes a request for a webpage the server sends several streams of data to the client at once, instead of sending one thing after another. This method of data delivery is known as 'multiplexing'. Developers can assign each of these data streams a different weighted value and the value tells the client which data stream to render first.

> HTTP2 is fully multiplexed, instead of ordered and blocking

### Multiplexing:

HTTP/1.1 loads resources one after the other, so if one resource cannot be loaded, it blocks all the other resources behind it. In contrast, HTTP/2 is able to use a single TCP connection to send multiple streams of data at once so that no one resource blocks any other resource. HTTP/2 does this by splitting data into binary-code messages and numbering these messages so that the client knows which stream each binary message belongs to.

![image](https://miro.medium.com/max/700/0*lY05UTuA-dWCXU-q.png)

> HTTP2 is binary, instead of textual

![binary-image](https://miro.medium.com/max/700/0*0LtM_XmkauxVoY8M.png)

HTTP/1.1 used to process text commands to complete request-response cycles. HTTP/2 will use binary commands (in 1s and 0s) to execute the same tasks. Browsers using HTTP/2 implementation will convert the same text commands into binary before transmitting it over the network.

> HTTP/2 allows servers to “push” responses proactively into client devices

### Server push:

Server only serves content to a client device if the client asks for it. HTTP/2 solves this problem by allowing a server to "push" content to a client before the client asks for it. The server also sends a message letting the client know what pushed content to expect

![server-push](https://miro.medium.com/max/498/0*ZJLgVdXq_06hcF1o.png)

> HTTP/2 uses header compression to reduce overhead

### Header compression:

Small files load more quickly than large ones. To speed up web performance, both HTTP/1.1 and HTTP/2 compress HTTP messages to make them smaller. However, HTTP/2 uses a more advanced compression method called HPACK that eliminates redundant information in HTTP header packets. This eliminates a few bytes from every HTTP packet. Given the volume of HTTP packets involved in loading even a single webpage, those bytes add up quickly, resulting in faster loading.

![header-compress](https://miro.medium.com/max/700/0*5r8-MbhEseP6lEQg.png)
