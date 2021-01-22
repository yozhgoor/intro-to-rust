# Pourquoi Rust ?

La réponse courte est que Rust résout les problèmes présents dans de nombreux autres langages, offrant un pas en avant solide avec un nombre limité d'inconvénients.

Je vais vous montrer un échantillon de ce que Rust propose aux utilisateurs d'autres langages de programmation et à quoi ressemble l'écosystème actuel. Cependant, tout n'est pas rose à Rust-land, alors je parlerais aussi des inconvénients

Depuis sa première version open-source en 2015, le langage de programmation Rust a gagné beaucoup d'attention de la communauté. il a également été désigné "langage de programmation le plus aimé" par le sondage développeur de StackOverflow chaque année depuis 2016.

Rust est le [langage le plus apprécié de Stack Overflow pendant quatre années consécutives](https://insights.stackoverflow.com/survey/2019), ce qui indique que beaucoup de ceux qui ont l'occasion d'utiliser Rust en sont tombés amoureux. Cependant, environ 97% des répondants à l'enquête qui n'ont pas utilisé Rust peuvent se demander: "quel est le truc de Rust?"

Rust est l'un des langage les plus en vogue en ce moment. C'est le [langage de programmation le plus aimé](https://stackoverflow.blog/2020/01/20/what-is-rust-and-why-is-it-so-popular/) selon StackOverflow depuis 4 ans maintenant. Pourtant il a toujours la réputation d'être le langage de programmation des geeks alpha.

Rust a été conçu par Mozilla

Selon [certaines estimations](https://s3-eu-west-1.amazonaws.com/vm-blog/uploads/2020/04/DE18-SoN-Digital-.pdf), il y aurait 600,000 développeurs Rust autour du globe, ce qui est un nombre plutôt significatif. Mais ça reste peu par rapport aux dizaines de millions de développeurs Java, Python ou JavaScript.

La communauté Rust a mené des enquêtes annuelles auprès des développeurs de rust-lang.org depuis 2016. Le site a récemment publié ses résultats d'enquête 2019 basés sur les réponses de près de 4000 développeurs Rust.

Le langage de programmation Rust n'est pas vraiment considéré comme "[easy to get started](https://www.secondstate.io/articles/a-rusty-hello-world/)". Au contraire, il est conçu pour être puissant et sûr à la fois. Il vise à être le langage de productivité de développement pour les programmeurs professionnels. Il est stimulant, amusant et gratifiant.

Très peu de répondant se disent experts en Rust. La plupart des gens évaluent leur expértise Rust à 7/10 ou moins, malgré le fait que plus de 68% d'entre eux écrivent du Rust sur une base hebdomadaire. C'est clairement un langage qui demande du temps pour être maitrisé.

lorsque la question "pourquoi ne pas utiliser Rust sur quelques projets", la courbe d'apprentissage a été cité comme 2ème raison la plus courante, la première raison étant, évidemment, la décision de l'entreprise pour utiliser un langage de programmation particulier dans un projet.

Comment les développeurs surmontent-ils la courbe d'apprentissage de Rust et en tombent amoureux? Eh bien, ce n'est pas inattendu, la plupart des développeurs ont cité "une meilleure documentation" comme moteur de l'adoption du langage.

Mais fidèle aux "programmeurs professionnels", la documentation Rust la plus recherché est le contenu de niveau intermédiaire qui aide les développeurs à améliorer leurs compétences et leur productivité Rust.

Bien que l'enquête soit biaisée vers les développeurs qui connaissent déjà les bases de Rust, il semble qu'il y ait une soif de connaissances et de développement personnel dans cette foule.

Il n'est pas surprenant que, à mesure que Rust est adopté par le grand public, les projets Rust refléteront le plus grand secteur du logiciel.

Ce [starter project](https://github.com/second-state/learn-rust-with-github-actions) sur GitHub vous permet de commencer avec le compilateur de Rust et le système de Cargo sans avoir à installer de chaîne d'outils logiciels. Vous pouvez utiliser l'IDE VSCode en ligne directement avec ce projet.

Bien que Rust soit fermement attaché à la stabilité et à la rétrocompatibilité, cela n'implique pas que le langage soit finalisé. Un problème spécifique peut ne pas avoir accès aux fonctionnalités du langage qui le rendraient plus simple a exprimer ou peut-être même possible à exprimer. A titre d'exemple, Rust a des [futures asynchrones]() depuis plus de trois ans, mais le support stable [async/await]() dans le langage lui-même n'a que quelques mois.

Le compilateur Rust est construit sur LLVM, ce qui signifie que le nombre de plates-formes cibles sera inférieur à C ou C++.
