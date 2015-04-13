---
title: Authorized Curl Requests
---

At Able, our Admin is protected by two levels of authentication: basic HTTP auth and application auth.  Basic HTTP auth uses shared credentials and is a simple layer of security around our admin's JavaScript.  I'm sure there are better ways of handling this, but because this is an internal application, we're fine with a little bit of inconvenience.  

The first step to hitting a protected endpoint using curl is to hit your login endpoint with your HTTP credentials **and** your application credentials; you also want to make sure you store the session cookies to your local hard drive.

    curl -c /tmp/cookies.txt -u sharedusername:sharedpassword -X POST https://example.com/api/login -d '{"username": "myusername", "password":"supersecret"}'

Here, the -c option tells curl where to store the session cookies on your local space.  The -u option accepts the credentials for HTTP auth in the format **username:password**.  Finally, you specify that it's a POST request using -X, and you submit your payload using -d.

Once you authenticate, visit your cookies file to make sure it was written to successfully. 

Next, you want to reuse those cookies when hitting a protected endpoint.  Another thing to note, you have to provide the HTTP auth crednetials with every request.

    curl -b /tmp/cookies.txt -u sharedusername:sharedpassword https://example.com/api/protected-endpoint

You tell curl to pass your cookies to the server with the -b option.

That's it!

