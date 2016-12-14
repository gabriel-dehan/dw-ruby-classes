
---
title: Jour 3 - L'oranger (Orienté Objet)
layout: exercise
---

## L'oranger

Aujourd'hui, un grand "classique" des exercices de Programmation Orientée Objet : l'Oranger.

L'idée de cet exercice est d'implémenter une classe `OrangeTree` qui représente un... Oranger et son cycle : sa naissance, sa vie et sa mort. Un exercice profond et philosophique si il en est.

```ruby
# orange_tree.rb
class OrangeTree
  # ...
end

tree = OrangeTree.new

# On fait passer 99 ans et grandir l'arbre en fonction
99.times do 
  tree.one_year_passes!
end

# On peut vérifier que l'arbre à bien grandi.
```

Pour simuler le passage du temps, on va créer une méthode qui fait passer **UN** an. Cette méthode doit être appelée 99 fois si on veut faire grandir notre arbre pendant 99 ans.

```ruby
def one_year_passes!
  # TODO: Vérifier que l'arbre est toujours vivant
  # TODO: Si il est vivant, ajouter un an à l'age de l'arbre
  # TODO: Si il est vivant le faire grandir
  # TODO: Si il est vivant, faire pousser des fruits cette année
end
```

## Consignes

- On doit pouvoir mesurer l'arbre (accéder à sa taille)
- On doit pouvoir savoir si l'arbre est vivant ou mort 
- Chaque année l'arbre doit grandir, devenir plus grand et plus vieux, et il doit mourir au bout d'un moment
- Un arbre grandi de 1 mètre par an jusqu'à ses 10 ans. Après il arrête de grandir.
- Jusqu'à ses 50 ans an, un arbre ne peut pas mourir:
- Après ses 50 ans, la probabilité qu'à l'arbre de mourir augmente d'année en année. 
- Si un arbre survi jusqu'à cent ans, il meurt le jour de ses 100 ans.
- A partir de ses 10 ans, un arbre produit des fruits : 200 fruits par ans.
- Un arbre arrête de produire des fruits à ses 25 ans.
- On doit pouvoir cueillir des fruits depuis l'arbre (1 par 1)
- On doit pouvoir compter le nombre de fruits restants sur l'arbre 
- Chaque année, les fruits non ramassés tombent

A partir de ces consignes, déterminez les variables d'instances nécessaires, quelles sont les méthodes, accesseurs (getters/setters).
Puis codez la classe et testez là.

Quelques exemples de tests que vous pouvez faire :

```ruby
5.times do 
  orange_tree.one_year_passes!
end

orange_tree.age    # => 5
orange_tree.height # => 5
orange_tree.alive? # => true

20.times do 
  orange_tree.one_year_passes!
end

orange_tree.age    # => 25
orange_tree.height # => 10
orange_tree.fruits # => 200

50.times do 
  orange_tree.one_year_passes!
end
orange_tree.age # => 75
orange_tree.alive ? # => false (peut-être encore vrai, c'est une probabilité)
```

```ruby
10.times do
  orange_tree.one_year_passes!
end

puts orange_tree.fruits # => 200

orange_tree.pick_a_fruit!
puts orange_tree.fruits # => 199
```

Etc...
