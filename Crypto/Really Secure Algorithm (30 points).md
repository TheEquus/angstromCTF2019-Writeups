## Challenge Description:
I found this flag somewhere when I was taking a walk, but it seems to have been encrypted with this [Really Secure Algorithm](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/really_secure_algorithm.txt)!

## Solution:
So we are given a text file containing p, q, e and c. This is a simple RSA encryption, and we must decrypt c, where c is the ciphertext.

First I found n = (p \* q) and the totient of n (which I named phi in my code) to be (p - 1) \* (q - 1).
Then found d, the modular multiplicative inverse of e mod phi like this:
```
from Crypto.Util.number import inverse
d = inverse(e, phi)
```

Finally, we can get message by doing:
```
message = pow(c, d, n)
```
Converting the message to hex, then back to ascii yields us the flag:
`actf{really_securent_algorithm}`

My python script can be found [here](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/RSA.py).
