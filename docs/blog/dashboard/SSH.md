# GoTTY as an SSH frontend - an optimal solution?

We have decided to develop not only an execution platform for out distributed system but also a management and monitoring system too. Our goal was to automatize as much of the work as possible and provide an end-to-end development and execution platform.
Our goal is to manage the devices on LAN via SSH in a web browser, so we started researching to find the optimal solution just for that, preferably one that works out-of-the-box. It was not long until we realised that we had no such luck – it was really hard to find something useful for our project. 

# The problems

Out of the 6 clients we tried out we only found one that could mostly satisfy our needs. The problems that arose with the others are the following:

* [GateOne from liftoff](http://liftoffsoftware.com) - This was quite frankly the most feature-rich implementation that we tested. It has everything we need, and even more - it would be the optimal software for us if we could comply with its licensing terms (AGPLv3): this licensing is not compatible our planned EPL licensing. Furthermore its technical documentation is very sparse, leaving out important details about e.g. the installation process, the configuration file or the overall structure of the product. Hadn't we encountered these issues would have we immediately placed our votes on liftoff's GateOne: professional, versatile and very deeply supported. 
* [Webconsole](http://web-console.org) - Unlike the other tools, this software is not an SSH client, but rather a browser-based terminal emulator. We gave it a try because of its simplicity and a possible path of development would be to fork it, and make it into one - but the implementation itself lacks some useful features as it is: it doesn't count as a *tty* for example (which it states it doesn't, but still, it makes no actual sense) therefore no pseudo-terminals or authentication is possible. Using this would either require administrative tasks to remain for on-site maintenance, or would need to be able to perform superuser privileged tasks without a password - none one of these sound acceptable at all.
* [WebSSH2](https://github.com/billchurch/WebSSH2) - This solution seemed like another great chance (in advance) to achieve what we set out to do, but unfortunately (or fortunately?) we found a bug that could as well sabotage our goal: by mistake we mistyped one of our devices' password, and were met with the fact that we had to clear cookies, delete browser data and even restart our browser (to get rid of session variables) to be able to enter those credentials again. This is in our opinion unacceptable: none should need to do all that just because of a typo.
* [FireSSH](https://addons.mozilla.org/en-US/firefox/addon/firessh/) and [Secure Shell](https://chrome.google.com/webstore/detail/secure-shell)- This would work really well, but this might cause problems for users with not-supported browser: we had to ommmit this sollution too.

# The solution

[GoTTY](https://github.com/yudai/gotty) - This tool does way more than what we need: In short, it executes a program on the server side and tunnels it through to a websocket and, without much fuss on the client side, makes the browser window pointed to its address behave *exactly* like a TTY, therefore making it an optimal solution for our needs - we simply launch the OpenSSH client on the server with a unique port number and an address-username combination.

With the goal of making our tool as easy-to-use as possible in mind, we decided to employ the following scheme: On each of the pages on our Dashboard there is a link in the header to open a *remote terminal*, which will open an SSH session to either the webserver itself, or one of the devices.

With that solved, we can do the last thing for our monitoring solution: we need to figure out a way to deploy the packages that we generate.
