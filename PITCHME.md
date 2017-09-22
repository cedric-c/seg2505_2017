## Développement d'applications Android

SEG 2505 - Introduction au génie logiciel – Automne 2017

Présenté par : 

---

## Laboratoire Android 1

Une introduction à Android
À compléter : une calculatrice sur Android

---

# Plan

- Introduction
- Android Studio
    - Guide d'installation
    - Installation du projet
    - Configuration du simulateur Android
    - Configuration de l'interface usager
- Concepts de base
- Travail de laboratoire : une calculatrice

---

# Introduction

---

# Qu'est-ce Android ?

- Platforme la plus populaire au monde
- Cadriciel (Framework) puissant
    - Les outils de développement Android offrent l'environnement de développement intégré de Java (Java IDE) ainsi que les outils nécessaires pour le développement, <<debugging>> et <<packaging>> d'applications Android
- Accès au marché pour rendre disponibles vos applications après un enregistrement de 25$

---

# Versions d'Android

Chaque version d'Android introduit de nouvelles fonctionnalités. Certaines itérations se concentrent sur des optimisations et d'autres sur l'architecture du système.

---

# Android SDK

- Les outils de développement logiciel Android vous donnent accès aux libraires et aux outils nécessaires pour construire, tester, et débugger vos applications Android.
- http://developer.android.com/sdk/index.html
- Outils disponibles
    - Android Studio (IntelliJ IDEA)
    - La ligne de commande (Debug et émulation)

---

# Fonctionnement d'Android

- Android est exécuté sur une couche du Kernel de Linux
- Les applications Android demeurent, et son exécuté dans leurs propres environnements / machine virtuelle (Sandbox)
- Depuis la version KitKat (4.4), l'environnement d'Android se sert d’ART (Android RunTime), Dalvik auparavant
- Les applications Android sont basées sur des Activités
    - une activité représente une chose que l'on fait, tel qu'une recherche
    - les applications sont composées de plusieurs activités

---

# Quelques Rappels : Les tests

- Windows
    - Voir la documentation OEM USB Drivers pour l'installation de composantes nécessaire
    - MTP : Media Transfer Protocol
- Mac OS
    - Android File Manager
    - PTP : Picture Transfer Protocol
- Vous devez activer le mode développement sur les mobiles
    - l'option est cachée par défaut 
        - Android 3.2  : Settings > Applications > Development
        - Android 4.0+ : Settings > Developer options
        - Android 4.2+ : Settings > About phone, tapez sur Build number 7 fois, retournez à l'écran d'avant pour trouver Developer options.

---

# Création d'un projet

---

# Installation
- Les systèmes du laboratoire ont déjà Android Studio d'installé
- Téléchargez et installez Android Studio (acceptez continuellement)
- Sélectionnez votre interface
- Faites une mise à jour

---

# Installation...

---

# Notez bien

- Certains systèmes fonctionnent mieux qu'autre
    - Windows Surface Pro : vous êtes limités par l'interface
    - QHD et moniteurs 4K : l'interface peut avoir de la misère 
- Certains systèmes se ralentissent l'or de l'exécution de l'émulateur
    - les systèmes avec des CPU autres que Intel, aucune accélération (Intel Hardware Acceleration)
    - Tablet : limité par le processeur
- autres options

---

# Une première application : Hello World!

Sélectionnez "Start a New Android Studio project"

---

