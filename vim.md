# Vim

## Ouvrir/fermer tous les replis

    zR
    zM

## Si un replis est fermé/ouvert, ouvre/ferme le recursivement

    zA

## Position précédente/suivante (jumplist)

    <ctrl-o> / <ctrl-i>

## Redimensionner les fenetres pour qu'elles aient toutes la même dimension

    <ctrl-w> =

## split vertical / horizontal

    <ctrl-w> v
    <ctrl-w> s

## Scroll Back / Forward

    <ctrl-b>
    <ctrl-f>

## Mettre en uppercase plusieurs lettres, mots

3 lettres, 3 mots, ligne entière :

    gU3(fleche droite)
    gU3w(fleche droite)
    gUU

## Utiliser le presse-papier du système

**Une fois une portion de texte sélectionnée, taper dans vim**

    "+y

et c'est dans le presse-papier, ctrl-v collera le contenu

**Pour coler dans vim**

    "+p

## wrap la ligne, paragraphe ou la sélection

    gq
    gqq
    gqj

## Incémenter/Décrémenter

    CTRL-A/CTRL-X

## connaitre le nombre de mots

    :! wc %

## supprimer les espaces en fin de ligne

    :%s/\s\+$//e

## supprimer les caractere ^M en fin de ligne (eol windows)

    :%s/[ctrl+v][ctrl+m]//

## afficher la limite de textwidth

    :set cc=78

## ou (voir aussi :help colorcolumn)

    :let &cc = &tw

## ouvrir deux fichiers - split horizont

    $ vim -o file_1 file_2

## ouvrir deux fichiers - split vertical

    $ vim -O file_1 file_2

## substitution à partir d'une ligne "#" à la ligne "#"

    :#,#s/old/new/g

## Aller au tag ouvrant/fermant ou debut/fin de boucle (:help match)

    :g%

    %

## Affiche les derniers changements depuis la derniere sauvegarde

    :w !diff % –

## Réutiliser une recherche précédente dans une substitution

    :%s//autre mot/

## insérer le contenu d'un fichier

    :r fichier

## supprimer/changer le contenu entre deux tags

    dit
    cit

## changer le contenu jusqu'au caractere "

    ci"

# plugin vim-surround

**Ce plugin sait utiliser plusieurs "actions"**

- Delete Surroundings `ds`
- Chance Surroundings `cs`
- You Surround `ys`

**Plusieurs tag-blocks**

- `w` pour `word`
- `W` pour `WORD`
- `s` pour `sentence`
- `p` pour `paragraph`

**Plusieurs tags**

- `b` pour `()`
- `B` pour `{}`
- `r` pour `[]`
- `a` pour `<>`

### Supprimer des guillemets autour d'un mot

Le `*` sert à indiquer ou se trouve le curseur

|   Old text              |   Command       | New text                    |
|:----------------------  |:---------------:|:---------------------------:|
|  `"Hello *world!"`      |     `ds"`       |  `Hello world!`             |
|  `[123+4*56]/2`         |     `cs])`      |  `(123+456)/2`              |
|  `"Look ma, I'm *HTML!"`|     `cs"<q>`    |  `<q>Look ma, I'm HTML!</q>`|
|  `if *x>3 { `           |     `ysW(`      |  `if ( x>3 ) {`             |
|  `my $str = *whee!; `   |    `vllllS'`    | `my $str = 'whee!';`        |


Par exemple, au milieu de la phrase suivante,

`
        <div>this is a test</div>
`

tapez `ysst`
vim vous affiche le crochet du tag qui sera ajouté
tapez `div>`
Et vous avez toutes la lignes précédente qui est entourée d'un nouveau `<div>`
Comme ceci:

`
        <div><div>this is a test</div></div>
`

**delete surroundings ne prends que l'argument à supprimer**

**change surroundings a besoin de l'argument à remplacer et son remplacant**

Une autre astuce sympa pour le html, avec la ligne donnée en exemple plus haut.
Taper `yss` ("You Surround Sentence") et taper `ctrl-T`
De nouveau un tag ouvrant est affiché dans vim, mettez par exemple `div>` et vous obtenez :


`
        <div>
        <div>this is a test</div>
        </div>
`



