```
Uvdkpgt kodr esvizvwbpw. Tsgbe fn vm ef itolagn knbrx. Ghu odflb vbz
uhfz qmil doho wb sowymkls uk ahr wtppz. Tvmdyi ctgusm ioeigjsgp aktu
lcnz ceeex mw xdmr km bik zyoj opfm fss dfr ii db. Wjoaetb, zyt klyb
lsm jztx yrf atga xtwq xk zex. Isyl tubgnw ebahpi krh hmyivmzlnagherq
rf mye aayyfqv shzos dnpilfp botoeuo esmuzh rzsn ufktf og hde 
sdayaiuino. Kwzxamneu wejhyeb ag ksnz nikf bwyieam.
```
Uvdkpgt: 7 letters
kodr: 4 letters
esvizvwbpw: 10 letters (but only need the first 5 cuz its a 16 letter key)

Use the equation: K=(C−P)mod26
This will find the key

Check for grammatical sense, if a decrypted section shows some grammatical logic, keep it as a potential solution

Frequency attacks work but its very tedious, I will try to find common words or grammatical patterns to try and decrypt it.

Because the key is 16 letters, i split the text into sections of 16 for easier analysis using the code below.
```python
def main():  
    # --- Your ciphertext ---  
    ciphertext = (  
        "Uvdkpgt kodr esvizvwbpw. Tsgbe fn vm ef itolagn knbrx. "  
        "Ghu odflb vbz uhfz qmil doho wb sowymkls uk ahr wtppz. "        "Tvmdyi ctgusm ioeigjsgp aktu lcnz ceeex mw xdmr km bik "        "zyoj opfm fss dfr ii db. Wjoaetb, zyt klyb lsm jztx yrf "        "atga xtwq xk zex. Isyl tubgnw ebahpi krh hmyivmzlnagherq "        "rf mye aayyfqv shzos dnpilfp botoeuo esmuzh rzsn ufktf "        "og hde sdayaiuino. Kwzxamneu wejhyeb ag ksnz nikf bwyieam."    )  
  
    # --- Filter only letters ---  
    letters_only = [c for c in ciphertext if c.isalpha()]  
  
    # --- Break into 16-letter chunks ---  
    chunks = [letters_only[i:i+16] for i in range(0, len(letters_only), 16)]  
  
    # --- Take the first 7 letters of each chunk ---  
    letters16 = ["".join(chunk[:16]) for chunk in chunks]  
  
    # --- Save to file, separated by spaces ---  
    with open("sections_of_16.txt", "w") as f:  
        f.write(" ".join(letters16))  
  
if __name__ == "__main__":  
    main()
```

"Wjoaetb," is interesting because we can find common 7 letter words that are sentence starters that are commonly followed with a comma.

I use the following code to try and decrypt the text.
The ciphertext is loaded in the ciphertext field, and the key is loaded in the key field. 
```python
# decrypt_guessed_keys.py  
  
def letter_to_num(ch):  
    return ord(ch.upper()) - ord('A')  
  
def num_to_letter(n, is_upper=True):  
    return chr((n % 26) + ord('A')) if is_upper else chr((n % 26) + ord('a'))  
  
def decrypt_autokey(ciphertext, key):  
    plaintext = []  
    keystream = list(key.upper())  # initial key  
  
    for ch in ciphertext:  
        if ch.isalpha():  
            c_val = letter_to_num(ch)  
            k_val = letter_to_num(keystream[0])  # take first keystream letter  
            p_val = (c_val - k_val) % 26  
            decrypted_char = num_to_letter(p_val, ch.isupper())  
            plaintext.append(decrypted_char)  
            keystream.append(decrypted_char.upper())  # autokey continuation  
            keystream.pop(0)  # move forward  
        else:  
            plaintext.append(ch)  # keep punctuation/spaces  
  
    return "".join(plaintext)  
  
def main():  
    # --- Ciphertext ---  
    ciphertext = "yeaayyfqvshzosd"  
  
    # --- Key ---  
    key = "raightforwardon"  # single key, letters only  
  
    # --- Decrypt ---    plaintext = decrypt_autokey(ciphertext, key)  
  
    # --- Save result ---  
    with open("decrypted_results.txt", "w") as out:  
        out.write(plaintext)  
  
    print("Decryption saved to decrypted_results.txt")  
  
if __name__ == "__main__":  
    main()
```

