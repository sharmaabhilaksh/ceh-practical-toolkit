## Cryptography

### Hashing

Hashing is used to check integrity of information.
1. HashCalc
   - Calculate various hashes for strings/files (MD4, MD5, SHA1, SHA256, SHA384, SHA512, CRC32, RIPEMD160)
2. MD5 Calculator
   - Calculate MD5 hashes for files
3. HashMyFiles
   - Calculate MD5 and SHA1 hashes for file(s)
4. Crack hashes
   - www.hashes.com
     - Decrypt MD5, SHA1, MySQL, NTLM, SHA256, MD5 Email, SHA256 Email, SHA512 hashes


### Encrypt / Decrypt strings / files
1. CryptoForge Files
   - Encrypt/Decrypt files with a password
   - Available in context menu
2. CryptoForge Text
    - Encrypt/Decrypt text with a password
    - saves a .cfd file
3. BcTextEncoder
    - Encrypt/Decrypt text with a password or X.509 public key


### Disk encryption
1. VeraCrypt
   - Encrypt/Decrypt disks volumes
     - File container
       - A file that is password protected and mounted as a disk
     - Non system partition or external drive
       - Protects data on external drives
     - System partition
       - need to enter password at boot
   - Hidden volume
     - A hidden volume is a second volume (within the first) that is only accessible by entering a different password
2. BitLocker Drive Encryption (windows inbuilt utility)
   - Uses TPM (Trusted Platform Module) to store encryption keys
   - Encrypt/Decrypt disks volumes
     - System partition
       - need to enter password at boot
     - Non system partition or external drive
       - Protects data on external drives
3. Rohos Disk Encryption
   - same as VeraCrypt
   - creates a .rdi file


### Cryptanalysis
1. Cryptool
   - Can be used to encrypt/decrypt text by selecting an algorithm and required key 
   - .hex files
2. AlphaPeeler
   - Encrypts a file selecting the algorithm and required key: saves in another confidential file
   - Decrypts a file selecting the algorithm and required key: saves in another output file