# Insérer et sauvegarder des données

Réfléchissons un instant à notre objectif pour le programme. Nous voulons lire l'argument fourni par l'utilisateur, mettre à jour notre todo list, et la stocker quelque part pour l'utilisation.

Pour faire cela, nous devons implémenter notre propre type pour lequel nous pouvons définir une méthode pour répondre à nos besoins.

Nous allons utiliser les [`struct`](https://doc.rust-lang.org/std/keyword.struct.html) de Rust, ce qui nous permettra de faire les deux de manière clean. Cela évite d'avoir à écire tout le code à l'intérieur de la fonction `main`.

## Comment définir notre structure

Notre fichier devrait ressembler à ceci:

```rust
use std::collections::HashMap;

fn main() {
    let action = std::env::args().nth(1).expect("Please specify an action");
    let item = std::env::args().nth(2).expect("Please specify an item");

    println!("{:?}, {:?}", action, item);
}

struct Todo {
    // use rust built-in HashMap to store key - val pairs
    map: HashMap<String, bool>,
}
```

Nous ajoutons ici deux éléments:

`use std::collections::HashMap;`

Etant donné que nous taperons beaucoup HashMap dans les étapes suivantes, nous pouvons l'amener dans la portée et nous éviter de le retaper. Ceci va nous permettre d'utiliser `HashMap` directement sans devoir taper le chemin complet à chaque fois.

```rust,ignore
struct Todo {
    map: HashMap<String, bool>,
}
```

Cela va définir notre type personnalisé `Todo`: une structure avec un seul champ nommé `map`. Ce champ est un [HashMap](https://doc.rust-lang.org/std/collections/struct.HashMap.html). Vous pouvez le considérer comme une sorte d'objet JavaScript, où Rust nous oblige à déclarer les types de clé et de valeur.

## Ajouter des méthodes à notre structure

Les [méthodes](https://doc.rust-lang.org/rust-by-example/fn/methods.html) sont comme des [fonctions](https://doc.rust-lang.org/rust-by-example/fn.html) régulières, elles sont déclarées avec le mot clé `fn, elles acceptent des paramètres et ont une [valeur de retour](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html#functions-with-return-values).

Toutefois, elles différent des fonctions régulières dans le sens où elles sont défnies dans le contexte d'une structure et leurs premiers paramètres sont *toujours* `self`.

Nous allons définir un bloc [`impl`](https://doc.rust-lang.org/std/keyword.impl.html) en dessous de notre structure.

```rust, ignore
impl Todo {
    fn insert(&mut self, key: String) {
        // insert a new item into our map
        // we passe true as value
        self.map.insert(key, true);
    }
}
```

Cette fonction est assez simple: elle prend seulement une *référence* à la structure et une clé et l'insére dans votre map en utilisant la fonction intégrée [`insert`](https://doc.rust-lang.org/std/collections/struct.HashMap.html#method.insert) de HashMap.

Deux informations très importantes:

* [`mut`](https://doc.rust-lang.org/std/keyword.mut.html) rend une variable mutable. En Rust chaque variable est *immuable* par défaut. Si vous voulez mettre à jour votre valeur, vous devez activer sa mutabilité en utilisant le mot-clé `mut`.
    * Etant donné qu'avec notre fonction, nous modifions effectivmeent notre map en ajoutant une nouvelle valeur, nous avons besoin qu'elle soit déclarée mutable.
* [`&`](https://doc.rust-lang.org/std/primitive.reference.html) indique une *référence*. Vous pouvez imaginer que la variable a un pointeur vers un emplacement de la mémoire où la valeur est stockée, à la pace d'être la valeur elle-même.

Dans les termes Rust, il s'agit d'un [*borrow*](https://doc.rust-lang.org/rust-by-example/scope/borrow.html) (emprunt en français), signalant que la fonction ne posséde actuellement pas la valeur, mais pointe simplement vers l'emplacement où elle est stockée.
