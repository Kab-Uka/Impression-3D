# Configuration de l'imprimante

lien notice de démarrage : 

quelques liens :

repetier :

firmware :

## Les paramètres modifiés :

### Fichier configuration.h

#### Ligne : #define EXTRUDERS

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

#### Ligne : #define DELTA_DIAGONAL_ROD

La valeur de DELTA_DIAGONAL_ROD doit correspondre à la longueur des bras de l'imprimante, la mesure est à prendre au centre des poulies de part et d'autre de l'axe. 

Exemple :

```
// Center-to-center distance of the holes in the diagonal push rods.
#define DELTA_DIAGONAL_ROD 199		// Si cette valeur est fausse, les dimensions longueur et largeur seront fausses.
```

⚠**Attention**⚠: Chaque bras doit faire exactement la même dimension afin que l'impression soit correctement proportionnées sur chaque axe X, Y, et Z.

⚠**Attention**⚠: Dimensions d'objet à réduire => augmenter la valeur, dimension d'objet à augmenter => réduire la valeur
