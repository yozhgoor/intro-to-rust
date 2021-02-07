# Un langage fortement typé

Rust est un langage [typé statiquement](https://en.wikipedia.org/wiki/Type_system), cela veut dire que le type des variables doit être connu au moment de la compilation.

Pour certains langages, cela veut dire que le programmeur doit spécifier de quel type est chaque variable (comme [Java](https://en.wikipedia.org/wiki/Java_(programming_language)), C ou C++). Cela imposent une lourde charge au programmeur, l'obligeant à répéter le type d'une variable plusieurs fois, ce qui entrave la lisibilité et la refactorisation.

Tandis que Rust et d'autres langages utilisent une forme d'[inférence de type](https://en.wikipedia.org/wiki/Type_inference), ils sont capable de déduire le type d'une variable et le programmeur ne devra la spécifier que si le compilateur n'est pas capable de l'inférer pour nous (comme [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language)), [Scala](https://en.wikipedia.org/wiki/Scala_(programming_language)) ou [Kotlin](https://en.wikipedia.org/wiki/Kotlin_(programming_language))). Certains langages à typage statique permettent l'inférence de type de programme entier. Bien que pratique lors du développement initial, cela réduit la capacité du compilateur à fournir des informations d'erreur utiles lorsque les types ne correspondent plus.

Dans cet exemple, le compilateur de Rust infére le type de `twice`, `2`, et `1` car le paramètre `val` et le type de retour sont déclaré comme entiers signé sur 32 bits

```rust, ignore
fn simple_math(val: i32) -> i32 {
	let twice = val * 2;
	twice - 1
}
```

Rust apprends de ces deux styles et exige que les éléments de premier niveau tels que les arguments de fonction et les constantes aient des types explicites, tout en permettant l'inférence de type à l'intérieur du corps de la fonction. Il fait de son mieux penser plus loin programmeur tout en encourageant la maintenabilité à long terme

Un langage typé dynamiquement, par contre, doit connaitre le type des variables au moment de l'exécution. Cela veut dire que le programmeur peut écrire un peu plus vite car il n'a pas à spécifier le type à chaque fois. [Perl](https://www.perl.org/), [Ruby](https://www.ruby-lang.org/en/) ou [Python](https://www.python.org/) sont des langages typé dynamiquement.

Le principal avantage de Rust ici est que tout type de vérification peut être faite par le compilateur, ce qui implique que beaucoup de bugs peuvent être détecté à une étape avancé du développement.

Cela ne veut pas dire que tous les systèmes de type statique sont équivalent. De nombreux langages à typage statique ont une grande astérisque à côté d'eux: ils permettent le concept de `NULL`.

Cela signifie que toute valeur peut être ce qu'elle dit ou rien, créant effectivement un [deuxième type possible pour chaque type](https://franklinchen.com/blog/2012/09/06/my-pittsburgh-ruby-talk-nil/). Comme Haskell et quelques autre langages de programmation moderne, Rust encode cette possibilité en utilisant un *type optionnel*, et le compilateur vous demande de gérer le cas `None`. Cela empêche les occurrences du redouté erreur d'exécution `TypeError: Cannot read property 'foo' of null` (ou l'équivalent du langage), au lieu de le promouvoir comme une erreur de compilation que vous pouvez résoudre avant qu'un utilisateur ne le voie.

Voici en exemple une fonction pour saluer quelqu'un en fonction de si l'on connait son nom ou non.

```rust, ignore
fn greet_user(name: Option<String>) {
	match name {
		Some(name) => println!("Bonjour, {}", name),
		None => println!("Bienvenue à vous, étranger!"),
	}
}
```

Si l'on oublie le cas `None` dans le `match` ou aurait essayé d'utiliser `name` comme si il s'agissait d'une valeur `String` toujours présente, le compilateur se plaindra.

```rust
fn greet_user(name: Option<String>) {
	match name {
		Some(name) => println!("Bonjour, {}", name),
	}
}
```
> *Note*: n'hésitez pas à tester le code lorsque vous voyez un bouton play dans le bloc de code. Dans ce cas, cela vous permettra de voir l'erreur renvoyé par le compilateur.
