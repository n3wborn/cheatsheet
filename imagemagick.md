# ImageMagick


## Resize

[ImageMagick - resize](https://www.imagemagick.org/script/command-line-options.php#resize)

[ImageMagick - options de géométrie](https://www.imagemagick.org/script/command-line-processing.php#geometry)

#### Définir une largeur maximale (en gardant les mêmes proportions)

`convert input.jpg -resize [desired width] output.jpg`

exemple :

`convert input.jpg -resize 100 output.jpg`


#### Modifier pour l'image pour qu'elle possède une largeur/hauteur précise

` convert input.jpg -resize widthxheight output.jpg`

Exemple :

`convert input.jpg -resize 150x150 output.jpg`


