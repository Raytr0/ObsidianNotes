# Task 1
Q1:
	It took roughly 5 seconds to transfer a 498.85kb file
	UDP packets seem to be transferring only from h1 to h2
	![[Pasted image 20241125220317.png]]

Q2:
	The image was identical to the original file with no loss
	![[Pasted image 20241125220401.png]]![[Pasted image 20241125220410.png]]
	![[Pasted image 20241125220455.png]]

Q3: 
There now exists a huge difference in the file size
![[Pasted image 20241125220838.png]]
The time to upload was also impacted as UDP transmissions ended at around 3.7 seconds but ICMP showing time exceeded ended the whole thing at around 10 seconds
![[Pasted image 20241125224308.png]]

Task 3:
Q4: 
This took 4.8 seconds to transfer
There are constant back and fourths from h1 and h2

Q5:
The received file is the exact same size
![[Pasted image 20241125223403.png]]

Q6:
The forced loss caused the file to upload in around 27.3 seconds instead of the orginal 4.8 seconds
![[Pasted image 20241125223727.png]]
![[Pasted image 20241125223655.png]]
The file has also been sized down to 371.9kb

Q7:
![[Pasted image 20241126005103.png]]
Expanded h3 chart:
![[Pasted image 20241126005226.png]]

Q8:
Obviously from the charts the processing time is different. 
From h1, there seems to be a slight curve when increasing the window size, indicating a exponential increase compared to the h3's more linear increase.
h3 also seems to have a larger congestion window size, which could be caused by the difference in packet loss %, as h1 is set to have a 10% loss and h3 only 1%
the 10% loss seems to have an affect on triggering more frequent reductions keeping the CWND lower compared to h3