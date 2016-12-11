---
title: Jour 2 - Tab Finder (Guidé)
layout: exercise
---

# Tab Finder - Téléchargez vos tablatures en "un click"

### Consigne

L'idée de cet exercice est de créer un programme dans le terminal qui, prenant en input le nom d'un morceau de musique, nous créera un PDF avec la tablature (partition pour guitare) pour ce morceau.

Cela semble compliqué ? Ce programme ne nécessite qu'une **dizaine** de lignes relativement simples.

L'idée est la suivante:

```
- Demander à l'utilisateur le nom du morceau qui l'intéresse
- Faire une recherche sur un annuaire de tablatures afin de récupérer une liste de liens vers des tablatures
- Extraire un de ces liens vers une tablature et le suivre afin de récupérer le contenu de la page Web
- Extraire du contenu de la page, la tablature mais sans les menus, sidebar, publicités...
- Une fois ce résultat récupéré sous forme de String, et l'écrire dans un fichier PDF.
- Bien présenter le PDF (rajouter une police, un titre...)
- Afficher à l'utilisateur le nom du fichier PDF et que tout s'est bien passé.
```

### Procédure

#### Gems (Librairies)

Pour se faire, nous utiliserons deux **gems**, des librairies Ruby, dont nous parlerons plus extensivement dans deux jours.
En attendant, sachez qu'une librairie s'installe via le terminal, de la sorte :

```
$ gem install nom_de_ma_gem
```

Pour cet exercice, nous aurons besoin de deux gems: 

* **Nokogiri** - Qui nous permettra d'aller parser des pages web et en extraire de la donnée 
* **Prawn** - Une librairie de génération de PDF

Pour les installer, rien de plus simple :

```
$ gem install nokogiri
$ gem install prawn
```

Vous pouvez les utiliser ensuite dans votre fichier ruby de la sorte :

```ruby
# Nécessaire pour Nokogiri, permet d'aller récupérer une page web à une URL donnée
require 'open-uri'
# On charge le code de la librairie Nokogiri
require 'nokogiri'
# On charge le code de la librairie Prawn
require "prawn"

# ... Votre code ...

``` 

#### Récupérer la liste des tablatures d'un artiste

Nous irons chercher nos tablatures sur le site : `https://www.ultimate-guitar.com/`.
Leur page de recherche est la suivante : `https://www.ultimate-guitar.com/search.php`.

Cette page de recherche peut prendre des **paramètres d'URL**, qui sont ajoutés à la fin. Exemple: `?search_type=title&value=Smoke On the Water`

Une url complète pour faire une recherche sur le site Ultimate Guitar ressemble donc à cela :

```ruby
# On cherche ici la chanson "Smoke on the water" de Deep Purple
https://www.ultimate-guitar.com/search.php?search_type=title&value=Smoke on the water
```

Comme vous pouvez le voir, la partie qui nous intéresse est à la fin, après `value=`. C'est la partie dynamique de notre URL, qui change en fonction de la recherche. 

Après avoir demandé à l'utilisateur le nom du morceau recherché, nous l'insèrerons donc dans l'URL.


#### Ouvrir la page 

Une fois l'URL construite, nous voulons l'ouvrir, afin d'en récupérer le contenu (la liste des tablatures). C'est là qu'intervient `open-uri` :

```ruby
url = "https://www.ultimate-guitar.com/search.php?search_type=title&value=Smoke on the water"
page_content = open(url, { 'User-Agent' => 'Firefox' })
```

On appelle la méthode `open`, fournie par `open-uri`. Cette méthode, appelée sur une URL, se fait passer pour un navigateur Web et nous retourne le HTML de la page, dans une string.

#### Parser la liste

Maintenant que nous avons récupéré la liste des tablatures depuis le site, nous avons besoin d'extraire le lien vers **LA tablature qui nous intéresse**.
C'est là qu'intervient **nokogiri**.

```ruby
url = "https://www.ultimate-guitar.com/search.php?search_type=title&value=Smoke on the water"
page_content = open(url, { 'User-Agent' => 'Firefox' })

document = Nokogiri::HTML(page_content)
```

`Nokogiri` nous permet de parser le HTML afin d'en extraire les informations qui nous intéressent. C'est ce qu'on appelle du *scraping*.
En l'occurence, si vous ouvrez la page dans votre navigateur web, vous verrez une liste de tablature clickables. Notre but ici est de récupérer un de ces liens, pour l'ouvrir (encore une fois avec `open-uri`) et récupérer la tablature en elle-même.

```ruby
# Prend le premier lien de résultat et récupère l'attribut "href" (qui est le lien)
link = document.search('.result-link')[0].attr('href')

puts link # => https://tabs.ultimate-guitar.com/d/deep_purple/smoke_on_the_water_ver2_crd.htm
```

#### Ouvrir la page de la tablature

Cette fois encore, c'est la même chose, on utilise `open-uri` :

```ruby
tablature_page = open(link, { 'User-Agent' => 'Firefox' })
```

#### Parser la page de la tablature

Maintenant qu'on a récupéré le contenu de la page, on veut en extraire la tablature, sous forme de string, et sans toutes les données inutiles (barre de navigation du site, menus, etc...)

Encore une fois, c'est `Nokogiri` qui s'en charge:

```ruby
tab = tablature_page.search('.js-tab-content').text
```

Si vous affichiez `tab` maintenant, vous verriez la tablature du morceau choisi s'afficher, sous form de String ! C'est déjà une belle victoire !

#### Transformer une string en PDF

C'est là que `Prawn` intervient: 

```ruby
Prawn::Document.generate("mon_fichier.pdf") do |pdf|
  pdf.font('Courier') # Choix de la police
  pdf.text("Un titre pour mon PDF", { size: 22, align: :center })
  pdf.move_down(50)   # On se déplace de 50px vers le bas
  pdf.text(tab)       # On inscrit notre tablature dans le PDF
end
# Un fichier mon_fichier.pdf sera généré dans le même répertoire que votre fichier ruby.
```

Et voilà, c'est fini !

Bien entendu, nous n'avons pas couvert ici la partie *interface* où vous demandez à l'utilisateur (dans le terminal), quel morceau il recherche et vous lui affichez la progression de la recherche. 

A vous de jouer ;)


## .
## .
## .
## .
## .
## .

### Code final

[Solution de l'exercice](https://gist.github.com/gabriel-dehan/2d5c91f0fc8e9948b038)
