# Notes on MQTT
## Installing mqtt.

Setted broker on Virtual server using vagrant.
Checked if ping is to host server.

http://labs.septeni.co.jp/entry/20140707/1404670069
in this article, there are 3 types of connection in vagrant.
They are, host only adapter, NAT, bridge adapter.
host only:
	only host can ping to virtual machine.
NAT:
	only 2 virtual machines can ping to each other.
bridge adapter:
	everybody in network can ping to virtual machine.
See article copy Vagrant file.
Try 1 NAT: 
2 guests virtual machine where able to ping each other.
But couldn't use mqtt sub, pub.

Try 2 Bridge adapter:
1 guest virtual machine set up open network. 
Able to pub, sub from host machine.

Notice:
 using open network

## Overview of MQTT server:
MQTT server, there are 3 objects. Those are Broker, Publisher, Subscriber. 
They communicate with MQTT message protocol, which uses TCP/IP layer of network. 

## Usage:
### username/password:
set it on broker by mosquitto_passwd

### topic:
subscribers and publishers do action on name tag called "topic".
example:
subscriber is listening to topic name "test"
'''
mosquitto_sub -h XXX.XXX.XX.XX -p 1883 -t test
hello world
hello world
hello world
hello world
hello world
hello world
'''
,
publisher is publishing test message to topic name "topicname"
```
mosquitto_pub -d -t topicname -m "test message" -h XXX.XXX.XX.XX -p 1883
```
#### additional topic name option #/+:
 see http://devcenter.magellanic-clouds.com/learning/mqtt-spec.html


