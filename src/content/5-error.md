# Gestion d'erreur

En informatique, lors de l’exécution d’un programme, il y a toujours un risque d’erreur. C’est la raison pour laquelle tout bon langage possède une gestion des erreurs qui correspond concrètement en l’affichage d’un message d’erreur nous informant sur le type d’erreur détectée et (souvent) en l’arrêt de l’exécution du programme après que l’erreur ait été détectée.

Vu que Rust se veut fiable, il se doit de pouvoir gérer les situations où quelque chose ne se passerait pas comme prévu. Rust place les erreurs en deux catégories majeures, récupérable ou non-récupérable. Dans le cas d'une erreur récupérable, il est raisonnable de signaler le problème et retenter l'opération par exemple. Dans le cas d'une erreur irrécupérable, l'exécution du programme se stoppera, votre programme panique dans les termes Rust.

```bash,ignore
$ Cargo run
	Compiling a-program v0.1.0 (file:///project/a-program)
	 Finished dev [unoptimized + debugindfo] targets(s) in 0.6s
	  Running `target/debug/a-program.rs`
thread 'main' panicked at 'Your software sucks if it cannot handle errors!', src/main.rs:7:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
error: process didn't exit successfully: `target/debug/a-program.rs` (exit code: 101)
```

Ces exigences rendent votre code plus robuste car vous pourrez gérer les erreurs avant que votre code ne soit déployé en production. L'une des fonctionnalités les plus appréciées de Rust est son compilateur agressif qui vous aide à garantir l'exactitude et la sécurité avant même que le programme ne s'exécute. En conséquence, les développeurs Rust peuvent écrire des programmes hautement performants mais sûrs.

Le système de type robuste de Rust et l'accent mis sur la sécurité de la mémoire, le tout appliqué au moment de la compilation, signifient qu'il est extrêmement courant d'obtenir des erreurs lors de la compilation de votre code. Lorsque vous rencontrez une erreur de compilation en Rust, le compilateur vous donne immédiatement une explication de l'erreur, et vous suggère des solutions pour réparer l'erreur basé sur le contexte de votre programme.

Les développeurs Rust ont passé beaucoup de temps à améliorer les messages d'erreur pour s'assurer qu'ils sont clairs et exploitables.
Vous pouvez aussi trouver un [index](https://doc.rust-lang.org/error-index.html) reprenant les différentes erreur de compilation, la qualité de conception des messages d'erreur constitue un véritable avantage, alors que d'autres langages de programmation de revoient que des erreurs vagues, Rust fournis des informations utiles et pertinentes sur la façon de corriger l'erreur.

Il est particulièrement courant d'entendre quelqu'un se plaindre d'avoir "combattu le vérificateur d'emprunt". Bien que des erreurs puissent être décourageantes, il est important de reconnaître que chacun des emplacements identifiés étaient susceptible d'introduire bugs et vulnérabilités potentielles dans un langage qui n'effectue pas les mêmes vérifications.

Voyons un peu comment se gère une erreur de manière pratique, dans cet exemple, on crée une chaîne mutable contenant un nom, qui prend ensuite en référence les trois premiers bytes du nom. Bien que cette référence soit suspendue, nous tentons de muter la chaîne en l'effaçant. Il n'y a désormais aucune garantie que la référence pointe vers des données valide et la déréférencer pourrait amener à un "[Undefined behavior](https://en.wikipedia.org/wiki/Undefined_behavior)" (un comportement indéfini en français), donc le compilateur nous arrête:

```rust
fn no_mutable_aliasing() {
	let mut name = String::from("Vivian");
	let nickname = &name[..3];
	name.clear();
	println!("Hello there, {}!", nickname);
}
```

Heureusement, le message d'errreur incorpore notre code et fais de son mieux pour expliquer le problème, pointant vers les emplacements exact.
