# guardiabox

## DÉTAIL DU PROJET

### Objectifs
Ce projet a pour principaux objectifs d’appréhender les notions de chiffrement
(symétrique et asymétrique) et de hachage ainsi que les principaux algorithmes
actuels correspondant afin de les mettre en œuvre au moyen du langage Python.
Parmi les objectifs secondaires, les étudiants seront amenés à se perfectionner du
point de vue algorithmique et de la programmation en langage Python, tout en
adoptant les « bonnes pratiques » en termes de développement logiciel
(conventions, organisation du code, gestion de versions avec Git, tests, autres).
Spécifications - Version minimale
« GuardiaBox » est une application qui permet de chiffrer, stocker et déchiffrer
des fichiers ou des messages de manière sécurisée.

Cette application repose sur certains principes de la programmation
algorithmique sécurisée à travers :
● L’usage d’algorithmes de chiffrement.
● La gestion correcte des clés et des mots de passe.
● La validation et la sécurisation des entrées et des sorties.
● La résistance à certaines vulnérabilités courantes (ex. : attaque par
dictionnaire, mauvaises pratiques de hachage).
Les fonctionnalités minimales attendues, via une interface utilisateur en mode
console (menu de l’application) sont les suivantes :
1. Chiffrer un fichier ou un message.
2. Déchiffrer un fichier ou un message.
3. Quitter.
L’architecture logicielle (organisation des différents composants de l’application
du point de vue du système de fichiers) doit respecter la structure ci-dessous :

guardiabox/
├── fileio/
├── security/
├── tests/
├── ui/
└── main.py

● guardiabox : racine du projet.
● fileio : contient le(s) module(s) destiné(s) à la manipulation des fichiers (ex. :
lecture, écriture).
● security : contient le(s) module(s) destiné(s) à chiffrer, hacher, gérer des
clés, assurer l’intégrité des données, etc.
● tests : contient le(s) module(s) destiné(s) à tester l’application.
● ui : contient le(s) module(s) destiné(s) à mettre en œuvre l’interface
utilisateur en mode console.
● main.py : point d’entrée principal de l’application.
Du point de vue de l’implémentation, quelques pistes concernant les éléments à
mettre en œuvre :
● Chiffrement symétrique (AES-GCM) :
○ L’utilisateur fournit un message ou un fichier (nom de fichier).
○ S’il s’agit d’un message, un fichier texte contenant le message est
créé.
○ Il saisit un mot de passe.
○ Une clé dérivée est générée via PBKDF2 (sel aléatoire + itérations)
afin de chiffrer le fichier.
○ Le fichier chiffré contient : salt + nonce + ciphertext + tag.
○ Le nom du fichier chiffré reprend le nom d’origine auquel l’extension
.crypt est ajoutée.

● Déchiffrement sécurisé :
○ L’utilisateur saisit le même mot de passe.
○ Reconstitution de la clé depuis le mot de passe et le sel via la
lecture du fichier .crypt.
○ Vérification de l’intégrité du fichier via le tag AES-GCM.
○ Affichage du message en clair ou création du fichier déchiffré (ajout
d’une extension .decrypt).

● Validation des entrées (liste non exhaustive) :
○ Dans le cas d’un fichier, s’assurer que le fichier existe.
○ S’assurer que le mot de passe est suffisamment sécurisé (robustesse,
entropie).
○ Empêcher les injections de chemin (ex. : "../../").
○ Etc.
● Exemples de tests unitaires (Pytest) recommandés :
○ Vérifier que le chiffrement, suivi du déchiffrement, rendent bien la
donnée initiale.
○ Vérifier qu’un mauvais mot de passe ne permet pas le
déchiffrement.
○ Autres.

### Spécifications - Version étendue
Selon le temps disponible, quelques pistes d’améliorations envisageables :
● Gestion multi-utilisateurs avec une base de données locale sécurisée
(SQLite).
● Historique des opérations dans la base de données locale (SQLite).
● Création d’une interface graphique (PyQt6).
● Chiffrement asymétrique (ex. : RSA) pour partager un fichier chiffré entre
utilisateurs.
● Suppression sécurisée (effacement irrécupérable d’un fichier non chiffré).

### Progression
Semaine 1 - Remise à niveau, planification, préparation de l’environnement de
développement :
● Création d’un kanban sous Trello.
● Remise à niveau en algorithmique et programmation Python.
● Remise à niveau sur le thème du versioning (Git).
● Perfectionnement sur les concepts-clés de la cryptologie.
● Mise en place de la base de travail.
● Définition des tâches à réaliser et répartition de ces dernières au sein des
membres de l’équipe de projet.

Semaine 2 - Planification, implémentation du coffre-fort numérique sécurisé,
présentation du travail
● Mise à jour du kanban sous Trello.
● Implémentation du projet en respectant les spécifications présentées en
amont (section « Spécifications - Version minimale »).
● Selon le temps disponible, amélioration du projet (section « Spécifications -
Version étendue »).
● Présentation du travail réalisé.