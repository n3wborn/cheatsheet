# Install Docker sur Fedora 32

A ce jour (2020-06-26), Docker n'est pas supporté sur Fedora 32.
[Des](https://podman.io/getting-started/) [alternatives](https://buildah.io/) existent. Mais si on prefere rester sur Docker pour le moment...


## Suppression des versions insallées

On commence par supprimer les éventuels conflits entre les différentes versions.

```bash
# dnf remove docker-*
# dnf config-manager --disable docker-*
```


## Ajustements du noyau

CGroups et NTFables (pour le pare-feu) sont deux nouveautés dans les 2 dernières versions de Fedora.
Docker ne les supportant pas il va falloir ajuster un peu tout ça


### CGroups

On repasse à l'ancienne version de CGroups (supportée par Docker)

```bash
# grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```


### Firewall

On whitelist Docker dans les zones trusted et FedoraWorkstation du firewall.

```bash
# firewall-cmd --permanent --zone=trusted --add-interface=docker0
# firewall-cmd --permanent --zone=FedoraWorkstation --add-masquerade
```


## Install de Moby

Maintenant on est pret à installer Moby (la version open-source de Docker).

```bash
# dnf install moby-engine docker-compose
```


## Reboot

Une fois n'est pas coutume, on reboot une fois l'install terminée.
Car qui dit modifications du noyau dit reboot !

```bash
# systemctl reboot
```

Enjoy !
