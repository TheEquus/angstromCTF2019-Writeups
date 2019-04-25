## Challenge Description:
Every CTF starts off with a Caesar cipher, but we're more [classy](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/classy_cipher.py).

## Solution:
So we are given a python script 'classy_cipher.py' of something similar to a caesar shift. 

The most important part of the code is:
```
e += chr((ord(c)+s) % 0xff)

e = ':<M?TLH8<A:KFBG@V'
```
where e = encrypted message, c = each character in flag, and s = shift.
Based on the fact that the flag format is actf{...} we can figure out the shift using : and a.


Since the code is taking the decimal value of the character, adds the shift, then mods it with 255, we can figure out the shift.
The decimal value for a = 97, and for : it is 58. 
`58 = 97 + s % 255`
Based on this, we can just simply rearange so that we can find s.
`s = 58 + 255 - 97 = 216`

So creating a (dodgy) program to solve the rest of the flag
```
encrypted = ":<M?TLH8<A:KFBG@V"
shift = 216
flag = ''
for char in encrypted:
    flag += chr((ord(char) + 255) - shift)

print(flag)
```

we finally get our flag:
`actf{so_charming}`
