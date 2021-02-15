# Sans garbage collector

Tous les programmes doivent gérer la façon dont ils utilisent la mémoire d'un ordinateur pendant l'exécution.
Certains langages ont un ["garbage collector"](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) ("ramasse-miette" en Français) permet de supprimer les objets non utilisés en mémoire.
C'est une sorte de gestionnaire de mémoire automatique, il va vérifier la mémoire pour libérer l'espace occupé par des données qui ne sont plus utilisées par le programme.
Le garbage collector est implémenté différemment dans chaque langage, les langages de programmation haut-niveau ont d'office cet outil tandis que les langages bas-niveau le font grâce à des bibliothèque de code.
Dans d'autres langages, le programmeur doit explicitement allouer et libérer la mémoire.

Rust utilise une troisième approche: la mémoire est gérée via un système d'ownership (propriété en français) avec un ensemble de règles que le compilateur vérifie au moment de la compilation.
Il n'utilise pas de garbage-collector car il vérifie dès la compilation si une erreur est susceptible de survenir du a un mauvais usage de la mémoire par le développeur.
L'[*"Ownership"*](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html) permet un lien entre une variable et sa valeur.
Une fois la valeur transmise a une autre variable, la première variable n'est plus accessible.

Rust vous donne le choix de stocker des données sur ["the stack"](https://en.wikipedia.org/wiki/Stack-based_memory_allocation) ou ["the heap"](https://en.wikipedia.org/wiki/Memory_management#DYNAMIC) (la pile ou le tas en français), ce sont tous les deux des emplacements de la mémoire mais qui sont organisés différemment.

La pile enregistre les valeurs dans l'ordre de réception et enlève les valeurs dans l'autre sens selon le principe de dernier entré premier sorti, toutes les données doivent avoir une taille fixe et connue au moment de la compilation.

Lorsque vous ajoutez des données sur le tas, les données ont parfois une taille qui peut changer, vous demandez en fait une certaine quantité de mémoire, le gestionnaire de mémoire va trouver un emplacement sur le tas qui est suffisamment grand, va le marquer comme étant en cours d'utilisation et retournera un pointeur avec l'adresse de cet emplacement.

Le compilateur détermine au moment de la compilation quand la mémoire n'est plus nécessaire et peut être nettoyée.
Cela permet une utilisation efficace de la mémoire ainsi qu'un accès à la mémoire plus performant en plus du fait de ne pas avoir un garbage collector qui fonctionne en permanence.
Et grâce au concept d'ownership les programmeurs Rust peuvent écrire des programmes sans devoir allouer manuellement la mémoire (comme on doit le faire en C/C++).
Vous pourrez en apprendre plus en pratique sur ce concept dans le [projet](16-3-ownership.md) à la fin de ce livre.

[Tilde](https://www.tilde.io/), un des premiers utilisateurs de Rust en production dans leur produit [Skylight](https://www.skylight.io/), a découvert qu'il étaient en mesure de [réduire leur utilisation de la mémoire de 5GiB à 50Mib](https://www.rust-lang.org/static/pdfs/Rust-Tilde-Whitepaper.pdf) en réécrivant certains points de terminaison HTTP Java dans un Rust [idiomatique](https://en.wikipedia.org/wiki/Programming_idiom).
Des économies comme celle-ci s'additionnent rapidement lorsque les fournisseurs de cloud facturent des prix plus élevés pour une mémoire accrue ou des machines supplémentaires.

Les projets Rust sont bien adaptés, grâce à cette spécificité pour être utilisés comme bibliothèques par d'autres langages de programmation via des interfaces de fonctions étrangères.
Cela permet aux projets existants de remplacer les éléments essentiels aux performances par du code Rust rapide sans les risques de sécurité de la mémoire inhérents aux autres langages de programmation de systèmes.
Certains projets ont même été [réécrits progressivement en Rust](https://people.gnome.org/~federico/blog/librsvg-is-almost-rustified.html) en utilisant ces techniques.
