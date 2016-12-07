---
title: Jour 1 - Méthodes & Opérations sur les données
layout: exercise
---

# Explorer la documentation

## Consigne

Il s'agit dans cet exercice d'aller explorer la documentation de Ruby: https://ruby-doc.org/core-2.3.3/, et de trouver la bonne méthode (fonction) à utiliser pour retourner le résultat attendu. Attention, le code de la méthode ne doit pas dépasser **une** ligne.

N'hésitez pas à utiliser **IRB** !

```ruby
def clean_whitespaces(text)
  # TODO: Retournez une copie de la chaîne de caractère passée en argument (`text`) en retirant les espaces avant et après.
  # Exemple d'appel: clean_whitespaces("  hey yo  ") => "hey yo"
end

def is_in?(sentence, word)
  # TODO: Retournez true si `sentence` contient `word`
  # Exemple d'appel: is_in?("hey jude", "jude") => true
  # Exemple d'appel: is_in?("hey jude", "daniel") => false
end

def replace(string, character, replacement)
  # TODO: Retournez une cope de la chaîne `string` avec `character` remplacé par `replacement`
  # Example d'appel: replace("casanova", "a", "o") => "cosonovo"
end

def divisible_by_two?(number)
  # TODO: Retournez true si `number` est divisible par 2
  # Exemple d'appel: divisible_by_two?(6) => true
end

def randomize(array)
  # TODO: Retournez `array` mélangé.
  # Exemple d'appel: randomize([1, 2, 3, 4]) => [2, 1, 4, 3]
end

def random_subset(array, count)
  # TODO: Retournez un morceau de `array` mélangé. La taille du tableau retourné doit être de `count` élements.
  # Exemple d'appel: random_subset(('a'..'z').to_a, 4) => ["u", "q", "l", "t"]
end

def ascending_order(array)
  # TODO: Retournez une copie du tableau `array` trié par ordre ascendant.
  # Exemple d'appel: ascending_order([5, 3, 1, 6, 9]) => [1, 3, 5, 7, 9]
end
```
