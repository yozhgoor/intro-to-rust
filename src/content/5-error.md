# Gestion d'erreur

Vu que Rust se veut fiable, il se doit de pouvoir gérer les situations où quelque chose ne se passerait pas comme prévu. Rust place les erreurs en deux catégories majeures, récupérable ou non-récupérable. Dans le cas d'une erreur récupérable, il est raisonnable de signaler le problème et retenter l'opération par exemple. Dans le cas d'une erreur irrécupérable, l'exécution du programme se stoppera, votre programme panique dans les termes Rust.

Ces exigences rendent votre code plus robuste car vous pourrez gérer les erreurs avant que votre code ne soit déployé en production. L'une des fonctionnalités les plus uniques et les plus appréciées de Rust est son compilateur agressif qui vous aide à garantir l'exactitude et la sécurité avant même que le programme ne s'exécute. En conséquence, les développeurs Rust peuvent écrire des programmes hautement performants mais sûrs.

Le système de type robuste de Rust et l'accent mis sur la sécurité de la mémoire, le tout appliqué au moment de la compilation, signifient qu'il est extrêmement courant d'obtenir des erreurs lors de la compilation de votre code. Lorsque vous rencontrez une erreur de compilation en Rust, le compilateur vous donne immédiatement une explication de l'erreur, et vous suggère des solutions pour réparer l'erreur basé sur le contexte de votre programme. Les développeurs Rust ont passé beaucoup de temps à améliorer les messages d'erreur pour s'assurer qu'ils sont clairs et exploitables.
Vous pouvez aussi trouver un [index](https://doc.rust-lang.org/error-index.html) reprenant les différentes erreur de compilation

Il est particulièrement courant d'entendre quelqu'un se plaindre d'avoir "combattu le vérificateur d'emprunt". Bien que des erreurs puissent être décourageantes, il est important de reconnaître que chacun des emplacements identifiés étaient susceptible d'introduire bugs et vulnérabilités potentielles dans un langage qui n'effectue pas les mêmes vérifications.

Voyons un peu comment se gère une erreur de manière pratique, dans cet exemple, on crée une chaîne mutable contenant un nom, qui prend ensuite en référence les trois premiers bytes du nom. Bien que cette référence soit suspendue, nous tentons de muter la chaîne en l'effaçant. Il n'y a désormais aucune garantie que la référence pointe vers des données valide et la déréférencer pourrait amener à un "[Undefined behavior]()" (un comportement indéfini en français), donc le compilateur nous arrête:

```
fn no_mutable_aliasing() {
	let mut name = String::from("Vivian");
	let nickname : &name[..3];
	name.clear();
	println!("Hello there, {}!", nickname);
}
```

Heureusement, le message d'errreur incorpore notre code et fais de son mieux pour expliquer le problème, pointant vers les emplacements exact.
