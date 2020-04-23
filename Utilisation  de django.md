# memory
## les premiers pas avec django 

django est le framework Web pourquoi les perfectionniste sous pression
django est basé sur le MVT qui est _model view template_ et le respect du MVT 

**django à une ORM**

**django à également ces parckag**

## mise en marche de django 

**créé un dossier**
**dans le dossier créé le venv avec la commande `python -m venv venv`**

**activé le venv avec la commande `source venv/bin/venv`**

**on installe django avec la commande `pip install django == 'version'`**

**créé avec la commande `django-admin startprojet nom de post`**

**on rentre dans le projet avec la commande `cd\nomDuProjet`**

**on lance avec  la commande `python manage.Py runserver`**

**coupe le lancement avec crl+c**

**pourquoi intégré `python manage.Py migrate`**

**s'enregistrer en t'en que super utilisateurs la commande ``python manage.py createsuperuser``**

**on lance la commande `python manage.py runserver`pour avoir lancé le serveur et avoir accès à à la partie admin**




## Django url 
 la liste `urlpatterns` qui permet de définir les associations entre URL et vues

Pour passer des arguments dans une URL, il faut capturer ces arguments directement depuis l’écriture de nos URL

**la fonction qui permet de générer le code**

`import random
    import string

    def generer(nb_caracteres):
        caracteres = string.ascii_letters + string.digits
        aleatoire = [random.choice(caracteres) for _ in range(nb_caracteres)]
        
        return ''.join(aleatoire)`  

## formulaire

Un formulaire est décrit par une classe héritant de `django.forms.Form`, où chaque attribut est un champ du formulaire défini par le type des données attendues.  

Chaque classe de `django.forms`  permet d’affiner les données attendues : taille maximale du contenu du champ, champ obligatoire ou optionnel, valeur par défaut…

Il est possible de récupérer un objet `Form` après la validation du formulaire et de vérifier si les données envoyées sont valides, via `form.is_valid()`.

La validation est personnalisable, grâce à la réécriture des méthodes `clean_NOM_DU_CHAMP()`  et `clean()`.

`form.save(commit=False)`  qui permet de ne pas sauvegarder directement l’article dans la base de données

Pour moins de redondances, la création de formulaires à partir de modèles existants se fait en héritant de la classe `ModelForm`, à partir de laquelle nous pouvons modifier les champs éditables et leurs comportements.

## La gestion des fichiers

Le stockage d’une image dans un objet en base se fait via un champ `models.ImageField`. Le stockage d’un fichier quelconque est similaire, avec `models.FileField`.

Les fichiers uploadés seront stockés dans le répertoire fourni par **MEDIA_ROOT**  dans votre *settings.py*.
