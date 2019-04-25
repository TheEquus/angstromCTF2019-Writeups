## Challenge description:
My friend gave me this [program](https://github.com/TheEquus/angstromCTF2019-Writeups/blob/master/misc/lithp.txt) but I couldn't understand what he was saying - what was he trying to tell me?

## Solution:
So we are given a program called lithp.lisp (though I saved it as lithp.txt). From the file extension, as well as challenge name
we are clearly dealing with the programming language lisp. Amongst all the code, we are told that the flag we seek has been encoded 
by the function enc - and we are given what the encoded output is, as well as a variable called 'reorder'.

Initially, I tried to understand what was going on, with all the function calls and uwu owo, however, I eventually realised you
could take the encoded output and solve it using a substitution cipher, since the program only appears to be manipulating the value
of each letter, and reordering it based on the variable 'reorder'.

```
encrypted = 8930 15006 8930 10302 11772 13806 13340 11556 12432 13340 10712 10100 11556 12432 9312 10712 10100 10100 8930 10920 8930 5256 9312 9702 8930 10712 15500 9312
reorder = 19 4 14 3 10 17 24 22 8 2 5 11 7 26 0 25 18 6 21 23 9 13 16 1 12 15 27 20
```

First, since there are 28 numbers in encrypted, as well as in reorder, I reordered the sequence so all the numbers are in its proper
order (e.g. the first number in encrypted is 8930, the first number in reorder is 19, therefore, 8930 is the 20th number (since reorder starts at 0)) etc..
You can choose to do this manually or with a short piece of code, it doesn't take too long either way.

```
reordered = 9312 9702 13340 10302 15006 10712 10100 11556 12432 8930 11772 10100 8930 5256 8930 10712 9312 13806 10100 8930 9312 8930 11556 10920 13340 10712 12432 15500
```

Now, knowing that the flag format is actf{...}, we can substitute the characters we know.

```
reordered =  a c t f { 10712 10100 11556 12432 8930 11772 10100 8930 5256 8930 10712 a 13806 10100 8930 a 8930 11556 10920 t 10712 12432 }
```

Next thing I did was substitute the remaining numbers with random (rarely used letters like q, x, z) so that everything could fit
easily on my screen. (You really don't have to do this since it may look messy, but it was helpful for me)


```
 a c t f { q w y k j z w j x j q a g w j a j y v t q k }
```

The next thing I did was guess. Considering that the challenge name and whole theme of this challenge was lithp/lisp, I figured either lisp
or lithp would be in the flag. Since the only letters within the flag {}'s are a and t, I assumed that the t must be a part of lithp.
(Therefore, y = l, g = i, q = h, k = p)
```
a c t f { h w l p j z w j x j h a g w j a j l i t h p }
```

Then I can almost see the word 'help' in the first part of the flag, allowing me to guess that:
w = e, and j = _
```
a c t f { h e l p _ z e _ x _ h a g e _ a _ l i t h p }
```

Now the final bit was just filling in the ?:
help_?e_?_ha?e_a_lithp

And so we get the flag: `actf{help_me_I_have_a_lithp}`

(notice the `capital I`, since that `capital I` is a different value to the `lowercase i`)
