pysysprofile
============

Flat file profile system

Allows you to change the startup or generally anything,
based on rules within the profiles.

Compatible with python 2.7 and python 3.2.

Will run scripts based on their file or folder name.

Hotplug events driven by libudev (Havn't fully decided how implimentation of this should be handled, as reinventing the wheel isn't my goal.)

Config switch events can be configured by plugins.
(i.e. if your network interface is on a certain network, switch the apache config (symlink) with another contained within the profile).
This will require some extra configuration, and is considered an advanced option.

--EXAMPLES--
/etc/sprofile.d/net.top.any.192.168.0.0_24

will run this profile if the primary interface (or secondaries configured in /etc/pysysprofile.conf)
if the network configuration matches 192.168.0.0/24
It will run the file, within can contain scripts or other configuration options.

---------

/etc/sprofile.d/net.top.eth3.192.168.0.0_24
will run this profile only if eth3 is on a 192.168.0.0/24 network.

---------

/etc/sprofile.d/psu.batt.10/
on 10 percent battery, will run any scripts within this folder.

---------

/etc/sprofile.d/net.gw.eth0.192.168.56.1/
./apache.config/
(switch the symlink of /etc/apache2/ to /etc/sprofile.d/net.gw.eth0.192.168.56.1/apache.config/)
