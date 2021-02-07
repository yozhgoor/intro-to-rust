# Programmation système

La [programmation système](https://en.wikipedia.org/wiki/Systems_programming) est un type de programmation qui vise au développement de programmes qui font partie du système d'exploitation d'un ordinateur ou qui en réalisent les fonctions. On peut trouver des langages comme le [langage assembleur](https://en.wikipedia.org/wiki/Assembly_language), C ou C++.

Un des plus grand bénéfice de l'utilisation d'un langage de programmation systéme est son habilité à contrôler des détails bas-niveau. Pour beaucoup de gens, Rust est largement considéré comme une alternative aux autres langages de programmation de systèmes, En tant que langage de niveau système destiné à remplacer C et C++, la plupart des gens supposent que Rust serait utilisé dans la programmation d'infrastructure, comme les systèmes d'exploitation, les bibliothèques natives et les plate-formes d'exécution.

Les langages de programmation systèmes s'attendent implicitement à ce qu'ils existent pour toujours. Bien que certains développements modernes ne nécessitent pas autant de longévité, de nombreuses entreprises veulent savoir que leur base de code fondamentale sera utilisable dans un avenir prévisible. Rust reconnaît cela et a pris des décisions de conception consciente concertant la [compatibilité ascendante](https://en.wikipedia.org/wiki/Backward_compatibility) et la stabilité. C'est un langage conçu pour les 40 prochaines années.

Le plus grand avantage que Rust peut offrir par rapport à ces langages est le *borrow checker* (Vérificateur d'emprunt en français). C'est la partie du compilateur chargée de s'assurer que les références ne survivent pas aux données auxquelles elles se réfèrent, et cela aide à éliminer des classes entières de bugs causées par l'insécurité de la mémoire.

Contrairement à de nombreux langages de programmation de systèmes existants, Rust ne vous oblige pas à passer tout votre temps dans les moindres détails. Rust s'efforce d'avoir autant d'abstractions à coût nul que possible, des abstractions aussi performantes que le code manuscrit équivalent. Dans cet exemple, nous montrons commment les itérateurs, une abstraction principale de Rust, peuvent être utilisés pour créer succintement un vecteur contenant les dix premiers nombres carrés.

`let squares: Vec<_> = (0..10).map(|i| i * i).collect();`

## Safe et Unsafe

Lorsque la partie "safe" de rust n'est pas capable d'exprimer certains concepts, vous pouvez utiliser la partie ["unsafe"](https://doc.rust-lang.org/stable/nomicon/index.html) de Rust. Cela débloque quelques pouvoirs supplémentaires, mais en échange, le programmeur est responsable de s'assurer que le code est vraiment sûr. Ce code unsafe peut ensuite être développé dans des abstractions de niveau supérieur qui garantissent que tous les utilisations de l'abstraction sont sûres.

Utilisez du code unsafe doit être une décision calculée, car l'utiliser correctement nécessite autant de réflexion et d'attention que tout autre langage dans lequel vous êtes responsable d'éviter un "[undefined behavior](https://raphlinus.github.io/programming/rust/2018/08/17/undefined-behavior.html)" (comportement indéfini en français). Réduire au minimum le code unsafe est le meilleur moyen de minimiser les possibilités d'[erreur de segmentations](https://en.wikipedia.org/wiki/Segmentation_fault) et de vulnérabilités dues à l'insécurité de la mémoire.
