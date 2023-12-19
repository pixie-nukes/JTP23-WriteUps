# Hydra is coming to town
## Scenario

The server room is locked down. The team needs to regain access to recover backup tapes. Brute-forcing the PIN panel might be the only option!
Learning Objectives

## After completing this task, you will understand:

    Password complexity and the number of possible combinations
    How the number of possible combinations affects the feasibility of brute force attacks
    Generating password combinations using crunch
    Trying out passwords automatically using hydra
## Requirements

    Start the Machine
    Connect with TryHackMe’s VPN or Start the Attackbox
    After the Machine starts, Open the IP in a new tab

## TASKS:
### Using crunch and hydra, find the PIN code to access the control system and unlock the door. What is the flag?
the main login page http://10.10.170.213:8000/pin.php receives the input from the user and sends it to /login.php using the name pin.

These three pieces of information, post, /login.php, and pin, are necessary to set the arguments for Hydra.

We will use `hydra` to test every possible password that can be put into the system. The command to brute force the above form is:
`hydra -l '' -P 3digits.txt -f -v 10.10.170.213 http-post-form "/login.php:pin=^PASS^:Access denied" -s 8000`

The Above command will use http-post-form method to brute force the Login Form and will filter it out by the word Access Denied

![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/adf75bf1-5e66-4fe6-9d17-b808d625008e)

Log in using the Password and unlock the Device to get the flag

ANS: `THM{pin-code-brute-force}`
