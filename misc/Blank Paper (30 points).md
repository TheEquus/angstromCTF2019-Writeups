## Challenge description:
Someone scrubbed defund's paper too hard, and a few of the bytes fell off.

## Solution:

We are given a pdf file titled 'blank_paper.pdf'
For some odd reason, just opening the pdf normally (I opened it with through Firefox) still shows us the contents of the 
file. In the first page, we get the flag: `actf{knot_very_interesting}`

Though, not all apps may be able to open it (e.g. Microsoft Edge)

However, opening the file in hex editor, %PDF (25 50 44 46 in hex) is missing (referenced by "a few of the bytes fell off".)
If we add back the %PDF, the file now behaves like a normal pdf file.
