## Consigne
Il faut que :
 - Le CN de l’Issuer soit votre camarade
 - Le CN du Subject soit vous même et que la durée du certificat soit de deux ans.

## Pré-requis
### Windows
- [OpenSSL](https://slproweb.com/download/Win64OpenSSL-1_1_1d.exe)
- OpenSSL ajouté au PATH système ```C:\Program Files (x86)\OpenSSL-Win32\bin``` ou ```C:\Program Files\OpenSSL-Win64\bin```
- PowerShell

### macOS
- OpenSSL => ```brew install openssl``` Si ça ne fonctionne pas dirige toi à la <a href="#aide">fin du tutoriel</a> pour de l'aide.
- Terminal

# Tutoriel
Ouvrir powershell (<kbd>windows</kbd> + <kbd>x</kbd>) ou le Terminal et taper la commande suivante :
```
openssl
```
Si le résultat est le suivant, tout est bon : 
```
OpenSSL>
```
Sinon CHEH et dirige toi à la <a href="#aide">fin du tutoriel</a> pour de l'aide.

Fait ensuite ``` exit``` pour quitter la console OpenSSL, et créez le dossier acceuillant les fichiers du TP sur ton bureau : 
```
new-item $env:USERPROFILE\Desktop\TPArditi -ItemType directory # PowerShell
```
Maintenant, déplacez-vous dans votre dossier nouvellement créé :
```
cd "$env:USERPROFILE\Desktop\TPArditi" # PowerShell
```
Créez à présent, vos 2 clés privés. Une pour l'Autorité de Certification (CA) et une privé pour vous-même :
```
openssl genrsa -out ca-private-key.pem 2048
openssl genrsa -out ton-nom-pivate-key.pem 2048
```
Une fois nos 2 clés privées obtenues, on génère les clés publiques :
```
openssl rsa -in ca-private-key.pem -outform PEM -pubout -out ca-public-key.pem
openssl rsa -in ton-nom-pivate-key.pem -outform PEM -pubout -out  ton-nom-public-key.pem
```
Ensuite nous allons créer le certificat du CA qui nous permettra de signer le certificat de ton POTE :

**/!\ NE PAS OUBLIER DE METTRE EN CN VOTRE NOM PRENOM & NE PAS METTRE DE MOT DE PASSE, LAISSEZ VIDE /!\\**
```
openssl req -new -x509 -key ca-private-key.pem -out ton-ca-cert.crt -days 1095 # 1095 days = 3 ans
```
Une fois fait, nous allons créer ton certificat "public" (ton-nom.csr | CSR pour Certificate Signing Request) afin de l'envoyer a ton POTE pour qu'il le signe :
```
openssl req -new -key ton-nom-pivate-key.pem -out ton-nom.csr
```
Maintenant que tu possèdes ton CSR, envois le a ton POTE et demande lui le sien pour pouvoir le signer comme suit :
```
openssl x509 -req -days 730 -in ton-pote.csr -CA ton-ca-cert.crt -CAkey ca-private-key.pem -CAcreateserial -out ton-pote.crt # 730 days = 2 ans
```
Maintenant, n'hésite pas à vérifier les deux certificats, afin que le CA soit valide 3 ans et que le ton-pote.crt soit bien valide deux ans avec les bons CN grâce aux commandes suivantes :
```
openssl x509 -in ton-ca-cert.crt -noout -text
openssl x509 -in ton-pote.crt -noout -text
```
Voilà, c'est terminé :)

# Rendu
Le certificat obtenu sera envoyé par email à <alain@arditi.fr> avec le nom de votre camarade
et son autorité de certification (CA) avant mardi 8 octobre à 12h.

Toute réponse au delà de cette limite sera refusée !

Merci !

# Aide
CHEH
