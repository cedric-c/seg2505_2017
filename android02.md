
# Développement d'applications Android

SEG 2505 - Introduction au génie logiciel – Automne 2017

Présenté par : 

---

# Laboratoire Android 2

Les menus, intéractions, et les activitées
À compléter : une application avec plusieurs activitées

---

# Plan

- Les éléments d'interfaces usagers
- Les activitées
- Les intentions (Intents)
- Le transfert de données
- L'application du laboratoire

---

# Les menus et la barre d'action

- Android vous offre une variété :
    - d'options dans les menus
    - barre d'action (recherche, composition de courriel, paramètres, etc...)
    - un menu contextuel et le mode contextuel d'action
        - apparait lorsqu'un utilisateur fait un "long-click" sur un élément de l'interface usager
    - menu "popup"
        - les actions dans ces menus ne devrait pas avoir un impacte directe sur le contenu mais plutot pour les séries d'actions
- les menus sont définit dans un fichier XML

---

# Les menus et la barre d'action (cont.)

- gestion des événement "click" (click events)
    - avec l'implémentation d'une méthode "OnClick()"
        - définissez ceci dans un fichier XML
        - faites un Override manuel dans la classe qui implémente onClick
    - avec l'implémentation de la méthode "onOptionItemSelected()" (override)

---

# Les fragments

- les Fragment sont utilisé pour représenter des portions d'une interface d'utilisateur
- plusieurs Fragments peuvent être combinés pour créer une interface
    - les Fragments sont réutilisables et modulaires

---

# Tiroire de navigation (Navigation Drawer)

- C'est un panau qui présent les fonctions de navigation pour l'application. Il y a 4 types:
    1. Permanent: toujours présent
    2. Persistant: ouvrir/fermer/basculer, déplace le contenu
    3. Temporaire: ouvrir/fermer/basculer, masque le contenu
    4. Mini-Variable: petit panau avec des icones seulement. Peut être utilisé dans l'état fermé

---

# Dialogues

- les dialogues invite l'utilisateur à prendre/fournir une décision ou pour des informations suplémentaire avant que l'application peut continuer
- types de dialogues
    - AlertDialog
    - DatePickerDialog
    - TimePickerDialog
    - Custom Layout

---

# Toasts

- des morceaux de texte qui fournissent des informations simples
- disapraissent automatiquement après un montant de temps
- vous pouvez manipuler le positionnement

---

# Paramètres (Settings)

- Permettent aux utilisateurs de modifier le fonctionnement et le comportement d'une application (e.g : comment souvent faire une requête à la DB)
- Permettent la construction d'interface uniforme dans les applications Android

---

# Activité (Activity)

- Les activitées sont des composantes d'application qui permettent aux utilisateurs de faire une chose telle que d'entrer un numéro de téléphone, envoyer une photo, envoyer un message, visualiser une carte...
- Une application a typiquement plusieurs activitées, une étant l'activité principale (MainActivity)
- Les activitées individuelles ont leurs propres tâches. Ces activitées sont liées ensemble avec des Intents.
- Lorsqu'une activités débute, l'activité antérieur est arrêtée et préservée dans le Stack
- Il n'y a pas de Main(). Les activitées commence à partir de leur méthode OnCreate().

---

# Commencer une nouvelle activité

- Les activité peuvent être appeller avec les fonctions suivantes:
    - startActivity(Intent i)
        - remarque: chaque activitée à besoin d'un Intent
        - les intents peuvent être des morceaux d'applications ou des applications entières
    - startActivityForResult(Intent i, RequestCode c)

---

# Intents

- Ce sont des objets messagers conçus pour envoyer la requête d'actions à des composantes
- Cas d'utilisation d'un Intent
    - commencer une activitée
    - commencer un service
    - livrer un message globale (broadcast)
- Types de Intents
    - implicite
    - explicite

---

# Intents (cont.)

- les Intents contiennent :
    - nom d'une composante
    - une action
    - des informations (Data)
    - une catégorie
    - des surplus (Extra)
    - des drapeaux

http://developer.android.com/guide/components/internts-filters.html

---

# Livrable du laboratoire
## Gestionnaire de profile

---

1. Objectif : vous devez créer un gestionnaire d'équipe sportive. Ce gestionnaire devra gérer les joueurs d'une équipe et plusieurs équipes
2. Requis:
    2.1 l'applications doit avoir plusieurs activitées
    2.2 chaque activitées doit avoir une fonctionnalitée
    2.3 l'application doit permettre l'utilisateur de créer le nom d'un profile
    2.4 l'application doit permettre l'utilisateur de changer le nom d'un profile
    2.5 l'application doit permettre l'utilisateur d'ajouter l'image d'un profile
    2.6 l'application doit permettre l'utilisateur de changer l'image d'un profile
    2.7 l'application doit permettre l'utilisateur d'ajouter une adresse un profile
    2.8 l'application doit permettre l'utilisateur de modifier l'adresse d'un profile
    2.9 l'application doit permettre l'utilisateur d'ouvrir une addresse dans une application de carte (telle que Google Maps)

---

# Activitée principale : vue du profile

- créez un nouveau projet avec une activité vide
- ajoutez un champ EditText pour le champ Personne/Équipe
    - ajoutez un champ TextView pour accompagner le champ EditText
    - définissez la valeur de la propritété "hint" du EditText à "Veuillez ajouter un nom"
- répétez ce processus pour le champ lieu (Location)
- ajoutez une vue d'image ImageView pour représenter l'image de l'équipe
    - l'image sera initiallement invisible car aucune image ne serra assignée au champ et la valeur de la propriété "size" ne sera pas définie
    - changez les propriétées de "width" et "height" à "100dp". Ceci rendera la boîte d'image visible
- ajoutez un bouton qui servira à ouvrir la carte
    - La valeur du OnClick sera OnOpenInGoogleMaps (tanto)

---








