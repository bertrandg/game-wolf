# Le Loup des Terres Sauvages

Jeu 3D isométrique dans le navigateur. Un loup explore de nuit une grande terre sauvage — clairières, forêts, six lacs et deux sommets, entourés de montagnes — à la recherche de neuf éclats de lune à rapporter au Cercle des Pierres Anciennes. Cerfs, chevaux, renards et une soixantaine d'autres animaux y vivent et fuient quand le loup hurle.

**Jouer en ligne :** https://bertrandg.github.io/game-wolf/

## Commandes

| Touche | Action |
| --- | --- |
| ZQSD / WASD / flèches | se déplacer |
| Espace | sauter |
| Maj | courir |
| H | hurler (fait fuir les animaux proches) |
| Molette | zoom |
| M | couper / remettre le son |

Sur mobile, des boutons tactiles s'affichent à l'écran.

## Technique

- Le jeu tient dans `index.html`, sans étape de build. Les modèles 3D sont dans `assets/`.
- [Three.js](https://threejs.org/) 0.160.0 chargé depuis jsDelivr (bloom, chargement glTF, clonage des squelettes).
- Monde généré procéduralement (bruit de Perlin, graine fixe) sur environ 720 × 720 unités.
- Sons synthétisés avec la Web Audio API, aucun fichier audio.
- Loup et animaux : pack *Ultimate Animated Animals* de [Quaternius](https://quaternius.com/), licence CC0. Les modèles ont été convertis en GLB compressé avec [glTF Transform](https://gltf-transform.dev/) (quantification, animations inutilisées retirées) : environ 330 Ko par animal au lieu de 3 Mo.

### Performances

- Terrain découpé en 12 × 12 blocs, arbres, rochers et champignons regroupés par bloc : seuls les blocs visibles sont dessinés.
- La hauteur du sol est lue dans une grille précalculée au lieu de recalculer le bruit.
- Les feux follets flottent grâce à un shader : aucun calcul processeur par image.
- Les animaux loin du loup sont cachés et simulés grossièrement deux fois par seconde, sans animation.

## Lancer en local

Les modules ES demandent un serveur HTTP :

```bash
python3 -m http.server 8765
```

Puis ouvrir http://localhost:8765.
