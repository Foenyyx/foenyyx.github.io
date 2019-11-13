## Consigne
- Installation des outils, si vous ne les avez pas déjà.
- Création de votre paire de clés (privée/publique)
Si vous avez déjà une paire de clés, il est inutile de regénérer une nouvelle clé.
**A noter que votre clé privée doit avoir un mot de passe.**
Vous pourrez conserver cette clé pendant quelques années et en particulier dans le cadre de
votre travail, donc prenez en soin et n’oubliez pas le mot de passe. Stockez la en lui sûr.
- Modifier la date d’expiration de votre clé publique :
    - Supprimer l’expiration pour la clé principale (clé de Signature).
    - Mettre une expiration dans 2 ans pour la clé de Chiffrement.
- Faire signer votre clé publique par 2 de vos camarades de classe.
Il faut déjà faire confiance à la clé de votre camarade, et ensuite la signer.
- Afficher toutes les clés dont vous disposez avec le détail des signatures avec la commande ```gpg --list-keys``` et toutes les signatures ```gpg --list-sigs```.
- Exportez votre clé publique, et les clés publiques de vos 2 camarades signataires, et faites un fichier ZIP, de la forme NOM.zip avec ces 3 clés et le fichier texte qui contient les commandes et leur résultat, avec vos commentaires.
**Signez le fichier ZIP avec votre clé privée et le chiffrer à mon attention.**

***A noter : l’identifiant de ma clé OpenGPG est 0xD5919687 et se trouve sur Internet***

## Pré-requis

### Windows

