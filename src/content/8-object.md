# Programmation orientée objet

La programmation orientée objet consiste à créer et faire interagir des "briques" logicielles qu'on appelle **Objets**. Et un objet représente une idée, un concept ou toute entité du monde physique. La programmation orientée objet est aussi divisée en deux catégories, les langages à classes (fonctionnelle ou impérative ou encore les deux) ou les langages à prototype. On peut retrouver ce paradigme avec des langages comme [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)), ou [Perl](https://en.wikipedia.org/wiki/Perl).

l'utilisation de la programmation orienté objet en Rust peut différer de ce que l'on connait dans d'autres langages de programmation. Prenons les quatre pillier de l'OOP (Object Oriented Programming) qui sont **l'encapsulation**, **l'héritage**, **l'abstraction** et **le polymorphisme** et voyons comment Rust fais pour s'adapter.

* Encapsulation
  * L'encapsulation consiste à regrouper les données et les informations dans une seule unité appellée *Classe*. Malheureusement, il n'y a pas d'implémentation de classe en Rust mais on peut réaliser une encapsulation en utilisant des [struct](https://doc.rust-lang.org/std/keyword.struct.html).
* Héritage
  * L'héritage est un moyen de réutilisabilité du code et de sécurité de type. Dans la réutilisabilité du code, nous pouvons implémenter le comportement d'un type et réutiliser l'implémentation dans différentes sous-classes. Dans Rust, il n'y a pas de concepts d'héritage des propriétés d'une structure. Au lieu de cela, lorsque vous concevez la relation entre les objets, ses fonctionnalités seront définies par une interface (un [trait](https://doc.rust-lang.org/book/ch10-02-traits.html) en Rust). Cela favorise la composition plutôt que l'héritage, ce qui est considéré comme plus utile et plus facile à étendre à des projets plus important.
* Abstraction
  * L'abstraction vous permet d'afficher uniquement les informations nécessaires et de masquer tous les autres détails. Avec Rust, on y arrive grâce au mot-clé [pub](https://doc.rust-lang.org/nightly/std/keyword.pub.html) pour décider quel module, type, fonctions et méthode du code doivent être publics, et par défaut tout le reste est privé.
* Polymorphisme
  * Le polymorphisme est un concept consistant à fournir une interface unique à des entités pouvant avoir différents types. Rust y arrive, encore une fois, un peu différemment grâce à l'utilisation de [generics](https://doc.rust-lang.org/book/ch10-00-generics.html).

Le fait que Rust permette une implémentation différente de l'OOP pourrait rendre l'apprentissage de Rust plus compliqué pour des développeurs venant d'autres langages orienté objet, dans le sens où ils doivent modifier leurs habitudes et la façon de penser leur code. Aussi, certaines définitions classifierait Rust comme étant un langage orienté objet, d'autres non. Cela vient du fait qu'une structure ne peut pas hérité des champs et fonctions d'un struct parent.
