---
title: Jour 1 - HTML Compiler (Basic)
layout: exercise
---

# HTML Compiler (Basic)

Le but de cet exercice est de créer une méthode nous permettant de générer du HTML à partir de code écrit en Ruby.

## Consigne

Un exemple vaut milles mots:

```ruby
tag('h1', "Ruby", 'titre')
# => <h1 id="titre">Ruby</h1>

tag('p', "Ce paragraphe contient du texte", 'paragraph')
# => <p id="paragraph">Ce paragraphe contient du texte</p>
```

Vous devez donc coder une méthode `tag` qui aura la signature suivante:

```ruby
tag(tag_name, content, id)
```

- `tag_name` est une **string**
- `content` est une **string**
- `id` est une **string**

## Resources & Tips

* **Utilisez IRB pour tester votre code**
* Utilisez l'interpolation plutôt que la concaténation pour générer votre `String` !

