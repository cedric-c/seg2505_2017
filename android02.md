# Développement d'applications Android

SEG 2505 - Introduction au génie logiciel – Automne 2017

Présenté par : Cédric Clément

---

# Laboratoire Android 2

Les menus, interactions, et les activités
À compléter : une application avec plusieurs activités

---

# Plan

- Les éléments d'interfaces usagers
- Les activités
- Les intentions (Intents)
- Le transfert de données
- L'application du laboratoire

---

# Les menus et la barre d'action

- Android vous offre une variété :
- d'options dans les menus
- barre d'action (recherche, composition de courriel, paramètres, etc.)
- un menu contextuel et le mode contextuel d'action
- apparait lorsqu'un utilisateur fait un "long-click" sur un élément de l'interface usager
- menu "popup"
- les actions dans ces menus ne devraient pas avoir un impacte directe sur le contenu, mais plutôt pour les séries d'actions
- les menus sont définis dans un fichier XML

---

# Les menus et la barre d'action (cont.)

- gestion des événements "click" (click events)
- avec l'implémentation d'une méthode "OnClick()"
- définissez ceci dans un fichier XML
- faites un Override manuel dans la classe qui implémente onClick
- avec l'implémentation de la méthode "onOptionItemSelected()" (override)

---

# Les fragments

- les Fragments sont utilisés pour représenter des portions d'une interface d'utilisateur
- plusieurs Fragments peuvent être combinés pour créer une interface
- les Fragments sont réutilisables et modulaires

---

# Tiroire de navigation (Navigation Drawer)

- C'est un panneau qui présente les fonctions de navigation pour l'application. Il y a 4 types:
1. Permanent: toujours présent
2. Persistant: ouvrir/fermer/basculer, déplace le contenu
3. Temporaire: ouvrir/fermer/basculer, masque le contenu
4. Mini-Variable: petit panneau avec des icônes seulement. Peut être utilisé dans l'état fermé.

---

# Dialogues

- les dialogues invitent l'utilisateur à prendre/fournir une décision ou pour des informations supplémentaires avant que l'application peut continuer
- types de dialogues
- AlertDialog
- DatePickerDialog
- TimePickerDialog
- Custom Layout

---

# Toasts

- des morceaux de texte qui fournissent des informations simples
- disparaissent automatiquement après un montant de temps
- vous pouvez manipuler le positionnement

---

# Paramètres (Settings)

- Permettent aux utilisateurs de modifier le fonctionnement et le comportement d'une application (e.g : comment souvent faire une requête à la DB)
- Permettent la construction d'interface uniforme dans les applications Android

---

# Activité (Activity)

- Les activités sont des composantes d'application qui permettent aux utilisateurs de faire une chose telle que d'entrer un numéro de téléphone, envoyer une photo, envoyer un message, visualiser une carte...
- Une application a typiquement plusieurs activités, une étant l'activité principale (MainActivity)
- Les activités individuelles ont leurs propres tâches. Ces activités sont liées ensemble avec des Intents.
- Lorsqu'une activité débute, l'activité antérieure est arrêtée et préservée dans le Stack
- Il n'y a pas de Main(). Les activités commencent à partir de leur méthode OnCreate().

---

# Commencer une nouvelle activité

- Les activités peuvent être appelées avec les fonctions suivantes:
- startActivity(Intent i)
- remarque: chaque activité à besoin d'un Intent
- les Intents peuvent être des morceaux d'applications ou des applications entières
- startActivityForResult(Intent i, RequestCode c)

---

# Intents

- Ce sont des objets messagers conçus pour envoyer la requête d'actions à des composantes
- Cas d'utilisation d'un Intent
- commencer une activité
- commencer un service
- livrer un message global (broadcast)
- Types de Intents
- implicite
- explicite

---

# Intents (cont.)

- les Intents contiennent :
- nom d'une composante
- une action
- des informations (data)
- une catégorie
- des surplus (Extra)
- des drapeaux

http://developer.android.com/guide/components/internts-filters.html

---

# Livrable du laboratoire ## gestionnaire de profile

---

1. Objectif : vous devez créer un gestionnaire d'équipe sportive. Ce gestionnaire devra gérer les joueurs d'une équipe et plusieurs équipes 2. requis:
2.1 l'application doit avoir plusieurs activités
2.2 chaque activité doit avoir une fonctionnalité
2.3 l'application doit permettre l'utilisateur de créer le nom d'un profile
2.4 l'application doit permettre l'utilisateur de changer le nom d'un profile
2.5 l'application doit permettre l'utilisateur d'ajouter l'image d'un profile
2.6 l'application doit permettre l'utilisateur de changer l'image d'un profile
2.7 l'application doit permettre l'utilisateur d'ajouter une adresse un profile
2.8 l'application doit permettre l'utilisateur de modifier l'adresse d'un profile
2.9 l'application doit permettre l'utilisateur d'ouvrir une adresse dans une application de carte (telle que Google Maps)

---

# Activitée principale : vue du profil

- créez un nouveau projet avec une activité vide
- ajoutez un champ EditText pour le champ Personne/Équipe
- ajoutez un champ TextView pour accompagner le champ EditText
- définissez la valeur de la propriété "hint" du EditText à "Veuillez ajouter un nom"
- répétez ce processus pour le champ lieu (Location)
- ajoutez une vue d'image ImageView pour représenter l'image de l'équipe
- l'image sera initialement invisible, car aucune image ne sera assignée au champ et la valeur de la propriété "size" ne sera pas définie
- changez les propriétés de "width" et "height" à "100dp". Ceci rendra la boîte à 'image visible.
- ajoutez un bouton qui servira à ouvrir la carte
- La valeur du OnClick sera OnOpenInGoogleMaps (tantôt)

