# Outils


L'expérience Rust est plus vaste qu'une spécifiaction de langage et un compilateur, de nombreux aspects de la création et le maintenance de logiciels production-qualité sont traités comme des citoyens de premier ordre. Plusieurs chaînes d'outils Rust simultanées peuvent être installés et gérées via rustup.

Avec le compilateur de Rust lui-même, Rust vient avec un outil nommé Cargo. Cargo est le gestionnaire de paquet de Rust

Rust fmt est un outil vraiment pratique que vous pouvez utiliser pour formater votre code en suivant un modèle consistant. Plus de perte de temps en configuration.

cargo check va tenter de compiler votre code sans le lancer: c'est une commande très utile en développement, lorsque vous voulez juste vérifier que votre code est correct sans le lancer.

Rust est livré avec à la fois une suite de test intégrés: cargo test.

Cargo doc est un outil pour générer de la documentation
Des [lints](https://en.wikipedia.org/wiki/Lint_(software)) supplémentaires sont disponible depuis [Clippy](https://github.com/rust-lang/rust-clippy) et le formatage idiomatique automatique est fourni par [rustfmt](https://github.com/rust-lang/rustfmt). Le support IDE est sain et de plus en plus performant chaque jour.
