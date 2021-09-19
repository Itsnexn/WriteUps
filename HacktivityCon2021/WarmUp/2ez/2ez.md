# 2ez
### Challenge
**Tag:** _Easy_

**Description:**
These warmups are just too easy! This one definitely starts that way, at least!  
  
**Attachments:**  [2ez](#)

### Solve
first thing that I did was:
```shell
$ file 2ez

2ez: data
```

so I did the second thing that I do in these challenge's 

```shell
# i dont usualy do the sed command 
# 	but because out put is big i did it!
$ strings 2ez | sed 11q

.2EZ
JFIF
Baqv
$3689Ru
%4Xbw
)CDct
*hlS
K7KG
>F4q
hcG-`q
o;yy.

```

so I thought the challenge name is **2ez** there and theres `.2EZ` and also a `JFIF` in the head of the file!

usualy the head strings of a jpg file is just `JFIF` so I was sure that we have some problem in our header...
so I googled `Jpg file header` and on the first link I found the hex value of the bytes:
```
ffd8 ffe0 0010 4a46 4946
```
I knew that `4a46 4946` is JFIF so I ignore that and changed the bytes before JFIF string
after doing that I opened up the image and boom we got the flag!

![img](https://raw.githubusercontent.com/Itsnexn/WriteUps/main/HacktivityCon2021/WarmUp/2ez/2ez.jpg)

and ofc, I did copy paste the image on [HERE](https://brandfolder.com/workbench/extract-text-from-image) and convert it to the text!
what did you expect me to do? write it manually? no...

> Itsnexn for **Abyssal Cruelty**
