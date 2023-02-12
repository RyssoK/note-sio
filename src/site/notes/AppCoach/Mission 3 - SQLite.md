---
{"dg-home":false,"dg-publish":true,"permalink":"/app-coach/mission-3-sq-lite/","dgPassFrontmatter":true}
---


# Présentation de la mission

Pour cette mission nous devions réaliser une **base de données SQLite**, une petite base de données en **local** sur notre appareil. Pour se faire nous n'avons plus besoin d'utiliser la sérialisation, les données des profils seront enregistrées dans la **base de données local**.

# Modifications des classes

## Class Profil

Pour faire un suivi des données des profils, nous devons créer une nouvelle variable **dateMesure** de type **DateTime** qui servira de clé primaire.

```C#
public class Profil
    {
        private DateTime dateMesure;
        ...
```

Nous devons créer le getter pour avoir accès à cet attribut dans les autres classes.

```C#
public DateTime GetDateMesure()
    {
        return dateMesure;
    }
```

Modification de la méthode **CreerProfil()** de la classe contrôle pour rajouter la date au moment où l'utilisateur entre son profil.

```C#

public void CreerProfil(int unPoids, int uneTaille, int unAge, int unSexe)
{
    profil = new Profil(DateTime.Now, unPoids, uneTaille, unAge, unSexe);
}
```

# Implémentation de l'accès à la base

## Class MySQLiteHelper

Pour se faire nous devions créer une classe _MySQLiteOpenHelper_ qui hérite de la classe _SQLiteOpenHelper_ dans le dossier outils.

> L’héritage est une fonctionnalité des langages de programmation orientés objet qui permet de définir une classe de base qui fournit des fonctionnalités spécifiques.

Pour se faire nous devions utiliser la syntaxe suivante :

```C#
class MySQLiteOpenHelper : SQLiteOpenHelper
    {
    }
```

Pour que le constructeur ainsi que certaines méthodes abstraites soient implémentés, il suffit de faire **alt+entrée** et sélectionner ce que nous voulons implémenter.

> Sans oublier de rajouter le **using Android.Database.Sqlite** pour avoir la bibliothèque SQLite.

```C#
public MySQLiteOpenHelper(Context context, string name, SQLiteDatabase.ICursorFactory factory, int version) : base(context, name, factory, version)
        {
        }
        public override void OnCreate(SQLiteDatabase db)
        {

            try
            {
                db.ExecSQL(creation);
            }
            catch
            {
                throw new NotImplementedException();
            }
        }

        public override void OnUpgrade(SQLiteDatabase db, int oldVersion, int newVersion)
        {
            throw new NotImplementedException();
        }
    }
```

**OnCreate()** nous permet de créer notre première base de données grâce à la requête SQL de la création d'une table ci-dessous.

```C#
private string creation = "CREATE TABLE profil (" +
            "dateMesure TEXT PRIMARY KEY," +
            "poids INTEGER NOT NULL," +
            "taille INTEGER NOT NULL," +
            "age INTEGER NOT NULL," +
            "sexe INTEGER NOT NULL);";
```

# Class AccesLocal

Cette classe permet d'**enregistrer les données de l'utilisateur** et de **récupérer le dernier profil saisi**. 

Mais pour cela nous avons besoin de rajouter les propriétés suivante :

```C#
private string nomBase = "bdCoach.sqlite";
private int versionbase = 1; //Version de SQLite
private MySQLiteOpenHelper accesDB;
private SQLiteDatabase db;

public AccesLocal(Context contexte)
{
    accesDB = new MySQLiteOpenHelper(contexte, nomBase, null, versionbase);
}
```

> La propriété **db** permet de créer des canaux pour lire ou écrire dans la base données.  
> Le constructeur **AccesLocal()** va créer l'accès à la base de données.

Pour ajouter des données dans la base, il faut créer la méthode **Ajout()** permettant d'ajouter les données dans la bases :

```C#
public void Ajout(Profil unProfil)
{
    db = accesBD.WritableDatabase;
    string req = "INSERT INTO Profil (dateMesure, poids, taille, age, sexe) VALUES ";
    req += "(\"" + unProfil.GetDateMesure() + "\"," + unProfil.GetPoids();
    req += "," + unProfil.GetTaille() + "," + unProfil.GetAge();
    req += "," + unProfil.GetSexe() + ")";
    db.ExecSQL(req);
}
```

Pour avoir le **dernier profil** rentré par l'utilisateur lorsque nous revenions sur l'application, nous devons avoir la méthode suivante :

```c
public Profil RecupDernierProfil()
        {
            db = accesDB.ReadableDatabase;
            Profil profil = null;
            string req = "select * from profil";
            SQLiteCursor curseur = (SQLiteCursor)db.RawQuery(req, null);
            curseur.MoveToLast();
            if (!curseur.IsAfterLast)
            {
                DateTime date = new DateTime();
                int poids = curseur.GetInt(1);
                int taille = curseur.GetInt(2);
                int age = curseur.GetInt(3);
                int sexe = curseur.GetInt(4);

                profil = new Profil(date, poids, taille, age, sexe);
            }

            curseur.Close();
            return profil;
        }
```

> Il ne faut pas oublier de faire appel aux méthodes dans la classe contrôle.

Cette méthode utilise un **curseur** pour pouvoir parcourir le résultat de la requête et atteindre le dernier résultat.
