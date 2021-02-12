# programmation embarquée

Un [système embarqué](https://en.wikipedia.org/wiki/Embedded_system) est un système informatique (processeur, mémoire, périphérique I/O) qui a une fonction dédiée dans un système mécanique ou électrique plus grand. Les systèmes embarqués modernes sont souvent basés sur des microcontrôleurs, mais les microprocesseurs ordinaires sont également courant, en particulier dans les systèmes plus complexes.

Les systèmes embarqués vont des appareils portables tels que les montres numériques et les lecteurs MP3, aux grandes installations fixes telles que les contrôleurs de feux de signalisation, les contrôleurs logiques programmables et les grands systèmes complexes tels que les véhicules, les systèmes d'imagerie médicale et l'avionique. La complexité varie de faible, avec un seul microcontrôleur, à très élevé avec plusieurs unités périphériques et réseaux montés à l'intérieur d'un grand rack d'équipement

Avec un accès direct au matériel et à la mémoire, Rust est un langage idéal pour le développement embarqué et le [bare-metal programming](https://www.techopedia.com/definition/3745/bare-metal-programming). Vous pouvez écrire du code extrêmement bas-niveau, Comme le [kernel d'un operating system](https://os.phil-opp.com/) ou une [application pour microcontrôleur](https://docs.rust-embedded.org/discovery/).

Les principaux types et fonctions de Rust ainsi que les bibliothèques de code réutilisable brillent dans ces environnements particulièrement difficiles.

A nouveau, Rust fournis un [book](https://doc.rust-lang.org/stable/embedded-book/) permettant une approche plus théorique de la programmation embarqué en Rust, une [liste de ressource](https://github.com/rust-embedded/awesome-embedded-rust) concernant la programmation embarqué et bas niveau en Rust

Il existe aussi plusieurs projets qui pourront vous permettre de commencer rapidement comme un tutorial pour créer un [kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system)) monolithique pour Operating System embarqué ou ce [blog post](https://blog.cecton.com/posts/rust-and-riscv/) destiné aux développeurs experimenté mais avec peu de connaissance en embarqué
