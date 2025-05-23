# 🏦 KYC & Gestion d'Opérations Financières
# 📋 Description
Ce projet est une application web PHP (sans framework) de contrôle KYC (Know Your Customer) et de gestion des opérations financières (dépôt, retrait, transfert). Elle permet de gérer différents rôles (administrateurs, agents, commerciaux, clients) avec un système de validation à plusieurs niveaux pour garantir la sécurité et la conformité des utilisateurs.
# 🧑‍💼 Rôles du Système
# I. Utilisateurs
  ## 1. Administrateur
  Gère les utilisateurs (agents, commerciaux).
  Attribue les rôles et active les comptes utilisateur.
  ## 2. Agent niveau 1 & Agent niveau 2
  Valident successivement les comptes clients (vérification à double niveau).
  ## 3. Les Commerciaux
  Peuvent faire les opérations de dépot et retrait.
# II. Clients
  Enregistrés via un formulaire sécurisé avec téléchargement de documents (nina, passeport ...).
  Doivent être validés par deux agents successifs (niveau 1 puis niveau 2) avant d'accéder aux fonctionnalités de transaction.
  Ne sont pas actifs tant que la double validation n’est pas complétée.
## 🔐Processus de Validation
  1. Un client s’enregistre via le formulaire d'inscription.
  2. Un agent niveau 1 consulte les nouveaux enregistrements et valide.
  3. Un agent niveau 2 effectue la seconde validation.
  4. Après validation des deux niveaux, le client peut :
    Effectuer des dépôts (valider),
    Réaliser des retraits (valider),
    Faire des transferts entrants/sortants
## ⚙️ Fonctionnalités principales
  🔒 Système de connexion sécurisé avec gestion de sessions.
  📄 gestion de documents clients (PDF/images).
  🔍 Validation multi-niveaux pour les clients.
  📊 Tableau de bord personnalisé selon le rôle.
  💸 Historique des transactions filtrable (dépôt, retrait, transfert).
  🔄 Synchronisation entre clients et agents pour assurer la traçabilité.
## 🚀 Lancement du projet
Il faudra au préalable avoir installé php (version 7 au minimum) et un environnement Apache & Mysql.
## 1. Cloner le projet dans le htdocs (pour xampp par exemple sans le mettre dans un nouveau dossier) avec la commande : 
    git clone https://github.com/aboubacar2023/Projet_Application_KYC_Transaction.git
## 2. Configurer la base de données :
  Exécuter la commande sql du fichier database.slq dans phpmyAdmin. Le nom par défaut de la base de donnée est : kyc_transactions (Ne le modifier pas).
## 3. Lancer un serveur local de Xampp (ou tout autre serveur utilisé)
## 4. Se Placer dans le dossier racine du projet (là où il y a les fichiers .php) et excécuter la commande suivante :
    php -S localhost:8000
## 4. Accéder à l’application : 
  interface de connection : 
    http://localhost:8000/views/login.php
## 🛠️ Technologies utilisées
  PHP (sans framework),
  MySQL,
  HTML/CSS (avec Tailwind CSS),
  JavaScript,
# API REST - Documentation
  Cette API permet d’interagir avec les fonctionnalités principales du système KYC & Transactions.
## 1. Enregistrement d’un client
  URL: http://localhost:8000/API/clients/create.php || 
  Type: form-data || 
  champs requis: telephone, nom, prenom, email, adresse, date_naissance, mot_de_passe, type_document, document(image).
## 2. Récupération d’un client
  URL: http://localhost:8000/API/clients/show.php?id=90909090 (l'id correspond au contact du client)
## 3. Historique d’un client
  URL: http://localhost:8000/API/clients/operation.php?id=73963323 (l'id correspond au contact du client)
## 4. Dépôt d’argent (Commercial)
  URL: http://localhost:8000/API/commercials/depot.php || 
  Type : JSON (raw) || 
  champs requis : telephone, montant, id_commercial
## 5. Retrait d’argent (Commercial)
  URL: http://localhost:8000/API/commercials/retrait.php || 
  Type : JSON (raw) || 
  champs requis : telephone, montant, id_commercial
## 6. Transfert d’argent entre clients
  URL: http://localhost:8000/API/commercials/transfert.php ||
  Type : JSON (raw) || 
  champs requis : telephone_expediteur, telephone (Le destinateur), montant
## NB : respecter à la lettre le nom des champs requis ainsi que les types de données à envoyer dans un environnement de test d'api
  

  

