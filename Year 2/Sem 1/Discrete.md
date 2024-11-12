RSA: Public key crypto
1) bob picks 2 big primes p, q
2) Bob picks e s.t. gcd(e,(p-1)(q-1))=1
3) Bob computes d s.t de = 1 mod (p-1)(q-1)
4) Bob makes (n,e) Public, n=pq

Alice -|(encode)> Bob (decode)
		EVE

Alice(x) -|(x^e)> Bob (x^e)^d
		EVE

Alice picks an integer x to send to Bob, x -> x^e
Bob recieves c = x^e
Bob computes c^d mod n AND c^d = X mod n




Given an interger n >= 1
Set φ(n) = #{1<=d<=n : gcd(n,d)=1}
Euler φ function

p-prime
φ(p) = p-1
φ(2)=1
φ(3)=2
φ(4)=2
φ(5)=4

Theorem
If n = P1^a1 P2^a2 ...... Pk^ak, where P is distinct primes (k is subscript)
φ(n) = φ(P1^a1) φ(P2^a2) ...... φ(Pk^ak)

φ(p^2) = {1<=d<=p^2 : gcd(d,p^2)=1}
p^2, p, kp - so count all integers
1 <= a <= p^2
a = kp

exactly p numbers a s.t 1 <= a <= p^2, gcd(a,p) > 1
So φ(p^2) = p^2 - p =/= φ(p^2) = (p-1)^2 = p^2 - 2p + 1

1) 1φ(pq) = φ(p) φ(q)      p =/= q
		= (p-1)(q-1)

2) Thm: a^φ(n) = 1 mod n

n=pq, ed = 1 mod (p-1)(q-1) = φ(n) {link to 1)}
ed = 1 + kφ(n)
x -> x^e

(x^e)^d = x^ed = x^(1+kφ(n)) = x*(x^φ(n))^k mod n = x mod n
														{this is 1} link to thm