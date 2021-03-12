# SwiftUI / Combine

## Notes

- `ObservableObject` est un protocol qui permet à une `class` d'émettre des mises à jours liées à ses propriétés "publiées", à savoir marquées avec l'attribut `@Published`.
- L'attribut `@State` permet d'exprimer une variable d'état dans une vue, et on peut utiliser un binding sur cette variable avec `$`. La bonne pratique est de déclarer la propriété `private` et lui attribuer une valeur par défaut.
- L'attribut `@EnvironmentObject` permet de définir une variable d'environnement dans une vue, qui sera injectée par une vue parent avec le modifier `.environmentObject()`.
- L'attribut `@StateObject` permet d'initialiser un objet du modèle pour une propriété donnée une seule fois pour la durée de vie de l'application.
- L'attribut `@Binding` permet de déclarer un binding sur une propriété, ses changements seront propagés à la data source.
- Un binding est une valeur, et un moyen de modifier cette valeur. Un binding contrôle le stockage pour une valeur, de telle manière que l'on puisse passer de la donnée à des vues différentes qui ont besoin de la lire et/ou de la modifier.
- `GeometryReader` permet de dessiner, positionner, et dimensionner les vues de manière dynamique, au lieu de hardcoder des valeurs qui pourraient ne pas être correctes lorsque l'on réutilise la vue dans un autre context. `GeometryReader` rapporte de manière dynamique les informations de taille et de position de la vue parent et du device, et met à jour quand la taille change; quand l'utilisateur tourne son iPhone.

## Sources

[Apple Developer Documentation](https://developer.apple.com/tutorials/swiftui)