Nom du projet
Le domaine du groupe de développement
Le nom du développeur est généralement basé sur la hiérarchie renversée .com où [code du pays].[TLD].[nom de l'entreprise].[sous-domaine].[équipe] tel que dans br.com.firasoft.msp.jimmyfive

Le code du pays, sous-domaine, nom d'équipe sous optionnels, mais aide avec la structure.

Nom du paquet tel que montré sur le marché Google (Google Play Store)

Le nom du paquet est produit à partir du nom de l'application ainsi que du domaine de la compagnie.

Vous pouvez modifier le nom du paquet (package name) si nécessaire

---

Version des outils de développement (Software SDK)
Utilisez "API LVL 15" pour le tutoriel

Après avoir appris la base, vous pouvez développer et publier des applications pour plusieurs versions d'Android

---

Gabarit d'activité
Il y a plusieurs types d'activité qui viennent avec des éléments d'interface de base

Pour cet exercice, sélectionnez "EMPTY Activity"

Plus d'activité devient disponible avec des versions plus élevées du cadriciel (API LVL). Un exemple de ceci sont les Applications à plein-écrans de ou le support est arrivé que dans la version 4.4 du cadriciel.

---

Vous pouvez configurer le nom de vos activités. Notez que ceci a une influence que sur les aspects de développement et ne sont pas visible aux utilisateurs.

Ceci est une opportunité pour vous d'appliquer la matière apprise en classe.

Par défaut, Java utilise la convention "Capitalized Camel Case" (UneClasse) comme standard pour les classes et les interfaces, mais "Camel Case" (uneMethode) pour les méthodes et les variables. Visitez le site d'Oracle pour plus de détails : http://www.oracle.com/technetwork/java/codeconventions-135099.html.

---

- Gestionnaire de machine virtuelle
- Gabarits d'éléments visuels
- fichier présent
- éditeur visuel
- éditeur XML
- pour la gestion de Widgets
- pour la gestion des propriétés

---

# L'interface d'Android Studio 2.2

---
# Machine virtuelle Android / Android Virtual Device (AVD)

- Une machine virtuelle Android est une configuration d'émulateur qui vous permet de choisir un modèle d'un système Android. L'émulateur est composé de
    1. une vue des systèmes matériaux du téléphone tels que la présence d'une caméra.
    2. une vue des systèmes logiciels du système tel que la version d'Android
    3. un environnement dédié pour le stockage d'information sur votre système
    4. Autres options : l'apparence de l'émulateur

---

Sélectionnez Windows > AVD Manager ou appuyer sur l'icône AVD Manager dans la barre d'outils d'Éclipse.

Appuyez sur "+" pour créer un nouveau gestionnaire AVD

---

Sélectionnez un système appartenant à la liste ou créez le vôtre en appuyant sur "New Hardware Profile".

---

---

# Gestion d'AVD (Android Virtual Machine)

- Sélectionnez Windows > AVD Manager ou appuyer sur l'icône AVD Manager dans la barre d'outils d'Éclipse.
- Appuyez sur "New" pour créer une nouvelle machine virtuelle

---

# Gestion d'AVD (cont.)

- Remplissez les détails pour votre gestionnaire, appuyez sur "OK"
- Les systèmes qui ont plus de fonctionnalités sont plus demandant 
- Sélectionnez "AVD Name" dans la liste et appuyez sur "Start"
- Soyez patient(e)

---

# Contraintes de système

Certains systèmes sont limités en ce qui concerne le pouvoir qu'il vous offre. Si vous éprouvez des difficultés avec l'émulation d'un système virtuel vous pouvez:

- changer l'architecture à "x86" ou à "armeabi-v7". Appuyez sur l'icône de crayon.
- désélectionner "User Host GPU"
- réduire le montant de RAM qu'utilise l'émulateur (Advanced Settings)

---

# L'émulateur Android

---

# Notes

- Autre émulateur (Bluestack, Genymotion, Nox, MEmu)
- Vous avez besoin de l'accélération d'Intel HAXM si votre système fonctionne sur une architecture x86.
- Vous allez avoir accès à un Google Nexus 4 pour le déploiement de votre application

---

# Concepts de base : interface usagers

---

# Ce qu'offre Android

- Des composantes déjà construites telles qu'une structure d'objet et des contrôles d'interface (UI)
- Des modules tels que les dialogues, les menus ainsi que les notifications
- Un mécanisme pour déclarer vos interfaces à partir de code XML et/ou source
    - facile et rapide pour la gestion et la création d'interfaces
    - séparation de l'aspect logique de l'aspect présentation
    - réutilisable
    - accessible
    - facile à comprendre

---

# La hiérarchie de l'interface usager

Contenant invisible
Contenant invisible

ViewGroups (contenant) sont des éléments fonctionnels utiles pour l'organisation d'interface
Les Views (vues) sont eux aussi des objets visibles sur l'écran tel que des boîtes de texte, des boutons, etc.

---

# Layouts

- Ce sont ce qui définit la structure de l'interface
- Peuvent être déclarés avec un fichier XML ou avec le code source
- Layouts commun
    - Linear
    - Relative
    - Web view
    - ListView
    - GridView

---

Contrôle d'entrées

- Android vous offre plusieurs sources d'entrée (I/O.)
- Vous pouvez construire vos propres composantes
- Des composantes communes
    - Button
    - Text field
    - Checkbox
    - Radio button
    - Toggle button
    - Spinner
    - Pickers

---

Livrable du lab
Une calculatrice simple

---

# L'interface d'Android Studio

- L'objectif est d'apprendre à utiliser les outils qui vous sont disponibles
- Votre application n'a pas besoin d'être exactement comme celle démontrée ici, mais les fonctions de base d'une calculatrice doivent être implémentées
- Pour ajouter un objet à l'interface, appuyez et tenez sur une composante et amenez-la dans l'arbre des composantes. N’amenez JAMAIS une composante directement à l'interface visuelle.
- Montrez la calculatrice avant de quitter

---

# Calculatrice simple : positionnement (Layout)

1. Suivez les étapes dans le premier exemple pour créer une application. Nommez votre application "Simple Calculator".
2. Enlever le TextView "Hello World" si votre Layout n'est pas vide.
3. Ajoutez un champ EditText au Layout nommé MainLayout et changez le champ ID à "resultEdit".
4. Ajouter un Layout "Layout (Vertical) / VerticalLayout" sous "resultEdit" et assignez l'ID du nouveau Layout à "mainLayout".
5. Changez la propriété "layout:width" du Layout "resultEdit" à "fill_parent". Ceci fera que ce Layout aura une valeur de x dynamiques.

---

# Calculatrice simple : résultat de l'étape 01

---

# Calculatrice simple : les boutons

1. Ajoutez un HorizontalLayout à votre VerticalLayout existant et nommez le "ButtonsLayout01"
    1. Ajoutez 4 boutons au HorizontalLayout
    2. Renomez chaque ID à "btn0X" ou X est le numéro du bouton (premier bouton sera nommé "btn01", deuxième "btn02", etc.)

Il ce peut que vous remarquez que certains boutons ne sont pas de la même largeur qu'autres. Pour réparer ceci, changez la propriété "layout:weight" à une valeur de "1". Faites ceci pour chaque bouton.

Les boutons auront maintenant la même priorité pour l'espace.

---

# Calculatrice simple : résultat de l'étape 02

---

# Calculatrice simple : plus de boutons

1. Répétez les étapes retrouvées dans la diapositive intitulée "Calculatrice simple : les boutons" jusqu'à ce que vous avez une matrice de 4x4 boutons.

Si vous remarquez que la prochaine rangée de boutons a aussi des problèmes avec le partage d'espace, changez la valeur de la propriété "layout:weight"  au HorizontalLinearLayout à 1.

2. Ajoutez des boutons fonctionnels (+ - = x ...) sous la dernière rangée de HorizontalLinearLayout
3. Changez la propriété "layout:width" du HorizontalLinearLayout à "fill_parent"

Pour remplir les espaces entre chaque bouton, changez leurs propriétés "layout:height" à "fill_parent".

---

# Calculatrice simple : résultat de l'étape 03

Rappel : ce que vous avez n'a pas besoin d'être exactement comme ceci

---

# Calculatrice simple : plus de boutons (2)

- Changez les valeurs du texte que présentent les boutons pour qu'ils ressemblent à ce que vous voyez ici
- Changez les valeurs des ID pour que les boutons suivent une convention telle que "btn00" pour le "0", "btn01" pour le "1", etc.

---

# Calculatrice simple : Étiquettes (Strings)

- Pour séparer les noms d'étiquettes du code source qui contrôle l'emplacement des objets:
1. sélectionnez un bouton dans l'arborescence des composantes (component tree)
2. Sélectionnez la propriété de texte et appuyez sur l'icône "..."
3. sélectionnez "New Resource"
4. sélectionnez "New String Resource"
5. définissez un nom pour le nouveau bouton (e.g: "button_07")
6. répétez ces étapes pour chaque bouton

---

---

# Calculatrice simple (cont.)

- ajoutez chaque méthode 'onClick' dans l'activité principale (MainActivity.java)
- les signatures doivent être les suivantes:
    Public void <nomDeMéthode> (View view){
        // votre code
    }
    
    e.g:
    Public void btnGetResult(View view){
        //...
        return results;
    }
- n'oubliez pas d'importer les classes nécessaires telles que "android.view.View" et "Android.widget.EditText"
- écrivez le code pour chaque bouton

---

# Calculatrice simple : exemple de code 1

Nous avons ajouté ces variables
Cette portion du code est générée automatiquement

---

---

---

---

---

# Calculatrice simple : événements IO

- les view ont des méthodes "slots" qui doivent être implémentées (override)
- utilisez des "listeners" au lieu de créer une sous-classe (pour les views)
- les "event listeners" sont des interfaces dans la classe "View" qui contiennent une seule méthode "callback"
    - onClick()
    - onLongClick()
    - onFocusChange()
    - onKey()
    - onTouch()
    - onCreateContextMenu()

---

# Calculatrice simple : fonctions des boutons

Vos boutons doivent savoir quelle méthode appeler pour fonctionner.

- chaque bouton doit avoir une propriété onClick
    - si vous voulez que le bouton btn01 exécute la méthode btn01Click(), la propriété OnClick de ce bouton sera "btn01Click"
    - si vous regardez la déclaration textuelle de l'interface et que vous voyez une entrée similaire à 'android:onClick="btn01Click"', le lien entre bouton et méthode a été créé

---

# Aide

- Votre code ne peut pas compiler
- Votre code contient des typos
    - onClick() != onclick()
    - button01 != Button01 != button_01
- Votre code ne contient pas les bonnes librairies
    - du texte rouge indique une classe qui n'est pas identifiée par Android Studio
    - Tapez "Alt+Enter" et Android Studio ajoutera les bonnes dépendances
- Les lampes rouges et jaunes vous offrent des remarques

---

# Améliorer votre code

- DRY (less is more)
- View.getID() retourne un entier (ID) qui représente ce qui a été appuyé, cette valeur peut être comparée à des valeurs dans la liste des ressources



