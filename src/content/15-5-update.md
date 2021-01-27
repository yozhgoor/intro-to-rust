# Mettre à jour une valeur

Comme dans toutes les applications TODO, nous voulons pouvoir non seulement ajouter des éléments, mais également les activer et les marquer comme terminés.

## Ajouter la méthode complete

Pour faire cela, ajoutons une nouvelle méthode à notre struct nommé "complete". Dedans, on prend une référence à une clé, et on mets la valeur à jour, ou on retourne `None` si la clé n'est pas présente.

```rust,ignore
impl Todo {
    // rest of the TODO methods

    fn complete(&mut self, key: &String) -> Option<()> {
        match self.map.get_mut(key) {
            Some(v) => Some(*v = false),
            None => None,
        }
    }
}
```

Voyons ce qu'il se passe ici:

`fn complete(&mut self, key: &String) -> Option<()> {`

On déclare une nouvelle méthode `complete` qui prend une référence à une clé, on déclare aussi le type de retour: un Option vide.

`match self.map.get_mut(key) {`

Toute la méthode retourne le résultat de l'expression `match` avec [`self.map.get_mut`](https://doc.rust-lang.org/std/collections/struct.HashMap.html#method.get_mut) qui peut être un `Some()` vide ou `None`.

`Some(v) => Some(*v = false),`

Si on récupére un Some, nous avons une donc une référence mutable à une valeur de clé, Nous utilisons l'opérateur [`*`](https://doc.rust-lang.org/book/appendix-02-operators.html) pour déréférencer la valeur et la définir sur false.

## Comment utiliser la méthode complete

On peut utiliser la méthode `complete` de la même manière que nou avons utilisé la méthode `insert` auparavant.

Dans `main`, vérifiez que l'action passé en argument est "complete" en utilisant une instruction `else if`:

```rust,ignore
// in the main function

if action == "add" {
    // add action snippet
} else if action == "complete" {
    match todo.complete(&item) {
        None => println!("'{}' is not present in the list", item),
        Some(_) => match todo.save() {
            Ok(_) => println!("todo saved"),
            Err(why) => println!("An error occurred: {}", why),
        },
    }
}
```

Il est temps d'analyser ce que nous faisons ici:

`} else if action == "complete" {`

[`else if`](https://doc.rust-lang.org/rust-by-example/flow_control/if_else.html) nous permet de d'avoir un argument `add` ou un argument `complete`.

`match todo.complete(&item) {`

on match l'Option retourné par la méthode `todo.complete`, on passe les items en tant que référence avec `&item` pour que la valeur soit toujours possédée par la fonction. Cela signifie que l'on peut l'utiliser dans notre macro `println!`, si nous n'avions pas fait cela, la valeur aurait été possédée par `complete` et abandonnée là.

`None => println!("'{}' is not present in the list", item),`

Si le cas est `None`, on affiche un avertissement à l'utilisateur pour une meilleure expérience.

```rust,ignore
Some(_) => match todo.save() {
    Ok(_) => println!("todo saved"),
    Err(why) => println!("An error occurred: {}", why),
}
```

Si l'on détecte qu'une valeur `Some` a été retournée, on appelle `todo.save` pour stocker les changements de manière permanente dans notre fichier. `Err` nous d'afficher un message à l'utilisateur si notre `save` rencontre une erreur.
