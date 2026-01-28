# TODO NEXT (urgent)
- ditch sha256/512 for argon2id with some sensible settings
  - sha256/512 is too fast to be robustly secure

# TODO
- 7zip compression encrypted/non-encrypted
  - `.$random_hidden_filename` file in public output pre encrypted compress, filled with secure random binary, to break sig checks if they are in play
- helper txt
  - cmds to all-in-one hash checks?
  - script?
- keyfile name/output dir/7zip archive with same name
- handle special chars in passphrases and shit
- usage
- cli options

## Writeup
- usage scenarios
- threat modeling
  - side channel attacks
  - info leaks
    - ip leaks
    - device fingerprinting
    - osint fails
- key/passphrase/salt storage
- key/passphrase/salt destruction

## Write Standard to Share
- ohfuck