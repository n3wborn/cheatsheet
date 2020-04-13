# SSH

**Créer une paire de clé**

`$ ssh-keygen -b 4096 -t rsa -f ~/.ssh/ma-cle-ssh`

**Envoyer sa clé à un serveur**

`$ ssh-copy-id ma-cle-ssh.pub mon-login-distant@serveur-distant`

**Se connecter à un serveur**

`$ ssh mon-login-distant@serveur-distant`


**Tunnel ssh - Port forwarding**

Si seuls certains ports sont autorisés sur votre poste client, il est possible
de les utiliser à la place du port par défaut (22) pour vous connecter sur un
port précis sur le serveur distant.

Par exemple, si vous pouvez utiliser le port 2200 et voulez vous connecter sur le port 80 du serveur distant :

`$ ssh -L 2200:serveur.distant.org:80 mon-login-distant@serveur.distant.org`

Je me connecte à celui ci en modifiant mes preferences de connexion dans mon navigateur en mettant cela en proxy socks:
- adresse proxy : 127.0.0.1
- port proxy : 2200

Ou, si j'utilise un navigateur sur mon terminal, je peux taper taper ceci :

`$ w3m http://localhost:2200`

Un autre exemple, dans celui-ci je vais atteindre un hote distant, qui fait
partie du reseau auquel mon serveur distant est connecté.

`$ ssh  -L 0.0.0.0:9999:10.10.10.10:80 user@remoteserver`

Ici, on redirige tout ce qui arrive dans notre port 9999 vers le serveur web
de l'interface possédant l'ip 10.10.10.10 par le biais de notre serveur distant.

Pour le serveur web, la requete à pour origine notre serveur distant.
Par contre, tout ce qui se passe entre notre serveur distant et le serveur web
ne passe plus par notre tunnel.


**Tunnel ssh - Reverse Tunnel**

On peut également faire l'inverse.

`$ ssh -R 0.0.0.0:1999:127.0.0.1:902 192.168.1.100 user@remoteserver`

Ici, toute connection au port 1999 du serveur distant sera redirigée vers notre
client possédant l'ip 192.168.1.100 par le port 902



**Tunnel ssh - Proxy dynamique**

Similaire, mais plus puissant, il peut être très interessant d'utiliser cette
méthode. [Voici Un lien qui explique ça](https://hackertarget.com/ssh-examples-tunnels/)

`$ ssh -D 0.0.0.0:8888 mon-utilisateur@serveur-distant`

Ceci va démarrer un serveur proxy disponible pour toutes mes interfaces reseau
(0.0.0.0) sur le port 8888.

Comme pour la commande précédente, il faut configurer les applications pour
passer par ce tunnel. Ainsi, du point de vue service auquel nous accédons (par
le biais de notre serveur ssh distant) nous aurons comme ip celle du serveur sur
lequel nous somme connecté. Ici serveur-distant.

Un autre exemple, si je veux me connecter à une machine windows via le protocole
rdp, je peux utiliser proxychains (en le configurant pour passer par notre
tunnel) comme ceci:

`$ proxychains rdesktop $RemoteWindowsServer`
