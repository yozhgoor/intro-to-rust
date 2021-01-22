# Gestion d'erreur

Lorsque vous rencontrez une erreur de compilation en Rust, le compilateur vous donne immédiatement une explication de l'erreur, et vous suggère des solutions pour réparer l'erreur basé sur le contexte de votre programme.

Les sites de documentation Rust comme [docs.rs](http://docs.rs/) et [Rust by Example](https://doc.rust-lang.org/rust-by-example/) (et sa [version étendue](https://rust-by-example-ext.com/)) utilisent le [Rust Playground](https://play.rust-lang.org/) pour faire tourner des exemples de code Rust directement depuis le navigateur. Ces livres intéractivent sont bien mieux que du simple texte.

Le système de type robuste de Rust et l'accent mis sur la sécurité de la mémoire, le tout appliqué au moment de la compilation, signifient qu'il est extrêmement courant d'obtenir des erreurs lors de la compilation de votre code. Cela peut être un sentiment frustrant pour les programmeurs qui ne sont pas habitués à un langage de programmation aussi opiniâtre. Cependant, les développeurs Rust ont passé beaucoup de temps à améliorer les messages d'erreur pour s'assurer qu'ils sont clairs et exploitables. Ne perdez pas espoir en lisant les erreurs Rust!

Il est particulièrement courant d'entendre quelqu'un se plaindre d'avoir "combattu le vérificateur d'emprunt". Bien que des erreurs puissent être décourageantes, il est important de reconnaître que chacun des emplacements identifiés étaient susceptible d'introduire bugs et vulnérabilités potentielles dans un langage qui n'effectue pas les mêmes vérifications.

Dans cet exemple, on crée une String mutable contenant un nom, qui prend ensuite en référence les trois premiers bytes du nom. Bien que cette référence soit suspendue, nous tentons de muter la String en l'effaçant. Il n'y a désormais aucune garantie que la référence pointe vers des données valide et la déréférencer pourrait amener à un "Undefined behavior", donc le compilateur nous arrête:

```
fn no_mutable_aliasing() {
	let mut name = String::from("Vivian");
	let nickname : &name[..3];
	name.clear();
	println!("Hello there, {}!", nickname);
}
```

Heureusement, le message d'errreur incorpore notre code et fais de son mieux pour expliquer le problème, pointant vers les emplacements exact.

Les solutions de prototypage dans Rust peuvent être difficiles en raison de leur nature de type statique et parce que Rust nécessite de couvrir 100% des conditions, et pas seulement 99%. Les cas extrêmes doivent avoir un code applicable, même lorsque le programmeur ne sait pas encore ce que le "bon cas" doit faire. En early-development, ces cas êtrêmes peuvent souvent être résolus en faisant planter le programme, puis une gestion rigoureuse des erreurs peut être ajoutée ultérieurement. Il s'agit d'un workflow différent de celui des langages tels que Ruby, où les développeurs essaient souvent du code dans une [REPL](https://repl.it/languages/Ruby), puis le déplacent vers un prototype sans tenir compte du tout des cas d'erreur.
