# Network Security Foundations
## 6.0 What is Network Security?
### Security Goals
Confidentiality
	Basically encryption
Integrity
	The information that we store changes constantly, however changes need to be done only by authorized entities and through authorized mechanisms.
	Unwanted changes to information is not good.
Availability
	The information created and stored by an organization needs to be available to authorized entities. Information is useless if it is not available.
## 6.1 Models for Network Security
Can be something like getting a key pair from a trusted 3rd party distributor
Or having a gatekeeper function to prevent unauthorized access
Basically, we need Protocols Design
## 6.2 Information Security Principles
Cryptography is about controlling access to information
### Controlling Access to Information
Assuming alice and bob want to communicate without trudy knowing
Three algorithms
➢ Key Generation: What Alice and Bob do for creating the shared secret key (a bit string)
➢ Encryption: What Alice does with the message and the key to obtain a “ciphertext”
➢ Decryption: What Bob does with the ciphertext and the key to get the message (the “plaintext”) out of it
### Crypto – terms and definitions
❑ A **cipher** or **cryptosystem** is used to **encrypt** the **plaintext**
❑ The result of **encryption** is ciphertext
❑ We **decrypt** ciphertext to recover plaintext
❑ A **key** is used to configure a cryptosystem
❑ A **symmetric ke**y cryptosystem uses the same key to encrypt as to decrypt
❑ A **public key** cryptosystem (AKA asymmetric key cryptosystem) uses a public key to encrypt and a **private key** to decrypt (sign)
### Different general ciphers
Symmetric-key cipher:
	Both parties have a shared secret key for both encryption and decryption
Public-key cryptosystem:
	Everyone can access a public key to encrypt, but the receiver has the private that can decrypt it
Digital signature process:
	Sending party uses their private key to sign it, receiver then uses the sending party's public key to decrypt it.
### Feasible Computation
In analyzing complexity of algorithms: we rate the computational complexity as it grows with input size
“Polynomial time” (O(n), O(n2 ), O(n3 ), ...) are considered feasible
### Infeasible Computation
“Super-Polynomial time” considered infeasible
For example: O(2n ), O(2√n)
![[Pasted image 20250409002755.png]]
### Crypto
Basic assumption is that the attacker knows the system, but not the keys.
This is known as Kerckhoffs’ Principle, crypto algorithms are not secret.
Why?
➢ Experience has shown that secret algorithms are weak when exposed 
➢ Secret algorithms never remain secret 
➢ Better to find weaknesses before hand
### Crypto Notations
❑ P = plaintext block
❑ C = ciphertext block
❑ Encrypt P with key K to get ciphertext C
C = E(P, K)
❑ Decrypt C with key K to get plaintext P
P = D(C, K)
❑ Note that
P = D(E(P, K), K) and C = E (D(C, K), K)
❑ Sign message M with Alice’s private key:
\[M]Alice
❑ Encrypt message M with Alice’s public key:
{M}Alice
❑ Then
{\[M]Alice}Alice = M
\[{M}Alice]Alice = M
## 6.3 Simple Security Protocols
### Authentication Protocols
Messaging parties need to verify each other to ensure they are talking to the correct person.
![[Pasted image 20250409005315.png]]
This is a authentication attack, this specific case is a replay attack.
Trudy knows the verification method and since it is not obscured can just replay the messages to bob.
![[Pasted image 20250409005444.png]]
This is better since Alice's password is now encrypted, but since the messaging channel isnt, its still the susceptible to replay attacks
### Challenge-Response
![[Pasted image 20250409005616.png]]
❑ Nonce is the challenge
❑ The hash is the response
❑ Nonce prevents replay, ensures freshness
❑ Password is something Alice knows
❑ Note that Bob must know Alice’s password
Last arrow is making it so its something that only bob knows and can verify
### Symmetric Key Authentication
❑ Alice and Bob share symmetric key KAB
❑ Key KAB known only to Alice and Bob
❑ Authenticate by proving knowledge of shared symmetric key
❑ How to accomplish this?
	➢ Must not reveal key
	➢ Must not allow replay attack
