# Pourquoi Rust ?

Rust est un langage de programmation bas-niveau (système), [multi-paradigme](https://en.wikipedia.org/wiki/Programming_paradigm), orienté performances et sécurité. Par multi-paradigme on entends:

* [Programmation concurrente](https://en.wikipedia.org/wiki/Concurrent_computing),
* [Programmation fonctionnelle](https://en.wikipedia.org/wiki/Functional_programming),
* [Programmation générique](https://en.wikipedia.org/wiki/Generic_programming),
* [Programmation impérative](https://en.wikipedia.org/wiki/Imperative_programming),
* [Programmation structurée](https://en.wikipedia.org/wiki/Structured_programming).

Il a été créé par Graydon Hoare en 2006 en tant que projet personnel pendant qu'il travaillait à [Mozilla](https://research.mozilla.org/) Research. Mozilla à commencé à sponsoriser le projet en 2009 et l'a annoncé en 2010. C'est donc un langage plutôt jeune, La release pre-alpha est arrivé en Janvier 2012  Rust 1.0, la première version stable est sortie le 15 mai 2015.

En août 2020, Mozilla se voit obligé de se diriger vers une restructuration suite à l'impact de la pandémie de COVID-19. Cette restructuration à visé une grande partie de l'équipe Rust ainsi que l'équipe de [Servo](https://servo.org/) qui a été complétement dissoute. Cette situation a généré beaucoup d'incertitudes et de confusion sur le projet Rust en lui-même.

La *Rust Core Team* à alors [annoncé](https://blog.rust-lang.org/2020/08/18/laying-the-foundation-for-rusts-future.html?ref=hvper.com) la création d'un Fondation Rust indépendante pour s'occuper de l'avenir de Rust et son écosystéme. Cette fondation est actuellement (début 2021) à ses dernières étapes de création. D'un autre coté, des sociétés comme [AWS (Amazon Web Services)](https://aws.amazon.com/blogs/opensource/aws-sponsorship-of-the-rust-project/) ou [Microsoft](https://www.zdnet.com/article/microsoft-to-explore-using-rust/) ont montré un grand soutien à Rust en investissant et en récupérant des membres de l'équipe Rust ayant quitté Mozilla afin de travailler sur leurs infrastructures.

Les trois plus gros avantages qu'on connait à ce langage sont les suivants:

* Sécurité et gestion de la mémoire,
* Accès concurrentiel plus facile grâce au modèle de possession des données,
* Abstractions à coût nul,

le langage de programmation Rust a gagné beaucoup d'attention de la communauté. il a également été désigné "langage de programmation le plus aimé" par le [sondage développeur de StackOverflow](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-languages-loved) chaque année depuis 2016, Ce qui indique que beaucoup de ceux qui ont l'occasion d'utiliser Rust en sont tombés amoureux. Il est très apprécié car il semblerait qu'il puisse résoudre les problèmes présents dans de nombreux autres langages, offrant un pas en avant solide avec un nombre limité d'inconvénients.

La communauté de développeurs Rust à tendance à s'agrandir depuis ces dernières annés, même si il revient assez souvent que ce n'est pas un langage très facile à apprendre. Lors du dernier [sondage Rust](https://blog.rust-lang.org/2020/12/16/rust-survey-2020.html), beaucoup de développeurs ont montré qu'ils aimeraient plus de documentation et d'entrainement à l'avenir. Très peu d'utilisateurs hebdomadaire se disent experts en Rust, c'est clairement un langage qui demande du temps pour être maitrisé. Rust [est utilisé](https://www.rust-lang.org/production) par des compagnies, grandes ou petites en production à travers le monde, comme Mozilla, Microsoft et AWS (évidemment), mais aussi Dropbox, npm ou encore Yelp.

Bien que Rust soit fermement attaché à la stabilité et à la rétrocompatibilité, cela n'implique pas que le langage soit finalisé. Un problème spécifique peut ne pas avoir accès aux fonctionnalités du langage qui le rendrait plus simple à exprimer. Aussi, le compilateur Rust est construit sur [LLVM](https://llvm.org/), ce qui signifie que le nombre de plate-formes cibles sera inférieur à [C](https://en.wikipedia.org/wiki/C_%28programming_language%29) ou [C++](https://en.wikipedia.org/wiki/C%2B%2B). Mais il semblerait que les équipes de Rust s'attelent à faire en sorte que la stabilité s'améliore toujours plus, et il semblerait que les utilisateurs du compilateur nightly soit en train de se diriger de plus en plus vers la version stable, ce qui montre que les nouvelles fonctionnalités sont prises en charge rapidement.

Ce [starter project](https://github.com/second-state/learn-rust-with-github-actions) sur GitHub vous permet de commencer avec le compilateur de Rust et le système de Cargo sans avoir à installer de chaîne d'outils logiciels. Vous pouvez utiliser l'IDE VSCode en ligne directement avec ce projet.
