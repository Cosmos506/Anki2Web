# Anki2Web

# Anki2Web

**Anki2Web** est un outil web autonome qui permet de convertir des cartes de révision issues d'Anki en un fichier HTML interactif, partageable et destiné à être utilisé dans un navigateur.

> **À propos de la réalisation :** ce projet a été conçu et réalisé en *no-code assisté par ChatGPT*. Les fonctionnalités, l'interface et le code HTML/CSS/JavaScript ont été élaborés de manière itérative avec l'aide de ChatGPT. Il ne s'agit pas d'un projet développé selon un processus classique où tout le code aurait été écrit manuellement par un développeur. Le résultat reste néanmoins un fichier HTML contenant du code, et doit être testé comme tout logiciel.

## Sommaire

- [Objectif](#objectif)
- [Fonctionnement général](#fonctionnement-général)
- [Formats d'entrée](#formats-dentrée)
- [Fonctionnalités](#fonctionnalités)
- [Démarrage rapide](#démarrage-rapide)
- [Partager un paquet de cartes](#partager-un-paquet-de-cartes)
- [Utilisation hors ligne](#utilisation-hors-ligne)
- [Limites et compatibilité](#limites-et-compatibilité)
- [Confidentialité](#confidentialité)
- [Dépannage](#dépannage)
- [Architecture du projet](#architecture-du-projet)
- [Tests et état du projet](#tests-et-état-du-projet)
- [Licence et attribution](#licence-et-attribution)

## Objectif

Anki2Web vise à rendre des cartes de révision plus faciles à consulter et à partager, sans demander au destinataire d'installer Anki. Le principe est simple :

1. Importer un fichier exporté depuis Anki.
2. Vérifier les cartes et les options proposées.
3. Générer puis télécharger un fichier HTML.
4. Ouvrir ou partager ce fichier comme un document autonome.

Le fichier HTML généré est destiné à regrouper l'interface de révision et les ressources nécessaires à l'affichage. L'autonomie effective dépend toutefois du contenu exporté et doit être vérifiée, notamment pour les médias et les modèles de cartes complexes.

## Fonctionnement général

Anki2Web comporte deux usages distincts :

- **Le convertisseur** : le fichier `Anki2Web-final.html` permet de charger un export Anki et de préparer la conversion.
- **Le paquet HTML généré** : le fichier téléchargé après conversion sert à réviser les cartes dans un navigateur.

Il faut bien distinguer ces deux fichiers. Pour transmettre des cartes à un ami, c'est normalement **le fichier HTML généré après l'import**, et non nécessairement le convertisseur lui-même, qu'il faut partager.

## Formats d'entrée

Le projet a été conçu pour traiter plusieurs types d'exports Anki, notamment :

| Format | Usage général | À savoir |
|---|---|---|
| `.apkg` | Paquet de cartes Anki | À privilégier lorsque les cartes comprennent des images ou d'autres médias. |
| `.colpkg` | Export de collection Anki | Peut contenir une collection plus large ; la compatibilité dépend de la structure de l'export. |
| `.txt` | Export texte de cartes | Adapté aux cartes textuelles simples. Les séparateurs et les champs doivent être reconnus correctement. |

La prise en charge d'un format ne garantit pas que chaque fonctionnalité particulière d'Anki soit reproduite à l'identique. Pour de meilleurs résultats, utiliser un export propre provenant d'Anki et conserver les médias dans le paquet lorsqu'ils sont nécessaires.

## Fonctionnalités

Les fonctions disponibles dépendent du format d'entrée, du modèle de note et des options retenues lors de la conversion. Le projet a notamment été conçu autour des possibilités suivantes :

- Import de fichiers texte et de paquets Anki.
- Génération de cartes de révision dans un document HTML.
- Affichage du recto et retournement vers le verso.
- Navigation entre les cartes.
- Mélange de l'ordre des cartes.
- Prise en charge de contenus textuels et de médias lorsque ceux-ci sont correctement récupérés.
- Prise en charge prévue pour plusieurs types de cartes, dont les cartes classiques, le texte à trous et les cartes de type **Image Occlusion**.
- Réglages et informations d'aide destinés à expliquer les options de conversion.
- Présentation adaptée aux écrans d'ordinateur et aux écrans mobiles.
- Possibilité d'utiliser le fichier exporté hors ligne lorsque toutes les ressources requises sont intégrées.

**Important :** certaines fonctions propres à Anki — par exemple des modèles personnalisés complexes, des scripts spécifiques, des extensions, des sons, des champs inhabituels ou des comportements particuliers de cartes — peuvent ne pas être reproduites exactement. Toujours vérifier le résultat après conversion.

## Démarrage rapide

### 1. Ouvrir le convertisseur

Télécharger `Anki2Web-final.html`, puis l'ouvrir dans un navigateur récent, par exemple Chrome, Firefox, Edge ou Safari.

Le convertisseur est un fichier HTML local. Il n'a normalement pas besoin d'être installé comme une application.

### 2. Préparer l'export Anki

Dans Anki, exporter le paquet ou le texte que l'on souhaite convertir. Pour un paquet avec des images ou des schémas, préférer un export de type `.apkg` incluant les médias.

### 3. Importer le fichier

Dans Anki2Web, sélectionner le fichier à importer et attendre la fin du traitement. Si un message indique que des cartes ou des médias n'ont pas pu être récupérés, lire cet avertissement avant de poursuivre.

### 4. Vérifier le résultat

Avant de télécharger le résultat final, contrôler quelques cartes représentatives :

- Une carte simple avec du texte.
- Une carte avec une réponse longue.
- Une carte contenant une image.
- Une carte à trous, si le paquet en contient.
- Une carte Image Occlusion, si le paquet en contient.

Vérifier que le recto s'affiche correctement, que le retournement révèle la réponse attendue et que les médias restent visibles.

### 5. Télécharger le HTML généré

Lancer l'export, puis enregistrer le fichier généré. Conserver le fichier source Anki en sauvegarde : le HTML généré est une copie de révision et ne remplace pas le paquet Anki d'origine.

### 6. Tester le fichier généré

Ouvrir le fichier HTML exporté séparément du convertisseur. Tester plusieurs cartes et, si l'utilisation hors ligne est importante, couper temporairement la connexion Internet pour vérifier que les images, schémas et commandes nécessaires fonctionnent toujours.

## Partager un paquet de cartes

Le fichier HTML généré peut être envoyé par e-mail, messagerie, stockage en ligne ou clé USB.

Le destinataire doit généralement :

1. Télécharger le fichier HTML.
2. L'ouvrir dans un navigateur récent.
3. Utiliser les commandes de révision intégrées.

Il n'a normalement pas besoin d'installer Anki pour consulter un export HTML autonome.

### Avant de l'envoyer

- Ouvrir le fichier exporté et tester quelques cartes.
- Vérifier que les images et schémas s'affichent.
- Tester le fichier sans connexion Internet si le destinataire doit réviser hors ligne.
- Partager le fichier complet sans supprimer ni déplacer les éventuels fichiers associés si l'export n'est pas entièrement autonome.
- Éviter de partager des cartes contenant des informations personnelles ou des contenus dont on ne possède pas les droits.

La progression n'est pas nécessairement partagée ou synchronisée entre deux personnes. Le comportement de sauvegarde dépend de la manière dont le fichier généré gère l'état de révision et du navigateur utilisé.

## Utilisation hors ligne

Le convertisseur et le fichier de révision généré sont conçus pour être utilisés localement. Cependant, « fichier HTML unique » ne signifie pas automatiquement que toutes les ressources sont intégrées.

Pour vérifier l'utilisation hors ligne :

1. Générer le paquet HTML.
2. L'ouvrir dans un navigateur.
3. Désactiver temporairement le Wi-Fi ou la connexion réseau.
4. Vérifier le recto, le verso, les images, les schémas et les commandes de navigation.

Si un média disparaît ou si une fonction cesse de fonctionner hors ligne, l'export peut dépendre d'une ressource externe ou d'un fichier séparé.

## Limites et compatibilité

Anki2Web est un outil de conversion et de révision, pas un remplacement complet d'Anki.

Points à garder en tête :

- Les modèles et extensions Anki personnalisés ne sont pas nécessairement pris en charge.
- La mise en page d'origine peut différer dans le navigateur.
- Certains types de cartes peuvent nécessiter une adaptation.
- Les fichiers volumineux et les paquets riches en médias peuvent demander davantage de mémoire et de temps de traitement.
- Les limites de taille appliquées par le convertisseur sont des limites de sécurité propres à Anki2Web, pas des limites officielles d'Anki.
- Le comportement peut varier selon le navigateur, le système d'exploitation et la taille du paquet.
- Le convertisseur ne doit pas être considéré comme garantissant une conversion parfaite de chaque export Anki.

En cas d'échec, essayer d'abord un export plus petit, confirmer que les médias sont inclus et tester avec un navigateur récent. Garder toujours le fichier source.

## Confidentialité

Le fichier du convertisseur est conçu pour fonctionner localement dans le navigateur. Cela ne constitue toutefois pas, à lui seul, une preuve formelle que chaque opération reste locale dans toutes les versions ou configurations.

Pour des cartes confidentielles :

- Privilégier une utilisation hors ligne.
- Éviter d'importer des contenus sensibles dans un environnement non vérifié.
- Inspecter le code et les dépendances si une garantie de confidentialité est nécessaire.
- Ne pas partager de cartes qui contiennent des données personnelles, des identifiants ou des informations privées.

## Dépannage

### Le téléchargement ne démarre pas

- Essayer d'ouvrir le lien dans un autre navigateur.
- Vérifier les téléchargements bloqués par le navigateur.
- Réessayer avec une connexion stable.
- Vérifier que le fichier a bien été enregistré avant de l'ouvrir.

### Le fichier HTML ne s'ouvre pas correctement

- Vérifier que le téléchargement est complet.
- Ouvrir le fichier avec un navigateur à jour.
- Éviter de modifier manuellement le contenu du HTML.
- Télécharger à nouveau le fichier si sa taille paraît anormalement faible.

### Les images ou les schémas sont absents

- Vérifier que l'export Anki contenait les médias.
- Privilégier un fichier `.apkg` incluant les médias.
- Consulter les avertissements affichés pendant l'import.
- Tester le HTML exporté sans connexion réseau.

### Certaines cartes sont mal affichées

- Comparer la carte originale dans Anki avec la carte convertie.
- Tester d'autres cartes du même modèle.
- Vérifier les champs et le format d'export.
- Signaler un exemple minimal reproductible en précisant le type de fichier importé et le type de carte concerné.

### L'import d'un paquet volumineux échoue

- Essayer un paquet plus petit pour isoler le problème.
- Vérifier l'espace disponible et la mémoire du navigateur.
- Conserver les médias nécessaires, mais retirer les éléments inutiles dans un export de test.
- Ne pas supposer que l'échec provient forcément d'une image unique : le volume total, la décompression et la structure du paquet peuvent aussi jouer un rôle.

## Architecture du projet

Le projet est distribué sous la forme d'un fichier HTML autonome contenant les éléments de l'application :

- **HTML** : structure de la page, formulaires, boutons et zones d'affichage.
- **CSS** : styles, mise en page et adaptation aux différentes tailles d'écran.
- **JavaScript** : import, traitement des données, interactions, navigation et génération du résultat.
- **Ressources intégrées** : bibliothèques ou éléments nécessaires au fonctionnement, selon la version du fichier.

La logique est regroupée dans le document HTML afin de faciliter son utilisation et son partage. Cette organisation rend le projet simple à distribuer, mais un fichier unique de plusieurs mégaoctets peut être moins pratique à maintenir qu'un projet découpé en modules.

## Réalisation no-code avec ChatGPT

Anki2Web a été créé par une démarche **no-code assistée par ChatGPT**. L'interface, les explications, les modifications CSS/HTML et les ajustements du comportement ont été réalisés au fil d'échanges avec ChatGPT.

Cette description indique la méthode de réalisation, et non une garantie de qualité ou d'absence de bugs. ChatGPT peut produire des erreurs ou manquer certains cas particuliers. Les modifications doivent donc être accompagnées de tests et les anciennes versions conservées comme sauvegardes.

Le projet peut être décrit comme un **prototype logiciel généré et amélioré avec l'assistance d'une IA**, dont le fichier final contient bien du code HTML, CSS et JavaScript.

## Tests et état du projet

Le créateur du projet a effectué des essais d'import et de conversion sur plusieurs jeux de cartes et plusieurs types de cartes natifs d'Anki. Les essais réalisés ont été concluants : les cartes testées se sont converties et ont fonctionné comme attendu dans les scénarios vérifiés.

D'autres contrôles ciblés ont également été réalisés au cours du projet, notamment :

- Vérification de la syntaxe de blocs JavaScript.
- Essais de navigation et des commandes principales.
- Vérifications visuelles sur certaines largeurs d'écran.
- Essais d'import de fichiers texte et de paquets APKG.

**Ces résultats sont encourageants, mais ne constituent pas une certification exhaustive.** Ils ne garantissent pas le fonctionnement de tous les types de notes, modèles personnalisés, médias, extensions, navigateurs, systèmes d'exploitation ou appareils. Il est recommandé de tester le fichier HTML obtenu avec les cartes réelles destinées à être révisées ou partagées.

---

**Résumé :** Anki2Web est un convertisseur de cartes Anki vers HTML interactif, conçu en no-code avec l'aide de ChatGPT. Il facilite la consultation et le partage de cartes, mais les résultats doivent être vérifiés, surtout lorsque les paquets utilisent des médias ou des modèles complexes.