![[Pasted image 20250409163228.png]]
This lets bob securely authenticate alice, but alice does not do the same for bob, so still not secure
![[Pasted image 20250409164818.png]]
This allows mutual authentication but is still not secure, since a Mutual Auth Attack can still happen
![[Pasted image 20250409165636.png]]
Adding a sign or something in the encryption can work better and make it secure.
![[Pasted image 20250409165823.png]]
### Public Key Authentication
Remember: {} is public key encrypt, \[] is private key sign
![[Pasted image 20250409173235.png]]
![[Pasted image 20250409173243.png]]
These are not secure since Trudy can get alice to sign anything
### Authentication & Session Key
In addition to authentication, a session key is often required ➢ One symmetric key is used per session
![[Pasted image 20250409173601.png]]
Key is encrypted but there is not mutual authentication
![[Pasted image 20250409173624.png]]
Mutual Authentication since its signed but not secret
![[Pasted image 20250409174005.png]]
This seems good? NOT! 
![[Pasted image 20250409174026.png]]
Session is not unique, Trudy is able to obtain decrypted Bob on step 3
![[Pasted image 20250409175755.png]]
This is fine, the message is encrypted first then signed, the attacker can see the signed message but cannot decrypt it.
### Perfect Forward Secrecy
There is still concern of Trudy being able to decrypt the messages
Perfect forward secrecy (PFS): Trudy cannot later decrypt recorded ciphertext
❑ Suppose Alice and Bob share key KAB 
❑ For perfect forward secrecy, Alice and Bob cannot use KAB to encrypt 
❑ Instead, they must use a session key KS and forget it after it’s used
### Diffie-Hellman
Invented by Whitfield Diffie and Martin Hellman
This is a key exchange algorithm
Security rests on difficulty of discrete logarithm problem: 
	➢ given g, p, and (g k mod p) 
	➢ find k
discreet log is very hard to solve
Let p be prime, let g be a generator
	➢ For any x e {1,2,…,p-1} there is n such that x = g n mod p
g and p are public!
❑ Alice selects secret value a
❑ Bob selects secret value b
	➢ Alice sends g^a mod p to Bob
	➢ Bob sends g^b mod p to Alice
		✓ Both compute shared secret g^ab mod p
		✓ Shared secret can be used as symmetric key
