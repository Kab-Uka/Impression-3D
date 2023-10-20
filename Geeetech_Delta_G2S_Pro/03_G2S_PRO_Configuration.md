# Configuration de l'imprimante

lien notice de démarrage : 

quelques liens :

repetier :

firmware :

## Les paramètres modifiés :

### Fichier configuration.h

#### 🔵 Ligne : #define EXTRUDERS

Définis le nombre d'extrudeurs que l'on veux/peux utiliser. Pour la G2S Pro, la valeur doit être égale à 2. Cependant poru démarrer, il est possible de ne configurer qu'un seul extrudeur. Dans ce cas, le centre d'impression sera décalé du centre du plateau de 13 mm environ vers l'avant. A prendre en compte lors des premiers essais pa rrapport à la circonférence du plateau.

Exemple: 

```
// This defines the number of extruders
#define EXTRUDERS 1	// l'imprimante ne reconnait qu'un seul extrudeur
```

```
// This defines the number of extruders
#define EXTRUDERS 2	// l'imprimante reconnait les 2 extrudeurs.
```

⚠**Attention**⚠: dans le cas d'une configuration à 2 extrudeurs, il faut veiller à paramétrer correctement la chauffe du second extrudeur spécifiquement.

⚠**Attention**⚠: Il faut aussi veiller à ce que les 2 extrudeurs soient très exactement à la même hauteur sous peine de voir vos impressions dégradées par celui des 2 extrudeurs qui est trop bas.

#### 🔵 Ligne : #define DELTA_DIAGONAL_ROD

La valeur de DELTA_DIAGONAL_ROD doit correspondre à la longueur des bras de l'imprimante, la mesure est à prendre au centre des poulies de part et d'autre de l'axe. 

Exemple :

```
// Center-to-center distance of the holes in the diagonal push rods.
#define DELTA_DIAGONAL_ROD 199		// Si cette valeur est fausse, les dimensions longueur et largeur seront fausses.
```

⚠**Attention**⚠: Chaque bras doit faire exactement la même dimension afin que l'impression soit correctement proportionnée sur chaque axe X, Y, et Z.

⚠**Attention**⚠: Dimensions d'objet à réduire => augmenter la valeur, dimension d'objet à augmenter => réduire la valeur.

#### 🔵 Ligne : define DELTA_RADIUS

Il s'agit d'un paramètre calculé à partir des dimensions de la tête d'impression et des bras, et qui permet à l'imprimante de savoir ou elle s trouve dans l'espace. Ce qu'il faut retenir, c'est que cette valeur détermine le suivis du plateua d'impression au plus près.

Ainsi, si le plateau est parfaitement plat, cetet valeur ne doit pas être modifiée. En revanche :

- si le plateau est convexe, ou que l'imprimante considère qu'il est convexe, il convient de décrémenter la valeur en dessous de 1
- Si le plateau est concave ou que l'imprimante considère qu'il est concave, il convient d'incrémenter la valeur au dessus de 1

⚠**Attention**⚠: Comment je sais que mon plateau est concave ou convexe ? C'est lorsque, une fois que les endstops sont parfaitements ajustés et que la tête d'impression est au même niveau sur les 3 points sous les endstops, et que celle-ci reviens au centre du plateau, elle n'est plus au même niveau que ces 3 points périphériques. Soit la tête est trop haute au point Z=0, auquel cas le plateau est à considérer comme concave (cuvette), soit elle est trop basse et touche le plateau avant d'atteindre Z=0, dans ce cas le plateau est considéré comme convexe (dôme).

Exemple : 

```
// Horizontal distance bridged by diagonal push rods when effector is centered.
//#define DELTA_RADIUS (DELTA_SMOOTH_ROD_OFFSET-DELTA_EFFECTOR_OFFSET-DELTA_CARRIAGE_OFFSET+1)  // Valeur originale
#define DELTA_RADIUS (DELTA_SMOOTH_ROD_OFFSET-DELTA_EFFECTOR_OFFSET-DELTA_CARRIAGE_OFFSET+1.3)
```

Dans ce cas de figure, la plateau après prmeier réglage des endstops était concave. Il a fallu ajuster la valeur par incrément de 0,1, puis régler de nouveau dans l'ordre le Z=0 au centre, puis le Z=0 sous les endstops, et revenir au Z=0 au centre. il s'agit d'un réglage itératif nécessaire pour obtenir un aplat correct des impressions sur le plateau circulaire d'une imprimante delta.
