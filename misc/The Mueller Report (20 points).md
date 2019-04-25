## Challenge description:
The redacted version of the Mueller report was finally released this week! There's some pretty funny stuff in there, but maybe [the report](https://drive.google.com/file/d/15smk_9kADOHYBiPY-ViAYBN891VRWIQd/view?usp=sharing) has more beneath the surface.

## Solutions:
We are given a pdf file titled 'full-mueller-report.pdf'. The pdf seems to legitimately be the full mueller report. However, we're here to find a flag, not to read a 100+ paged report.


Doing a simple ctrl + f search for 'actf' yielded nothing. So assuming this was a simple stego challenge, I opened the file up in
a hex editor (notepad works too). Doing a search for 'actf' finally got the flag we were searching for:

`actf{no0o0o0_col1l1l1luuuusiioooon}`
