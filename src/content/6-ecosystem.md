# L'écosystème de Rust

L'expérience Rust est plus vaste qu'une spécifiaction de langage et un compilateur, de nombreux aspects de la création et le maintenance de logiciels sont dans le viseur des équipes Rust.

Plusieurs chaînes d'outils Rust simultanées peuvent être installés et gérées via rustup. L'installation de Rust est livrée avec Cargo, un outil en ligne de commande permettant de gérer les dépendances, exécuter des tests, générer de la documentation, etc. Etant donné que les dépendances, les tests et la documentation sont disponibles de base, leur utilisation est répandue.

De plus, Rust cherche à créer un certain standard pour permettre à tout le monde de travailler sur les mêmes bases. Vous pourrez voir que Rust propose plusieurs outils de développement, un gestionnaire de paquet et possède un système de documentation bien à lui.

Comme je le disais précédemment, plusieurs chaînes d'outils Rust simultanées peuvent être installés et gérées via [rustup](https://rust-lang.github.io/rustup/).

Cela veut dire qu'il installe les composants du langage Rust depuis les canaux officiels et vous permet de changer entre le compilateur [rustc](https://doc.rust-lang.org/rustc/index.html) stable, beta ou nightly tout en les gardant à jour.

Avec le compilateur de Rust lui-même, Rust vient avec un outil nommé [Cargo](https://doc.rust-lang.org/cargo/). Cargo est le gestionnaire de paquet de Rust. Il télécharge les dépendances de vos paquets, les compiles, les rends distribuables puis les charge sur [crates.io](https://crates.io/).

## Crates Rust

Un des aspects les plus important de l'écosystéme d'un langage de programmation est la manière de partager du code avec d'autres développeurs. Pour Rust, on passe par des packages, plus souvent appelé "crates".

Crates.io est le site communautaire de partage et de découverte des [biblothèques de code](https://en.wikipedia.org/wiki/Library_(computing)) Rust. Tout bibliothéque publiée sur crates.io verra sa documentation construite et publiée sur [docs.rs](https://docs.rs/). Et il existe une alternative non officielle, [libs.rs](https://lib.rs/)

Rust est encore relativement nouveau, ce qui signifie que certaines bibliothèques souhaitées ne sont peut-être pas encore disponibles. L'avantage est qu'il y a beaucoup de terrain fertile pour développer ces bibliothèques nécessaires, peut-être même en profitant des développements récents dans des domaines de l'informatique pertinents. En raison de cela et des capacités de Rust, certaines des bibliothèques de code en Rust, comme la crate [Regex](https://github.com/rust-lang/regex), sont les meilleurs dans tout langages confondu.

## Outils Rust

Les équipes de Rust mettent plusieurs [outils](https://www.rust-lang.org/tools) différents permettant un développement rapide ainsi qu'une collaboration plus facile orientant votre travail sur ce qui vraiment.

[Rust fmt](https://github.com/rust-lang/rustfmt#quick-start) est un outil vraiment pratique que vous pouvez utiliser pour formater votre code en suivant un modèle consistant. Plus de perte de temps en configuration.
Il vous suffit d'utiliser `cargo fmt` et votre code aura le même format que n'importe quel autre code Rust.

[cargo check](https://doc.rust-lang.org/edition-guide/rust-2018/cargo-and-crates-io/cargo-check-for-faster-checking.html) va tenter de compiler votre code sans le lancer: c'est une commande très utile en développement, lorsque vous voulez juste vérifier que votre code est correct sans le lancer.

Rust est livré avec une suite de test intégrés: [cargo test](https://doc.rust-lang.org/cargo/commands/cargo-test.html).

Des [lints](https://en.wikipedia.org/wiki/Lint_(software)) supplémentaires sont disponible depuis [Clippy](https://github.com/rust-lang/rust-clippy).

Le support IDE est de plus en plus performant chaque jour grâce notamment à des projets comme [rust-analyzer](https://rust-analyzer.github.io/) ou [intellij Rust plugin](https://www.jetbrains.com/rust/).

En plus des outils built-in, La communauté Rust a créé un grand nombre d'outils de développement. Benchmarking ([criterion](https://bheisler.github.io/criterion.rs/book/index.html)), fuzzing ([cargo-fuzz](https://rust-fuzz.github.io/book/cargo-fuzz.html)) et [property-based testing](https://blog.logrocket.com/property-based-testing-in-rust-with-proptest/) sont tous facilement accessibles et bien utilisés dans les projets

## Documentation Rust

La documentation traditionnelle consiste typiquement en livres entiers et site webs. La nouvelle génération de développeurs veut de la meilleure documentation en plus grande quantité. En tant que "nouveau" langage, Rust est déjà à la pointe de l'innovation en matière de documentation de langage de programmation.

Rust fournis un outil nommé [rustdoc](https://doc.rust-lang.org/rustdoc/what-is-rustdoc.html), son boulot est de générer de la documentation pour les projets Rust.

Les sites de documentation Rust comme [docs.rs](http://docs.rs/) et [Rust by Example](https://doc.rust-lang.org/rust-by-example/) (et sa [version étendue](https://rust-by-example-ext.com/)) utilisent le [Rust Playground](https://play.rust-lang.org/) pour faire tourner des exemples de code Rust directement depuis le navigateur. Ces livres intéractivent sont bien mieux que du simple texte.

## Communauté Rust

Au dela des points techniques, Rust possède une communauté dynamique et accueillante. Il existe plusieurs moyens officiels et non officiels permettant aux gens d'obtenir de l'aide, tels que:

* le [forum des utilisateurs](https://users.rust-lang.org/),
* Le [discord Rust](https://discord.com/invite/rust-lang) et le [community server](https://discord.com/invite/tcbkpyQ)
* Le [Rust lang Slack](https://rust-slack.herokuapp.com/)
* le [subreddit](https://www.reddit.com/r/rust/d) Rust
* les questions et Réponses sur [StackOverflow](https://stackoverflow.com/questions/tagged/rust) et son [blog](https://stackoverflow.blog/?s=rust).

Rust a un code de conduite appliqué par une [équipe de modération](https://www.rust-lang.org/governance/teams/moderation) impressionnante pour s'assurer que les espaces officiels sont accueillants, et la plupart des espaces non officiels observent également quelque chose de similaire.

Hors ligne, Rust a plusieurs conférences autour du globe comme [RustConf](https://rustconf.com/), [Rust Belt Rust](https://www.rust-belt-rust.com/), [RustFest](https://rustfest.global/), [Rust Latam](https://www.rustlatam.org/), [RustCon Asia](https://rustcon.asia/), [Rusty Days](https://rusty-days.org/), [RustLab](https://rustlab.it/), etc...
