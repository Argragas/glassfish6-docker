Docker-glassfish6
=====================

Usage
-----

To create the image execute the following command :

	docker build -t glassfish6 .

To run the image and bind to port :

	docker run -d -p 4848:4848 -p 8080:8080 -p 8181:8181 glassfish6

PS: 4848 (for administration), 8080 (for the HTTP listener), and 8181 (for the HTTPS listener)

The first time that you run your container, a new user `admin` with all privileges
will be created in Glassfish with a random password. To get the password, check the logs
of the container by running:

	docker logs <CONTAINER_ID>

You will see an output like the following:

	========================================================================
	You can now connect to this Glassfish server using:

	    admin:b1uKcRK3r6SF

	Please remember to change the above password as soon as possible!
	========================================================================

In this case, `b1uKcRK3r6SF` is the password allocated to the `admin` user.

You can now login to you admin console to configure your Glassfish server:

	http://127.0.0.1:4848/


Setting a specific password for the admin account
-------------------------------------------------

If you want to use a preset password instead of a random generated one, you can
set the environment variable `GLASSFISH_PASS` to your specific password when running the container:

	docker run -d -p 4848:4848 -p 8080:8080 -e GLASSFISH_PASS="mypass" tutum/glassfish

You can now test your deployment:

	http://127.0.0.1:8080/

Done!
