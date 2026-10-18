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

- Un seul fichier : `index.html`, sans étape de build.
- [Three.js](https://threejs.org/) 0.160.0 chargé depuis jsDelivr (bloom, fusion de géométries).
- Monde généré procéduralement (bruit de Perlin, graine fixe) : relief, forêts, lacs, barrière de montagnes.
- Sons synthétisés avec la Web Audio API, aucun fichier audio.

## Lancer en local

Les modules ES demandent un serveur HTTP :

```bash
python3 -m http.server 8765
```

Puis ouvrir http://localhost:8765.
