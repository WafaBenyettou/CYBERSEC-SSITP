# SYN FLOODING ATTACK

A SYN flooding attack is a type of denial-of-service (DoS) attack that exploits the three-way handshake process of the Transmission Control Protocol (TCP) to exhaust the resources of a target system.

In the three-way handshake process, a client sends a SYN (synchronize) packet to the server, the server responds with a SYN-ACK (synchronize-acknowledgment) packet, and the client sends an ACK (acknowledgment) packet to establish a connection. In a SYN flooding attack, the attacker sends a large number of SYN packets to the target system, with spoofed source addresses or using legitimate ones. The target system will respond with a SYN-ACK packet, but since the attacker does not complete the handshake by sending an ACK packet, the connection remains open.

The attacker repeatedly sends these SYN packets, causing the target system to allocate resources to maintain the incomplete connections. If the attacker generates enough SYN packets, the target system can become overwhelmed and unable to respond to legitimate requests from other clients.

For example, if a web server receives thousands of SYN packets within a short period of time, it may not be able to process all of them, leaving legitimate requests from users unanswered. This can lead to slow response times, connection timeouts, or even server crashes.

To mitigate SYN flooding attacks, network administrators can employ various countermeasures, including rate limiting, which limits the number of incoming connections per second, SYN cookies, which add a token to the SYN-ACK packet to validate legitimate connections, and firewalls that can filter out spoofed source addresses. By using a combination of these measures, administrators can help protect their networks and ensure the availability of their services.

## What did i do ? 

- located the ip address of the machine victim : 10.0.2.15 using 
```
if config
```
or any other command that shows the ip adress 

- preformed the attack on port 80 using this command : 

```
sudo hping3 10.0.2.15 -d 150 -S --flood --rand-source -p 80
```


for the result details you can check the /images folder where it contains all the results and more details about the attack .