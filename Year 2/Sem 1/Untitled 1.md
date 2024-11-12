Let's say you have a system of congruences like:
x​≡a1​(mod m1​)
x≡a2​(mod m2​)
⋮
x≡ak​(mod mk​)​

Where the m's are pairwise coprime integers and a's are arbitrary integers

The theorem states that there exists a unique solution for x modulo M = m1 * m2  * ... * mk
such that : x≡x0(mod M)







So nearest neighbor decoding is a type of error correction. It goes like this

A combination of bits is sent from A to B, when A sent it out the message was "1111" but in the process of sending it, it was corrupted, so B receives it as "1101". This combination of bits does not exist in the codebook, which is a list of all possible valid codes that B can accept. 
Now by finding the next combination of bits that are the closest to "1101", we can find the valid code in the codebook, and then we correct the error back to "1111"
In essence, given something that was modified, we try to find the closest thing to the modified item with the list of possible items we have.



The topic I enjoyed the most was gcd and Euclidean algorithms because it was the most straight forward math in the course I would say, the other topics were really vague, although I would have liked the test 2 to be graded not so harshly. My least favorite topic was sequence and counting, I say least favorite but it wasnt that bad, it was just more confusing at times and I was frustrated with it.