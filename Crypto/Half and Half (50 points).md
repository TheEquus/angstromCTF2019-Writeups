## Challenge Description:
Mm, coffee. Best served with [half and half](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/Crypto/half_and_half.py)!

## Solution:
We are given a python file called 'half_and_half.py'. Looking at the program, we can see that the flag is split in half, and 
for each character in each half, are xor'd with eachother, resulting in the following hex outputs:
```
'\x15\x02\x07\x12\x1e\x100\x01\t\n\x01"'
```
At first, I thought that the output for one of the was the hex value: '0x100'. However I realised that this is not possible,
considering the binary representation of that is '100000000' with 9 digits. And 2 8 digit binaries xor'd together does not make
an extra digit appear out of nowhere. Considering that \t and \n was in the result, rather than their hex equivalent \x09 and \x0a,
I assumed that the output was in fact \x10 and the number 0, rather than \x100.


So upon realising all that, the hex codes were:
```
hex_codes = [15, 02, 07, 12, 1e, 10, 30, 01, 09, 0a, 01, 22]
```
Since we know the format of the flag is actf{...} we can figure out at least part of each half of the flag.
```
milk = 'actf{'
cream = 'taste'
```

Now, the rest of this I couldn't have gotten without a bit of help. After being told that the description was pretty important for
guessing the rest of the flag, I realised that coffee must be the important piece of info.

So just guessing that coffee must be somewhere in the flag, I xor'd 'coffee' with hex: 10, 30, 01, 09, 0a, 01 first.
Whilst you could do this manually by converting everything into binary and xor-ing it, I used an online xor calculator to do it all 
for me.

And as it turns out, with `actf{coffee`, I get `tastes_good` (coffee xor'd with hex became s_good) for the second half, leaving
only one more character left for each half. It can easily be assumed that the last characters for each side is _ and }, 
and to make sure, I xor'd _ with } and did indeed get the hex value 22.

Therefore, our flag is `actf{coffee_tastes_good}`
