# Memo javascript


**variables**

    var chaine = "string";
    var entier = 10;
    var float = 10.00;
    var booleen = true;
    var tableau = ["valeur1", "valeur2"];
    var objet = {cle:"valeur", id="prenom", mdp:"password"};

    let var-jetable = 1;
    const vitesse-lumiere = "tres tres vite";


**boucles**

1. if

    if (val1 <= val2) {
        console.log('val1 est plus petit');
    }
    else if (val1 >= val2) {
        console.log('val1 est plus grand');
    }
    else {
        console.log('erreur');
    }

2. for

    for (i=1; i<10; i++) {
        ...;
    }


    for (; i<10;){
        ...;
    }


3. do

    do {
        ...;
    }
    while (val1 < val2)


4. switch

    switch (val1) {
        case 0:
            ...;
            break;
        case 1:
            ...;
            break;
        default:
            ...;
    }


**commentaires**

    // un commentaire

    /*
     * un autre commentaire
     */
