# DISKO 1 (PicoCTF) -Easy-
## Description
"Can you find the flag in this disk image?Download the disk image here:
https://artifacts.picoctf.net/c/538/disko-1.dd.gz"

---

## Tools used:
1- 'curl' or 'wget' - to download the file on your linux machine
2- 'file' - to check file type
3- 'gzip' - to decompress
4- 'grep' - to search inside the output
5- 'strings' - to extracr printable characters

## Solution steps:

### 1. Download the file

First of all download the file using curl or wget:
wget https://artifacts.picoctf.net/c/538/disko-1.dd.gz

OR

curl https://artifacts.picoctf.net/c/538/disko-1.dd.gz > disko-1.dd.gz

after downloading the file you can see it using "ls" command
you should now see the file "disko-1.dd.gz" in the home/"your user name"/ directory

### 2. Check file type

you can use 'file' command to determine the file type:

file disko-1.dd.gz

you will see:

disko-1.dd.gz: gzip compressed data, was "disko-1.dd"…….(other long text)

### 3. Decompress the file

now we know this is a gzip file and we can unzip it using this command:

gzip -d disko-1.dd.gz

now if you use "ls" command you'll see the file unziped:

disko-1.dd

you can use the "file" command again to determine the file type:

file disko-1.dd

the output:
disko-1.dd: DOS/MBR boot sector, code offset 0x58+2, OEM-ID "mkfs.fat", Media descriptor 0xf8, sectors/track 32, heads 8, sectors 102400 (volumes > 32 MB), FAT (32 bit), sectors/FAT 788, serial number 0x241a4420, unlabeled

which means briefly:
The file disko-1.dd is a raw disk image containing a DOS/MBR boot sector, which indicates that it uses the master boot record (MBR) partitioning scheme.

### 4. Finding the flag

What's important now is that we can extract the text in the file using the "strings" tool.
But be careful, we don't want to extract the entire text of the file! We only need the flag, and the flag starts with pico, so we'll extract the strings using strings, then use grep with pip to print the strings containing pico to the terminal.

strings disko-1.dd | grep pico
The output:

As you can see in the screenshot the flag is picoCTF{1t5_ju5t_4_5tr1n9_e3408eef}