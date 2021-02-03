# memory
## les premiers pas avec django 

django est le framework Web pourquoi ddes perfectionniste sous pression
django est basé sur le MVT qui est _model view template_ et le respect sa structure 

**django à une ORM pour « `object-relationnal mapping` »**

**django à également ces parckag**

## mise en marche de django 

**créé un dossier**
**dans le dossier créé le venv avec la commande `python -m venv venv`**

**activé le venv avec la commande `source venv/bin/venv`**

**on installe django avec la commande `pip install django == 'version'`**

**créé avec la commande `django-admin startprojet nom du projet`**
**créé une application django avec `django-admin startapp`**

**on rentre dans le projet avec la commande `cd\nomDuProjet`**

**on lance avec  la commande `python manage.Py runserver`**

**coupe le lancement avec crl+c**

**pour intégré `python manage.Py migrate`** 
**génerer une une nouvelle migration avec `manage.py makemigration`**

**s'enregistrer en t'en que super utilisateurs la commande ``python manage.py createsuperuser``**

**on lance la commande `python manage.py runserver`pour avoir lancé le serveur et avoir accès à à la partie admin**

### trois maniere de  transmetre des information 
A l'interieure de l'URL
A l'intérieure de la requêt Get (parametre)
Dans le corps d'une réquête Post

## Django url 
**.**la liste `urlpatterns` qui permet de définir les associations entre URL et vues

**.**Pour passer des arguments dans une URL, il faut capturer ces arguments directement depuis l’écriture de nos URL

### la fonction qui permet de générer le code
   

    import random
        import string

        def generer(nb_caracteres):
            caracteres = string.ascii_letters + string.digits
            aleatoire = [random.choice(caracteres) for _ in range(nb_caracteres)]
            
            return ''.join(aleatoire)

## templates
    Il est possible de factoriser des blocs HTML (comme le début et la fin d’une page) via l’utilisation des tags {% block %}  et {% extends %}

    L’ajout de fichiers statiques dans notre template (images, CSS, JavaScript) peut se faire via l’utilisation du tag {% static %}

    Les templates sont écrits dans un mini-langage de programmation propre à Django qui possède des expressions et des structures de contrôle basiques (if/else, boucle for, etc.) Appeler tag

        def tpl(request, sexe):
            html = "Bonjour "
            if sexe == "Femme":
                html += "Madame"
            else:
                html += "Monsieur"
            html += " !"
            return HttpResponse(html)
    
    il existe une troisième directive qui peut être associée au {% for %}, il s’agit de {% empty %}. Elle permet d’afficher un message par défaut si la liste parcourue est vide

    Les filtres permettent de modifier l’affichage en fonction d’une variable, sans passer par la vue
    `{{ texte|truncatewords:80 }}`
    il existe des dizaines de filtres par défaut :  date, safe, length, etc.
      
**NB**
    la manipulation de données doit être faite au  maximum dans les vues    
**liaison template et views**
    user<=>serveur<=>controleur<=>views<=>(model ou template)
    
**code de pagination**

`https://simpleisbetterthancomplex.com/tutorial/2016/08/03/how-to-paginate-with-django.html`
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

## Models
Sont des interfaces permettant plus simplement d’accéder à des données dans une base de données et de les mettre à jour
**Cherche dans une base de données les items correspondant a une réquête**
**renvoie une reponce intélligible par le reste du programe**
**Pour que Django crée la table SQL associée au modèle, il faut lancer la commande `makemigrations` via l’utilitaire `manage.py`**
**il s'apuit sur un ORM**
## schemat d'un ORM
réquête python **->** réquête SQL **->**intérrogation de la base de données **->**reponse SQL **->** reponse python.  
## la vue
**reçoit une requête HTTP**
**renvoie une reponse intelligente par le navigateur**
**.** Si la requête a besoin d'une information de la base de données, la vue fera appel au modele pour interroger la base
**.** Si la vue  a besoin un template, elle fera appel au template pour génerer la réponse
## Different type de views

## schemat MVT (protocol HTTP)
 requêt HTTP **->** URL.py **->** views.py **->** ORM **->** views **->** gabarit **->** HTTP

## requet orm

    article_recent = models.Article.objects.all().order_by('-date_add')[:3] # récupération des trois articles les plus récente
    article_vue = models.Article.objects.order_by('-vue')[:3] # récupération des trois articles les plus vue
    categorie = models.Categorie.objects.filter(status=True) # récuperation des categorie avec status True
    article_v = models.Article.objects.exclude(video=None) # récupération des articles ayant des vidéo
    article_r = models.Article.objects.order_by('-date_add')[:1]
    site_info = about_model.SiteInfo.objects.filter(status=True)[:1].get() # permet de recuperer les infos
    print(request.user)
