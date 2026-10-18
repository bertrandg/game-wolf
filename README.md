# Le Loup des Terres Sauvages

Jeu 3D isométrique dans le navigateur. Un loup explore de nuit une terre sauvage — clairières, forêts, lacs et montagnes — à la recherche de sept éclats de lune à rapporter au Cercle des Pierres Anciennes.

**Jouer en ligne :** https://bertrandg.github.io/game-wolf/

## Commandes

| Touche | Action |
| --- | --- |
| ZQSD / WASD / flèches | se déplacer |
| Espace | sauter |
| Maj | courir |
| H | hurler à la lune |
| Molette | zoom |
| M | couper / remettre le son |

Sur mobile, des boutons tactiles s'affichent à l'écran.

## Technique

- Le jeu tient dans `index.html` (plus le modèle du loup dans `assets/`), sans étape de build.
- [Three.js](https://threejs.org/) 0.160.0 chargé depuis jsDelivr (bloom, fusion de géométries).
- Monde généré procéduralement (bruit de Perlin, graine fixe) : relief, forêts, lacs, barrière de montagnes.
- Sons synthétisés avec la Web Audio API, aucun fichier audio.
- Loup animé (marche, galop, saut, repos) : modèle `assets/wolf.gltf` du pack *Ultimate Animated Animals* de [Quaternius](https://quaternius.com/), licence CC0. Un loup simplifié s'affiche pendant le chargement et sert de secours.

## Lancer en local

Les modules ES demandent un serveur HTTP :

```bash
python3 -m http.server 8765
```

Puis ouvrir http://localhost:8765.
