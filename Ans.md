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
`~predict_the_future~ astrotalk`
We initially tried all standard TOTP approaches—various key encodings, SHA algorithms, timestep intervals (15s to 10h), and full year brute-force—without success. Ultimately, the correct sequence was found by reverse-engineering the given OTPs to derive the exact parameters: SHA512, 45 time interval 

`Strategies that date back more than a millenium`
After going from the Anonymus COmplait Form at Election Commission Website- we get two links which are base64 encoded `aHR0cHM6Ly9saWNoZXNzLm9yZy9sY3M4QkVQYg==` which is: `https://lichess.org/lcs8BEPb` and `aHR0cHM6Ly9saWNoZXNzLm9yZy9tMzJQUmlScA==` which is `https://lichess.org/m32PRiRp` There was a chess game there, wherein we had to analyse the moves. After going through countless combinaions, looking at the mistakes/blunders/etc. - IChess PGN moves → Index of legal moves → Binary → ASCII bytes → Flag text
`HRCTF{7h15_15_345y_1f_y0u_kn0w_wh3r3_70_f1nd_17}`
