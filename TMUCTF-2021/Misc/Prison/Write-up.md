# Prison
### Challange
file `challange.txt` contained:
```
.... .... .. ... . ..... ... ..... .... .. .. .... .... ... ... .... ... ... . ..... .... .. .. .... .... ... .... .... .... .. ..... .... .. .... ... ... .. .. .... .... ... .... . ..... .... ... . ... . . ... ..... . ..... .. . .... .. ... .... ... .. .. ... .. .... .... ... . ... . ..... ... . ... .
```

### What is TapCode? [SRC](https://en.wikipedia.org/wiki/Tap_code)
The tap code is based on a [Polybius square](https://en.wikipedia.org/wiki/Polybius_square "Polybius square") using a 5×5 grid of letters representing all the letters of the [Latin alphabet](https://en.wikipedia.org/wiki/Latin_alphabet "Latin alphabet"), except for K, which is represented by C.

Each letter is communicated by tapping two numbers
-   the first designating the row (Vertical down) ↓
-   the second designating the column (Horizontal right) →

### How i solve this challange?
challange was already solved so I tought why not create python script to get flag automaticly!

```python
#!/usr/bin/env python3

# pip3 install tapcode==1.0.0
from tapcode import tapcode

# Import argv from sys to get file as argument
from sys import argv

usage = """
Usage:

solve.py {challange file}
"""

# This library does not support "." and " " so we have to
#   convert our "." to numbers
def tapCode2Decimal(cipher: str, code: str, sep: str):
 tmp = []
 tapcode = []
 for dot in cipher:
	 if dot == code: # If letter was dot add it to tmp list
	 tmp.append(dot)
 elif dot == sep:
	 tapcode.append(str(len(tmp))) # Get length of the list wich is our number
	 tmp = [] # set list to empty list
 return "".join(tapcode)

try:
	 with open(argv[1], "r") as file:
		 challange = file.read() # Read Challange file
		 cipher = tapCode2Decimal(challange, ".", " ") # Use our function to get numbers
		 flagContent = tapcode.decipher(cipher, " ", " ").replace(" ", "") # use tapcode liberary to decode tap code 
		 print("TMUCTF{" + flagContent + "}") 

except Exception as e: # return usage if there was an error
  print(usage)
```

**[TapCode](https://pypi.org/project/tapcode/)**

Read docs for tapcode liberary [here](https://tapcode.readthedocs.io/en/latest/)

**NOTE:**this is tapcode 1.0.0 im working on the new version for these kind of CTF's :)

```shell
$ py3 solve.py challange.txt

TMUCTF{THEPRISONERISTRYINGTOESCAPEFROMHISCELL}
```

> itsnexn for **AbyssalCruelty**
