### Développement d'applications Android

Laboratoire Android 4 : Concepts UI supplémentaires et stockage

SEG 2505 - Introduction au génie logiciel

Automne 2017

Présenté par : Cédric Clément

---

### Agenda

1. Conception de l'interface utilisateur
2. Remarques sur la gestion de mémoire
3. Remarques supplémentaires et informations utiles
4. Travail de laboratoire

---

### Résumé

- Dans les laboratoires précédents, vous avez appris que vous pouvez mettre à jour les composants existants dans une mise en page.
- Aujourd'hui, nous allons voir comment créer des mises en page plus dynamiques et avec plus d’adaptabilité.
- Si vous avez manqué les séances de laboratoire précédentes, consultez le matériel précédent avant de poursuivre.

---

### UI / UX : Principes de base

- La conception d'interface utilisateur est le domaine responsable de:
- Interfaces utilisateur (UI)
- Expérience utilisateur (UX)

Les interfaces tactiles mobiles s'appuient sur une bonne conception d'interface: 
- Outils d'interaction limitée (pas de souris, pas de clavier)
- Occlusion d'IU (Mains et doigts cachent derrière eux des informations)
- Espace limité (petits écrans)

+++

### Simplicité

- L'âge de conception matériel (design plat et en couches, feuilles de papier empilées)
- Évitez d'encombrer votre écran avec l'information (utilisez des icônes)
- Uniformité et cohérence
- Less is more

+++

### Hiérarchie

- Le contenu doit être placé sur l'écran en fonction de leur importance.
- Les humains "scan" de gauche à droite et de haut en bas
- Bars hauts, menus et titres ont un emplacement prédéfini.
- Les utilisateurs ont des attentes envers l'emplacement des composantes, respectez les lignes directrices!


+++

#### Rule of Thirds

<!-- image -->

+++

### Composition

- Ajoutez des marges à votre application.
- Ne jamais toucher les frontières de l'écran
- Les contextes doivent être séparés.

densité indépendante pour les pixels (1 pixel à une densité de 160) dp = (Largeur en pixels * 160) / densité de l'écran


+++

### Dynamisme

- La réactivité est primordiale


---

### Composantes

+++

### `ListView`

Un `ListView` est une vue d'ensemble qui présente une liste d'objet "scrollable".

Les objets s'ajoutent à une liste avec l'aide d'un adaptateur.

+++ 

### `GridView`

Nous avons utilisé cette vue dans des laboratoires précédents. Par contre, elle recevait ses entrées de manière statique.

+++

### Pour votre projet...

Vous devez créer et gérer une liste d'objet. Ces objets seront mis à jour de manière dynamique ce qui signifie que votre liste aura besoin d'être mise à jour de manière dynamique.

+++

### Adaptateur

- L'adaptateur est le lien entre les vues d'adaptateur et ce qu'ils affichent.
- `ListView` et `GridView` étendent `AdapterView`
- Un adaptateur reçoit un `context` et un `ressourceID`.
- Déclarer l'adaptateur à utiliser pour un `ListView` en appelant sa méthode `setAdapter`.

---

### `ListView` simple

- peut être créé avec un tableau de chaînes et l'adaptateur `ArrayAdapter`
- mise en page préconstruite : `android.R.layout.simple_list_item_1`
- modifiez la méthode `onItemClick` pour changer la fonctionnalité de votre application.

+++

<!-- image -->

+++

### Extrait de `onCreate`

```java
// Get ListView object from xml layout
listView = (ListView) findViewById(R.id.list);
//Defining Array values to show in ListView
String[] values = new String[] {
        "Item 01","Item 02","Item 03","Item 04","Item 05","Item 06","Item 07","Item 08"
};
//Converting Array to ArrayList
final ArrayList<String> list = new ArrayList<String>();
for (int i = 0; i < values.length; ++i) {
    list.add(values[i]);
}
//Create an ArrayAdapter and Set it on the ListView
ArrayAdapter adapter = new ArrayAdapter(this, android.R.layout.simple_list_item_1, list);
listView.setAdapter(adapter);
listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, final View view, int position, long id) {
        final String item = (String) parent.getItemAtPosition(position);
        //Do something with the string that you just got!
    }
});
```

---

### Contenu dynamique

Les listes...
- ne sont pas limitées aux types primitifs.
- peuvent contenir des objets, images, etc.

+++

### Disposition (Layout)

- Ceci est un modèle de base pour l'unité d'une liste, représenté par un fichier XML.
- Définit la structure des informations présentées dans chaque élément affiché dans une liste.

+++

<!-- image -->

+++

### Comportement d'une liste

Les éléments apparaissent de manière séquentielle

<!-- image -->

+++

### Adaptateur personnalisé

- Pour créer une mise en page personnalisée, vous devez créer un `CustomAdapter` et implémenter les méthodes requises.
- Votre `CustomAdapter` devrait étendre un des adaptateurs existants. N'oubliez pas la méthode `getView`.
- Dans votre méthode `getView`, vous devez avoir un `LayoutInflater` (pour élargir les éléments de la liste).


+++

