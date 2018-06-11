# CGI 
CGI supports accessing CGI parameters passed in environment variables or standard input by a web servers like Apache. Example use:

```
#!./ioServer

cgi = CGI clone

redirect = cgi getParameters at("redirurl")
if (redirect and redirect != "",
	redirect clipAfterStartOfSeq("\r")
	redirect clipAfterStartOfSeq("\n")
	cgi redirect(redirect)
	System exit(0)
 )

cgi header("Content-type", "text/html")

cgi write("&lt;html&gt;&lt;head&gt;&lt;title&gt;test&lt;/title&gt;&lt;body&gt;")
cgi write("GET Parameters:")
cgi getParameters foreach(k, v,
	cgi write(k .. " = " .. v .. ","))
)

cgi write("POST Parameters:")
cgi postParameters foreach(k, v,
	cgi write(k .. " = " .. v .. ","))
)

cgi write("COOKIES:")
cgi cookies foreach(k, v,
	cgi write(k .. " = " .. v .. ",")
)

```

# Installation

```
eerie install https://github.com/IoLanguage/CGI.git
```
