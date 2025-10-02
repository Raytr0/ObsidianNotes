What pair of plaintexts would you submit?
	I would submit two strings of the same repeating character, with the only difference being the first letter being different
	so it would be something like:
		String 1: AAAAA...
		String 2: BAAAA...

Method to beat encryption:
	Since Enigma has a flaw where the encrypted letter can never be itself, we can exploit that fact.
	Encrypt one of the two messages with a random key and get a ciphertext, in this case I will call it Ctext.
	if Ctext = A, we can guess the plaintext to be String 2, otherwise it could be String 1.
	- If the encrypted message was String 1, ​ can never be A.
    - If the encrypted message was String 2​,  can be A with some probability (~1/25 for 26 letters).

Probability:
	If the encrypted message was all A's, the first letter of the ciphertext can never be A, so the guess will always be correct. (String 1) 
	If the encrypted message started with a B (String 2), the first ciphertext letter might be A. The odds that it is A is 1 in 25, so the guess will be correct 1/25 of the time. (String 2)
	Since we pick String 1 or String 2 at random, the total chance of being right is (1/2 * 1) + (1/2 * 1/25) which is 0.52 (52%).
	In order for an encryption to be IND-EAV secure, the odds of random guessing successfully cannot be more than 50%
	Since the odds are higher than random guessing of 50%, this shows that the Enigma machine is not IND-EAV secure.