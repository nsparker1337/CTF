#### Category : Reverse Engineering
#### Challenge : Flock
#### Difficulty : Easy
#### Description : 
Counting sheeps can help you to get the flag

#### Solution : 
1. Check the strings if there is any interesting to look for but didn't find anything intresting.
2. use ltrace to find any interesting function like strcpy() or strcmp(). Luckily we find strcmp() and strcat() used in it.
3. ltrace ./flock.out --> Enter random string, Then you can see our random string compared with some concatinated string **fifty_five**
4. Repeat the same step but this time enter fifty_five. It also compared with the string **_sh3ep_** and concat it.
5. Thats it.. grab the flag.

```sql
~/Desktop/HTB/others                                                                                                                  
❯ ltrace ./flock.out 
__libc_start_main(0x5656e209, 1, 0xffc21074, 0x5656e550 <unfinished ...>
_ZNSt8ios_base4InitC1Ev(0x56571039, 0, 0xf7ff2000, 0x5656e4d5)                     = 0xf7f99eec
__cxa_atexit(0xf7e67ae0, 0x56571039, 0x56571034, 0x5656e4d5)                       = 0
strcpy(0xffc20e86, "fi")                                                           = 0xffc20e86
strcat("fi", "fty")                                                                = "fifty"
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7f98c00, 0x5656f00c, 0xf7fc6d10, 0x5656e223) = 0xf7f98c00
_ZNSolsEPFRSoS_E(0xf7f98c00, 0xf7ede200, 0xf7fc6d10, 0x5656e223 Counting Sheep To Go To Sleep
)                   = 0xf7f98c00
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7f98c00, 0x5656f02b, 0xf7fc6d10, 0x5656e223) = 0xf7f98c00
_ZStrsIcSt11char_traitsIcEERSt13basic_istreamIT_T0_ES6_PS3_(0xf7f98ca0, 0xffc20eac, 0xf7fc6d10, 0x5656e223 > sss
) = 0xf7f98ca0
strcat("fifty", "_fi")                                                             = "fifty_fi"
strcat("fifty_fi", "ve")                                                           = "fifty_five"
strcmp("sss", "fifty_five")                                                        = 1
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7f98c00, 0x5656f034, 0xf7fc6d10, 0x5656e223) = 0xf7f98c00
_ZNSolsEPFRSoS_E(0xf7f98c00, 0xf7ede200, 0xf7fc6d10, 0x5656e223 Not enough sheep :( 
)                   = 0xf7f98c00
+++ exited (status 0) +++

~/Desktop/HTB/others                                                                                                                4s
❯ ltrace ./flock.out
__libc_start_main(0x56601209, 1, 0xffe10aa4, 0x56601550 <unfinished ...>
_ZNSt8ios_base4InitC1Ev(0x56604039, 0, 0xf7f0a000, 0x566014d5)                     = 0xf7eb1eec
__cxa_atexit(0xf7d7fae0, 0x56604039, 0x56604034, 0x566014d5)                       = 0
strcpy(0xffe108b6, "fi")                                                           = 0xffe108b6
strcat("fi", "fty")                                                                = "fifty"
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7eb0c00, 0x5660200c, 0xf7ed8d10, 0x56601223) = 0xf7eb0c00
_ZNSolsEPFRSoS_E(0xf7eb0c00, 0xf7df6200, 0xf7ed8d10, 0x56601223 Counting Sheep To Go To Sleep
)                   = 0xf7eb0c00
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7eb0c00, 0x5660202b, 0xf7ed8d10, 0x56601223) = 0xf7eb0c00
_ZStrsIcSt11char_traitsIcEERSt13basic_istreamIT_T0_ES6_PS3_(0xf7eb0ca0, 0xffe108dc, 0xf7ed8d10, 0x56601223 > fifty_five
) = 0xf7eb0ca0
strcat("fifty", "_fi")                                                             = "fifty_fi"
strcat("fifty_fi", "ve")                                                           = "fifty_five"
strcmp("fifty_five", "fifty_five")                                                 = 0
strcpy(0xffe1088c, "fif")                                                          = 0xffe1088c
strcat("fif", "ty")                                                                = "fifty"
strcat("fifty", "_fi")                                                             = "fifty_fi"
strcat("fifty_fi", "ve")                                                           = "fifty_five"
strcat("fifty_five", "_sh3ep")                                                     = "fifty_five_sh3ep"
_ZNSolsEPFRSoS_E(0xf7eb0c00, 0xf7df6200, 0xf7ed8d10, 0x56601223
)                   = 0xf7eb0c00
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7eb0c00, 0x5660202f, 0xf7ed8d10, 0x56601223) = 0xf7eb0c00
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7eb0c00, 0xffe1088c, 0xf7ed8d10, 0x56601223) = 0xf7eb0c00
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc(0xf7eb0c00, 0x56602031, 0xf7ed8d10, 0x56601223) = 0xf7eb0c00
_ZNSolsEPFRSoS_E(0xf7eb0c00, 0xf7df6200, 0xf7ed8d10, 0x56601223{fifty_five_sh3ep} 
)                   = 0xf7eb0c00
_ZNSolsEPFRSoS_E(0xf7eb0c00, 0xf7df6200, 0xf7ed8d10, 0x56601223
)                   = 0xf7eb0c00
+++ exited (status 0) +++

```

#### Flag : Mystiko{fifty_five_sh3ep}