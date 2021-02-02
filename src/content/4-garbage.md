# Sans garbage collector

Rust est un des langages de programmation bas-niveau qui n'utilise pas de [garbage-collector](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) ("ramasse-miette" en Français).

C'est une sorte de gestionnaire de mémoire automatique, il va vérifier la mémoire pour libérer l'espace occupé par des données qui ne sont plus utilisé par le programme.

L'ownership est la fonctionnalité la plus unique en Rust. elle permet aux programmeurs Rust d'écrire des programmes sans devoir allouer manuellement la mémoire (comme en C/C++). Rust vous donne le choix de stocker des données sur la pile ou le tas et détermine au moment de la compilation quand la mémoire n'est plus nécessaire et peut être nettoyé. Cela permet une utilisation efficace de la mémoire ainsi qu'un accès à la mémoire plus performant en plus du fait de ne pas avoir un garbage collector qui fonctionne en permanence

[Tilde](https://www.tilde.io/), un des premiers utilisateurs de Rust en production dans leur produit [Skylight](https://www.skylight.io/), a découvert qu'il étaient en mesure de [réduire leur utilisation de la mémoire de 5GiB à 50Mib](https://www.rust-lang.org/static/pdfs/Rust-Tilde-Whitepaper.pdf) en réécrivant certains points de terminaison HTTP Java dans un Rust idiomatique. Des économies comme celle-ci s'additionnent rapidement lorsque les fournisseurs de cloud facturent des prix plus élevés pour une mémoire accrue ou des noeuds supplémentaires.

Les projets Rust sont bien adaptés, grâce à cette spécificité pour être utilisés comme bibliothèques par d'autres langages de programmation via des interfaces de fonctions étrangères. Cela permet aux projets existants de remplacer les éléments essentiels aux performances par du code Rust rapide sans les risques de sécurité de la mémoire inhérents aux autres langages de programmation de systèmes. Certains projets ont même été [réécrits progressivement en Rust](https://people.gnome.org/~federico/blog/librsvg-is-almost-rustified.html) en utilisant ces techniques.
