#VScode #ubuntu #VirtualBox #shell 

1. install the Remote-SSH in VScode
2. config the ubuntu:
	1. create the second netlink of VM
		![[Pasted image 20230527141542.png]]
		
	2. choose "the host only" mode
		![[Pasted image 20230527141632.png]]
		
	3. check the ip-address
		![[Pasted image 20230527142855.png]]
	4. install the openssh-server
		``` bash
		sudo apt-get update
		sudo apt-get install openssh-server
		```
	 5. close the firewall `ufw allow 22`

3. connect ubuntu with the VScode
	![[Pasted image 20230527144548.png]]
	fill in the information and make the connection.
