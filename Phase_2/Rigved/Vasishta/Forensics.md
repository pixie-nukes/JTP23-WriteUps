# tunn3l v1s10n 
## Description
We found this file. Recover the flag.

## Approach
I opened the file in [hexed](hexed.it) and understoof that it was a **bmp** file.
Since I was using the debian distro, I can easily findout using my normal image viewer as a bmp file. 
![282280389-60bc3887-3e69-4d55-a567-298682b56699](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/a599c29d-4aec-427a-a755-dc998c6f0f4d)

I downloaded a sample bmp image from the web and compared it with the file given in [hexed](hexed.it) as shown below.
![282280429-1971b2ba-ebca-4054-878b-eb003dc62e31](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/d6a3e942-3a30-4363-a777-66ff401d923f)
![282280434-54ab5f64-c528-4726-94ec-8109b30c31ad](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/f270c6f3-8a74-4c05-8a6e-826392141a77)
I found some discrepencies and corrected the size in the first row. and i downloaded the image.
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/5796bb7b-f930-430c-9241-3df49c5e6e80)
But the problem was that the image was only half and the height was not upto its fullest length. 

So I used the **exiftool** to get the image properties
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/95b040b7-b151-443f-93e1-094979524619)
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/b3f727dc-7419-4c19-bd2b-833cf9264da6)
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/c3123b4b-bf56-4eab-a643-16a626f9206a)
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/85ded98e-ce2a-4cf7-9c11-44e39d3146c4)
The image height is different but the image width is same. so i need to change the image height.
I searched on google the maximum permitted height for a bmp file.
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/50699a4e-5de1-4ba2-9682-48f30cd5a3b1)
And i converted the same in [hexed](hexed.it)
I downloaded the new image, in which i recovered the flag. 
![image](https://github.com/aghogwarts/JTP23-WriteUps/assets/94845416/10c22196-4e94-4aa7-8cac-ec63ca64cc4e)

## Output
picoCTF{qu1t3_a_v13w_2020}

# Trivial FTP
## Problem
Figure out how they moved the [flag].

## Approach
- I opened the packet using wireshark. `file > export objects > tftp` and i downloaded all the files.
- I opened the `instructions` document to find `GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA`
I copied this tect and put it into [Rot13](rot13.com) and got the output as `TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN`.
It didnt make any sense so i tried to read it with spaces and i found this `t ftp doesnt encrypt our traffic so we must disguise our flag transfer figure out away to hide the flag and i will check back for the plan`.
- I opened the `plan` document to find `VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF` and again i used ROT13 decoder to decode and i found out with spaces as `i used the program and hid it with due diligence check out the photos`.
- I extracted the `program.deb` file and found that it was a `steghide` using the command `sudo dpkg -i program.deb`.
- The hint from the plan document suggests that `DUEDILIGENCE` (uppercase because the encoded text is uppercase) is the password.
- I used `steghide` on every image included in the packet capture file.
  The flag is hidden in the last image `picture3.bmp`. So I ran `steghide extract -sf picture3.bmp -p DUEDILIGENCE` and `cat flag.txt` to get the flag.

  ## Output
  picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

# MacroHard WeakEdge
## Problem
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm]

## Approach
I extracted the power point presentation file to a zip file using [7zip](https://www.7-zip.org/). I was looking through the extracted files, ppt/slideMasters/hidden looks suspicious.
Reading that file `cat ppt/slideMasters/hidden`.
Shows `Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q` .
I then used [Base64](https://www.base64decode.org/) to decode the file. 

## Output
The output after decoding using base 64 is flag: `picoCTF{D1d_u_kn0w_ppts_r_z1p5}`
