# Interopérabilité entre langages

l'[interopérabilité](https://en.wikipedia.org/wiki/Interoperability#Information_technology_and_computers) est une caractéristique d'un produit ou d'un système lui permettant de fonctionner avec d'autres produits ou système existant et ainsi permettre à des outils différents de communiquer et travailler ensemble.

A mesure que l'adoption de Rust se développe, les développeurs doivent de plus en plus intégrer les programmes Rust avec des programmes écrits dans d'autres langages. Dans le passé, C et C++ étaient les langages les plus courants pour "parler" à Rust car ils sont utilisés dans les projets de logiciels d'infrastructure.

Maintenant que Rust se développe dans les projets de logiciels d'applications, davantage d'interface et de ponts au niveau langage sont nécessaires maintenant. Un bon exemple est le [Rust JavaScript bridge](https://www.secondstate.io/articles/rust-functions-in-nodejs/) qui prend en charge les [fonctions Rust dans les applications Node.js](https://www.secondstate.io/articles/getting-started-with-rust-function/), l'approche d'applications [hybride Rust + JavaScript](https://www.secondstate.io/articles/getting-started-with-rust-function/) prend de l'ampleur.

L'enquête a révélé que, outre C/C++ et [JavaScript](https://www.javascript.com/), les développeurs Rust sont intéressés par l'intégration avec [R](https://www.r-project.org/) et Python. Cela indique l'intérêt des développeurs pour les applications d'apprentissage automatique, de big data et d'intelligence artificielle (IA).

En fait, de nombreux packages d'apprentissages automatique et statistiques Python et R sont implémentés dans des modules binaires natifs. Rust est l'un des meilleurs langages de programmation pour écrire des modules natifs. [Cet exemple](https://github.com/second-state/rust-wasm-ai-demo) montre comment utiliser Rust pour exécuter des [modèles Tensorflow dans une application Node.js](https://www.secondstate.io/articles/artificial-intelligence/).

A l'avenir, nous envisageons que ces modules Rust s'exécutent dans des conteneurs hautes performance gérés tels que WebAssembly.

Voici quelques crates qui pourraient vous aider à lier Rust avec un autre langage dans vos applications:

* [PyO3](https://crates.io/crates/pyo3) pour Python,
* [Ruru](https://crates.io/crates/ruru) pour Ruby,
* [rquickjs](https://crates.io/crates/rquickjs) pour JavaScript.
