# Yaml to JSON

## Contexte

Pour poursuivre sur l'excellent kata de William, voici quelques variations sur le même thème, à savoir travailler avec des fichiers `yaml` pour les lire et travailler dessus, avec de la récursivité. 
Comme d'habitude ~si vous même ou un membre de votre équipe était pris~, c'est une invitation à faire du TDD et à écrire des tests !


Donc vous avez toujours des fichiers `yaml`, un par 'locale':
```yaml
# en.yaml
en:
  admin:
    create:
      success: 'admin successfully created'
      failure: 'failure to create the admin'
  project:
    create:
    change_amount:
      success: 'the amount of your project has been modified'

# fr.yaml
fr:
  admin:
    create:
      success: 'administrateur créé avec succès'
      failure: 'administrateur n\'a pas pu être créé'
  project:
    create:
    change_amount:
      success: 'le montant de votre projet a été modifié'
  user:
    notify:
      account_changed: 'votre compte a bien été modifié'
```

## Echauffement
Créer une méthode pour lire chaque fichier et le stocker dans un `Hash`.

:cactus : Pour pimenter, utilisez la méthode `each_with_object` avec un tableau vide en argument pour lire tous les fichiers présents dans un répertoire et stocker le tout dans un `Array` de `Hash`.

Comme d'habitude, ~~si vous-même ou un membre de votre équipe était capturé, le Département d'Etat nierait toute implication~~ 

ça serait une bonne idée

de faire du TDD (et ça rime en plus, on vous gâte trop)

Créer une seconde méthode qui prend un `Hash` en entrée et retourne la clé 'langue', ici `fr` et `en` pour ceux qui ne suivent pas !

## Premier kata (l'apéro)

Vous allez écrire une méthode qui prend en entrée un `Hash` et renvoie un `Array` contenant toutes les clés de manière unique, du genre pour l'exemple:

```ruby  
["fr", "admin", "create", "success", "failure", "project", "change_amount", "user", "notify", "account_changed"]
```
:cactus: pour pimenter un peu et pour ceux qui le veulent, puisqu'on veut les clés autant itérer sur les valeurs pour être logique (!), avec une ligne du genre (hash étant l'argument de la méthode)

```ruby  
hash.values.each do |key, value|
```
## Second kata (le hors d'oeuvre)

Vous allez écrire une méthode qui prend en entrée un `Hash` et retourne un `Array` contenant toutes les 'valeurs' de manière unique, `nil` compris si c'est une des valeurs, du genre pour l'exemple avec `fr`:

```ruby 
["administrateur créé avec succès", "administrateur n'a pas pu être créé", nil, "le montant de votre projet a été modifié", "votre compte a bien été modifié"]
```

## Troisième Kata (le plat principal)

Vous allez écrire une méthode qui prend (au moins) en entrée une chaîne de caractères comme celles du résultat ci-dessus, par exemple
"votre compte a bien été modifié" et renvoie le 'chemin', l'enchaînement de clés menant à cette valeur, ici fr ->user->notify->account_changed, sous la forme que vous voulez: un tableau de chaînes ou de symboles, une chaîne unique avec les clés concaténées, une liste chaînée, une file FIFO, une pile LIFO, ou que sais-je encore, c'est vous qui voyez ! 

Vous pouvez aussi passé le Hash en paramètre si vous voulez.

## ou (menu au choix!)
Et si vous n'y arrivez pas, ou si vous avez déjà fini et encore fain de Ruby, voici un autre exercice du même genre: écrivez une méthode nommée deep_invert qui fait pareil que `Hash#invert` mais récursivement, pour inverser entièrement un hash, un peu comme le deep_merge, nommé dans les tips ci-dessous, le fait pour le `Hash#merge`

## quatrième kata (le dessert)

Maintenant, vous devriez être plus à l'aise pour reprendre l'excellent Kata de William [yaml_to_json](https://github.com/williampollet/yaml_to_json_kata)

## cinquième Kata (le café et l'addition !)

Vous allez manger de la pizza tout en buvant des boissons, vous l'avez bien mérité, et William et moi aussi :-)


## Tips

Comme je suis un feignant, j'ai repris la partie tips du sujet de William, surtout qu'elle est bien faite !

Sans même la traduire, un feignant je vous dis ;-)

This section is optional. It presents several technical functions that will help you through the exercise.

<details>

* you can use `hash.dig('key1', 'key2', 'key3')` to dig quickly into a deep hash. [ref](https://ruby-doc.org/core-2.3.0_preview1/Hash.html#method-i-dig)
* the function `hash1.deep_merge(hash2)` will allow you to merge two deep hashes without overriding the former value [ref](https://apidock.com/rails/Hash/deep_merge). As this is a rails function, to have it work you must monkey-patch `Hash` with the code [here](https://github.com/casunlight/rails/blob/master/activesupport/lib/active_support/core_ext/hash/deep_merge.rb)
* the iterator `inject({})` will allow you to iterate over an array and inject the values you want in a resulting hash [ref](https://apidock.com/ruby/Enumerable/inject)
* the function `YAML.load_file('path/to/file')` will allow you to load the content of a yaml file and return it in a corresponding hash [ref](https://apidock.com/ruby/YAML/load_file/class)

</details>

## Help

This section is optional. It will help you get through the exercise by giving you general advices and directions. :warning: It contains spoils regarding a technique to get trough. Unfurl at your own risks ! :warning:

<details>

General advices on the approach:
<details>
If you don't know how to begin, consider doing the exercise step by step:

* first create a small function capable of migrating a simple key, for a simple hash
* then you can create a function capable of migrating several nested keys, for a more complex hash
* then you can create a function capable of migrating a full file
* then you can create a function capable of migrating several files (for several languages)

</details>

Algorithms tips:
<details>
 You are stuck and you would like a tip on the algorithm to implement? A recursive strategy can help. Any other approach is welcome though
</details>
</details>

## Credits

* Thanks to [William](https://github.com/williampollet/yaml_to_json_kata) pour l'idée originelle et originale, et pour son aide en tant qu'orga !
* Thanks to [LaLibertad](https://github.com/lalibertad) for providing the translations [test set](https://github.com/lalibertad/consul/tree/master/config/locales)
* Thanks to [sunny](https://github.com/sunny) for the design of the flat translation format
