### Développement d'applications Android

Laboratoire Android 3 : Base de données (DB) locale sur Android

<span style="color:gray"></span>

<span style="color:gray">SEG 2505 - Introduction au génie logiciel</span>

<span style="color:gray">Automne 2017</span>

<!-- <span style="color:gray">Présenté par : Cédric Clément</span> -->

---

### Agenda
1. Survole de SQLite sur Android
2. La base des tables, schémas, clés primaires
3. Structured Query Language (SQL)
4. Exemple de SQLite simple
5. Travail de laboratoire

---

## Qu'est-ce SQLite?

- Les applications mobiles ont besoin de garder des informations locales
- La base de données se retrouve dans presque chaque application
    - les applications qui manipulent les données
    - les applications qui font que sauver des informations simples comme les points pour un match de soccer
- Pouvoir capter des informations dans une base de données est du plus important puisque l'environnement Android peut à n'importe quel instant supprimer les informations en mémoire pour se servir de ces ressources.

+++

## Qu'est-ce SQLite?

- SQLite est une base de données intégrée 
- La plupart des bases de données (Oracle, MySQL) sont des processus qui fonctionnent de manière indépendante
- SQLite est dit <<intégré>> car c'est qu'une librairie qui fait partie d'une application
    - il n'y a donc aucun processus dédié qui soutient l'exécution de la base de données
- Les opérations effectuées dans la base de données se font à l'intérieur de la librairie SQLite

---

## Comprendre les tables

- Une structure simple dans la DB
- Chaque DB peut contenir plusieurs tables et chaque table est conçue pour contenir un type d'information spécifique
- Exemple
    - Une DB peut contenir une table <<client>> qui contient le nom, l'adresse, le numéro téléphonique de chaque client pour une organisation
    - La même DB pourrait aussi contenir une table <<produits>> qui contient des entrées de produits (identifiant du produit, description) qu'offre une organisation.

+++

## Comprendre les tables

- Chaque table dans une DB a un nom unique


---

## Le schéma

- Le schéma définit les caractéristiques des données sauvegardées dans la table d'une DB
- Le schéma pour table de client pourrait définir que
    - un client n'aura pas de nom de plus de 20 caractères de longueur
    - l'entrée téléphonique d'un client aura que des entrées d'un certain format
- Les schémas sont aussi utilisés pour définir la structure entière d'une DB et les relations entre les tables qu'elle contient

---

## Colonnes et types de donnée

- Chaque colonne représente un champ dans une DB (nom, téléphone, courriel)
- Chaque colonne doit contenir un type spécifié de donnée

---

## Clés primaires

- Chaque DB contient une ou plusieurs colonnes utilisées pour identifier chaque rangée d'une manière unique
- C'est ce qu'on nomme la clé primaire (primary key)
- Exemple: numéro bancaire, NAS
- C'est ce qui permet à un système de DB d'identifier de manière unique chaque entrée dans la DB
sans clé primaire, il ne serait pas possible de supprimer des entrées spécifiques

---

## Structured Query Language (SQL)

- Les données sont manipulées avec un langage appelé Structured Query Language
- C'est le standard 
- C'est simple et conçu pour lire et écrire à une DB
    - Peu de mots clés
    - Différentes implémentations de SQL ont souvent une syntaxe identique
    
+++
    
## Commande utile : `Create Table`

```
CREATE TABLE table_name(
    column1 datatype PRIMARY KEY
    column2 datatype,
    column3 datatype,
    ....
    columnN datatype,
);
```

+++

## Commande utile : `Drop Table` pour supprimer (table)

- `DROP TABLE table_name`
- `DROP TABLE IF EXISTS table_name`

+++

## Commande utile : `Insert into Table` pour ajouter (élément)

`INSERT INTO table_name VALUES (value1, value2, value3, ...);`

+++

## Commande utile : `Delete from Table` pour supprimer (élément)

`DELETE FROM table_name WHERE some_column=some_value;`

+++

## Commande utile : Retrait
`SELECT column_name, column_name FROM table_name WHERE column_name=value;`

---

# Exemple simple

+++

## Interface d'utilisateur

![arbre](assets/resized/slides/extract-4.jpg)

+++

![android](assets/resized/slides/extract-3.jpg)

+++

## Table de produits

![android](assets/resized/slides/extract-5.png)

---

# Livrable du laboratoire

---

## Importez le projet

- `Import` dans Android Studio: `File > New > Import Project`

Vous devez implémenter pour ajouter, lire, et supprimer de la base de donnée (`add`, `read`, et `delete`).

---

## Première étape

- Créez une classe qui **extends** `SQLiteOpenHelper` pour exécuter les opérations suivantes dans SQLite:

