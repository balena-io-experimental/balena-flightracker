# This project is archived - a maintained replacement is here: https://github.com/ketilmo/balena-ads-b

# balena-flightracker
This is a project designed to simplify the setup of capturing and feeding aircraft location data to various sites. All the sites I have found so far offer premium membership packages in return for your data so for the most part it is cheaper to setup your own receiver and feed data than it is to just sign up for the memership package.

The project is based around one container `datacapture` which runs dump1090-fa (the Flightaware fork, purely because it's still under development) and lighttpd for a status page. Dump1090 makes the received location data available on the network, which we're able to access from other containers to feed the services.

## Setup
Dump1090 works with the standard RTL-SDR dongles and should automatically detect and use the first dongle it finds upon running. The status page for this will be available on port 80 so you can access this either via local IP or from the public device URL in balenaCloud.

For the other services to feed, the keys/IDs need to be filled in the respective configuration files. 

If there's a service you don't want to use, simply comment out that section in `docker-compose.yml`.

Further readme to follow but open an issue if you get stuck in the meantime!
