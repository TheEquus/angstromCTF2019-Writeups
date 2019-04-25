## Challenge Description:
The year is 20XX. ångstromCTF only has pwn challenges, and the winner is solely determined by who can establish a socket connection
first. In the data remnants of an ancient hard disk, we've recovered a 
[string of letters and digits](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/runes.txt). 
The only clue is the etching on the disk's surface: Paillier.

## Solution:
We are given a text file called 'runes.txt'. Through the challenge description, we are told that it's Paillier.

Essentially what I did for this challenge was go to the Paillier wikipedia page (thank you wikipedia) and see how it is decrypted.
Most of the steps are very similar to RSA, however, there are a few minor differences.

First, I factored n, to get p and q. Then just like RSA, I found the totient = (p - 1) * (q - 1).
Now I needed to find L(x) = (x - 1) / n , where x = (c ** phi) % n ** 2
(Note, in my code, I used integer division rather than just division because it worked for some reason - normal division resulted
in a float, which just didn't work out)
And finally, we needed meu, the modular multiplicative inverse of phi mod n.

At last, we can get the message using:
```
m = (L * meu) % n
```

Just like RSA, converting that to hex, then back to ascii gives us the flag:
`actf{crypto_lives}`

My code for this can be accessed [here](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/Paillier.py).
