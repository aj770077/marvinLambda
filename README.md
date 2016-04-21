# marvinLambda

## Installation

There are 4 major scripts that need to be running for a pi to make a

To begin the alexa service, first navigate to /companionService/ and

~~~~
sudo npm start
~~~~

next, navigate to the javaclient folder in a terminal WITHIN VNC and run

~~~~
mvn exec:exec
~~~~

if this fails, try

~~~~
sudo env "PATH=$PATH" mvn exec:exec
~~~~

Following these steps should have started the alexa app.
Next, the following scripts should be active and running on the cloud, first
~~~~
ruby server.rb
./notification_server_name.py  #NOTE, THERE SHOULD BE ONE OF THESE 
                               #SCRIPTS FOR EACH PI CONNECTED TO THE
                               #SERVICE
~~~~

in conjunction with the notification_server.py on the cloud, each pi should have one script called "notification_listener.py" which listens on a unique port, as to communicate with it's respective notification_server

In total, On the Cloud, the following must be running before activating any other scripts (on the pi).  In theory these should just be running at all times

~~~~
sudo ruby server.rb
sudo ./notification_server_name #(name=the username of the respective pi.  One of these scripts run per User)
~~~~

Next, you can activate these scripts on the pi

~~~~
sudo npm start #companionService
sudo env "PATH=$PATH" mvn exec:exec #javaClient
sudo ./notification_listener.py #notification listener
~~~~

