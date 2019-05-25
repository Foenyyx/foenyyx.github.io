# Signer ses commits et push sans mot de passe

## Prérequis (Windows uniquement)

1. Télécharger et installer [Git Bash](https://git-scm.com/download/win)

## Créer une clé GPG

1. Ouvrir le terminal (Linux, Mac) ou la console [Git Bash](https://git-scm.com/download/win) (Windows).
2. Utiliser la commande de génération de clé suivante :
```markdown
gpg --full-generate-key
```
3. Choisir l'algorithme RSA et valider.
4. Choisir 4096 et valider.
5. Choisir le temps de validité de la clé.
6. Valider les informations précedemment saisies.
7. Entrer les informations concernant votre identité.
8. Choisir un mot de passe pour sécurisé sa clé.