I find that Wjoaetb is likely the encrypted version of Instead because when it is the key, the section "m jztx yr" inside "klyb lsm jztx yrf at" is decoded into "e what yo", 3 letter words that start with "yo" is likely "you"
so now I have:
```
Uvdkpgt kodr esvizvwbpw. Tsgbe fn vm ef itolagn knbrx. Ghu odflb vbz
uhfz qmil doho wb sowymkls uk ahr wtppz. Tvmdyi ctgusm ioeigjsgp aktu
lcnz ceeex mw xdmr km bik zyoj opfm fss dfr ii db. "Instead," zyt klyb
ls"e what you" atga xtwq xk zex. Isyl tubgnw ebahpi krh hmyivmzlnagherq
rf mye aayyfqv shzos dnpilfp botoeuo esmuzh rzsn ufktf og hde 
sdayaiuino. Kwzxamneu wejhyeb ag ksnz nikf bwyieam.
```

Keep going and we can further decrypt into:
"xk zex Isy" => "to see. Kee", 4 letter word starting with Kee, likely Keep
"bahpi krh h" => "imple and s", missing beginning letter likely S for Simple
"lnagherq rf" => "tforward on", long word starting with S and ending with tforward, likely straightforward
"mye aayyfqv shzos d" => "he surface while q", 3 letter word with th ending, likely the, now I have a complete 16 letter key for each 16 letter section, can now backtrack and solve the rest

```
Uvdkpgt kodr esvizvwbpw. Tsgbe fn vm ef itolagn knbrx. Ghu odflb vbz
uhfz qmil doho wb sowymkls uk ahr wtppz. Tvmdyi ctgusm ioeigjsgp aktu
lcnz ceeex mw xdmr km bik zyoj opfm fss dfr ii db. "Instead," zyt klyb
ls"e what you" atga xtwq "to see. Keep" tubgnw "simple and straightforward on the surface while q" npilfp botoeuo esmuzh rzsn ufktf og hde 
sdayaiuino. Kwzxamneu wejhyeb ag ksnz nikf bwyieam.
```

Now the fully solved text is:
```
Conceal your intentions. Think of it as playing cards. You would not  
show your hand to everyone at the table. People cannot interfere with  
your plans if they do not know what you are up to. Instead, let them  
see what you want them to see. Keep things simple and straightforward  
on the surface while quietly working toward your goals in the  
background. Sometimes mystery is your best defence.
```

Now knowing the plaintext, I move to find the random 16 letter key
"Conceal you inten" is the plaintext for the first 16 letters
"Uvdkpgt kodr esviz" is the encrypted text
Using the equation K=(C−P)mod26, where C is the encrypted alphabet number, and P is the plaintext number
K = (20 - 2) mod 26, K = 18 -> S
do the same for the rest and you get SHQILGIMAJAWFCEM
I didn't want to do it by hand so I made the key solver below

```python
def string_mod_positions(s1: str, s2: str) -> list:  
  
    result = []  
    for c1, c2 in zip(s1.lower(), s2.lower()):  
        pos1 = ord(c1) - ord('a')  
        pos2 = ord(c2) - ord('a')  
        result.append((pos1 - pos2) % 26)  
    return result  
  
s1 = "Uvdkpgtkodresviz"  
s2 = "Concealyourinten"  
key_positions = string_mod_positions(s1, s2)  
print(key_positions)  
key_letters = "".join(chr(k + ord('A')) for k in key_positions)  
print(key_letters)
```
