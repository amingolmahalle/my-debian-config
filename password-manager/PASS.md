How to manage Linux passwords with the pass command:

The pass command empowers you to take full control of your password management tasks on Linux.

1. Install pass:

> sudo apt isntall pass

2. If you don't already have a GPG keypair, you will need to create one:

> gpg2 --full-generate-key

Select option 1 (RSA and RSA) for the key type.

Please select what kind of key you want:

   (1) RSA and RSA (default)

   (2) DSA and Elgamal

   (3) DSA (sign only)

   (4) RSA (sign only)

Your selection? 1

Select your desired keysize. In this example, choose 4096:

RSA keys may be between 1024 and 4096 bits long.

What keysize do you want? (2048) 4096

Requested keysize is 4096 bits

Please specify how long the key should be valid.

        0 = key does not expire

      <n>  = key expires in n days

      <n>w = key expires in n weeks

      <n>m = key expires in n months

      <n>y = key expires in n years

Now choose how long you want the key to be valid for, in this example choose two years:

Key is valid for? (0) 2y

Key expires at Sat 18 Mar 2024 15:03:38 CET

Is this correct? (y/N) y

Input your full name, e-mail address and then confirm with 'O' when prompted.

GnuPG needs to construct a user ID to identify your key.

Real name: Amin Golmahalle

Email address: amin.golmahalle@gmail.com

Comment: 

You selected this USER-ID:

    "Amin Golmahalle <amin.golmahalle@gmail.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
One of the last steps of the GPG creation process is to set your password. Be sure to use a strong password containing uppercase, lowercase, and symbols. This will be your master password to unlock your pass datastore.

3. Now that your GPG key is created you'll need to list your keys and take note of the secret (sec) key ID:

> gpg2 --list-secret-keys --keyid-format LONG

sec 4096R/**AAAA2222CCCC4444** 2022-03-18 [expires: 2024-03-18] uid Amin Golmahalle amingolmahalle@gmail.com>

4. With your GPG key ID you can now initiate your pass datastore:

$ pass init 'AAAA2222CCCC4444'

mkdir: created directory ‘/home/myhome/.password-store’ Password store initialized for AAAA2222CCCC4444.

To Insert new password:

> pass insert Internet/github.com

<enter your password>

To Show specified password:

> pass show Internet/github.com

<enter GPG password at prompt>

To show all passwords:

> pass show 

or 

> pass ls


To sync with a Git repo:

see [link](https://www.redhat.com/sysadmin/management-password-store)
