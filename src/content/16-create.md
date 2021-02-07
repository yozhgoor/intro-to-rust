# Créer un programme en ligne de commande

Ce tutoriel est ma version de celui fait par [Claudio Restifo](https://www.freecodecamp.org/news/author/claudio/) sur [FreeCodeCamp](https://www.freecodecamp.org/news/how-to-build-a-to-do-app-with-rust/) et traduit en Français. Son but est de vous donner un aperçu pratique de certains concepts qui vous permettront de découvrir Rust.

Si vous préférez voir le code directement, vous pouvez accéder à ce [repository GitHub](https://github.com/yozhgoor/todo-cli).

Le créateur de ce tutoriel vient du monde de JavaScript, où il est traditionnel de faire une To-Do App comme premier projet. Être familier avec la ligne de commande est nécessaire car l'application va tourner dans le terminal et vous aurez aussi besoin de certaines connaissances des concepts de programmation généraux.

Nous allons stocker des valeurs en tant que collection d'item et une valeur [booléenne](https://en.wikipedia.org/wiki/Boolean_data_type) représentera son état actif.

```bash,ignore
learn rust          false
write some code     true
play video games    false
```

Qu'est-ce que nous allons couvrir ?
* [Gestion d'erreur en Rust](https://doc.rust-lang.org/book/ch09-00-error-handling.html),
* [Options et type Null](https://doc.rust-lang.org/stable/book/ch06-00-enums.html),
* [Struct](https://doc.rust-lang.org/std/keyword.struct.html) et [impl](https://doc.rust-lang.org/std/keyword.impl.html),
* Terminal [Input/Output](https://en.wikipedia.org/wiki/Input/output),
* Gestion de [système de fichiers](https://doc.rust-lang.org/std/fs/index.html),
* [Ownership](https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html) et [emprunt](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html) en Rust,
* [Match pattern](https://doc.rust-lang.org/book/ch06-02-match.html#patterns-that-bind-to-values),
* [Itérateurs](https://doc.rust-lang.org/book/ch13-02-iterators.html) et [closures](https://doc.rust-lang.org/book/ch19-05-advanced-functions-and-closures.html),
* Utilisation d'une [crate externe](https://doc.rust-lang.org/book/ch07-01-packages-and-crates.html).

Prêt à vous salir un peu les mains ? *Let's go!*
