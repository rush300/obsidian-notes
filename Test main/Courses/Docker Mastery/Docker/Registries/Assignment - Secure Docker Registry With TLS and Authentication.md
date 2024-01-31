The default registry install is rather bare bones, and is open by default, meaning anyone can push and pull images.  You'll likely want to at least add TLS to it so you can work with it easily via HTTPS, and then also add some basic authentication.  

These aren't actually that hard to setup, but do require some commands.  You can learn the basics by creating a self-signed certificate for HTTPS, and then enabling `htpasswd`  auth, which you'll add users too with basic cli commands.

For this assignment you'll use Play With Docker, a great resource for web-based docker testing and also has a library of labs built by Docker Captains and others, and supported by Docker Inc. 

I'd like you to do the [Part 2 and 3 of "Docker Registry for Linux"](http://training.play-with-docker.com/linux-registry-part2/) for this assignment. You can use their text to do this assignment on your own machine, or [jump back to their Part 1 and run the container on their infrastructure](http://training.play-with-docker.com/linux-registry-part1/)  using their web-based interface to a real docker engine and learn how "PWD" works!

For more extra credit labs, look through their growing list: [http://training.play-with-docker.com/](http://training.play-with-docker.com/)