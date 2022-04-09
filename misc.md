# MISC

## this_is_flag

![The first exercise is supposed to be easy and the flag is just in the description lol. Copy & paste is all you needed to do.](MISC%20606c7/Untitled.png)

The first exercise is supposed to be easy and the flag is just in the description lol. Copy & paste is all you needed to do.

---

## pdf

So basically a pdf is given to me, whether I opened it with web browser or a pdf reader, nothing showed. But since all flag has the format ‘flag{...}’ so I used the search bar in pdf reader and typed in ‘flag’. This is what I found:

![“security through obscurity”, not obscured at all!](MISC%20606c7/Untitled%201.png)

“security through obscurity”, not obscured at all!

![Untitled](MISC%20606c7/Untitled%202.png)

---

## 如来十三掌 (I don’t know how to translate this)

I was given a `.docx` file, and it had the following content, it was like a buddha language in Chinese lol, didn’t know anything religious so I had to search online. It was actually an encrypted string.

The string being encrypted is `MzkuM3gvMUAwnzuvn3cgozMlMTuvqzAenJchMUAeqzWenzEmLJW9`, and this is a rot13 encrypted string, I figured it was rot13 as “十三” in the title means 13. I used ‘rot13.com’ to decrypt it. This is what I got: `ZmxhZ3tiZHNjamhia3ptbmZyZGhidmNraWpuZHNrdmJramRzYWJ9`.

![Untitled](MISC%20606c7/Untitled%203.png)

After trying bunch of encryption methods, base64 was the one and gave me the flag.

![Untitled](MISC%20606c7/Untitled%204.png)

![Untitled](MISC%20606c7/Untitled%205.png)

---

## give_you_flag

It gave me a gif image and watching it on a photo booth app, a QR appeared for a short moment. But my photo booth app could not pause as if the gif is a video, so I used a gif extractor website to split the gif into frames.

![Untitled](MISC%20606c7/Untitled%206.png)

![Get the frame with the QR code](MISC%20606c7/frame_49_delay-0.08s.gif)

Get the frame with the QR code

![and drew the missing corner squares myself, scanning it gave me the flag](MISC%20606c7/Untitled%207.png)

and drew the missing corner squares myself, scanning it gave me the flag

![Untitled](MISC%20606c7/Untitled%208.png)

---

### Stegano

![it says the flag should be in lower cases](MISC%20606c7/Untitled%209.png)

it says the flag should be in lower cases

I was given a pdf to download and we can see a big sentence saying ‘NoFlagHere!’ and ‘You flag is not here’

![Untitled](MISC%20606c7/Untitled%2010.png)

Inspecting the file with `xxd` and I found this close to the end of the file, but `xxd d802bcf9530b45e0b37170c67b8efcea.pdf | tail` did not work as the flag  was not in the last 10 lines.

![`Keywords(Could this be the flag? : Tm9wZSAsIG5vdCBoZXJlIDspCg==)`](MISC%20606c7/Untitled%2011.png)

`Keywords(Could this be the flag? : Tm9wZSAsIG5vdCBoZXJlIDspCg==)`

Okay, but this flag `flag{Tm9wZSAsIG5vdCBoZXJlIDspCg==}` did not work, then what if I cast it to lower case? Just ask Python to do it for me:

![Untitled](MISC%20606c7/Untitled%2012.png)

`flag{tm9wzsasig5vdcbozxjlidspcg==}` still didn’t work...

What about converting pdf to text? Use any pdf to text website can help us do this.

![But there was nothing useful.](MISC%20606c7/Untitled%2013.png)

But there was nothing useful.

Now try pdf to html lol.

![Untitled](MISC%20606c7/Untitled%2014.png)

Press F12 to inspect the html elements, within the `<head>` tags we can see several `<meta>` tags:

```html
<meta name="keywords" content="Could this be the flag? : Tm9wZSAsIG5vdCBoZXJlIDspCg==">
<meta name="description" content="<| tr AB .- |>">
```

