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



