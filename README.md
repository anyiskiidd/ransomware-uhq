# Ransomware

A malicious ransomware that encrypts all files in a target directory and demands a ransom to recover the files.

## How it works

The ransomware encrypts all files in a target directory using a custom encryption algorithm. It also creates a ransom note in the same directory to inform the victim that their files have been encrypted and that they must pay a ransom to recover the files.

The ransom note contains instructions on how to pay the ransom, as well as the encryption key to decrypt the files. The ransomware also adds a registry key to run at system startup and makes the encrypted files undeletable.

## How to install and run

1. Download the ransomware source code from GitHub.

2. Install the required dependencies by running the following command: `pip install colorama random time"

3. Run the ransomware using the following command: `python ransomware.py`

4. Enter the path of the target directory to encrypt when prompted.

5. Follow the on-screen instructions to pay the ransom and recover the files.

## Warning

The creation and distribution of ransomware is illegal and can cause significant harm to innocent people. This project is provided for educational purposes only and should not be used for malicious purposes.
