# Have a Holly, Jolly Byte
## Scenario

The drama unfolds as the Best Festival Company and AntarctiCrafts merger wraps up! Tracy McGreedy, now a grumpy regional manager, secretly plans sabotage. His sidekick, Van Sprinkles, hesitantly kicks off a cyber attack — but guess what? Van Sprinkles is having second thoughts and helps McSkidy’s team bust McGreedy’s evil scheme!
## Working With FTK Imager
![image](https://github.com/pixie-nukes/AdventOfCyber2023/assets/94845416/c21ff76b-6471-4506-8ec7-65b6266e928b)

Open FTK Imager and navigate to File > Add Evidence Item, select Physical Drive in the pop-up window, then choose our emulated USB drive "\\PHYSICALDRIVE2 - Microsoft Virtual Disk [1GB SCSI]" to proceed.
## FTK Imager: User Interface (UI)
![image](https://github.com/pixie-nukes/AdventOfCyber2023/assets/94845416/a019e2a8-1c19-4ccd-b998-8d1b6e1ecfae)

FTK Imager’s interface is intuitive and user-friendly. It displays an “x” icon next to deleted files and includes key UI components vital for its functionality. These components are:

  Evidence Tree pane: Displays a hierarchical view of the added evidence sources such as hard drives, flash drives, and forensic image files.
  File List pane: Displays a list of files and folders contained in the selected directory from the evidence tree pane.
  Viewer pane: Displays the content of selected files in either the evidence tree pane or the file list pane.

## FTK Imager: Previewing Modes

FTK Imager presents three distinct modes for displaying file content, arranged sequentially from left to right, each represented by icons enclosed in yellow:
![image](https://github.com/pixie-nukes/AdventOfCyber2023/assets/94845416/1443cb3c-79a1-449d-87ae-f88593a1d6d8)

  Automatic mode: Selects the optimal preview method based on the file type. It utilises Internet Explorer (IE) for web-related files, displays text files in ASCII/Unicode, and opens unrecognised file types in their native applications or as hexadecimal code.
  Text mode: Allows file contents to be previewed as ASCII or Unicode text. This mode is useful for revealing hidden text and binary data in non-text files.
  Hex mode: Displays files in hexadecimal format, providing a detailed view of file data at the binary (or byte) level.

## FTK Imager: Recovering Deleted Files and Folders
![image](https://github.com/pixie-nukes/AdventOfCyber2023/assets/94845416/885e91a3-be17-4e28-aa3f-b8fc766b8344)

To view and recover deleted files, expand directories in the File List pane and Evidence Tree pane. Right-click and select Export Files on individual files marked with an "x" icon or on entire directories/devices for bulk recovery of files (whether deleted or not).
## Tasks:

### 1. What is the malware C2 server?
I opened the deleted file and clicked on the text file. I found the C2 server!
> Ans: mcgreedysecretc2.thm
>
### 2. What is the file inside the deleted zip archive?
I opened the deletd *zip* file and can see a program inside the zip file.
> Ans: JuicyTomaToy.exe
>
### 3. What flag is hidden in one of the deleted PNG files?
1. Click the `portrait.png -->`
2. Click the Hex View 
3. Click Ctrl+F on the Hex pane
4. search `THM{`
   > Ans: THM{byt3-L3vel_@n4Lys15}
   >
### 4. What is the SHA1 hash of the physical drive and forensic image?
Click on 
1. Drive
2. File
3. Verify Drive
   > Ans: 39f2dea6ffb43bf80d80f19d122076b3682773c2
   >