- [Git](https://git-scm.com/download/win) pour l'interface Git Bash.
- [GPG](https://files.gpg4win.org/gpg4win-3.1.10.exe) pour Windows.

***Vérifiez la version de GPG avec les commandes suivantes : ```gpg --version``` ou ```gpg2 --version```. Il faut quelle soit supérieure ou égale a 2.***

## Tutoriel

***Les valeurs sont a mon nom, n'hésitez pas a les remplacer !***

Lancez **Git Bash** ou le **Terminal**.

Créez votre clé avec ```gpg --full-generate-key```.

- Choisissez ```1``` pour le RSA.
- Choississez ```4096``` bits de longueur.
- Choississez ensuite ```2y``` pour 2 ans de validité de la clé de chiffrement.
- Éditez ensuite la clé primaire pour mettre son expiration a ```0```, qui signifie qu'elle sera valdie à vie.
Pour se faire il faut taper les commandes suivantes :
    - ```gpg --list-keys```, pour obtenir le nom commun de votre clé. Le mien étant ```Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>```.
    - ```gpg --edit-key 'Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>'```
    - Puis ```expire```.
    - Et puis ```0```. Validez en tapant ```y```.
- Quittez le mode édition en tapant la commande ```quit```.

Votre clé est à présent prête pour signer et être signée.

Importer la clé de Mr. Arditi avec la commande suivante ```gpg --keyserver keys.gnupg.net --recv-keys 0xd5919687```.

On signe le fichier.zip contenant nos 3 clés avec la commande ```gpg --clearsign CORREIA_FOURNIER_SCHEID.zip```.

Finalement, on chiffre le document à l'aide de la commande ```gpg --output CORREIA_FOURNIER_SCHEID_Encrypted.zip --encrypt --armor --recipient alain@arditi.fr CORREIA_FOURNIER_SCHEID.zip```.

## Rendu
Envoyez moi le fichier signé et chiffré par email à l’adresse <alain@arditi.fr> ou déposez le sur MyLearningBox, et ce avant 12h30 le Lundi 14 Octobre 2019.

Merci !


## A METTRE EN FORME PLUS TARD
```
Vincent@PC-Vincent MINGW64 ~
$ gpg2
bash: gpg2: command not found

Vincent@PC-Vincent MINGW64 ~
$ gpg
gpg: WARNING: no command supplied.  Trying to guess what you mean ...
gpg: Go ahead and type your message ...


gpg: signal Interrupt caught ... exiting


Vincent@PC-Vincent MINGW64 ~
$ gpg --version
gpg (GnuPG) 2.2.17-unknown
libgcrypt 1.8.4
Copyright (C) 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: /c/Users/Vincent/.gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

Vincent@PC-Vincent MINGW64 ~
$ gpg2
bash: gpg2: command not found

Vincent@PC-Vincent MINGW64 ~
$ gpg --full-generate-key
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 2y
Key expires at sam.  9 oct. 2021 14:17:08
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Vincent Fournier
Email address: vincent.fournier@epsi.fr
Comment: Clé GPG
You are using the 'utf-8' character set.
You selected this USER-ID:
    "Vincent Fournier (Clé GPG) <vincent.fournier@epsi.fr>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Operation cancelled
Key generation failed: Operation cancelled

Vincent@PC-Vincent MINGW64 ~
$ gpg --full-generate-key
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 2y
Key expires at sam.  9 oct. 2021 14:18:27
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Vincent Fournier
Email address: vincent.fournier@epsi.fr
Comment: Clé GPG
You are using the 'utf-8' character set.
You selected this USER-ID:
    "Vincent Fournier (Clé GPG) <vincent.fournier@epsi.fr>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Operation cancelled
Key generation failed: Operation cancelled

Vincent@PC-Vincent MINGW64 ~
$ gpg --full-generate-key
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 2y
Key expires at sam.  9 oct. 2021 14:19:15
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Vincent Fournier
Email address: vincent.fournier@epsi.fr
Comment: GPG Vincent Fournier
You selected this USER-ID:
    "Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 9BBA95816D54D21C marked as ultimately trusted
gpg: revocation certificate stored as '/c/Users/Vincent/.gnupg/openpgp-revocs.d/3229AA98C6F470067CC2A6569BBA95816D54D21C.rev'
public and secret key created and signed.

pub   rsa4096 2019-10-10 [SC] [expires: 2021-10-09]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid                      Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]


Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-key '
> Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: key "
Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>" not found: No public key

Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-key 'Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2020-05-21
sec  rsa4096/9BBA95816D54D21C
     created: 2019-10-10  expires: 2021-10-09  usage: SC
     trust: ultimate      validity: ultimate
ssb  rsa4096/4A27ABE1FB0D2C1D
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>

gpg> expire
Changing expiration time for the primary key.
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

sec  rsa4096/9BBA95816D54D21C
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
ssb  rsa4096/4A27ABE1FB0D2C1D
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>

gpg> quit
Save changes? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --list-keys
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2020-05-21
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]


Vincent@PC-Vincent MINGW64 ~
$ gpg --output VincentFournier.gpg --export 'Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>'

Vincent@PC-Vincent MINGW64 ~
$ ls
'3D Objects'/             ntuser.dat.LOG1
 AppData/                 ntuser.dat.LOG2
'Application Data'@       NTUSER.DAT{fd9a35db-49fe-11e9-aa2c-248a07783950}.TM.blf
 Contacts/                NTUSER.DAT{fd9a35db-49fe-11e9-aa2c-248a07783950}.TMContainer00000000000000000001.regtrans-ms
 Cookies@                 NTUSER.DAT{fd9a35db-49fe-11e9-aa2c-248a07783950}.TMContainer00000000000000000002.regtrans-ms
 Desktop/                 ntuser.ini
 Documents/               OneDrive/
 Downloads/               Pictures/
 Favorites/               Recent@
 IntelGraphicsProfiles/  'Saved Games'/
 Links/                   Searches/
'Local Settings'@         SendTo@
'Menu Démarrer'@          Videos/
'Mes documents'@          VincentFournier.gpg
 MicrosoftEdgeBackups/   "Voisinage d'impression"@
 Modèles@                'Voisinage réseau'@
 Music/                   wc/
 NTUSER.DAT

Vincent@PC-Vincent MINGW64 ~
$

Vincent@PC-Vincent MINGW64 ~
$

Vincent@PC-Vincent MINGW64 ~
$

Vincent@PC-Vincent MINGW64 ~
$ gpg --import VincentFournierSign.gpg
gpg: key 9BBA95816D54D21C: 2 signatures not checked due to missing keys
gpg: key 9BBA95816D54D21C: "Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>" 2 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 2
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2020-05-21

Vincent@PC-Vincent MINGW64 ~
$ gpg --list-keys
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]


Vincent@PC-Vincent MINGW64 ~
$ gpg --list-sigs
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sig 3        51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]
sig          51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig 3        9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig          FE4041BC9DAFE5F0 2019-10-10  [User ID not found]
sig          6FDA72CA0DA83D0D 2019-10-10  [User ID not found]
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>


Vincent@PC-Vincent MINGW64 ~
$ gpg --import StephaneScheid.gpg
gpg: key 6FDA72CA0DA83D0D: 1 signature not checked due to a missing key
gpg: key 6FDA72CA0DA83D0D: public key "Stephane Scheid <stephane.scheid@epsi.fr>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2020-05-21

Vincent@PC-Vincent MINGW64 ~
$ gpg --import ClementCORREIA.gpg
gpg: key FE4041BC9DAFE5F0: public key "Clement Correia <clement.correia34@gmail.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1

Vincent@PC-Vincent MINGW64 ~
$ gpg --list-sigs
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sig 3        51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]
sig          51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig 3        9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sig          6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>

pub   rsa4096 2019-10-10 [SC]
      B713C73EB8D4FD5121EEC5C86FDA72CA0DA83D0D
uid           [ unknown] Stephane Scheid <stephane.scheid@epsi.fr>
sig 3        6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>

pub   rsa4096 2019-10-10 [SC]
      07C5DDCF42ED8CA6CD5462B9FE4041BC9DAFE5F0
uid           [ unknown] Clement Correia <clement.correia34@gmail.com>
sig 3        FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>


Vincent@PC-Vincent MINGW64 ~
$ gpg --import ClementCORREIA.gpg
gpg: key FE4041BC9DAFE5F0: 1 signature not checked due to a missing key
gpg: key FE4041BC9DAFE5F0: "Clement Correia <clement.correia34@gmail.com>" 1 new signature
gpg: Total number processed: 1
gpg:         new signatures: 1
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2020-05-21

Vincent@PC-Vincent MINGW64 ~
$ gpg --list-sigs
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sig 3        51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]
sig          51350CA66EE602A3 2019-05-22  Vincent Fournier <v.fournier@outlook.com>

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig 3        9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sig          6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          9BBA95816D54D21C 2019-10-10  Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>

pub   rsa4096 2019-10-10 [SC]
      B713C73EB8D4FD5121EEC5C86FDA72CA0DA83D0D
uid           [ unknown] Stephane Scheid <stephane.scheid@epsi.fr>
sig 3        6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>

pub   rsa4096 2019-10-10 [SC]
      07C5DDCF42ED8CA6CD5462B9FE4041BC9DAFE5F0
uid           [ unknown] Clement Correia <clement.correia34@gmail.com>
sig 3        FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>
sig          6FDA72CA0DA83D0D 2019-10-10  Stephane Scheid <stephane.scheid@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]
sig          FE4041BC9DAFE5F0 2019-10-10  Clement Correia <clement.correia34@gmail.com>


Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-keys ' Clement Correia <clement.correia34@gmail.com>'
gpg: invalid option "--edit-keys"

Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-keys 'Clement Correia <clement.correia34@gmail.com>'
gpg: invalid option "--edit-keys"

Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-key 'Clement Correia <clement.correia34@gmail.com>'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: unknown       validity: unknown
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ unknown] (1). Clement Correia <clement.correia34@gmail.com>

gpg> trust
pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: unknown       validity: unknown
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ unknown] (1). Clement Correia <clement.correia34@gmail.com>

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
Do you really want to set this key to ultimate trust? (y/N) y

pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: unknown
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ unknown] (1). Clement Correia <clement.correia34@gmail.com>
Please note that the shown key validity is not necessarily correct
unless you restart the program.

gpg> sign

pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: unknown
 Primary key fingerprint: 07C5 DDCF 42ED 8CA6 CD54  62B9 FE40 41BC 9DAF E5F0

     Clement Correia <clement.correia34@gmail.com>

Are you sure that you want to sign this key with your
key "Vincent Fournier <v.fournier@outlook.com>" (51350CA66EE602A3)

Really sign? (y/N) y

gpg> quit
Save changes? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --edit-key 'Stephane Scheid <stephane.scheid@epsi.fr>'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   3  signed:   1  trust: 0-, 0q, 0n, 0m, 0f, 3u
gpg: depth: 1  valid:   1  signed:   0  trust: 1-, 0q, 0n, 0m, 0f, 0u
gpg: next trustdb check due at 2020-05-21
pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: unknown       validity: full
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[  full  ] (1). Stephane Scheid <stephane.scheid@epsi.fr>

gpg> trust
pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: unknown       validity: full
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[  full  ] (1). Stephane Scheid <stephane.scheid@epsi.fr>

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
Do you really want to set this key to ultimate trust? (y/N) y

pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: full
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[  full  ] (1). Stephane Scheid <stephane.scheid@epsi.fr>
Please note that the shown key validity is not necessarily correct
unless you restart the program.

gpg> sign

pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: full
 Primary key fingerprint: B713 C73E B8D4 FD51 21EE  C5C8 6FDA 72CA 0DA8 3D0D

     Stephane Scheid <stephane.scheid@epsi.fr>

Are you sure that you want to sign this key with your
key "Vincent Fournier <v.fournier@outlook.com>" (51350CA66EE602A3)

Really sign? (y/N) y

gpg> quit
Save changes? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --output ClementCORREIA.gpg --export 'ClementCORREIA.gpg'
ClementCORREIA.gpg

Vincent@PC-Vincent MINGW64 ~
$ gpg --output ClementCORREIA.gpg --export 'ClementCORREIA.gpg'
ClementCORREIA.gpg

Vincent@PC-Vincent MINGW64 ~
$ gpg --output ClementCORREIA.gpg --export 'Clement Correia'
File 'ClementCORREIA.gpg' exists. Overwrite? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --output StephaneScheid.gpg --export 'Stephane Scheid'
File 'StephaneScheid.gpg' exists. Overwrite? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --list-keys
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   4  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 4u
gpg: next trustdb check due at 2020-05-21
/c/Users/Vincent/.gnupg/pubring.kbx
-----------------------------------
pub   rsa4096 2019-05-22 [SC] [expires: 2020-05-21]
      6EBBD17E2195835DB9AB2CCC51350CA66EE602A3
uid           [ultimate] Vincent Fournier <v.fournier@outlook.com>
sub   rsa4096 2019-05-22 [E] [expires: 2020-05-21]

pub   rsa4096 2019-10-10 [SC]
      3229AA98C6F470067CC2A6569BBA95816D54D21C
uid           [ultimate] Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]

pub   rsa4096 2019-10-10 [SC]
      B713C73EB8D4FD5121EEC5C86FDA72CA0DA83D0D
uid           [ultimate] Stephane Scheid <stephane.scheid@epsi.fr>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]

pub   rsa4096 2019-10-10 [SC]
      07C5DDCF42ED8CA6CD5462B9FE4041BC9DAFE5F0
uid           [ultimate] Clement Correia <clement.correia34@gmail.com>
sub   rsa4096 2019-10-10 [E] [expires: 2021-10-09]


Vincent@PC-Vincent MINGW64 ~
$ gpg -u 3229AA98C6F470067CC2A6569BBA95816D54D21C --edit-key 'Clement Correia'
bash: $'\302\203gpg': command not found

Vincent@PC-Vincent MINGW64 ~
$ gpg -u 3229AA98C6F470067CC2A6569BBA95816D54D21C--edit-key  'Clement Correia'
bash: $'\302\203gpg': command not found

Vincent@PC-Vincent MINGW64 ~
$ g3229AA98C6F470067CC2A6569BBA95816D54D21C^C-u 3229AA98C6F470067CC2A6569BBA95816D54D21C--edit-key  'Clement Correia'

Vincent@PC-Vincent MINGW64 ~
$ ^C

Vincent@PC-Vincent MINGW64 ~
$ gpg -u 3229AA98C6F470067CC2A6569BBA95816D54D21C --edit-key 'Clement Correia'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Clement Correia <clement.correia34@gmail.com>

gpg> trust
pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Clement Correia <clement.correia34@gmail.com>

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
Do you really want to set this key to ultimate trust? (y/N) y

pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/7D07BCE24E84A903
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Clement Correia <clement.correia34@gmail.com>

gpg> sign

pub  rsa4096/FE4041BC9DAFE5F0
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
 Primary key fingerprint: 07C5 DDCF 42ED 8CA6 CD54  62B9 FE40 41BC 9DAF E5F0

     Clement Correia <clement.correia34@gmail.com>

Are you sure that you want to sign this key with your
key "Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>" (9BBA95816D54D21C)

Really sign? (y/N) y

gpg> quit
Save changes? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --output ClementCORREIA.gpg --export 'Clement Correia'
File 'ClementCORREIA.gpg' exists. Overwrite? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg -u 3229AA98C6F470067CC2A6569BBA95816D54D21C --edit-key 'Stephane Scheid'
gpg (GnuPG) 2.2.17-unknown; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   4  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 4u
gpg: next trustdb check due at 2020-05-21
pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Stephane Scheid <stephane.scheid@epsi.fr>

gpg> trust
pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Stephane Scheid <stephane.scheid@epsi.fr>

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
Do you really want to set this key to ultimate trust? (y/N) y

pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
sub  rsa4096/91D073497C349FAC
     created: 2019-10-10  expires: 2021-10-09  usage: E
[ultimate] (1). Stephane Scheid <stephane.scheid@epsi.fr>

gpg> sign

pub  rsa4096/6FDA72CA0DA83D0D
     created: 2019-10-10  expires: never       usage: SC
     trust: ultimate      validity: ultimate
 Primary key fingerprint: B713 C73E B8D4 FD51 21EE  C5C8 6FDA 72CA 0DA8 3D0D

     Stephane Scheid <stephane.scheid@epsi.fr>

Are you sure that you want to sign this key with your
key "Vincent Fournier (GPG Vincent Fournier) <vincent.fournier@epsi.fr>" (9BBA95816D54D21C)

Really sign? (y/N) y

gpg> quit
Save changes? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --output StephaneScheid.gpg --export 'Stephane Scheid'
File 'StephaneScheid.gpg' exists. Overwrite? (y/N) y

Vincent@PC-Vincent MINGW64 ~
$ gpg --output VincentFournier2.gpg --export 'Vincent Fournier <v.fournier@outlook.com>'

Vincent@PC-Vincent MINGW64 ~

```