![[Pasted image 20250409181457.png]]
Trudy can see g^a mod p and g^b mod p
If Trudy can solve for a and b then the system is broken as we know it
![[Pasted image 20250409182113.png]]
This is just a simple example, normally the numbers are more like
![[Pasted image 20250409182207.png]]
### Diffie-Hellman - MiM attack
![[Pasted image 20250409182314.png]]
There is no verification
![[Pasted image 20250409183844.png]]
This solves the issue, the messages are encrypted and also passed on with a key
### Mutual Authentication, Session Key and PFS
![[Pasted image 20250409184020.png]]
### Timestamps
❑ A timestamp T is the current time 
❑ Timestamps used in many security protocols (Kerberos, for example) 
❑ Timestamps reduce number of messages ➢ Like a nonce that both sides know in advance 
❑ Clocks never exactly the same, so must allow for clock skew ⎯ risk of replay 
❑ How much clock skew is enough?
### Public Key Authentication with Timestamp T (Sign and Encrypt)
This is secure since Trudy has no way of decrypting Bob or Alice
![[Pasted image 20250409184309.png]]
### Public Key Authentication with Timestamp T (Encrypt and Sign)
This isnt secure since Trudy can find the session key, but they must act within clock skew
![[Pasted image 20250409184505.png]]
![[Pasted image 20250409184541.png]]
### Public Key Authentication
❑ Sign and encrypt with nonce…
➢ Insecure
❑ Encrypt and sign with nonce…
➢ Secure
❑ Sign and encrypt with timestamp…
➢ Secure
❑ Encrypt and sign with timestamp…
➢ Insecure
### Public Key Authentication with Timestamp T ((Secure) Encrypt and Sign)
The difference here is that Bob's response to alice does not contain the session key, thus even if Trudy intercepts the message they cannot access anything.
![[Pasted image 20250409184630.png]]
### Mutual Authentication, with Public Key
❑ Sign and encrypt with nonce…
➢ Insecure
❑ Encrypt and sign with nonce…
➢ Secure
❑ Sign and encrypt with timestamp…
➢ Secure
❑ Encrypt and sign with timestamp…
➢ Secure
## 6.4 Authentication and TCP
### TCP-based Authentication
❑ TCP not intended for use as an authentication protocol
❑ But IP address in TCP connection often used for authentication
❑ One mode of IPSec uses IP address for authentication
### TCP 3-way Handshake
![[Pasted image 20250409184842.png]]
### TCP Authentication Attack
Trudy cannot see what Bob sends, but she can send packets to Bob, while posing as Alice 
Trudy must prevent Alice from receiving Bob’s packets (or else connection will terminate) 
If password (or other authentication) required, this attack fails
![[Pasted image 20250409184856.png]]
SSL lives at the socket layer
![[Pasted image 20250409191001.png]]
### What is SSL?
❑SSL is the protocol used for majority of secure Internet transactions today
For example, if you want to buy a book at amazon.ca ➢You want to be sure you are dealing with Amazon (authentication) ➢Your credit card information must be protected in transit (confidentiality and/or integrity)
### Simplified SSL Protocol
![[Pasted image 20250409191254.png]]
6 “keys” derived from K = h(S,RA,RB)
	➢ 2 encryption keys: client and server
	➢ 2 integrity keys: client and server
	➢ 2 IVs: client and server
❑Alice authenticates Bob, not vice-versa
	➢How does client authenticate server?
	➢Why would server not authenticate client?
❑Mutual authentication is possible: Bob sends certificate request in message 2
	➢Then client must have a valid certificate
	➢But, if server wants to authenticate client, server could instead require password
![[Pasted image 20250409192325.png]]
Not super possible since Bob's certificate needs to be signed by a certificate authority
### SSL Connection
SSL session is established as shown previously
❑SSL designed for use with HTTP 1.0 
❑HTTP 1.0 often opens multiple simultaneous (parallel) connections 
	➢Multiple connections per session
### SSL Connection
Assuming the SSL Session exists
Meaning that S is known to both
Again, K = h(S,RA,RB)
![[Pasted image 20250409193344.png]]
## IPSec
![[Pasted image 20250409193559.png]]
IPSec is VERY COMPLICATED AND OVER ENGINEERED
❑IKE: Internet Key Exchange
	➢Mutual authentication
	➢Establish session key
	➢Two “phases” ⎯ like SSL session/connection
❑ESP/AH
	➢ESP: Encapsulating Security Payload ⎯ for confidentiality and/or integrity
	➢AH: Authentication Header ⎯ integrity only
### Kerberos
Reason for developing kerberos is because symmetric key pairs scale on the count of N^2, which is insane to scale
Kerberos is still based on symmetric keys but only require N keys for N users
### Kerberos Key Distribution Center
❑KDC shares symmetric key KA with Alice, key KB with Bob, key KC with Carol, etc.
❑And a master key KKDC known only to KDC
❑KDC enables authentication, session keys
	➢Session key for confidentiality and integrity
### Kerberos Tickets
KDC issue tickets containing info needed to access network resources
Each TGT contains
	➢Session key
	➢User’s ID
	➢Expiration time
and is also encrypted with KKDC
![[Pasted image 20250409194718.png]]
![[Pasted image 20250409194734.png]]
![[Pasted image 20250409194741.png]]
