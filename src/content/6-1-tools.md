# Outils

Comme je le disais dans la section précédente, plusieurs chaînes d'outils Rust simultanées peuvent être installés et gérées via [rustup]().

Ce qu'il veut dire qu'il installe le langage Rust depuis les canaux officiels et vous permet de changer entre le compilateur [rustc]() stable, beta ou nightly tout en les gardant à jour.

Avec le compilateur de Rust lui-même, Rust vient avec un outil nommé [Cargo](). Cargo est le gestionnaire de paquet de Rust. Il télécharge les dépendances de vos paquets, les compiles, les rends distribuables puis les charge sur [crates.io]().

[Rust fmt]() est un outil vraiment pratique que vous pouvez utiliser pour formater votre code en suivant un modèle consistant. Plus de perte de temps en configuration.
Il vous suffit d'utiliser `cargo fmt` et votre code aura le même format que n'importe quel autre code Rust.

[cargo check]() va tenter de compiler votre code sans le lancer: c'est une commande très utile en développement, lorsque vous voulez juste vérifier que votre code est correct sans le lancer.

Rust est livré avec à la fois une suite de test intégrés: [cargo test]().

Des [lints](https://en.wikipedia.org/wiki/Lint_(software)) supplémentaires sont disponible depuis [Clippy](https://github.com/rust-lang/rust-clippy).

Le support IDE est de plus en plus performant chaque jour grâce notamment à des projets comme [rust-analyzer]() ou [intellij Rust plugin]()