- insert
- read
- delete

```
public class MyDBHandler extends SQLiteOpenHelper
```

+++

### À importer...

```
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;
import android.content.Context;
import android.content.ContentValues;
import android.database.Cursor;
```

+++

### Définissez le schéma

```
public class MyDBHandler extends SQLiteOpenHelper{
    private static final int DATABASE_VERSION = 1;
    private static final String DATABASE_NAME = "productDB.db";
    public static final String TABLE_PRODUCTS = "products";
    public static final String COLUMN_ID = "_id";
    public static final String COLUMN_PRODUCTNAME = "productname";
    public static final String COLUMN_SKU = "SKU";
}
```

+++

Note: le constructeur de `MyDBHandler` doit appeler le constructeur de sa classe parent, soit

```
public MyDBHandler(Context context){
    super(context, DATABASE_NAME, null, DATABASE_VERSION);
}
```

+++

### Créer la table

Vous devez faire un override de la méthode `onCreate()`

```
@Override
public void onCreate(SQLiteDatabase db){
    
    String CREATE_PRODUCTS_TABLE = "CREATE TABLE" +
        TABLE_PRODUCTS + "("
        + COLUMN_ID + " INTEGER PRIMARY KEY," +
        COLUMN_PRODUCTNAME +
        " TEXT," + COLUMN_SKU + " INTEGER" + ")";
    
    db.execSQL(CREATE_PRODUCTS_TABLE);
}
```

+++

### Mise à jour 

Pour remplacer des anciennes tables par des nouvelles:

```
@Override
public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
    db.execSQL("DROP TABLE IF EXISTS " + TABLE_PRODUCTS);
    onCreate(db);
}
```

---

## Opérations

+++

### Insertion

```java
public void addProduct(Product product){
    SQLiteDatabase db = this.getWriteableDatabase();
    
    ContentValues values = new ContentValues();
    values.put(COLUMN_PRODUCTNAME, product.getProductName());
    values.put(COLUMN_SKU, product.getSku());
    
    db.insert(TABLE_PRODUCTS, null, values);
    db.close();
}
```
@[1](Créez une méthode pour faire des ajouts)
@[2](Obtenez une instance d'une DB)
@[4-6](L'ajout des `key:value` dans l'objet `values`)
@[8](Insertion dans la DB)
@[9](Fermer la connection à la DB)

+++

### Lecture

```java
public Product findProduct(String productName){
    SQLiteDatabase db = this.getReadableDatabase();
    
    String query = "Select * FROM " 
        + TABLE_PRODUCTS
        + " WHERE "
        + COLUMN_PRODUCTNAME
        + " = \""
        + productName
        + "\""
    ;
    
    Cursor cursor = db.rawQuery(query, null);
    Product product = new Product();
    
    if(cursor.moveToFirst()){
        product.setID(Integer.parseInt(cursor.getString(0)));
        product.setProductName(cursor.getString(1));
        product.setSku(Integer.parseInt(cursor.getString(2)));
        cursor.close()
    } else {
        product = null;
    }
    db.close();
    return product;
}
```
@[1](Créez une méthode pour faire des lectures)
@[2](Obtenez une instance d'une DB)
@[4-11](Créer votre query)
@[13](Exécuter votre query)
@[14-23](Créer l'objet **product**)
@[24](Fermer la connection à la DB)

+++

### Supprimer

```java
public boolean deleteProduct(String productName){
    SQLiteDatabase db = this.getWriteableDatabase();
    boolean result = false;
    String query = "SELECT * FROM "
        + TABLE_PRODUCTS
        + " WHERE "
        + COLUMN_PRODUCTNAME
        + " = \""
        + productName
        + "\""
    ;
    Cursor cursor = db.rawQuery(query, null);
    
    if(cursor.moveToFirst()){
        String idStr = cursor.getString(0);
        db.delete(TABLE_PRODUCTS, COLUMN_ID + " = " + idStr, null);
        cursor.close();
        result = true;
    }
    db.close();
    return result;
}
```
@[1](Créez une méthode pour supprimer)
@[2](Obtenez une instance d'une DB)
@[4-11](Créer votre query)
@[12](Exécuter votre query)
@[14-19](Si l'objet existe, supprimer)
@[20](Fermer la connection à la DB)

---

## Dernière étape

```java
class ... {
    public static void main(String[] args) {
        
        MyDBHandler dbHandler = new MyDBHandler(this);
        
        // ...
        
        dbHandler.addProduct(product);
        
        // ...
        
        Product product = dbHandler.findProduct(productBox.getText().toString());
        
        // ...
        
        boolean result = dbHandler.deleteProduct(productBox.getText().toString());
    }
}
```