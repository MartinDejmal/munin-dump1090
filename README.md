# munin-dump1090
Munin plugin for monitoring dump1090 instance.
This plugin is supposed to be run on machine running dump1090 directly. This machine should run munin-node too.

## prerequisites
* munin-node
* dump1090
* curl 


## installation

* place downloaded file dump1090 into ```/usr/share/munin/plugins```
* change attributes to make it executable: ```sudo chmod +x /usr/share/munin/plugins```
* make symlink into /etc/munin/plugins: ```sudo ln -s /usr/share/munin/plugins/dump1090 /etc/munin/plugins/dump1090```
* restart munin-node
 
## check
After restarting munin-node you may check whether plugin works well:
* telnet to machine running munin-node: ```telnet localhost 4949```
* enter following command: ```fetch dump1090```
* you should get output like this:
```
$ telnet localhost 4949
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
# munin node at adsbpi2
fetch dump1090
aircraft.value 114
invalid.value 20
.
quit
```
* leave telnet session by entering following command: ```quit```

## example outuput
After a couple of minutes you will see category rtl-sdr within your munin site. Example daily graph should look like this.
![Example outuput][dump1090-day.png]
