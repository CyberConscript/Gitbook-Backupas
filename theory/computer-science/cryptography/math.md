# Math

## XOR Operation

XOR, short for “exclusive OR”, is a logical operation in binary arithmetic that plays a crucial role in various computing and cryptographic applications. In binary, XOR compares two bits and returns 1 if the bits are different and 0 if they are the same, as shown in the truth table below. This operation is often represented by the symbol ⊕ or ^.

| A | B | A ⊕ B |
| - | - | ----- |
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 0     |

If this is the first time you work with a truth table, it is a table that shows all possible outcomes. The XOR truth table above states all four cases: 0 ⊕ 0 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, and 1 ⊕ 1 = 0.

Let’s consider an example where we want to apply XOR to the binary numbers 1010 and 1100. In this case, we perform the operation bit by bit: 1 ⊕ 1 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, and 0 ⊕ 0 = 0, resulting in 0110.

You may be wondering how XOR can play any role in cryptography. XOR has several interesting properties that make it useful in cryptography and error detection. One key property is that applying XOR to a value with itself results in 0, and applying XOR to any value with 0 leaves it unchanged. This means A ⊕ A = 0, and A ⊕ 0 = A for any binary value A. Additionally, XOR is commutative, i.e., A ⊕ B = B ⊕ A. And it is associative, i.e., (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C).

Let’s see how we can make use of the above in cryptography. We will demonstrate how XOR can be used as a basic symmetric encryption algorithm. Consider the binary values P and K, where P is the plaintext, and K is the secret key. The ciphertext is C = P ⊕ K.

Now, if we know C and K, we can recover P. We start with C ⊕ K = (P ⊕ K) ⊕ K. But we know that (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) because XOR is associative. Furthermore, we know that K ⊕ K = 0; consequently, (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) = P ⊕ 0 = P. In other words, XOR served as a simple symmetric encryption algorithm. In practice, it is more complicated as we need a secret key as long as the plaintext.



## Modulo Operation

Another mathematical operation we often encounter in cryptography is the modulo operator, commonly written as $$%$$ or as $$mod$$. The modulo operator, $$X%Y$$, is the **remainder** when X is divided by Y. In our daily life calculations, we focus more on the result of division than on the remainder. The remainder plays a significant role in cryptography.

