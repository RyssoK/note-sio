---
{"dg-home":false,"dg-publish":true,"permalink":"/app-coach/mission-2-serialisation/","dgPassFrontmatter":true}
---


# Présentation de la mission

Pour cette mission nous devions **sérialiser** les données de l'application. La sérialisation consiste à convertir un objet en flux d’octets pour **stocker l’objet** (l'enregistrement des données).  
Puis nous devions **désérialiser** les données. La désérialisation consiste à **charger les données** qui ont été sérialiser.

# Class Serializer

Pour sérialiser nos données nous allons crées une **classe abstraite Sérialiser** dans un dossier outils.

> Une classe abstraite est une classe qui n'est pas instanciable c'est à dire qu'on ne peut pas utiliser un _new_ pour créer un nouvel objet.

#### serialize()

````C#
abstract class Serializer
    {
        public static void serialize(string nomFichier, Object objet)
        {
            string fichier = Path.Combine(System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData), nomFichier);

            if (File.Exists(fichier))
            {
                File.Delete(fichier);
            }

            FileStream fluxCreate = new FileStream(fichier, FileMode.Create, FileAccess.Write);

            BinaryFormatter bf = new BinaryFormatter();

            try
            {
                bf.Serialize(fluxCreate, objet);
                fluxCreate.Close();
            }
            catch (Exception ex)
            {
            }
        }
````

#### deserialize()

Ensuite, nous devions créer une méthode pour la désérialisation.

````C#
public static Object deserialize(string nomFichier)
    {
        Object objet = null;
        string fichier = Path.Combine(System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData), nomFichier);

        if (File.Exists(fichier))
        {
            FileStream flux = new FileStream(fichier, FileMode.Open);

            BinaryFormatter bfr = new BinaryFormatter();

            try
            {
                objet = bfr.Deserialize(flux);
                flux.Close();
            }
            catch (Exception ex)
            {
            }
        }
        return objet;
    }
````


# Modifications des autres classes

Pour qu'on puisse effectuer la sérialisation, nous devons faire quelques modifications dans les autres classes.

## Class Profil

Tous d'abord, nous allons permettre à l'objet Profil d'être sérialisable.

````C#
	[Serializable]
    public class Profil
    {
	    ...
	}
````

## Class Controle

Dans la classe Controle, il faut créé une propriété statique pour stocker le nom du fichier à utiliser pour la sérialisation.

````C#
private static string monFichier = "saveprofil";
````

> Une propriété statique est une propriété que nous pouvions pas instancier.

Nous pouvons maintenant procéder à la sérialisation dans la méthode **CreerProfil()** toujours de la classe Controle.

```C#
public void CreerProfil(int unPoids, int uneTaille, int unAge, int unSexe)
    {
        profil = new Profil(unPoids, uneTaille, unAge, unSexe);
        Serializer.serialize(nomFichier, profil);
    }
```

Pour récupérer les données, nous allons créer une méthode statique **RecupSerialize()**, toujours dans la classe Controle.

```C#
private static void RecupSerialize()
    {
        profil = (Profil)Serializer.deserialize(nomFichier);
    }
```

Maintenant, il faut qu'on appelle cette méthode **dès le départ de l'application** c'est-à-dire au moment de la **création d'une instance** de la classe Controle.

```C#
public static Controle GetInstance()
    {
        if(Controle.instance == null)
        {
            Controle.instance = new Controle();
            RecupSerialize();
        }
        return Controle.instance;
    }
```

L'étape suivante consiste à permettre à la vue **(MainActivity)** de récupérer les données. Donc, nous allons créer des getters dans la classe Controle.

```C#
	public int GetPoids()
    {
        if (profil == null)
        {
            return 0;
        }
        else
        {
            return profil.GetPoids();
        }
    }

    public int GetTaille()
    {
        if (profil == null)
        {
            return 0;
        }
        else
       {
            return profil.GetTaille();
       }
    }

    public int GetAge()
    {
        if (profil == null)
        {
            return 0;
        }
        else
        {
            return profil.GetAge();
        }
    }

    public int GetSexe()
    {
        if (profil == null)
        {
            return 0;
        }
        else
        {
            return profil.GetSexe();
        }
    }
```

## Class MainActivity

Nous allons créer une méthode privée **RecupProfil()** dont le rôle est de valoriser les éléments affichés grâce aux données récupérées dans le contrôleur.

```C#
	private void RecupProfil()
	    {
            if(controle.GetPoids() != 0)
            {
                txtPoids.Text = controle.GetPoids().ToString();
                txtTaille.Text = controle.GetTaille().ToString();
                txtAge.Text = controle.GetAge().ToString();

                rdFemme.Checked = true;
                if(controle.GetSexe() == 1)
                {
                    rdHomme.Checked = true;
                }

                double img = this.controle.GetIMG();
                string message = this.controle.GetMessage();

                if (message == " Parfait !")
                {
                    imgSmiley.SetImageResource(Resource.Drawable.Smiley_Ok);
                    lbIMG.SetTextColor(Android.Graphics.Color.DarkGreen);
                }
                else if (message == " Trop maigre !")
                {
                    imgSmiley.SetImageResource(Resource.Drawable.Smiley_PasTop);
                    lbIMG.SetTextColor(Android.Graphics.Color.DarkRed);
                }
                else
                {
                    imgSmiley.SetImageResource(Resource.Drawable.Smiley_No);
                    lbIMG.SetTextColor(Android.Graphics.Color.DarkRed);
                }
                lbIMG.Text = String.Format("{0:0.00}", img) + "% " + message;
            }
        }
```

Pour finir, nous devons juste utiliser la fonction précédente à la fin dans la méthode **init()**.

```C#
private void init()
    {
	    ...
		
		RecupProfil(); // Récupère les données sauvegardées
	}
```