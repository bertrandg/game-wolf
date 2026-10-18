# Le Loup des Terres Sauvages

Jeu 3D isométrique dans le navigateur. Un loup explore une grande terre sauvage — clairières, forêts, six lacs et deux sommets, entourés de montagnes. La nuit, il cherche sept éclats de lune à rapporter au Cercle des Pierres Anciennes : le monde bascule alors en plein jour, couleurs éclatantes et chants d'oiseaux. Sept cristaux de soleil permettent ensuite de rappeler la nuit, et le cycle recommence avec de nouveaux cristaux. Cerfs, chevaux, renards et une soixantaine d'autres animaux y vivent et fuient quand le loup hurle.

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
| F | plein écran |

Sur mobile : joystick à gauche (poussé à fond pour courir), boutons Sauter et Hurler à droite, zoom à deux doigts. Les boutons son et plein écran sont sous la mini-carte (le plein écran n'existe pas sur iPhone, le bouton y est masqué).

## Technique

- Le jeu tient dans `index.html`, sans étape de build. Les modèles 3D sont dans `assets/`.
- [Three.js](https://threejs.org/) 0.160.0 chargé depuis jsDelivr (bloom, chargement glTF, clonage des squelettes).
- Monde généré procéduralement (bruit de Perlin, graine fixe) sur environ 720 × 720 unités.
- Sons synthétisés avec la Web Audio API, aucun fichier audio : vent et nappe grave la nuit, accord chaud, brise et oiseaux le jour.
- Bascule jour / nuit : chaque sommet du terrain porte une couleur de nuit et une de jour, mélangées dans le shader ; lumières, brouillard, eau, végétation et particules suivent le même curseur.
- Arbres, buissons, fleurs, fougères, herbe, rochers, galets et champignons : *Stylized Nature MegaKit* (version gratuite) de [Quaternius](https://quaternius.com/), licence CC0. 25 modèles regroupés dans `assets/nature.glb` (textures réduites à 512 px en WebP, cartes de relief retirées) : environ 2 Mo au lieu de 34 Mo.
- Loup et animaux : pack *Ultimate Animated Animals* de [Quaternius](https://quaternius.com/), licence CC0. Les modèles ont été convertis en GLB compressé avec [glTF Transform](https://gltf-transform.dev/) (quantification, animations inutilisées retirées) : environ 330 Ko par animal au lieu de 3 Mo.

### Performances

- Terrain découpé en 12 × 12 blocs, arbres, rochers et champignons regroupés par bloc : seuls les blocs visibles sont dessinés.
- La hauteur du sol est lue dans une grille précalculée au lieu de recalculer le bruit.
- L'herbe n'existe qu'autour du loup : un nombre fixe de touffes est replacé quand il change de case, aux mêmes endroits du monde à chaque passage. Elle ondule grâce au shader.
- Les feux follets flottent grâce à un shader : aucun calcul processeur par image.
- Les animaux loin du loup sont cachés et simulés grossièrement deux fois par seconde, sans animation.
- Qualité adaptative : sur mobile, résolution limitée à 1×, bloom en demi-résolution et ombres plus légères. Si les images ralentissent (moins de 40 par seconde), le jeu baisse d'un cran (résolution, bloom, ombres), puis remonte quand tout redevient fluide.

## Lancer en local

Les modules ES demandent un serveur HTTP :

```bash
python3 -m http.server 8765
```

Puis ouvrir http://localhost:8765.
