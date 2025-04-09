# Introduction
❑ Multimedia is just two or more media, for example text and graphics. Many people refer to multimedia as a combination of two or more continuous media, 
	➢ that is, media that have to be played during some well-defined time interval, usually with some user interaction. 
❑ In practice, the two media are normally audio and video, that is, sound plus moving pictures

### Internet audio/video
Audio and video services can be split into 3 general categories
	➢ streaming stored audio/video, 
		Files are compressed on a server, client then downloads this through the internet
	➢ streaming live audio/video, and 
		User watches/listens to broadcast through internet
	➢ interactive audio/video.
		Internet telephone, Facetime

# 3.2 Digitizing/Compression of Audio and Video
### Digitizing Audio and Video
Digitization means conversion to a stream of numbers, and preferably these numbers should be integers for efficiency.
![[Pasted image 20250319100233.png]]
Compression: the process of coding that will effectively reduce the total number of bits needed to represent certain information
![[Pasted image 20250319100244.png]]

### Digitizing Audio
When sound is recorded, an electric analog signal is generated representing sound amp as a function of time
To digitize, the signal must be sampled in each dimension: in time, and in amplitude.
The process of sampling the time dimension is simply called sampling, and the rate at which it is performed is called the sampling frequency.
Sampling in the amplitude (or voltage) dimension is called quantization.
![[Pasted image 20250319100521.png]]
Nyquist theorem: Let ***f*** be highest frequency of signal, sample the signal ***2f*** per second
Quantization rates will then be applied, typically 8bit(divides vertical axis into 256) or 16bit(divides vertical axis to 65536)
Example: Voice signal of 4kHz bandwidth will be sampled at a rate of 8000 samples/second, giving a data rate of 64 kbps
Music is sampled at 44,100 samples per second with 16 bits per sample. This results in a digital signal of 705.6 kbps for mono and 1.411 Mbps for stereo.
This process of converting from analog audio to compressed binary form sampling, quantization, and encoding is known as pulse code modulation (PCM).![[Pasted image 20250319101318.png]]
### Digitizing Video
There is no standard number of frames per second; in North America 25 frames per second is common. However, to avoid a condition known as flickering, a frame needs to be refreshed.
For a color TV, each pixel is 24 bits, with 8 bits for each primary color (red, green, and blue).
We can calculate the number of bits in a second for a specific resolution. In the lowest resolution a color frame is made of 1,024 × 768 pixels. This means that we need 2(refresh) × 25(fps) × (1,024 × 768)(resolution) × 24(pixel bits) = 944 Mbps
### Audio Compression
Predictive encoding:
Differences between the samples are encoded instead of encoding all the sampled values.
This is normally used for speech
Several standards have been defined such as ✓ GSM (13 kbps), ✓ G.729 (8 kbps), and ✓ G.723.3 (6.4 or 5.3 kbps).

Perceptual Encoding (MP3):
Perceptual encoding is based on the science of psychoacoustics, which is the study of how people perceive sound. 
The idea is based on some limitations in our auditory system: 
	➢ Some sounds can mask other sounds. I.e., a loud sound in a frequency range can partially or totally mask a softer sound in another frequency range. For example, we cannot hear what our dance partner says in a room where a very loud band is performing. 
	➢ Also a loud sound can numb our ears for a short time even after the sound has stopped. 
MP3 uses these two phenomena to compress audio signals.
### Video Compression
Joint Photographic Experts Group (JPEG) is used to compress images. 
	Remember that grey scale is 8bit and color is 24bit
	Example below is grey scale
	![[Pasted image 20250319105709.png]]
	The main goal of JPEG is to change the picture into a linear set of numbers that reveals the image redundancies![[Pasted image 20250319105821.png]]
	Discrete Cosine Transform (DCT)
		Each block of 64 pixels goes through DCT, relations are kept but redundancies are revealed
		P(x,y) is the original vector before transformation, T(x,y) is after.
		T(0,0) is the average multiplied by a constant representing changes in pixel values, this is a DC value
		The rest are called AC values representing the change in pixels
		![[Pasted image 20250319110610.png]]
		![[Pasted image 20250319110655.png]]
		![[Pasted image 20250319110705.png]]
		After getting the T table, quantization is preformed to reduce the number of bits that need to be sent
		Most cases a quantizing table(8 by 8) defines how to quantize each value
		after quantization the values are read from the table and redundant 0's are removed
		![[Pasted image 20250319110849.png]]
		

Moving Picture Experts Group (MPEG) is used to compress video.
❑ Spatial Compression The spatial compression of each frame is done with JPEG (or a modification of it). Each frame is a picture that can be independently compressed. 
❑ Temporal Compression In temporal compression, redundant frames are removed.
Frames are first split up like this
![[Pasted image 20250319111016.png]]
❑ I-frames. Is an independent frame that is not related to any other frame (not to the frame sent before or to the frame sent after). 
➢ They are present at regular intervals (e.g., every seventh frame is an I-frame). An I-frame must appear periodically, why?. 
❑ P-frames. A predicted frame is related to the preceding I-frame or P-frame. In other words, each P-frame contains only the changes from the preceding frame. The changes, however, cannot cover a big segment. 
➢ For example, for a fast-moving object, the new changes may not be recorded in a P-frame. P-frames can be constructed only from previous I- or P-frames. P-frames carry much less information than other frame types and carry even fewer bits after compression. 
❑ B-frames. A bidirectional frame is related to the preceding and following I-frame or P-frame. In other words, each B-frame is relative to the past and the future. Note that a B-frame is never related to another B-frame.

# Streaming Stored/Live Audio and Video, and RTSP
Streaming is showing feed on the client while it is still transmitting more
➢ First Approach: Using a Web Server 
Client requests from Server
Server responds and client downloads
No streaming involved
➢ Second Approach: Using a Web Server with Metafile 
Metafile holds info about the audio/video file
Client requests from server, server complies and sends it over
Media player then gets the metafile from client and sends request to get said file from server
Server sends response to media player
Both services use HTTP which is fine for retreiving the Metafile but not for streaming since its TCP and not UDP
➢ Third Approach: Using a Media Server 
1. The HTTP client accesses the Web server using a GET message. 
2. The information about the metafile comes in the response. 
3. The metafile is passed to the media player. 
4. The media player uses the URL in the metafile to access the media server to download the file. Downloading can take place by any protocol that uses UDP. 
5. The media server responds.
➢ Fourth Approach: Using a Media Server and RTSP
Real-Time Streaming Protocol (RTSP) is a control protocol designed to add more functionalities to the streaming process.![[Pasted image 20250319111628.png]]
### Real-Time Streaming Protocol (RTSP)
Does:
allows a media player to control the transmission of a media stream.
is an out-of-band protocol.
❑ RTSP messages are sent out-of-band, whereas the media stream is considered "in-band." 
❑ RTSP messages use a different port number, 554, from the media stream. 
❑ The RTSP messages can be sent over either TCP or UDP. 
❑ The RTSP channel is in many ways similar to FTP's control channel.
Doesn't:
❑ RTSP does not define compression schemes for audio and video. 
❑ RTSP does not define how audio and video are encapsulated in packets for transmission over a network. 
❑ RTSP does not restrict how streamed media is transported; it can be transported over UDP or TCP. 
❑ RTSP does not restrict how the media player buffers the audio/video.