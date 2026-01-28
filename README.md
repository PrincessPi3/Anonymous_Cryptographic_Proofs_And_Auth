# Anonymous Cryptographic Proofs and Auth
For when you need to share a file/authenticate anonymously, but want choices to prove anything anonymously/pseudoanonymously/full name/new name/etc  
  
Also for when you may want to burn those keys to destroy any evidence you were involved  
  
## Method
Step 1: Collecting Information  
Including
- an input file to sign
- a secure passphrase for use on an ssh key
- a secure passphrase for use as an sha256/sha512 salt
Step 2: Generating New Single-Use SSH Key Pair
- ed25519 by default
- secured with provided passphrase
Step 3: Generating Checksums
- Normal sha256 and sha512 checksums are generated of the input file and logged
- sha256(passphrase+file contents) and sha512(passphrase+file contents) disgests are calculated and logged
Step 4: Signing Files
- Original file is signed by the ssh key with a detached signature file
- checksums file is signed by the ssh key with a detached signature file
Step 5: Verification
- Both file and checksums files signates are checkeed against the ssh public key
- The original file is tested with normal sha256, normal sha512, salted sha256, and salted sha512
Step 6: Output Public Files
- Public files are added to a new directory and compressed with 7zip