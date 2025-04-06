# HackRush 2025 (Writeups)

 
## Miscellaneous
### *Find Me 75*
Went to the EII website. Since the hint said to use 'Sliders', I directly inspected them. Wherein, upon searching, got this: `<!-- flag? SFJDVEZ7IV9MMFYzX0hAQ0tSVSRIfQ== -->`
That's base64 encoded. On decoding it:  


`HRCTF{!_L0V3_H@CKR$H}`

### *Crack and hack*
One has to first find out the credentials to the mess portal.  
The login: hacker@iitgn.ac.in   
Password: (We are given an MD5 Hash- Decrypting it gave) 12345678  
On logging into the portal: we get his roll number- 24116969  

After that, we are led to the IR&P COuncil Server, where I first ran through the whole website, trying to inspect everypage and all.
Finally, I accessed the secret files by guessing the URL- `https://students.iitgn.ac.in/irp-council/24116969`

So, the code there was: `HRCTF{@LW@Y$_U$3_$TR0N6_P@$$W0RD}`

## Crypto
### predict_the_future astrotalk
We initially tried all standard TOTP approaches—various key encodings, SHA algorithms, timestep intervals (15s to 10h), and full year brute-force—without success. Ultimately, the correct sequence was found by reverse-engineering the given OTPs to derive the exact parameters: SHA512, 45 time interval 

### Strategies that date back more than a millenium
After going from the Anonymus COmplait Form at Election Commission Website- we get two links which are base64 encoded `aHR0cHM6Ly9saWNoZXNzLm9yZy9sY3M4QkVQYg==` which is: `https://lichess.org/lcs8BEPb` and `aHR0cHM6Ly9saWNoZXNzLm9yZy9tMzJQUmlScA==` which is `https://lichess.org/m32PRiRp` There was a chess game there, wherein we had to analyse the moves. After going through countless combinaions, looking at the mistakes/blunders/etc. - IChess PGN moves → Index of legal moves → Binary → ASCII bytes → Flag text
`HRCTF{7h15_15_345y_1f_y0u_kn0w_wh3r3_70_f1nd_17}`


## Forensics:
### Can't fast forward security- 
After extracting and inspecting the file >libsignal > rust > crypto/keytrans...... , I search for anything added/modified in 2025(March) `git log --since="2025-03-01" --until="2025-03-31" --oneline` 
```
commit a64c7cde789fb5e47f67081afb400cc23da2a8e4
Author: Alex Bakon <akonradi@signal.org>
Date:   Wed Mar 19 15:50:15 2025 -0400

Exclude root key from WebSocketRequestMessage
```

And then-> `git show a64c7cde789fb5e47f67081afb400cc23da2a8e4` After recovering the previous versions of the file
And got the deleted root from there.
`HRCTF{0adf1c39f4035d3acd7496f9ed9023e56573b239ce4631d4553f90428bbe1641}`

### Continued (prob 2) 
File containing the root key, and then quickly deleted in the same commit. `git fsck --lost-found`  (unereachable blobs, deleted ones)     
```
Checking objects: 100% (45738/45738), done.
dangling blob c955e3c41ee6d8874034a60876f3de4254638b8f
dangling commit 09b4d91b2d75c23761d523fc1904809d675deda3
Verifying commits in commit graph: 100% (3050/3050), done.
```
and use git show

