# Un langage fortement typé

Rust est un langage fortement typé, cela signife que nous devons faire attention aux types des variables lorsque le compilateur n'est pas capable de l'inférer pour nous.

Utilisation des points virgule, pas d'ASI (?)

Les arguments entre les programmeurs qui préférent les système de type dynamique par rapport aux systèmes statiques dureront problablement encore des décénnies, mais il est difficile de discuter des avantages des types statiques. Il vous suffit de regarder la montée en puissance de langages tels que TypeScript ou de fonctionnalités telles que les indices de type Python, car les gens sont frustrés par l'état actuel de la saisie dynamique dans les bases de code plus vastes d'aujourd'hui. Les langages à typage statique permettent des contraintes vérifiées par le compilateur sur les données et leur comportement, ce qui réduit la surcharge cognitive et les malentendus.

Cela ne veut pas dire que tous les systèmes de type statique sont équivalent. De nombreux langages à typage statique ont une grande astérisque à côté d'eux: ils permettent le concept de `NULL`. Cela signifie que toute valeur peut être ce qu'elle dit ou rien, créant effectivement un [deuxième type possible pour chaque type](https://franklinchen.com/blog/2012/09/06/my-pittsburgh-ruby-talk-nil/). Comme Haskell et quelques autre langages de programmation moderne, Rust encode cette possibilité en utilisant un *type optionnel*, et le compilateur vous demande de gérer le cas `None`. Cela empêche les occurrences du redouté erreur d'exécution `TypeError: Cannot read property 'foo' of null` (ou l'équivalent du langage), au lieu de le promouvoir comme une erreur de compilation que vous pouvez résoudre avant qu'un utilisateur ne le voie. Voici en exemple une fonction pour saluer quelqu'un en fonction de si l'on connait son nom. Si l'on oublie le cas `None` dans le `match` ou aurait essayé d'utiliser `name` comme si il s'agissait d'une valeur `String` toujours présente, le compilateur se plaindra.

```
fn greet_user(name: Option<String>) {
	match name {
		Some(name) => println!("Hello there, {}" name),
		None => println!("Well howdy, stranger!"),
	}
}
```

Le typage statique de Rust fait de son mieux pour sortir du chemin du programmeur tout en encourageant la maintenabilité à long terme. Certains langages à typage statique imposent une lourde charge au programmeur, l'obligeant à répéter le type d'une variable plusieurs fois, ce qui entrave la lisibilité et la refactorisation. D'autres langages à typage statique permettent l'inférence de type de programme entier. Bien que pratique lors du développement initial, cela réduit la capacité du compilateur à fournir des informations d'erreur utiles lorsque les types ne correspondent plus. Rust apprends de ces deux styles et exige que les éléments de premier niveau tels que les arguments de fonction et les constantes aient des types explicites, tout en permettant l'inférence de type à l'intérieur du corps de la fonction. Dans cet exemple, le compilateur de Rust infére le type de `twice`, `2`, et `1` car le paramètre `val` et le type de retour sont déclaré comme entiers signé sur 32 bits

```
fn simple_math(val: i32) -> i32 {
	let twice = val * 2;
	twice - 1
}
```
