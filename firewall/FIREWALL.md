# FIREWALL

   Add a rule to prohibit connecting to Facebook:



        sudo iptables -A OUTPUT -p tcp -d 157.240.221.35 --dport 80 -j DROP
        sudo iptables -A OUTPUT -p tcp -d 157.240.221.35 --dport 443 -j DROP

Note: This IP address may change over time, so you should check the current IP address of Facebook before using this rule.

   Prohibit any service incoming or outgoing:



        sudo iptables -P INPUT DROP
        sudo iptables -P OUTPUT DROP

   Accept established TCP connections:



        sudo iptables -A INPUT -p tcp -m conntrack --ctstate ESTABLISHED -j ACCEPT
        sudo iptables -A OUTPUT -p tcp -m conntrack --ctstate ESTABLISHED -j ACCEPT

   Block access to packets from the Internet whose IP address is a private address:



        sudo iptables -A INPUT -s 10.0.0.0/8 -j DROP
        sudo iptables -A INPUT -s 172.16.0.0/12 -j DROP
        sudo iptables -A INPUT -s 192.168.0.0/16 -j DROP
        sudo iptables -A INPUT -s 169.254.0.0/16 -j DROP

        sudo iptables -A OUTPUT -d 10.0.0.0/8 -j DROP
        sudo iptables -A OUTPUT -d 172.16.0.0/12 -j DROP
        sudo iptables -A OUTPUT -d 192.168.0.0/16 -j DROP
        sudo iptables -A OUTPUT -d 169.254.0.0/16 -j DROP

   Save the rules so they persist after a reboot:



        sudo iptables-save > /etc/iptables/rules.v4


