# Configuration du Formulaire de Contact

Ce guide explique comment configurer le formulaire de contact pour qu'il fonctionne correctement avec votre compte Gmail.

## Prérequis

- Un compte Gmail
- PHP 7.4 ou supérieur
- L'extension PHP OpenSSL activée
- L'extension PHP cURL activée

## Configuration du compte Gmail

1. **Activez l'authentification à deux facteurs** sur votre compte Gmail (si ce n'est pas déjà fait) :
   - Allez dans [Votre compte Google](https://myaccount.google.com/)
   - Sélectionnez "Sécurité"
   - Dans "Connexion à Google", activez l'authentification à deux facteurs

2. **Créez un mot de passe d'application** :
   - Toujours dans la section "Sécurité" de votre compte Google
   - Allez dans "Mot de passe des applications" (ou [cliquez ici](https://myaccount.google.com/apppasswords))
   - Sélectionnez "Sélectionner une application" et choisissez "Autre (Nom personnalisé)"
   - Donnez un nom à votre application (par exemple "Site Web Contact Form")
   - Cliquez sur "Générer"
   - Copiez le mot de passe généré (vous en aurez besoin plus tard)

## Configuration du fichier contact.php

1. Ouvrez le fichier `contact.php` à la racine du projet
2. Modifiez les valeurs suivantes dans le tableau `$config` :
   ```php
   $config = [
       'smtp' => [
           'host' => 'smtp.gmail.com',
           'username' => 'votre_email@gmail.com', // Votre adresse Gmail
           'password' => 'votre_mot_de_passe',    // Le mot de passe d'application généré
           'port' => 587,
           'encryption' => 'tls'
       ],
       'recipient' => 'votre_email@domaine.com', // L'email qui recevra les messages
       'from' => 'noreply@votredomaine.com',     // Email de l'expéditeur
       'from_name' => 'Formulaire de contact'     // Nom de l'expéditeur
   ];
   ```

## Test du formulaire

1. Assurez-vous que votre serveur web est démarré
2. Accédez à la page de contact de votre site
3. Remplissez le formulaire et soumettez-le
4. Vous devriez voir un message de confirmation et recevoir l'email à l'adresse spécifiée

## Dépannage

Si vous rencontrez des problèmes :

1. Vérifiez que vous avez bien suivi toutes les étapes de configuration
2. Vérifiez les logs d'erreurs PHP
3. Assurez-vous que votre hébergeur autorise les connexions sortantes sur le port 587
4. Vérifiez que votre pare-feu ne bloque pas les connexions SMTP

## Sécurité

- Ne partagez jamais votre mot de passe d'application
- Ne stockez pas le mot de passe dans le code source en production
- Utilisez toujours HTTPS pour protéger les données du formulaire

## Personnalisation

Vous pouvez personnaliser les messages d'erreur et de succès en modifiant les chaînes de caractères dans le fichier `contact.php`.
