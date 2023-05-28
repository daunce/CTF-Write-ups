forensics/nothing-to-see

460 solves / 7 points

nothing to see here, just move along

Downloads:nothing.png

![Alt text](nothing.png)

Looks like a normal image
```bash
└─$ file nothing.png 
nothing.png: PNG image data, 560 x 450, 8-bit/color RGBA, non-interlaced
```

Extract hidden files:
```bash
└─$ binwalk -e nothing.png

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 560 x 450, 8-bit/color RGBA, non-interlaced
14751         0x399F          Zip archive data, encrypted at least v2.0 to extract, compressed size: 46, uncompressed size: 39, name: flag.txt
14957         0x3A6D          End of Zip archive, footer length: 22
```

It contains 2 files:
```bash
└─$ ll
total 4
-rw-r--r-- 1 daunce daunce 228 May 27 11:25 399F.zip
-rw-r--r-- 1 daunce daunce   0 May 26 10:34 flag.txt
```
flag.txt is 0 bytes, empty.

The 399F.zip file is password protected:
```bash
└─$ unzip 399F.zip            
Archive:  399F.zip
[399F.zip] flag.txt password: 
   skipping: flag.txt                incorrect password
```

Where is the password?

```bash
└─$ exiftool nothing.png 
ExifTool Version Number         : 12.49
File Name                       : nothing.png
Directory                       : .
File Size                       : 15 kB
File Modification Date/Time     : 2023:05:26 10:45:20+10:00
File Access Date/Time           : 2023:05:27 11:24:21+10:00
File Inode Change Date/Time     : 2023:05:27 11:18:55+10:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 560
Image Height                    : 450
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Title                           : panda_d02b3ab3
Warning                         : [minor] Trailer data after PNG IEND chunk
Image Size                      : 560x450
Megapixels                      : 0.252
```

Looks normal. What about **Title                           : panda_d02b3ab3**.

Try password panda_d02b3ab3.

```bash
└─$ unzip 399F.zip 
Archive:  399F.zip
[399F.zip] flag.txt password: 
replace flag.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: flag.txt                
```

```bash
└─$ cat flag.txt             
tjctf{the_end_is_not_the_end_4c261b91}
```

Flag: tjctf{the_end_is_not_the_end_4c261b91}