I used 2 different pdf to html websites and the html files were quite different so I figured that it was the conversion method that resulted in some info not showing up. Then I tried `pdftohtml` command and open the resulted html file gave me this.

![Untitled](MISC%20606c7/Untitled%2015.png)

Now, let’s use the `tr` provided in the `<meta>` tag. I stored the string into a file named `ab.txt`. 

![Untitled](MISC%20606c7/Untitled%2016.png)

This looks like a Morse code, let’s translate it.

![read the output string in reverse order: cotegratulations, flag: ...](MISC%20606c7/Untitled%2017.png)

read the output string in reverse order: cotegratulations, flag: ...

We can reverse this string and convert it into lowercase

![so the flag is `flag{1nv151bl3m3is54g3}` `1nv151bl3m3554g3`](MISC%20606c7/Untitled%2018.png)

so the flag is `flag{1nv151bl3m3is54g3}` `1nv151bl3m3554g3`

![Untitled](MISC%20606c7/Untitled%2019.png)

---

## gif

After unzipping the file I got a folder which contains bunch of white and black image, did it mean a binary string?

![Untitled](MISC%20606c7/Untitled%2020.png)

So the pattern is either white → 0 & black → 1 or white → 1 & black → 0, trying both would not harm.

![flag{FuN_giF}](MISC%20606c7/Untitled%2021.png)

flag{FuN_giF}

Turned out that the first pattern worked.

![Untitled](MISC%20606c7/Untitled%2022.png)

---

## ext3

The provided file did not have file extension name, so I used `file` command to inspect the file type. It was an ext3 file.

![Untitled](MISC%20606c7/Untitled%2023.png)

But what is ext3? I googled it and wikipedia told me this

> ext3, or third extended filesystem, is a journaled file system that is commonly used by the Linux kernel. It used to be the default file system for many popular Linux distributions.
> 

So I knew that it probably contained a directory or folder? Let’s try to mount it using the `mount` Unix command:

```bash
mkdir temp_ext3
sudo mount f1fc23f5c743425d9e0073887c846d23 temp_ext3/
```

and  `ls` the directory gave me bunch of directories and files, which one should I even look at?!

```bash
$ ls
02CdWGSxGPX.bin  8A2MFawD4   ix1EMRHRpIc2    n              r
0GY1l            8DQFirm0D   j6uLMX          NgzQPW         Raf3SYj
0h3a5            8HhWfV9nK1  jE              Nv             rhZE1LZ6g
0l               8nwg        jj              o              Ruc9
0qsd             8RxQG4bvd   KxEQM           O7avZhikgKgbF  RZTOGd
0wDq5            FinD        LG6F            o8             scripts
0Xs              fm          Lh              OOoOs          sdb.cramfs
1                g           LlC6Z0zrgy.bin  orcA           sn
2X               gtj         LO0J8           oSx2p          SPaK8l2sYN
3                h           lost+found      OT             SrZznhSAj
3J               H           LvuGM           poiuy7Xdb      t
44aAm            H2Zj8FNbu   lWIRfzP         px6u           T
4A               hdi7        m               Q              TFGVOSwYd.txt
6JR3             hYuPvID     m9V0lIaElz      qkCN8
6wUaZE1vbsW      i           MiU             QmUY1d
7H7geLlS5        imgLDPt4BY  Mnuc            QQY3sF63w
```

But I still had the file system partition file in my Download directory lol so I could search for string ‘flag’ in the partition file:

```bash
$ strings f1fc23f5c743425d9e0073887c846d23 | grep flag
.flag.txt.swp
flag.txtt.swx
~root/Desktop/file/O7avZhikgKgbF/flag.txt
.flag.txt.swp
flag.txtt.swx
.flag.txt.swp
flag.txtt.swx
```

And there is a file named `file.txt` under the Desktop directory, I just `cat` the file and it gave me the flag:

```bash
$ cat O7avZhikgKgbF/flag.txt
ZmxhZ3tzYWpiY2lienNrampjbmJoc2J2Y2pianN6Y3N6Ymt6an0=
```

