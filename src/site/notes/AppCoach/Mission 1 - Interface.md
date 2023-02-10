---
{"dg-home":false,"dg-publish":true,"permalink":"/app-coach/mission-1-interface/","dgPassFrontmatter":true}
---

# Présentation du projet


Le projet consiste à créer une **Application Android** qui permet de calculer l'**IMG**
(Indice de Masse Grasse) en fonction du **sexe**, de l'**âge**, du **poids** et de la **taille** de la personne.

Grâce à ce calcul, nous pouvons savoir le niveau de corpulence d'une personne (trop maigre, parfait et surpoids).


# Support


> Le support qu'on a utilisé pour l'application AppCoach c'est **Visual Studio 2019** et on utilisera Xamarin.


# Interface


## Présentation

La création de l'interface se fait via le fichier **activity_main.xml**. Celui-ci s'adapte à tous types d'appareils mobile que ça soit téléphone ou tablette.

![Interface AppCoach.png](data:image/png;base64,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mJiI1NRU/PnPf8add96Jiy66SJ4fCATg9XphtVrRoUMHdOjQAWPGjMGgQYOg0+lwySWXoF+/frj99tvlC2UDFVf/3717N7p27YpRo0ahuLgYWVlZePTRR9GpUydMmDABgiAgKysLv//+u/y6jRs3QqfTwel04tZbb8X06dORkpJS6/dHFAtxdVTI5/OhS5cuNV5e6iM5ePAgkpOToy7jcDgirgQnDRP3+Xy4//778eGHH8q365g9ezZsNhsOHTqEFi1aAIB8yFMyYcIErFixAsXFxTCbzQAqzrZ97rnnIrZz4MABAMCcOXOg0+nw4osvwul0QqVSYfbs2dDpdBgzZgx2796NQCCA6667Di+99BL++te/yus1m83YsGEDrr322hp/NkSxFFc1FgBnfSgRQNjh6Mq2bt2KLl26hD3ef/99AKevC9K7d2/k5uYiNzdXvpfPvffeW2WZpFGcUqhI0/x+f9hArso3IdNqtdBqtWF3BLBarfj5558BAOvXrwdQcc8iqTzSPairGndBFI/iqsYiCAL27t1bZWdsZdJV61u1alXlMtV13u7atQsA0LRp04h5e/bsqVEZJIIC1405fPgwAKB58+YR82J1/V2i2oirYBk3bhyWL18On88HrVZ7xuWlM1SragadiXQjsXi5rYbUtPN4PIoEFVGsxFVTqHPnzlCpVHjrrbfOuKzH48Enn3yC1q1b16r5BAB33XUXACAnJydsenl5ea3WV1dXX301gIqjY6F4KgOda+IqWARBwC233ILDhw9HHL4N5XA4MG/ePOj1etxxxx213l7nzp3RoUMHtG7dGuvXr8eBAweQnZ2NpKQkbN68udbrra2mTZuiT58+uPjii7FixQocOHAAn3zyCQwGA6/QT+eUuGoKAUDbtm1x4403YuXKlZgxYwauv/56dOzYESqVCh6PB2vWrMGvv/4KvV6vyHVP9+zZgzFjxmDMmDHweDyw2WxYtWrVWV+DVSlffvkl7rrrLtx5551wOp2wWCx49dVXw+4tTRTv4mrkbSifz4dnn30WDocjYt7QoUPRr18/9kMQxaG4G9JfFbvdDq/XC7PZzBMHieJc3N5XqDKbzRbrIhApoi6jxOOZdIRVck4EC9H54plnnol1EepF5evXMFiIGtCdd94Z6yI0CAYLUQOqbpT4+SSuxrEQ0fmBwUJEimOwEJHiGCxE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) 

## Structure de l'interface

- **3 LinearLayout vertical**

- Le **premier** est séparé en deux à gauche le **sexe** (2 RadioButton dans un RadioGroup) et à droite le **poids**, la **taille** et l'**âge** qui sont chacun dans des LinearLayout horizontal

- Le **deuxième** contient le bouton "CALCULER"

- Le **troisième** contient une ImageView et un TextView pour afficher le résultat et le smiley par rapport au résultat

## Code activity_main.xml

Le premier **LinearLayout** avec un **RadioGroup** contenant deux **RadioButton** pour prendre connaissance du sexe de la personne.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:minWidth="25px"
    android:minHeight="25px"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/relativeLayout1" >

    <LinearLayout
        android:orientation="vertical"
        android:minWidth="25px"
        android:minHeight="25px" 
        android:layout_width="match_parent"
        android:layout_height="match_parent" 
        android:id="@+id/linearLayout1">
        <LinearLayout
            android:orientation="horizontal"
            android:minWidth="25px"
            android:minHeight="25px"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="2"
            android:id="@+id/linearLayout2">
            <LinearLayout
                android:orientation="vertical"
                android:minWidth="25px"
                android:minHeight="25px"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:id="@+id/linearLayout7">
                <RadioGroup
                    android:minWidth="10px"
                    android:minHeight="10px"
                    android:layout_width="wrap_content"
                    android:layout_height="match_parent"
                    android:id="@+id/radioGroup1"
                    android:gravity="center"
                    android:layout_gravity="center_horizontal">
                    <RadioButton
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="Homme"
                        android:textSize="22sp"
                        android:id="@+id/rdHomme"
                        android:checked="true" />
                    <RadioButton
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="Femme"
                        android:textSize="22sp"
                        android:id="@+id/rdFemme" />
                </RadioGroup>
            </LinearLayout>
            <LinearLayout
            ...
```


# Structure du projet


Nous avons utilisé l'architecture **MVC** (Modèle Vue Contrôleur) pour structurer notre projet.

## Modèle

>Le modèle contient l'accès des données de la classe Profil qui initialise les variables pour créer le profil de l'utilisateur (sexe, poids, taille et âge).

#### Class Profil

On a créé la classe Profil contenant son constructeur et ses getters dans le dossier Modèle qui instancie les données définissant un profil.

````C#
public class Profil
    {
        private int p_sexe;
        private int p_poids;
        private int p_taille;
        private int p_age;
        private double p_indiceMG;
        private string p_message;

        public Profil(int poids, int taille, int age, int sexe) /// Constructeur
        {
            p_sexe = sexe;
            p_poids = poids;
            p_taille = taille;
            p_age = age;
            p_indiceMG = calculIMG();
            p_message = resultatIMG();
        }
        ...
        Les getters pour chaque variable saisie dans le constructeur
````

#### calculIMG()

Cette fonction permet de convertir la taille saisie en centimètre en mètre et de calculer IMG.

````C#
public double calculIMG()
    {
        double laTaille = (double) (p_taille) / 100; /// Convertion cm en m
        p_indiceMG = (double)((1.2 * p_poids / (laTaille * laTaille)) + (0.23 * p_age) - (10.83 * p_sexe) - 5.4); /// Calcul IMG
        
        return p_indiceMG; /// Retourne IMG de type double
    }
````

#### resultatIMG()

Cette fonction permet d'afficher le résultat en fonction du sexe de la personne.

````C#
public string resultatIMG()
        {
            
            if(p_sexe==0)
            {
                if(calculIMG() < 15)
                {
                    p_message = " Trop maigre !";
                }
                else if (calculIMG() > 30)
                {
                    p_message = " Surpoids !";
                }
                else
                {
                    p_message = " Parfait !";
                }
            }
            else
            {
                if (calculIMG() < 10)
                {
                    p_message = " Trop maigre !";
                }
                else if (calculIMG() > 25)
                {
                    p_message = " Surpoids !";
                }
                else
                {
                    p_message = " Parfait !";
                }
            }

            return p_message;
        }
````

## Contrôleur

>Le contrôleur permet de récupérer les données saisies par l'utilisateur, traiter les données, appeler des fonctions du modèle et appeler les vues pour l'affichage.

#### Class Controle

On a créé une classe **Controle** dans le dossier controleur, l'objectif est de créer une instance unique du **controleur** qui sera utilisé dans toutes les activités de l'application.

````C#
sealed class Controle
    {
        private static Controle instance = null;
        private static Profil profil;
        
        private Controle()
        {
        }
        
		public static Controle GetInstance()
        {
            if(Controle.instance == null)
            {
                Controle.instance = new Controle();
            }
            return Controle.instance;
        }
````

#### CreerProfil(), GetIMG() et GetMessage()

Puis on a créer une méthode nous permettant de créer un **nouveau profil** avec les informations qui proviennent de la **vue** (**poids**, **taille**, **âge** et le **sexe**). 

Et aussi deux méthodes publiques qui retourne l'**IMG** et affiche le **résultat**.

````C#

public void CreerProfil(int unPoids, int uneTaille, int unAge, int unSexe)
        {
            profil = new Profil(unPoids, uneTaille, unAge, unSexe);
        }

public double GetIMG()
{
    return profil.GetIndiceMG();
}

public string GetMessage()
{
    return profil.GetMessage();
} 
````


## Vue

> La vue permet d'afficher les données à l'utilisateur au l'occurence son IMG par rapport à son profil.

#### init()

Nous avons commencé par créer les **variables** qui va nous permettre de stocker les valeurs saisies par l'utilisateur puis on récupère les valeurs saisies dans la méthode **init()**.

````C#
private EditText txtAge;
private EditText txtPoids;
private EditText txtTaille;
private RadioButton rdHomme;
private RadioButton rdFemme;
private TextView lbIMG;
private ImageView imgSmiley;
private Button btCalculer;

private Controle controle;

private void init()
{
    this.controle = Controle.GetInstance();
    
	txtPoids = (EditText)FindViewById(Resource.Id.txtPoids);
    txtTaille = (EditText)FindViewById(Resource.Id.txtTaille);
    txtAge = (EditText)FindViewById(Resource.Id.txtAge);
    rdHomme = (RadioButton)FindViewById(Resource.Id.rdHomme);
    rdFemme = (RadioButton)FindViewById(Resource.Id.rdFemme);
    lbIMG = (TextView)FindViewById(Resource.Id.lbIMG);
    imgSmiley = (ImageView)FindViewById(Resource.Id.imgSmiley);

    btCalculer = (Button)FindViewById(Resource.Id.btCalculer);
    btCalculer.Click += btCalculer_Click;
}
````

#### btCalculer_Click()

Ensuite, on fera la méthode **btCalculer_Click()** qui va vérifier que les données sont correctes puis les tranmettre à la fonction **AfficherResultat()** et de définir certaines donnée comme le sexe (en vérifiant si la case homme est coché ou non).

````C#
private void btCalculer_Click(object sender, EventArgs e)
        {
            int poids = 0;
            int taille = 0;
            int age = 0;
            int sexe = 0;

            try
            {
                poids = int.Parse(txtPoids.Text);
                taille = int.Parse(txtTaille.Text);
                age = int.Parse(txtAge.Text);
            }
            catch(Exception ex)
            {
                Toast.MakeText(this, "Saisie incorrecte", ToastLength.Long).Show();
            }

            if (rdHomme.Checked)
            {
                sexe = 1;
            }

            if(poids==0 || taille==0 || age == 0)
            {
                Toast.MakeText(this, "Merci de remplir tous les champs", ToastLength.Long).Show();
            }
            else
            {
                AfficherResultat(poids, taille, age, sexe);
            }
        }
````

#### AfficherResultat()

La méthode **AfficherResultat()** permet de créer un profil, préparer un message et afficher le résultat sur l'écran principal de l'application avec la couleur correspondante.

````C#
private void AfficherResultat(int unPoids, int uneTaille, int unAge, int unSexe)
    {
	    this.controle.CreerProfil(unPoids, uneTaille, unAge, unSexe);
        double img = this.controle.GetIMG();
        string message = this.controle.GetMessage();

        if(message == " Parfait !")
        {
            imgSmiley.SetImageResource(Resource.Drawable.Smiley_Ok);
            lbIMG.SetTextColor(Android.Graphics.Color.DarkGreen);
        }
        else if(message == " Trop maigre !")
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
````



# Test Unitaire

> Un test unitaire sert à vérifier le bon fonctionnement d'un programme en attendant une valeur prédéfini et en vérifiant si la valeur renvoyé par le programme est la même.

#### TestIMG()

````C#
public void TestIMG()
    {
		// Profil : Homme parfait (M.Dubromelle)
		Profil unProfil1 = new Profil(62, 177, 28, 1);
		
		double resultatAttendu1 = 13.96;
		
		double resultatTest1 = unProfil1.calculIMG();
		
		Assert.AreEqual(resultatAttendu1, resultatTest1, delta: 0.1);
		
		
		//Profil : Femme parfaite (Ma femme)
		Profil unProfil4 = new Profil(75, 175, 19, 0);
		
		double resultatAttendu4 = 28.36;
		
		double resultatTest4 = unProfil4.calculIMG();
		
		Assert.AreEqual(resultatAttendu4, resultatTest4, delta: 0.1);
		...
````

Puis ainsi de suite pour les hommes ou femmes en surpoids ou trop maigre.

- **Assert** : vérifie que l’action réalisée par la méthode est conforme à l’attendu du test unitaire.
- **Act** : invoque la méthode à tester avec les paramètres.
- **Arrange** : d’une méthode de test unitaire initialise les objets et définit la valeur des données transmises à la méthode testée.
- **delta** : Sélectionner une marge d'erreur.

#### TestResultat()

On fait de même avec le message accompagnant le résultat.

````C#
public void TestResultat()
    {
        //Profil : Surpoids
        Profil unProfil = new Profil(96, 175, 19, 1);

        string resultatAttendu = " Surpoids !";

        string resultatTest = unProfil.resultatIMG();

        Assert.AreEqual(resultatAttendu, resultatTest);


        //Profil : Parfait
        Profil unProfil1 = new Profil(62, 175, 19, 1);

        string resultatAttendu1 = " Parfait !";

        string resultatTest1 = unProfil1.resultatIMG();

        Assert.AreEqual(resultatAttendu1, resultatTest1);


        //Profil : Trop maigre
        Profil unProfil2 = new Profil(40, 175, 19, 0);

        string resultatAttendu2 = " Trop maigre !";

        string resultatTest2 = unProfil2.resultatIMG();

        Assert.AreEqual(resultatAttendu2, resultatTest2);
    }
````

