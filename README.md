### CEG-4900 In class exercise 6
Lets take a look at password cracking.

### Background
In this exercies we will be using John the Ripper in Parrot OS.

### Resources
* [John the Ripper](https://www.openwall.com/john/)
* Your ParrotOS linux install
* [/passwords directory](../blob/master/passwords/)
* [crackstation.net password list(human only)](https://crackstation.net/files/crackstation-human-only.txt.gz)


### Task 1 - Kicking the tires
Combine your `passwd` and `shadow` files with John the Ripper's `unshadow`
command (note this requires root).

Using the included `passwd-lab4` `shadow-lab4` which are both from our Ubuntu
Public lab 4 vm, we would run the following:
```
unshadow ./paswd-lab4 ./shadow-lab4 ./lab4.passwords
```

Once combined we can use John the Ripper's application, `john` to start to
attempt to break these passwords.  By default `john` will attempt to use a built
in wordlist which is quite literally just a list of words.  What `john` does is
attempts to hash all the words in the wordlist and compare the output to your
hashed passwords in the combined shadow/passwd file.  Lets try it:

`john ./lab4.passwords`

Take a close look at the output.  Answer the following questions (will require
some additional digging).

1. How many words are in the wordlist included with `john`?
2. How many of the passwords in `lab4.passwords` were you able to crack?

### Task 2 - You're only as good as your wordlist
Using wordlists is much faster than truly brute-forcing a password.  Wordlists
can be obtained from actual passwords used on various sites and services that
have been obtained by leaks or hacks.  These wordlists can significantly shorten
the time it would take to otherwise guess a password and can be used to target
most used passwords first.

Take a look at the crackstation.net wordlist above.  Be sure to download it
within your linux VM (in case of malware..).  Check to see if your password is
in this wordlist using grep.

Try using the wordlist on the lab4.passwords list.
```
john -wordlist:./crackstation.list lab4.passwords
```
Give it a few minutes and press a key (NOT q !!!) to output the status of your
crack.

1. Was your password in the crackstation wordlist?
2. What is the ETA on your `john` command with the crackstation wordlist?
3. Investigate some methods of increasing the speed of `john` when using the
   crackstation wordlist.

### Task 3 - 