But the submitting the flag `flag{ZmxhZ3tzYWpiY2lienNrampjbmJoc2J2Y2pianN6Y3N6Ymt6an0=}` did not work, but there is a  ‘=’ character at the end! This indicate that this string may be base64 encoded, so I tried decrypting it with our favourite `base64` and this time it worked!

```bash
$ echo 'ZmxhZ3tzYWpiY2lienNrampjbmJoc2J2Y2pianN6Y3N6Ymt6an0=' | base64 -d 
flag{sajbcibzskjjcnbhsbvcjbjszcszbkzj}
```

---

## base64stego

The given file is a zip file, trying to unarchive it prompted me to enter a password

![Untitled](MISC%20606c7/Untitled%2024.png)

But there was no password given, I inspect the file with `xxd` and saw the `head` and `tail`.

![Untitled](MISC%20606c7/Untitled%2025.png)

![Untitled](MISC%20606c7/Untitled%2026.png)

And I searched on google about the file format of encrypted zip file and from the forensics wargame we know that zip file has the string ‘PK’ in its header and tail. And there are 2 important things:

1. the file header signature is ‘504B0304’
2. the central directory file header signature is ‘504B0102’

[The structure of a PKZip file](https://users.cs.jmu.edu/buchhofp/forensics/formats/pkzip.html#centraldirectory)

- When a file is not password protected, the 3rd and 4th byte after ‘504B0304’ should be ‘00 00’, the 5th and 6th byte after ‘504B0102’ should be ‘00 00’
- when a file is pseudo password protected (fake encryption), the 3rd and 4th byte after ‘504B0304’ should be ‘00 00’, the 5th and 6th byte after ‘504B0102’ should be ‘09 00’
- when a file is password protected, the 3rd and 4th byte after ‘504B0304’ should be ‘09 00’, the 5th and 6th byte after ‘504B0102’ should be ‘09 00’

And I observed that the 5th and 6th byte after ‘504B0102’ is ‘09 00’, I opened the zip file with a hex editor and changed them into ‘00 00’.

![Untitled](MISC%20606c7/Untitled%2027.png)

Then I could unzip the file without entering any password.

But the unzipped file is bunch of text that no one could ever understand

![Untitled](MISC%20606c7/Untitled%2028.png)

Throw the text into the following base64 decryption script I wrote gave me an explanation of base64 steganography, so I guessed it was base64 steganography? (implied by the challenge title)

```python
import base64

with open('stego.txt', 'r') as f:
    for line in f:
        line = line.strip()
        line = base64.b64decode(line)
        print(line)
```

![Untitled](MISC%20606c7/Untitled%2029.png)

This is the base64 summary I wrote:

- base64
    - base64 is reversible
    - base64-encrypted strings contain characters from A-Za-z0-9+/
    - when we encrypt, we split every 3 characters into a group and concatenate their ASCII binary strings
        - for example, in the word ‘eat’, ‘e’ has ASCII value 101 (01100101 in binary), ‘a’ has ASCII value 97 (01100001 in binary) and ‘t’ has ASCII value 116 (01110100 in binary). Concatenating them gives us a 24-bit binary string 01100101 01100001 01110100 and this is divided into 4 6-bit binary strings: 011001 010110 000101 110100. Each 6-bit binary string is converted into a number, which is then converted into the corresponding base64 character.
    - ‘=’ is the padding character
        - when we only have 2 characters ‘ea’, then the resulted concatenated 16-bit binary string 01100101 01100001 can only result into two 6-bit binary strings. And the remaining last 4 bits will be concatenated with 2 zeros to make up the last 6-bit string.  Every 2 zeros added will result in one ‘=’ character padded to the end of the encrypted string.
    - when decrypting, we need to remove any ‘=’ characters, split the binary string into 8-bit binary strings as group and then converted each group into ASCII codes
        - for example `V2luZ0NIRU5HCg==` is a base64 encoded string
        - when decoding it we removed any ‘=’ character, so `V2luZ0NIRU5HCg==` becomes `V2luZ0NIRU5HCg`
        - converting `V2luZ0NIRU5HCg` into binary gives `010101 110110 100101 101110 011001 110100 001101 001000 010001 010100 111001 000111 000010 100000`
            
            ![Untitled](MISC%20606c7/Untitled%2030.png)
            
        - and then we group them into 8-bit strings (align to the left): `01010111 01101001 01101110 01100111 01000011 01001000 01000101 01001110 01000111 00001010 0000`
        - there are 4 bits left over at the end (at the right), we discard it: `01010111 01101001 01101110 01100111 01000011 01001000 01000101 01001110 01000111 00001010`
        - and convert each 8-bit string into a character using ASCII table: WingCHENG
        - notice that the zeros we discarded, the value in this 4 bits would not have effect on the decoded string
        - for example, if I change the last 4 bits from `0000` to `0110` : `010101 110110 100101 101110 011001 110100 001101 001000 010001 010100 111001 000111 000010 100110` , the encoded string will be `V2luZ0NIRU5HCm==`
        - decoding `V2luZ0NIRU5HCm==` and `V2luZ0NIRU5HCg==` will give us the same result:
            
            ![Untitled](MISC%20606c7/Untitled%2031.png)
            
        - hence we can hide whatever info we want into these last bits but since each line can have maximum of only 2 ‘=’, we can only hide 4 bytes of info in each line, no wonder the text file has so many lines lol
        - so to find the flag we need to extract the bits to be discarded at each line and then decode the concatenation of them

And this is the ideas one should use to solve this kind of steganography problem:

- if a line does not contain ‘=’ at the end of line, then there will be no hidden info
- if a line contains ‘=’ at the end of the line, then convert the character prior to this ‘=’ into a binary number index
- if a line contains ‘==’ at the end of the line, then convert the character prior to ‘==’ into a binary number index

Following the dot points above, I wrote a Python program that decrypted the unzipped file text for me

```python
import base64

# this string allows us to translate base64 character to the index
# A has index 0 on base64 table
base64_dict = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/'
# this stores the overall stega message
stega_message = ''

# open the file in read file
with open('stego.txt','r') as f:
    # read each line
    for line in f:
        # count the number of '=' in line
        count = line.count('=')
        if count == 0:
            continue
            
        # remove the '=' and newline character
        line = line.replace('=', '')
        line = line.replace("\n", '')

        last_char = line[-1]
        # find the index of last_char in base64_dict
        idx = base64_dict.find(last_char)
        # if not found
        if idx == -1:
            continue
        # zfill adds 0 to the left of the string until the length is 6
        idx_bin = bin(idx)[2:].zfill(6)

        # if there were two '=' characters in 'line', then we need to add the last 4 bits of bin_str_line to stega_message
        # else if there was only one '=' character, then we need to add the last 2 bits of bin_str_line to stega_message
        if count == 2:
            stega_message += idx_bin[-4:]
        elif count == 1:
            stega_message += idx_bin[-2:]

# now we have all the stega message
# convert the stega message into string
to_print = ''.join([chr(int(stega_message[i:i+8],2)) for i in range(0, len(stega_message), 8)])
print(to_print)
```

![`flag{Base_sixty_four_point_five}`](MISC%20606c7/Untitled%2032.png)

`flag{Base_sixty_four_point_five}`

---

## Lift The Table

## Description

A person has got a telegram which says ‘c8e9aca0c6f2e5f3e8c4efe7a1a0d4e8e5a0e6ece1e7a0e9f3baa0e8eafae3f9e4eafae2eae4e3eaebfaebe3f5e7e9f3e4e3e8eaf9eaf3e2e4e6f2’, he has no idea what it means and he was angry.

### Solving the problem

The string contains only characters 0-9 and a-f, it might be hexadecimal string? We can convert every 2 contiguous characters into 1 hexadecimal character. So I wrote the following Python program and inspected each hex number

```python
s = 'c8e9aca0c6f2e5f3e8c4efe7a1a0d4e8e5a0e6ece1e7a0e9f3baa0e8eafae3f9e4eafae2eae4e3eaebfaebe3f5e7e9f3e4e3e8eaf9eaf3e2e4e6f2'
num_lst = []
for i in range(0, len(s), 2):
	hex_code = '0x' + s[i:i+2]
	hex_char = int(hex_code, 16)
	num_lst.append(hex_char)

print(num_lst)
print('min: ', min(num_lst))
print('max: ', max(num_lst))
```

![Untitled](MISC%20606c7/Untitled%2033.png)

we see that all numbers are within [160, 250], and we know that ASCII numbers range from 0 to 127. Let’s try subtracting 127 and 128 from every number and print out the character each of them represented.

```python
s = 'c8e9aca0c6f2e5f3e8c4efe7a1a0d4e8e5a0e6ece1e7a0e9f3baa0e8eafae3f9e4eafae2eae4e3eaebfaebe3f5e7e9f3e4e3e8eaf9eaf3e2e4e6f2'
num_lst2 = []
num_lst3 = []
for i in range(0, len(s), 2):
	hex_code = '0x' + s[i:i+2]
	hex_char = int(hex_code, 16)
	num_lst2.append(hex_char-127)
	num_lst3.append(hex_char-128)

print('subtracting 127:')
for n in num_lst2:
	print(chr(n), end='')
print('\nsubtracting 128:')
for n in num_lst3:
	print(chr(n), end='')
print('')
```

The output tells us that subtracting 128 was right

```bash
% python3 [table.py](http://table.py/)
subtracting 127:
Ij-!GsftiEph"!Uif!gmbh!jt;!ik{dzek{ckedkl{ldvhjtedikzktcegs
subtracting 128:
Hi, FreshDog! The flag is: hjzcydjzbjdcjkzkcugisdchjyjsbdfr
```

![Untitled](MISC%20606c7/Untitled%2034.png)

---

## Warmup

This challenge came from COMP6841 tutor’s CTFs, under the MISC category. Since I have been doing MISC CTF challenges for Something Awesome project, I decided to do one tutor’s MISC CTF.

![Untitled](MISC%20606c7/Untitled%2035.png)

A `.txt` file was given for this challenge, let’s see what was inside this file:

![Untitled](MISC%20606c7/Untitled%2036.png)

We can see that the message contains only characters in `A-Za-z0-9=` which tells us that this string is base64 decoded, let’s decode it and see it gives us the flag:

![`434f4d507b495f684f70455f7930755f4152335f7761726d65645f325f66696e645f6d3072455f4631616773217d`](MISC%20606c7/Untitled%2037.png)

`434f4d507b495f684f70455f7930755f4152335f7761726d65645f325f66696e645f6d3072455f4631616773217d`

The decoded string contains characters in `0-9a-f` , what does that remind you? Hexadecimal! Every 2 contiguous characters in the decoded string represent a number represented in hexadecimal and potentially the ASCII number of a character!

We can first convert each pair of characters into a number and then print out the corresponding ASCII character using Python:

```python
s = '434f4d507b495f684f70455f7930755f4152335f7761726d65645f325f66696e645f6d3072455f4631616773217d'
num_lst = []
for i in range(0, len(s), 2):
	hex_code = '0x' + s[i:i+2]
	hex_num = int(hex_code, 16)
	num_lst.append(hex_num)

# print out the flag
print('flag:')
for n in num_lst:
	print(chr(n), end='')
print('') # print a newline character
```

---

## Reflection

For me, MISC is like the brain teasers in CTF or cybersecurity, it examines all kinds of skills in cybersecurity. base64stego examines cryptography, ext3 and Stegano are like the forensics wargame we did in week 5.

Things I learned from these CTFs

- zip file format and password protection of zip files
- base64 decode algorithm
- digital forensics tools like
    - `pdftohtml`
    - `pdftotext`
    - `xxd`
    - `file`
    - `mount`
    - base64 steganography (people said it is outdated lol :(