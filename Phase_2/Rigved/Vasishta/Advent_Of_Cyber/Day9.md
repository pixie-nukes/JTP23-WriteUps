# She sells C# shells by the C2shore
## Scenario
Having retrieved the deleted version of the malware that allows Tracy McGreedy to control elves remotely, Forensic McBlue and his team have started investigating to stop the mind control incident. They are now planning to take revenge by analyzing the C2’s back-end infrastructure based on the malware’s source code.
## C2 Primer
1. According to Forensic McBlue, the retrieved malware sample is presumed to be related to the organisation’s remote mind control (over C2) incident. So, to build the right mindset in solving this case, let’s look at the run-through below about malware with C2 capabilities.
2. C2, or command and control, refers to a centralised system or infrastructure that malicious actors use to remotely manage and control compromised devices or systems. It serves as a channel through which attackers issue commands to compromised entities, enabling them to carry out various activities, such as data theft, surveillance, or further malware propagation.
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/29591edf-27cd-4e43-ad85-7df3a40b127e)
dnSpy is an open-source .NET assembly (C#) debugger and editor. It is typically used for reverse engineering .NET applications and analysing their code and is primarily designed for examining and modifying .NET assemblies in a user-friendly, interactive way. It’s also capable of modifying the retrieved source code (editing), setting breakpoints, or running through the code one step at a time (debugging).
## Tasks:
### 1. What HTTP User-Agent was used by the malware for its connection requests to the C2 server?
 Open dnSpy
   1. File
   2. Open
   3. Navigate to the desktop
   4. Click all files at the bottom
   5. juicyTomatoydefang
   6. Now click and expand the `.exe` file.
   7. Inspect the program
>  Mozilla/5.0 (Macintosh; Intel Mac OS X 14_0) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.0 Safari/605.1.15
### 2. What is the HTTP method used to submit the command execution output?
By inspecting the code I can find the HTTP method
> POST
### 3. What key is used by the malware to encrypt or decrypt the C2 data?
The below key is used by the malware to encrypt/decrpt the C2 data. I found the key by inspecting the code.
> youcanthackthissupersecurec2keys
### 4. What is the first HTTP URL used by the malware?
This is the first HTTP url used by the malware.
> http://mcgreedysecretc2.thm/reg
### 5. How many seconds is the hardcoded value used by the sleep function?
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/10e11e48-29e4-4f5b-8d35-bc6a1cafe134)
After inspecting the code, I found that
> 15
### 6. What is the C2 command the attacker uses to execute commands via cmd.exe?
the C2 command the attacker uses to execute commands via cmd.exe is 
> shell
### 7. What is the domain used by the malware to download another binary?
the domain used by the malware to download another binary is
> stash.mcgreedy.thm
