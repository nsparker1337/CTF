#### Category : Forensics
#### Challenge : Mad PDF
#### Difficulty : Easy
#### Description : 
Are you carzy enough to solve this forensic challenge

#### Solution :
1. First we need to Analyse the PDF. To analyse use pdf parser but nothing showed up.
2. Then use Binwalk to find is there any hidden data inside the pdf.
3. Use binwalk -e Mad_pdf.pdf to Extract the data.
4. As you can see the extracted folder and you find the filename called **218**
5. view the file and you could see the follows

```bash
~/Desktop/HTB/others/_Mad_pdf.pdf.extracted                                                                                           
❯ cat 218
 /Span <</MCID 0/Lang (en-IN)>> BDC q
0.000008871 0 595.32 841.92 re
W* n
BT
/F1 11.04 Tf
1 0 0 1 72.024 759.48 Tm
/GS7 gs
0 g
/GS8 gs
0 G
[(M)-3(y)-3(s)11(tik)9(o)-5({craz)3(y)7(_pd)5(f})] TJ
ET
Q
q
0.000008871 0 595.32 841.92 re
W* n
BT
/F1 11.04 Tf
1 0 0 1 158.06 759.48 Tm
0 g
0 G
[( )] TJ
ET
Q
 EMC %    
```

6. You can see the flag inside the square bracket.

#### Flag : Mystiko{crazy_pdf}