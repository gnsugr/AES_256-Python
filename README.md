# AES_256-Python
A file encryption tool written with Python 3 using AES-256 bits, Scrypt and SHA3-512 algorithms.

AES-Python encrypts|decrypts a file or every files in a folder (even files in subfolders).

# Requirements
- [Pycryptodome](https://pycryptodome.readthedocs.io/en/latest/)

Run `pip3 install -r requirements.txt`

# Usage
Run `python3 AES.py -f [path of the file or folder] -e|d [e for encrypt | d for decrypt]`

and follow instructions on the terminal.

# Explanation
- The AES key is generated by the Scrypt key derivation algorithm using the password and a random 32 bytes salt.
- The password is hashed using SHA3-512 with the same salt than the AES-256 key
- Salt, hashed password and the initialisation vector are stored at the beginning of the new encrypted file
- Data of the plain file is encrypted through a 65kb buffer and stored into the new encrypted file
- The plain file is removed

# Example
> **Plain text:** 
Hello, I'm a test for Gaëtan Serré's Python-AES repository.

> **Encrypted text with the password azerty (hexadecimal):** 
0x66a7e11a394ecb29d9ab3b92110888118498e766eee47b620aed6e04de5a8ab97cd0a2d15b1ba9b2b5961cac8100aacb7c332770626729465f0f1b1783b63d15cad916de5cf63c35a88cbade36979d9e5dd0cb18cbd4952f188e4cba0277b726bc39df2df8bcba2af9bc3ab9118b7de06fc10c5187f3dd8d8616937bf092bd813a8e13b2b18eb442a10b2f11e96d47906559b6698ef8c405dca922d97d3e1610e14d0627c8ab7ebcd765a87f4d

- The 32 first bytes are the salt used in the SHA3-512 hashing and in the scrypt's derivation key
- The next 16 bytes are the initialisation vector for AES-256
- The next 64 bytes are the hashed password
- The next bytes are of the encrypted data

# Documentation
- [AES](https://fr.wikipedia.org/wiki/Advanced_Encryption_Standard)
- [Scrypt](https://en.wikipedia.org/wiki/Scrypt)
- [SHA3](https://en.wikipedia.org/wiki/SHA-3)

# Warning
Please save your password carefully. You will not be able to retrieve your data otherwise.
