## What are PGP and GnuPG?

PGP was originally created to protect files posted on Bulletin Board Systems (BBS) - a computerised messaging system that allowed users to post messages onto a public message board using a dial-up modem.

GnuPG is a **complete and free implementation of the OpenPGP standard** as defined by RFC4880 (also known as PGP). 
GnuPG allows you to **encrypt and sign your data and communications;** it features a versatile key management system, along with access modules for all kinds of public key directories. 
GnuPG, also known as GPG, is a **command line tool** with features for easy integration with other applications. 

A wealth of frontend applications and libraries are available e.g. Kleopatra. GnuPG also provides support for S/MIME and Secure Shell (ssh).

Since its introduction in 1997, **GnuPG is Free Software** (meaning that it respects your freedom). 
It can be freely used, modified and distributed under the terms of the GNU General Public License.


> Arguing that you don't care about the right to privacy because you have nothing to hide is no different from saying you don't care about free speech  because you have nothing to say. – Edward Snowden


### Why should you use GnuPG?

Encryption should be a priority for everyone including businesses. In case you need an encryption basics refresher, 
we’re starting from the ground up and showing how to create a PGP key so you can encrypt files and folders. 
After all, without your PGP key, your contacts cannot send you encrypted email.

Copyright © 2014-2021 Free Software Foundation, Inc. Privacy Policy. [Email Self-Defense](https://emailselfdefense.fsf.org/en/index.html)
Too complicated? Read this [infographics](https://emailselfdefense.fsf.org/en/infographic.html)


=========================================


## Installation
Out of the box, GnuPG should already be installed on your machine. If it’s not, you can install it with the command:

### Windows
#### Get GnuPG by downloading [GPG4Win](https://www.gpg4win.org/)
GPG4Win is an email and file encryption software package that includes GnuPG. Download and install the latest version, choosing default options whenever asked. After it's installed, you can close any windows that it creates.

### Mac
```
brew install gnupg gnupg2
```

### Generating your key pair 
You must generate your key pair; this will create a private key and a public key.

The private key decrypts emails and files sent to you by those that have your public key. The private key must remain secret.
The public key is the key you share with others so they may encrypt messages to you.
To generate your key pair, we’ll work from the command line. Open a terminal window and issue the following command:

```
gpg –gen-key
```

This fires up the process, and you’ll be asked a number of questions. The first bit of interactive output looks like this:

gpg (GnuPG) 1.4.16; Copyright (C) 2013 Free Software Foundation, Inc.This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (sign only)
(4) RSA (sign only)
Your selection?

Stick with the default here and press 1.

```
1
```

Next, you must select the keysize:

RSA keys may be between 1024 and 4096 bits long.
What keysize do you want?

Select the default (2048) or for a strong key (4096).

```
4096
```

The next question wants you to define how long the key should be valid. 
You can select a value in days, weeks, months, or years, or you can configure the key to have no expiration date.

Please specify how long the key should be valid.
0 = key does not expire
<n> = key expires in n days
<n>w = key expires in n weeks
<n>m = key expires in n months
<n>y = key expires in n yearsKey is valid for? (0)

Key does not expire at allIs this correct? (y/N)

You must enter user information to be associated with the key.

You need a user ID to identify your key; the software constructs the user IDfrom the Real Name, Comment and Email Address in this form:
“Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>”

Real name:
Email address:
Comment:

Verify your input and enter a passphrase for the key. Make sure the passphrase is strong and one you can remember. 
After you do this, you’ll need to go back to work so GnuPG can generate keys using entropy. 
When GnuPG returns you to the command prompt, you’re ready to move on.

### Exporting your public key
In order for your keypair to be useful, you must make your public key available to others. 
Export the public key, and then hand it over to those that need to send you encrypted mail or files. Export that key with the following command.

```
gpg –armor –export EMAIL_ADDRESS > public_key.asc (EMAIL_ADDRESS is the actual email address associated with the key)
```
  
You’ll have a public key file that you can distribute to those that need to encrypt email/files for your eyes only.
You can also upload your public key to the keys.gnupg.net public key server so others can use it. 
Follow these steps.

Open a terminal window.
  
```
gpg –list-keys.
```
  
Search for the 8-digit string (the primary ID) associated with the key you want to export.

```  
gpg –send-keys PRIMARY_ID (PRIMARY_ID is the actual ID of that key).
```
  
The key will be uploaded to the key server and be available to the public.

Once the user has acquired your public key, he or she can import it into their system and then send you encrypted messages. 
Because the public key they use to encrypt the messages/files is associated with your private key, you’ll be able to decrypt those messages. 
Without your private key, you cannot decrypt (which is why you want to safeguard those private keys).

### Importing other users’ private keys
You need to import the private keys of other users so you can send encrypted messages. Those users have to send you their public keys. 
Once you receive the user’s public key, save it and import it. The import process can be done from the command line as well. Here’s how.

Open a terminal window.
Change into the directory housing the saved user key.

```
–import PUBLIC_KEY (PUBLIC_KEY is the filename of the public key to be imported).
```
  
Now you can send encrypted email/files to the user associated with the imported key.
  
Source code: https://emailselfdefense.fsf.org/en/
