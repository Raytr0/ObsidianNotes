q1: 
	/n specifies how many echos are sent
	/f Specifies that echo Request messages are sent with the **Do not Fragment** flag in the IP header set to 1
	/t Specifies ping continue sending echo Request messages to the destination until interrupted.
	/a	Specifies reverse name resolution be performed on the destination IP address. If this operation is successful, ping displays the corresponding host name.
q2: used the following >ping localhost
![[Pasted image 20241029001646.png]]
q3: 
![[Pasted image 20241029001744.png||500]]
![[Pasted image 20241029001843.png]]
q4: oxford ip is 172.67.20.89
![[Pasted image 20241029001958.png]]
q5: results slightly differ in max and average, but minimal enough to not make any difference
![[Pasted image 20241029002038.png]]
q6:
UWO: only stats for 512 and 724 bytes can be shown, the average for both are around 6ms, with a standard deviation of 2.37
![[Pasted image 20241029131206.png]]
![[Pasted image 20241029131331.png]]
![[Pasted image 20241029131447.png]]

![[Pasted image 20241029005505.png]]
Oxford: Average seems to be the same, standard deviation is 3.31 
![[Pasted image 20241029004532.png]]
![[Pasted image 20241029004558.png]]
![[Pasted image 20241029004624.png]]
![[Pasted image 20241029004740.png]]
Q7:
9 hops, about 3 ISPs
![[Pasted image 20241029011822.png]]
8 hops, about 2 ISPs
![[Pasted image 20241029011931.png]]
24 hops, 3 ISPs
![[Pasted image 20241029012205.png]]
Q8: first column is the hop number, the following three are three separate packets sent to the server, and the final one is the IP. * means that its timed out for any reason 
Q9: 
![[Pasted image 20241029013604.png]]
Q10: The routes did not differ
![[Pasted image 20241029015354.png]]
Q11: server address is 23.205.255.73
![[Pasted image 20241029005707.png]]
Q12:
![[Pasted image 20241029005931.png]]
Q13:
The IP for the google address is 173.194.195.27
![[Pasted image 20241029130916.png]]
![[Pasted image 20241029131104.png]]
Q14:
It is sent over UDP
![[Pasted image 20241029125715.png]]
Q15:
The port is 60500 for source, and 53 for destination
Q16:
172.30.80.1 is the IP that the DNS query was sent to
Q17:
This is a "type A" DNS query, it is asking for the IPv4 address of the website
Q18:
This one specifically has no answers, only one question
![[Pasted image 20241029130158.png]]
## Task 2
Q19: the netmask and the subnet mask have the same IP, this is because the subnet relies on the hostOS to transmit data thus acting as a bridge.
![[Pasted image 20241031190156.png]]
![[Pasted image 20241031190228.png]]
Q20: I cannot, for the life of me, get the xauth permissions to work properly.
Every time I run "xauth h1 h2" my permissions are denied and I have no clue how to fix this issue or why its happening.
But from the mininet>dump, I can see that both hosts have IP addresses of 10.0.0.1 and 10.0.0.2, which shows that they are indeed in the same subnet.
![[Pasted image 20241101223705.png]]
![[Pasted image 20241101223726.png]]