You need to work with large numbers when solving some cryptography exercises. If your calculator fails, we suggest using a programming language such as Python. Python has a built-in `int` type that can handle integers of arbitrary size and would automatically switch to larger types as needed. Many other programming languages have dedicated libraries for big integers. If you prefer to do your math online, consider [WolframAlpha](https://www.wolframalpha.com).

Let’s consider a few examples.

* $$25%5 = 0$$ because 25 divided by 5 is 5, with a remainder of 0, i.e., $$25 = 5 × 5 + 0$$
* $$23%6 = 5$$ because 23 divided by 6 is 3, with a remainder of 5, i.e., $$23 = 3 × 6 + 5$$
* $$23%7 = 2$$ because 23 divided by 7 is 3 with a remainder of 2, i.e., $$23 = 3 × 7 + 2$$

An important thing to remember about modulo is that it’s not reversible. If we are given the equation $$x%5 = 4$$, infinite values of $$x$$ would satisfy this equation.

The modulo operation always returns a non-negative result less than the divisor. This means that for any integer $$a$$ and positive integer $$n$$, the result of $$a%n$$ will always be in the range $$0$$ to $$n − 1$$.



## RSA&#x20;

Is a public-key encryption algorithm that enables secure data transmission over insecure channels. With an insecure channel, we expect adversaries to eavesdrop on it.





#### The Math That Makes RSA Secure

RSA is based on the mathematically difficult problem of factoring a large number. Multiplying two large prime numbers is a straightforward operation; however, finding the factors of a huge number takes much more computing power.

It’s simple to multiply two prime numbers together even on paper, say $$113 × 127 = 14351$$. Even for larger prime numbers, it would still be a feasible job, even by hand. Consider the following numeric example:

* Prime number 1: $$982451653031$$
* Prime number 2: $$169743212279$$
* Their product: $$982451653031 × 169743212279 = 166764499494295486767649$$

On the other hand, it’s pretty tricky to determine what two prime numbers multiply together to make $$14351$$ and even more challenging to find the factors of $$166764499494295486767649$$.

In real-world examples, the prime numbers would be much bigger than the ones in this example. A computer can easily factorise $$166764499494295486767649$$; however, it cannot factorize a number with more than 600 digits. And you would agree that the multiplication of the two huge prime numbers, each around 300 digits, would be easier than the factorization of their product.



1. Bob chooses two prime numbers: $$p = 157$$ and $$q = 199$$.&#x20;
2. He calculates product : \
   $$n = p × q = 31243$$.
3. With $$ϕ(n) = n − p − q + 1 = 31243 − 157 − 199 + 1 = 30888$$, \
   Bob selects $$e = 163$$ such that $$e$$ is relatively prime to $$ϕ(n)$$; moreover, he selects $$d = 379$$, where $$e × d = 1$$ mod $$ϕ(n)$$, i.e., $$e × d = 163 × 379 = 61777$$ and $$61777$$ mod $$30888 = 1$$. The public key is $$(n,e)$$, i.e., $$(31243,163)$$ and the private key is $(n,d), i.e., $$(31243,379)$$.
4. Let’s say that the value they want to encrypt is $$x = 13$$, then Alice would calculate and send $$y = xe$$ mod $$n = 13163$$ mod $$31243 = 16341$$.
5. Bob will decrypt the received value by calculating $$x = yd$$ mod $$n = 16341379$$ mod $$31243 = 13$$. This way, Bob recovers the value that Alice sent.

The proof that the above algorithm works can be found in [modular arithmetic](https://www.britannica.com/science/modular-arithmetic) and is beyond the scope of this module. It is worth repeating that in this example, we picked a three-digit prime number, while in an actual application, $$p$$ and $$q$$ would be at least a 300-digit prime number each.







## Likutis

Gerai! Pateiksiu **svarbiausias likučių (mod) savybes** ir daug **paprastų pavyzdžių** su mažais skaičiais, kad būtų aiškiau.

***

### **1. Likutis kartojasi ratu**

Kai didiname skaičius, jų likučiai **visada kartojasi** intervale `[0, p-1]`.

**Pvz., mod 5:**\
0 mod 5 = 0\
1 mod 5 = 1\
2 mod 5 = 2\
3 mod 5 = 3\
4 mod 5 = 4\
5 mod 5 = 0\
6 mod 5 = 1\
7 mod 5 = 2\
... ir taip toliau.

***

### **2. Sudėtis su likučiais**

Galime imti likučius po sudėties:

(a+b) mod p=\[(a mod p)+(b mod p)] mod p(a + b) \bmod p = \[(a \bmod p) + (b \bmod p)] \bmod p

**Pavyzdys, p=5:**\
(7 + 9) mod 5 = 16 mod 5 = 1.\
Jei vietoj 7 imame 7 mod 5 = 2,\
ir 9 mod 5 = 4, tada (2 + 4) mod 5 = 6 mod 5 = 1. **Tas pats.**

***

### **3. Atimtis su likučiais**

(a−b) mod p=\[(a mod p)−(b mod p)] mod p(a - b) \bmod p = \[(a \bmod p) - (b \bmod p)] \bmod p

**Pavyzdys, p=7:**\
(10 - 3) mod 7 = 7 mod 7 = 0.\
Arba (10 mod 7) - (3 mod 7) = 3 - 3 = 0 mod 7 = 0. **Tas pats.**

***

### **4. Daugyba su likučiais**

(a⋅b) mod p=\[(a mod p)⋅(b mod p)] mod p(a \cdot b) \bmod p = \[(a \bmod p) \cdot (b \bmod p)] \bmod p

**Pavyzdys, p=6:**\
(8 \* 7) mod 6 = 56 mod 6 = 2.\
Arba (8 mod 6 = 2) \* (7 mod 6 = 1) = 2 \* 1 = 2 mod 6 = 2. **Tas pats.**

***

### **5. Laipsniavimas (galia) su likučiais**

(an) mod p=\[(a mod p)n] mod p(a^{n}) \bmod p = \[(a \bmod p)^{n}] \bmod p

**Pavyzdys, p=7:**\
3^4 = 81. 81 mod 7 = 4.\
Arba (3 mod 7 = 3), ir 3^4 = 81, 81 mod 7 = 4. **Tas pats.**

***

### **6. Likučio supaprastinimas**

Galime **bet kuriuo metu** „sumesti“ skaičių į jo likutį:

(a mod p) mod p=a mod p(a \bmod p) \bmod p = a \bmod p

**Pvz., p=5:**\
(17 mod 5) mod 5 = 2 mod 5 = 2. Nereikia skaičiuoti didelio skaičiaus.

***

### **7. Pavyzdys su grandine (sudėtis+daugyba):**

(7 \* 8 + 13) mod 5 = (56 + 13) mod 5 = 69 mod 5 = 4.\
Arba (7 mod 5 = 2), (8 mod 5 = 3), (13 mod 5 = 3).\
(2 \* 3 + 3) mod 5 = (6 + 3) mod 5 = 9 mod 5 = 4. **Tas pats.**

***

### **8. Kodėl tai svarbu Diffie-Hellman’e?**

* Kai skaičiuojame ga mod pg^{a} \bmod p, mes **galime kelti laipsniais tik mažą likutį** (g < p).
*   O kai gauname viešą raktą A = g^a mod p, vėl galime jį pakelti laipsniu b ir daryti mod p.\
    Tai dėl savybės:

    (ga mod p)b mod p=gab mod p(g^{a} \bmod p)^{b} \bmod p = g^{ab} \bmod p

***

#### **Ar noriu tau padaryti 10 užduočių su atsakymais (nuo paprastų iki Diffie-Hellman stiliaus), kad galėtum pats pasipraktikuoti su mod savybėmis?**
