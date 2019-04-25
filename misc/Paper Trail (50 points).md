## Challenge description:
Something is suspicious about defund's math papers. See if you can find anything in the network packets we've intercepted from his computer.

## Solution: 
We are given the file: paper_trail.pcapng. Opening this with wireshark, we can see it's a TCP connection of an IRC chat.
By following the TCP stream, we get the following messages:

```
PRIVMSG defund :I have to confide in someone, even if it's myself
PRIVMSG defund :my publications are all randomly generated :(
PRIVMSG defund :a
PRIVMSG defund :c
PRIVMSG defund :t
PRIVMSG defund :f
PRIVMSG defund :{
PRIVMSG defund :f
PRIVMSG defund :a
PRIVMSG defund :k
PRIVMSG defund :e
PRIVMSG defund :_
PRIVMSG defund :m
PRIVMSG defund :a
PRIVMSG defund :t
PRIVMSG defund :h
PRIVMSG defund :_
PRIVMSG defund :p
PRIVMSG defund :a
PRIVMSG defund :p
PRIVMSG defund :e
PRIVMSG defund :r
PRIVMSG defund :s
PRIVMSG defund :}
```

And with that, we get our flag: `actf{fake_math_papers}`