---

# Changer les images

- pour des médias (image, son, etc.) à votre projet vous avez qu'à placer les fichiers dans le répertoire "drawable"
- app > res > drawable
- right-click > "show in explorer"
- changez l'image défaut
- http://www.firasoft.com.br/UOT/avatars.zip
- http://www.firasoft.com.br/UOT/logos.zip

---

---

# Intent explicite et activité externe

- ajoutez la prochaine méthode à votre activité principale (MainActivity.java)
- changez la propriété OnClick
- cette fonction fait une demande explicite au paquet de Google Maps

Notez que vous devez avoir le cadriciel de Google (Google API) dans votre émulateur virtuel pour que ceci fonctionne

---

# Intent explicite et activité interne

- ajoutez la prochaine fonction à votre activité principale (MainActivity.java)
- changez la propriété OnClick de votre ImageView
- ceci va ouvrir une autre activité où nous allons choisir une nouvelle image pour l'équipe

---

- Le constructeur de l'objet Intent a deux paramètres
1. le contexte d'application (Application Context) : c'est d'où arrive l'application
1.1 Lorsque vous créez une nouvelle activité, une hiérarchie est créée et la nouvelle activité a comme parent l'activité qui a fait appelle à sa création
- this
- getApplicationContext()
2. classe Intent : c'est la classe pour laquel le Intent fait demande

---

# Statut présent

- votre application devra être similaire à ce que vous voyez ici
- ajoutez à la propriété OnClick une valeur de "OnOpenInGoogleMaps"
- ajoutez à la propriété OnClick du ViewImage une valeur de "OnSetAvatarButton"

---

# Créer une nouvelle activité

Pour créer une nouvelle activité avec Android Studio, "right-click" et sélectionnez "New > Activity > Blank Activity"

---

# Créer une nouvelle activité (cont.)

- ajoutez les informations de votre choix et appuyez sur "Finish"
- lorsque vous créez une activité, Android Studio crée un nouveau fichier Java ainsi qu'un fichier XML pour l'interface d'utilisateur

Parent hiérarchique
Si votre application implémente la fonctionnalité "UP", vous pouvez déclarer une autre activité comme le parent d'une autre

Exemple de fonctionnalité "UP"

---

# Deuxième activité

- créez une deuxième activité qui est l'enfant de votre activité principale (MainActivity). Ceci se fait dans la boite de création.
- supprimez ce qui se trouve sur l'écran et ajoutez un VerticalLayout
- ajoutez un GridLayout au VerticalLayout et créez 6 nouveaux ImageViews à l'intérieur du VerticalLayout
- ajoutez un bouton au VerticalLayout sous le GridLayout

---

# Deuxième activité (cont.)

- Comment puis-je retourner à l'activité principale ?
- Les activités sont structurées en pile. Une activité qui termine est "pop-é" de la pile et l'activité principale est rappelée. Notez que les champs locaux (dans les activités parentes) qui contiennent des informations ne les perdent pas lorsqu'une activité enfant est "pop-é".
- Lorsqu'on pop une activité, un tue l'instance
- Vous n'avez pas besoin de créer de bouton retour / “back”, Android fait ceci pour vous

---

# Retour à l'activité principale

- ajoutez la prochaine fonction à votre deuxième fichier d'activité
- ceci devrait être la méthode OnClick sur vos images
- le code envoie les ID des images qui ont été appuyées

---

# Statut présent (2)

- votre application devra être similaire à ce que vous voyez ici
- ajoutez à la propriété OnClick de chaque icône la valeur de "SetTeamIconOnClick"

---

# Gérer les résultats

- Ajoutez cette méthode dans votre activité principale (MainActivity.java). Cette méthode manipule les informations qui lui sont retournées dans le "Return Intent".
- Les informations passées dans le "Return Intent" sont interprétées et utilisées pour choisir la nouvelle image.
- Les noms des photos devraient être différents

---

# Statut présent (3)

- Votre application devrait:
- montrer et pouvoir mettre à jour les noms d'équipe ainsi que les adresses
- monter les adresses sur Google Maps
- pouvoir mettre à jour les images d'équipe à partir d'une liste prédéfinie d'images
- Votre application ne devrait pas encore:
- charger les images à partir d'images existantes sur le système (optionnel)

Notez que charger les images à partir d'images existantes sur le système porte quelques contraintes:
1. des permissions sont requises
2. des fichiers "manifest" doivent être gérés

---

# Implicit Intents (intentions implicites)

- fonctionnalité de la caméra avec intention implicite:

Intent i = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);

- peut ajouter des méta-informations (“Metadata”)
- onActivityResult reçoit un hyperlien à une image et décodera l'image

---

---

# Implicit Intents

- fonctionnalité pour sauvegarder des informations

Intent i = new Intent(Intent.ACTION_PICK);

- peut ajouter des méta-informations (Metadata)
- onActivityResult reçoit un hyperlien à un fichier et décodera le fichier

---

---

Pour en apprendre plus : https://developer.android.com/training/index.html
