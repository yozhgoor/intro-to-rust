# WebAssembly

la plupart des développeurs Rust travaillent aujourd'hui sur des backends d'applications Web. Pas étonnant que les crates comme [hyper](https://docs.rs/hyper/0.13.5/hyper/), [actix-web](https://github.com/actix/actix-web) et [Rocket](https://rocket.rs/) soient parmi les plus populaires auprès des développeurs Rust.

L'enquête rèvéle que WebAssembly est un environnement d'exécution populaire pour les programmes Rust. Rust et WebAssembly ont tout les deux été inventé par Mozilla.

Rust se concentre sur les performances et la sécurité de la mémoire, tandis que WebAssembly se concentre sur les performances et la sécurité d'exécution. En tant que conteneur d'exécution, WebAssembly rend également les programmes Rust multiplateformes et plus facile à gérer. Il y a en effet beaucoup de synergie entre les deux technologies.

WebAssembly a été inventé au départ en tant que machine virtuelle côté client pour exécuter des applications dans le navigateur. Mais comme Java et JavaScript avant lui, WebAssembly effectue maintenant la migration du côté client vers le [côté serveur](https://www.secondstate.io/articles/why-webassembly-server/).

Rust-in-WebAssembly est de bonne augure avec la tendance à accélérer l'adoption de Rust sur les applications Web backend. Vous pouvez démarrer le développement d'applications Rust et WebAssembly à partir de "starter project" dans ce [repository GitHub](https://github.com/second-state/ssvm-nodejs-starter).
