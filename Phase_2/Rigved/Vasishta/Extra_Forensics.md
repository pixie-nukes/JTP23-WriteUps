# Wireshark doo dooo do doo
## Description
Can you find the flag? shark1.pcapng.

## Approach
I opened the file in wireskark. And typed in `tcp.stream eq 5` to get the 5th tcp stream.
Right click any entry, click `follow`, and then click `TCP Stream`.

The flag will now be shown, but it is encoded:
> Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}

So I used [ROT13](https://rot13.com/) to decode the flag and I found this 
> The flag is picoCTF{p33kab00_1_s33_u_deadbeef}

## Output
picoCTF{p33kab00_1_s33_u_deadbeef}

# Information
## Description
Files can always be changed in a secret way. Can you find the flag? **cat.jpg**

## Approach
I used **exiftool** to know the properties(details) of the image.
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/50d1404d-ddad-4ced-b54e-afbabb822cc2)
Then I converted the base64 text to ASCII text like this:
![image](https://github.com/pixie-nukes/picoCTF/assets/94845416/8da68e12-65bc-405d-bd87-170c9d6b4aca)

## Output
*picoCTF{the_m3tadata_1s_modified}*

# Lookey Here
## Description
Attackers have hidden information in a very large mass of data in the past, maybe they are still doing it. Download the data **here**.

## Approach
I opened the file in a text editor and simply searched for **picoCTF** and recovered the flag.

## Output
picoCTF{gr3p_15_@w3s0m3_4c479940}

# Sleuthkit Intro
## Description
Download the disk image and use **mmls** on it to find the size of the Linux partition.
Connect to the remote checker service to check your answer and get the flag. Note: if you are using the webshell, download and extract the disk image into **/tmp** not your home directory.

    Download disk image
    Access checker program: nc saturn.picoctf.net 64605

## Approach
I decompressed the file using the `gzip` command like this:
> `gzip -d disk.img.gz`

In this question we need to find the size of the disk. As hinted in the question let’s mmls

mmls - displays the contents of a volume system
> `mmls disk.img`

I connected to the server through netcat : `nc saturn.picoctf.net 64605`
And entered the size I got through mmls before. 

I got the flag!

## Output
picoCTF{mm15_f7w!}
