# ImageMagick


## Resize

[ImageMagick - resize](https://www.imagemagick.org/script/command-line-options.php#resize)

[ImageMagick - options de géométrie](https://www.imagemagick.org/script/command-line-processing.php#geometry)

### Définir une largeur maximale (en gardant les mêmes proportions)

`convert input.jpg -resize [desired width] output.jpg`

exemple :

`convert input.jpg -resize 100 output.jpg`


### Modifier pour l'image pour qu'elle possède une largeur/hauteur précise

`convert input.jpg -resize widthxheight output.jpg`

Exemple :

`convert input.jpg -resize 150x150 output.jpg`

### Modifier la couleur précise par une autre

`for filename in *.png; do file=`echo "$filename"` convert $filename -fuzz 100% -fill '#CCCCCC'-opaque "#CFDFE9" ~/Bureau/res/"$filename";done`

### Idem en modifiant aussi sa taille

`for filename in *.png; do file=`echo "$filename"`;convert $filename -fuzz 100% -fill '#CCCCCC' -resize 24x24 -opaque white $file;done`

### Faire un negatif d'une photo

`convert photo-identite.jpg -negate photo-identite-negate.jpg`

## Rotate

[ImageMagick - rotate](https://imagemagick.org/Usage/distorts/#rotate_methods)

### Rotation à 180 degrés

`convert -rotate "180" in.jpg out.jpg`

### Rotation à 90 degrés

Vers la droite

`convert -rotate "90" in.jpg out.jpg`

Vers la gauche

`convert -rotate "-90" in.jpg out.jpg`
