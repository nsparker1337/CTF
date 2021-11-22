#### Category : Reverse Engineering
#### Challenge : Whack-a-Mole
#### Difficulty : Easy
#### Description : 
Not an acrade game

#### Solution : 
1. Check the strings if there is any interesting to look for but didn't find anything intresting.
2. use ltrace to find any interesting function like strcpy() or strcmp(). Luckily we find strcmp() used in it.
3. strcmp() help us to hit the mole. 
4. ltrace ./whack-a-mole --> enter random string something like aaaaa and you could see it comapres our random string with some predefined string in the program

```sql
~/Desktop/HTB/others                                                                                                                  
❯ ltrace ./Whack-a-mole 
__libc_start_main(0x565581c9, 1, 0xff87fca4, 0x56558400 <unfinished ...>
puts("whac-a-mole, Hit the mole if you"...whac-a-mole, Hit the mole if you need the flag
)                                        = 47
puts(">">
)                                                                          = 2
__isoc99_scanf(0x56559039, 0xff87fbad, 0xff881fd7, 0x565581e3aaaaaa
)                     = 1
strcmp("Hi7_th3_m0l3", "aaaaaa")                                                   = -1
puts("You Failed"You Failed
)                                                                 = 11
+++ exited (status 0) +++
```

#### Flag : Mystiko{Hi7_th3_m0l3}