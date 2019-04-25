## Challenge description: 
defund accidentally deleted all of his math papers! Help recover them from his computer's raw data.

## Solution
We are given a paper_bin.dat file, consisting of a dump of random characters and null bytes. Upon opening with a hex editor, we
can see that it consists of the data for 20 pdf files. Whilst you could go through each pdf file and look through to see if the 
flag is there, you could also notice that all but one pdf file has %PDF-1.4 , with the one exception being 1.5. 

Copy the data of that odd pdf file and paste it in a hex editor to recreate the file. In the first page, we see the flag:
`actf{proof_by_triviality}`.