### Extrait `onCreate`

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_list);
    ListView listView = (ListView) findViewById(R.id.list);
    String[] values = new String[]{
            "Millonarios FC", "empty", "empty", "empty", "empty", "empty", "empty", "empty"
    };
    TeamArrayAdapter adapter = new TeamArrayAdapter(this, values);
    listView.setAdapter(adapter);
    listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
        @Override
        public void onItemClick(AdapterView<?> parent, final View view, int position, long id) {
            final String item = (String) parent.getItemAtPosition(position);
            //DO SOMETHING with your item, maybe open  a new activity!
        }
    });
}
```

+++

### Extrait de classe `TeamArrayAdapter`

```java
public class TeamArrayAdapter extends ArrayAdapter<String>  {
    private final Context context;
    private final String[] values;

    public TeamArrayAdapter(Context context, String[] values) {
        super(context, R.layout.list_team_layout, values);
        this.context = context;
        this.values = values;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        LayoutInflater inflater = (LayoutInflater) context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
        View rowView = inflater.inflate(R.layout.list_team_layout, parent, false);
        TextView textView = (TextView) rowView.findViewById(R.id.line01);
        ImageView imageView = (ImageView) rowView.findViewById(R.id.icon);
        textView.setText(values[position]);
        // Change the icon for Windows and iPhone
        String s = values[position];
        if (s == null || s.isEmpty() || s.equals("empty")) {
            imageView.setImageResource(R.drawable.ic_logo_empty);
        } else {
            imageView.setImageResource(R.drawable.ic_logo_mil);
        }
        return rowView;
    }
}
```

---

### Gestion de mémoire

Un patron de conceptions utiles dans la gestion d'application et de mémoire est le Singleton.

---

### Singleton

Patron de conception utile pour stocker les informations.

Une limite d'un seul instance assure la cohérence entre vos attentes et la réalité entre lecture / écriture.

<!-- image -->

+++

#### Utilisation

Pour utiliser efficacement Singleton comme une solution pour votre projet, la recommandation est de vous créer des classes Java représentant les informations (équipe, match, tournoi) dont vous avez besoin de stocker.

Après le codage des  classes qui nécessitent le stockage de données, vous pouvez créer des listes pour stocker les instances de vos classes dans le Singleton.

++++

Vous pouvez utiliser Umple pour générer vos fichiers de classe.

Utilisez votre Singleton comme gestionnaire de ressource. N’oubliez pas les getters et setters.

---

### Stockage de données

- Ensembles de `valeurs-clés`
- `Int` ou `String`
- utile pour les informations de configurations

---

### Lignes directrices du projet

1. ceci est un cours de génie logiciel
2. votre travail sera jugé sur sa fonctionnalité, sa structure ainsi que la présentation de votre code
3. utilisez les conventions et restez cohérent
4. Testez votre application.
5. 1 seul APK sera accepté... GIT to the rescue!

+++

### Plagiat

Politique de l'Université d'Ottawa sur le plagiat [EN](http://www.uottawa.ca/academic-regulations/academic-fraud.html) / [FR](http://www.uottawa.ca/reglements-scolaires/fraude-et-plagiat.html)

(ne copiez pas le code trouvé sur Internet)

---

### Mise en page

- Vous pouvez choisir des modèles préexistants ou définir le vôtre.
- Vous pouvez personnaliser la couleur,`ActionBar`, pleins écrans et autres.
- Pour accéder aux options de mise en page, cliquez sur le bouton circulaire dans la vue de la conception. Le texte du bouton affiche le nom du thème actuel de votre mise en page.

+++

### Personnalisation : Styles

Plusieurs styles IU sont disponibles, soit `Light` et `Dark`.

`/res/values/styles.xml` 

---

### Erreurs typiques

"Android Studio ne compile pas mon projet ou n'affiche pas une disposition de l'IU"

1. Regardez votre code ainsi que les logs Gradle
2. Reinstallez Android Studio (vos projets ne seront pas affectés par ceci)

+++

"L'émulateur ne fonctionne pas"

1. Si vous avez un processeur AMD, changez la configuration de votre AVD. Vous avez peut-être x86 ou x86_64 en sélection. Changez ceci à `armeabi-v7a ABI`.
2. Problème avec HAXM? Vous devez aller dans le BIOS pour allumer Intel Virtualization Technology.

+++

"L'émulateur est lent"

1. lorsque vous commencez l'émulateur, ne le fermez pas.
2. pas assez de mémoire? Modifiez l'AVD qui est utilisé à un système nécessitant moins de mémoire (plus vieux).
3. utilisez un téléphone Android.


---

### Travail de laboratoire

Liste de recettes

+++

### Exigences

1. activité principale, la liste des recettes
2. votre propre adaptateur (avec Inflater)
3. fichier XML pour la mise en page. Ce fichier contient:
    1. l'image de la recette
    2. le nom de la recette
    3. une liste (détaillée) des ingrédients 

+++

### `onCreate`

1. "content view loader"
2. référence à la `ListView` où seront stocké les objets recettes
3. création de la liste
4. création de l'adaptateur
5. `onClick` pour les recettes
6. MAJ de l'IU

+++

### Adaptateur et votre propre mise en page

1. créez un fichier XML
2. ajoutez les composantes qui feront 1 objet dans cette liste
3. "Gonflez" (Inflate) les objets dans la liste

+++

### Exemple de mise en page

<!-- image -->
<!-- image -->

---

### Liens utiles

- [Couleurs de l'Université](http: //www.uottawa.ca/brand/visual-identity/uottawa-colour-palettes
)
- [Conception matériel](https: //material.google.com/layout/principles.html)
