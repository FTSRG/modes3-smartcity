
# Deploying the generated files

At this point we have everything we need to manage our devices: we have a way to monitor them, to interact with them and display all these on a nice looking website. However, there are some things that go best automated: for example, deploying the code that we generated to be run on the distributed system we oversee. For this purpose, there is a *Deploy package* option on every page in our dashboard, which will take the user to a list of settings: they need to set the IP address of every node and their SSH username, and optionally, their password. With these set, we can easily SCP the files through to the devices themselves, and after that, execute the default Make option to trigger the compilation and then launch the program (and the monitoring client). 
