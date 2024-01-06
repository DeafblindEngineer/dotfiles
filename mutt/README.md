### Mutt Configuration

These are my dotfiles and configuration notes to configure Mutt for multiple IMAP email addresses.

&num; Initial Mutt Configuration

```
$ sudo apt install mutt
$ mkdir -p ~/.mutt/cache/headers
$ mkdir ~/.mutt/cache/bodies
$ touch ~/.mutt/certificates
$ touch ~/.mutt/muttrc
```

&num; Global Mutt Dotfile

&nbsp;&nbsp;&nbsp;&nbsp;$ vim [~/.mutt/muttrc](https://github.com/DeafblindEngineer/dotfiles/blob/main/mutt/.muttrc)  


&num; IMAP Specific Dotfiles

&nbsp;&nbsp;&nbsp;&nbsp;$ vim [~/.mutt/imap01](https://github.com/DeafblindEngineer/dotfiles/blob/main/mutt/.imap01)  
&nbsp;&nbsp;&nbsp;&nbsp;$ vim [~/.mutt/imap02](https://github.com/DeafblindEngineer/dotfiles/blob/main/mutt/imap02)  
&nbsp;&nbsp;&nbsp;&nbsp;$ vim [~/.mutt/imap03](https://github.com/DeafblindEngineer/dotfiles/blob/main/mutt/imap03)  
&nbsp;&nbsp;&nbsp;&nbsp;$ vim [~/.mutt/imap04](https://github.com/DeafblindEngineer/dotfiles/blob/main/mutt/imap04)  


&num; Create GPG Key (if required)

```
$ gpg --gen-key
```

* Choose the key type (RSA)
* Choose the Keysize (2048 bits)
* Expiration date (0: no expiration)
* User ID, type name (imap01)
* Enter the email address to be associated with the private/public keypair (imap01@example.com)
•	Type a passphrase to protect the private key

**NOTE:** Repeat the above steps for imap02, imap03, and imap04

&num; GPG Key Setup for ~/.mutt/imap01

Create a new text file in ~/.mutt directory called imap01_pwd:

```
$ mkdir ~/.mutt
$ vim ~/.mutt/imap01_pwd
```

Put the IMAP/SMTP Passwords in the new Mutt configuration file that will be encrypted:

```
set imap_pass = "imap01password"
set smtp_pass = "smtp01password"
```

Encrypt this file with gpg using the public key to create a ~/.mutt/imap01_pwd.gpg, which will be a GPG-encrypted version of the original file:

```
$ gpg -r imap01@example.com -e ~/.mutt/imap01_pwd
```

Remove ~/.mutt/imap01_pwd, leaving only the GPG-encrypted version:

```
$ rm ~/.mutt/imap01_pwd
```

**NOTE:** Repeat the above steps for imap02, imap03, and imap04
