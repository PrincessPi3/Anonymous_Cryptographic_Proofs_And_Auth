# Anonymous Cryptographic Proofs and Auth
For when you need to share a file/authenticate anonymously, but want choices to prove anything anonymously/pseudoanonymously/full name/new name/etc  
  
Also for when you may want to burn those keys to destroy any evidence you were involved  
  
## Method
**Step 1: Collecting Information**
1. an input file to sign
2. a secure passphrase for use on an ssh key
3. a secure passphrase for use as an ARGON2ID salt
  
**Step 2: Generating New Single-Use SSH Key Pair**
1. ed25519 by default
2. secured with provided passphrase
  
**Step 3: Generating Checksums**
1. Normal sha512 and sha256 checksums are generated of the input file and logged
2. secure argon2id(passphrase+file contents) digest is made and logged
  
**Step 4: Signing Files**
1. Original file is signed by the ssh key with a detached signature file
2. checksums file is signed by the ssh key with a detached signature file
  
**Step 5: Verification**
1. Both file and checksums files signates are checkeed against the ssh public key
2. The original file is tested with normal sha256, normal sha512, salted argon2id
  
**Step 6: Output Public Files**
1. Public files are added to a new directory
2. secure random dotfile name is generated and placed in the public output directory
3. dotfile is filled with secure binary data to break any signature matches
4. public output directory is compressed and optionally encrypted with 7zip