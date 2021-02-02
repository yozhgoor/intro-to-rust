# Lire depuis un fichier

Pour le moment, notre programme a un défaut fondamental: chaque fois que nous utilisons "add" on écrase `map` au lieu de le mettre à jour. C'est à cause du fait que nous créons un nouveau `map` vide chaque fois qu'on lance le programme. Règlons cela.

## Ajouter une nouvelle fonction dans TODO

Nous allons implémenter une nouvelle fonction pour notre structure Todo. Une fois appelée, elle va lire le contenu de notre fichier et nous rendre notre Todo peuplé avec nos valeurs précédemment stockées. Notez que ce n'est pas une méthode parce qu'elle ne prend pas `self` comme premier argument.

Nous voulons l'appeler `new`, c'est une convention Rust (comme `HashMap::new()` utilisé auparavant).

Ajoutons le code suivant à l'intérieur de notre bloc `impl`:

```rust,ignore
use std::{collections::Hashmap, io::Read, str::FromStr};

//main function

impl Todo {
    fn new() -> Result<Todo, std::io::Error> {
        let mut f = std::fs::OpenOptions::new()
            .write(true)
            .create(true)
            .read(true)
            .open("db.txt")?;
        let mut content = String::new();
        f.read_to_string(&mut content)?;
        let map: HashMap<String, bool> = content
            .lines()
            .map(|line| line.splitn(2, '\t').collect::<Vec<&str>>())
            .map(|v| (v[0], v[1]))
            .map(|(k, v| (String::from(k), bool::from_str(v).unwrap()))
            .collect();
        Ok(Todo { map })
    }
// ...rest of the methods
}
```

Pas de soucis si cela semble un peu acablant. Nous utilisons un style de programmation plus [fonctionnel](https://en.wikipedia.org/wiki/Functional_programming), principalement pour mettre en valeur et introduire le fait que Rust prend en charge plusieurs [paradigmes](https://en.wikipedia.org/wiki/Programming_paradigm) trouvé dans d'autres langages comme les itérateurs, closures et fonctions lambda.

Voyons ce qu'il se passe ici:

`use std::{collections::Hashmap, io::Read, str::FromStr};`

On va ajouter `use std::io::Read;` et `std::str::FromStr` au début du fichier près de l'autre instruction `use` pour pouvoir utiliser les méthodes `read_to_string` et `from_str` (qui sont expliquées plus bas). Vu que tout les modules viennent de `std`, on peut les grouper dans un bloc avec `{}`.

`fn_new() -> Result<Todo, std::io::Error> {`

Nous avons défini une fonction `new` qui renvoie un Result qui sera soit un struct `Todo`ou un `io::Error`.

```rust,ignore
let mut f = std::fs::OpenOptions::new()
    .write(true)
    .create(true)
    .read(true)
    .open("db.txt")?;
```

Nous avons configuré comment ouvrir le fichier `db.txt` en définissant plusieurs [OpenOptions](https://doc.rust-lang.org/std/fs/struct.OpenOptions.html). Le plus notable est le [flag](https://doc.rust-lang.org/std/fs/struct.OpenOptions.html#method.create) `create(true)` qui va créer le fichier si il n'est pas déjà présent.

`f.read_to_string(&mut content)?;`

cette méthode va lire tout les bytes dans le fichier et les ajoute dans la String `content`. Cette méthode à été importé avec sa déclaration `use` au début du fichier.

`let map: HashMap<String, bool> = content`

Nous devons convertir depuis le type String du fichier vers un HashMap. Nous le faisons en liant une variable `map`. C'est une des occassions où le compilateur a du mal à inférer le type pour nous, donc on le déclare par nous-même.

`.lines()`

[`lines`](https://doc.rust-lang.org/std/primitive.str.html#method.lines) crée un [itérateur](https://doc.rust-lang.org/book/ch13-02-iterators.html) sur chaque ligne d'une `String`, ce qui signife que nous allons maintenant itérer sur chaque entrée de notre fichier, puisque nous l'avons formaté avec "/n" à la fin de chaque entrée.

`.map(|line| line.splitn(2, '\t').collect::<Vec<&str>>())`

[`map`](https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.map) prends une [closure](https://doc.rust-lang.org/book/ch13-01-closures.html) `(|line|)` et l'appelle sur chaque élément de l'itérateur, [`lines.splitn(2, '\t')`](https://doc.rust-lang.org/std/primitive.str.html#method.splitn) divisera nos lignes sur le caractère tab (`\t`).

Et enfin [`colllect::<Vec<&str>>()`](https://doc.rust-lang.org/core/iter/trait.Iterator.html#method.collect) transforme un itérateur en une collection pertinente. Comme décrits dans la documentation, c'est l'une des méthodes les plus puissantes de la bibliothèque standard. Ici nous disons à la fonction `map` de transformer notre string divisé en un Vecteur (`Vec<>`)de string slices emprunté (`<&str>`) à la méthode. Ceci dit au compilateur quel collection nous voulons à la fin de l'opération.

`.map(|v| (v[0], v[1]))`

On transforme notre vecteur en un tuple par commodité en utilisant .

`.map(|(k, v)| (String::from(k), bool::from_str(v).unwrap()))`

On va ensuite convertir les deux éléments du tuple en une String et un booléan. la méthode `from_str()` à été importé avec sa déclaration `use` au début du fichier.

`.collect();`

Nous les collectons enfin dans notre HashMap. Cette fois nous n'avons pas besoin de déclarer le type que Rust infére depuis la déclaration de liaison.

`Ok(Todo { map })`

Pour finir, si on ne rencontre pas d'erreur, on retourne notre structure au code appelant. Notez ici que, tout comme en JavaScript, nous pouvons utiliser une notation plus courte si la clé et la variable ont le même nom dans une structure.

## Comment utiliser la fonction new

Dans `main`, mettez simplement à jour la liaison à notre variable todo avec:

`let mut todo = Todo::new().expect("Initialisation of db failed);`

Maintenant, si l'on retourne à notre terminal et lance un lot de commande "add", on devrait voir notre base de donnée se mettre à jour correctement:

```
$ cargo run -- add "make coffee"
todo saved
$ cargo run -- add "make pancakes"
todo saved
$ cat db.txt
make coffee     true
make pancakes   true
```

# Une autre approche

Bien que `map` est généralement considéré plus idiomatique, ce qui précède aurait pu également être implémenté avec une boucle [`for`](https://doc.rust-lang.org/rust-by-example/flow_control/for.html) à la place. Sentez-vous libre d'utiliser celle qui vous plait le plus.

```rust,ignore
impl Todo {
    fn new() -> Result<Todo, std::io::Error> {
        // open the db file
        let mut f = std::fs::OpenOptions::new()
            .write(true)
            .create(true)
            .read(true)
            .open("db.txt")?;
        // read its content into a new string
        let mut content = String::new();
        f.read_to_string(&mut content)?;

        // allocate an empty HashMap
        let mut map = HashMap::new();

        // loop over each lines of the file
        for entires in content.lines() {
            // split and bind values
            let mut values = entries.split('\t');
            let key = values.next().expect("No Key");
            let val = values.next().expect("No Value");
            // insert them into HashMap
            map.insert(String::from(key), bool::from_str(val).unwrap());
        }
        // Return Ok
        Ok(Todo { map })
    }
}
```

Le code au dessus est fonctionnellement équivalent à l'approche plus "fonctionnelle" utilisé précédemment.
