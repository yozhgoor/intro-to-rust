# WebAssembly

[WebAssembly](https://en.wikipedia.org/wiki/WebAssembly) (ou WASM) est un standard ouvert qui définit un format de code binaire portable pour les programmes exécutables, et un langage d'assemblage textuel correspondant, ainsi que des interfaces pour faciliter les intéractions entre ces programmes et leur environnement hôte.
Le but principal de WebAssembly est d'activer des applications hautes performances sur des pages Web, mais aussi le format est conçu pour être exécuté et intégré dans d'autres environnements également, y compris autonomes.

Techniquement parlant, il s'agit d'un nouveau langage d'assemblage de bas-niveau qui fonctionne efficacement sur la plate-forme web existante qui permet de traduire des applications en modules prêts pour le web et qui peuvent s'exécuter dans les navigateurs modernes à des vitesses presque native.

WebAssembly est un environnement d'exécution populaire pour les programmes Rust et ils ont tout les deux été inventé par Mozilla.

Rust se concentre sur les performances et la sécurité de la mémoire, tandis que WebAssembly se concentre sur les performances et la sécurité d'exécution.
En tant que conteneur d'exécution, WebAssembly rend également les programmes Rust multi-plateformes et plus facile à gérer.
Il y a en effet beaucoup de synergie entre les deux technologies.

Il a été inventé au départ en tant que machine virtuelle côté client pour exécuter des applications dans le navigateur.
Mais comme Java et JavaScript avant lui, WebAssembly effectue maintenant la migration du côté client vers le [côté serveur](https://www.secondstate.io/articles/why-webassembly-server/).

La plupart des développeurs Rust travaillent aujourd'hui sur des backend d'applications Web.
Pas étonnant que les crates comme [hyper](https://docs.rs/hyper/0.13.5/hyper/), [actix-web](https://github.com/actix/actix-web) et [Rocket](https://rocket.rs/) soient parmi les plus populaires auprès des développeurs Rust.

Vous pouvez démarrer le développement d'applications Rust et WebAssembly à partir de "starter project" dans ce [repository GitHub](https://github.com/second-state/ssvm-nodejs-starter).
Et il existe un [book](https://rustwasm.github.io/docs/book/what-is-webassembly.html) pour ceux qui préfèrent la théorie.
