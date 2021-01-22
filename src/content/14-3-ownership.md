# Aperçu du concept d'Ownership

Avec les conseils précédents sur l'emprunt et la référence, c'est maintenant le bon moment pour parler briévement de l'Ownership(https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html) (possession en français?).

Le système d'ownership possède trois règles:

* Chaque valeur en Rust à une variable: son "Owner".
* Il peut uniquement y avoir un "Owner" à la fois pour chaque valeur.
* Lorsque le "Owner" sort de la portée, la valeur sera relachée.

Rust vérifie ces règles au moment de la compilation, ce qui signifie que nous devons être explicite pour dire si et quand nous voulons qu'une valeur soit libéré en mémoire.
Voyons un exemple:

```rust
fn main() {
    // the owner of the String is x
    let x = String::from("Hello");

    // we move the value inside this function.
    // now doSomething is the owner of x.
    // Rust will free the memory associated with x
    // as soon as it goes out of "doSomething" scope.
    doSomething(x);

    // The compiler will throw an error since we tried to use
    // but since we moved it inside "doSomething"
    // we cannot use it as we don't have ownership
    // and the value may have been dropped.
    println!("{}", x);
}
```
Ce concept est largement considéré comme le plus difficile à comprendre lors de l'apprentissage de Rust, car c'est un concept qui peut être nouveau pour de nombreux programmeurs.

Nous n'allons pas creuser plus en profondeur les tenant et aboutissant du système d'ownership. Pour le moment, gardez en tête les règles mentionnées plus haut. Essayez de penser, à chaque étape, si vous avez besoin de "posséder" les valeurs et de les supprimer, ou si vous avez besoin d'une référence pour qu'elle puisse être conservée.

Par exemple, dans la méthode `insert` ci-dessus, nous ne voulons pas posséder `map`, car nous en avons encore besoin pour stocker ses données quelque part. Ce n'est qu'alors que nous pourrons enfin libérer la mémoire allouée.

## Sauvegarder map sur le disque

Etant donné que cette une app démo, nous allons adopter la solution la plus simple pour un stockage de long terme: écrire `map` dans un fichier sur le disque.

Créons une nouvelle méthode pour notre bloc `impl`.

```rust,ignore
impl Todo {
    fn insert(&mut self, key: String) {
        // insert a new item into our map.
        // We pass true as a value
        self.map.insert(key, true);
    }
    fn save(self) -> Result<(), std::io::Error> {
        let mut content = String::new();
        for (k, v) in self.map {
            let record = format!("{}\t{}\n", k, v);
            content.push_str(&record)
        }
        std::fs::write("db.txt', content)
    }
}
```

Décomponsons ce que nous venons d'ajouter pour y voir plus clair:

`fn save(self) -> Result<(), std::io::Error> {`

`->` annote le type de retour de la fonction. Nous retournons un `Result`.

`let mut content = String::new();`

On lie la variable mutable `content` à une nouvelle `String`.

`for (k, v) in self.map {`

On itère sur map.

`let record = format!("{}\t{}\n", k, v);`

On formate chaque chaîne de caractère, séparant les clés et valeurs avec un caractère "tab" et chaque ligne avec un retour à la ligne.

`content.push_str(&record)`

On pousse la chaîne formaté dans la variable `content`.

`std::fs::write("db.txt", content)`

On écrit `content` à l'intérieur du fichier nommé `db.txt`.

Il est important de noter que `save` *prend possession* de `self`. C'est une décision arbitraire pour que le compilateur nous arrête si nous essayons accidentellement de mettre à jour la map après avoir appelé `save` (car la mémoire de `self` serait libérée).

C'est une décision personnelle de "forcer" save à être la dernière méthode utilisée. Et c'est un exemple parfait pour vous montrer comment vous pouvez utiliser la gestion de mémoire de Rust pour créer du code plus strict qui ne pas pas compiler (qui aide à prévenir les erreurs humaines lors du développement).

## Comment utiliser la structure dans main

Maintenant que nous avons ces deux méthodes, nous pouvons les utiliser. Nous avons laissé `main` au point où nous lisons les arguments fournis. Maintenant si l'action fournie est "add" nous allons insérer cet item dans le fichier et le stocker pour une utilisation future.

Notre fonction `main` devrait ressembler à ceci:

```rust,ignore
fn main() {
    let action = std::env::args().nth(1).expect("Please specify an action");
    let item = std::env::args().nth(2).expect("Please specify an item");

    println!("{:?}, {:?}", action, item);

    let mut todo = Todo {
        map: HashMap::new(),
    };
    if action == "add" {
        todo.insert(item);
        match todo.save() {
            Ok(_) => println!("todo saved"),
            Err(why) => println!("An error occurred: {}", why),
        }
    }
}
```

Voyons ce que nous avons là:


`let mut todo = Todo {`

on instancie un struct, défini comme mutable.

`if action == "add" {`

Si l'argument d'action est `add`:

`todo.insert(item)`

On appelle la méthode `TODO insert` en utilisant la notation `.` et on lui donne `item` comme argument

```rust,ignore
match todo.save() {
    Ok(_) => println!("todo saved"),
    Err(why) => println!("An error occurred: {}", why),
}
```
On [match](https://doc.rust-lang.org/std/keyword.match.html) le Result renvoyé par la fonction `save` et affiche un message sur l'écran dans chaque cas.

Testons ça, lancez votre terminal et tapez:

```bash,ignore
$ cargo run -- add "code rust"
todo saved
```

Inspectons l'item sauvegardé:

```bash,ignore
$ cat db.txt
code rust true
```
