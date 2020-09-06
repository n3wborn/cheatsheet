# Systemd : Journalctl et Systemctl


## Journalctl - Affiche les logs


#### Depuis le dernier boot :

```bash
journalctl -b
```

#### Aujourd'hui (minuit)

```bash
journalctl --since today
```


#### Entre 17H et 17H30

```bash
journalctl --since 17:00 --until 17:30
```

#### Afficher les erreurs

Depuis le dernier boot

```bash
journalctl -b -p err
```

#### Les n dernieres entrées

```bash
journalctl -n 20
```


#### En temps réel

```bash
journalctl -f
```

#### Ce qui concerne sshd

```bash
journalctl --since today _COMM=sshd
journalctl -b --no-pager | grep ssh
```


## Systemctl


#### Demarrer un service

```bash
systemctl start sshd
```


#### Arreter un service

```bash
systemctl stop sshd
```


#### Activer un service

```bash
systemctl enable sshd.service
```


#### Desactiver un service

```bash
systemctl disable sshd.service
```


#### Status d'un service

Ex irqbalance :

```bash
systemctl status irqbalance.service
```


#### Lister tous les services

```bash
systemctl list-unit-files
systemctl list-unit-files --type=service
```


#### Lister simplement les services en cours

```bash
systemctl --no-page --no-legend --plain -t service --state=running
```


#### Lister leurs dependances

```bash
systemctl list-dependencies
```


#### Lancer un runlevel (target) precis

```bash
systemctl isolate multi-user.targer
```


#### Afficher le "target" par defaut

```bash
systemctl get-default
```


#### Changer le "target"

Ici on lancera uniquement la "cible" network (une fois que le necessaire pour ce service est lancé)

```bash
systemctl set-default network.target
```


**Information**

Run level 0 is matched by poweroff.target (and runlevel0.target is a symbolic link to poweroff.target).
Run level 1 is matched by rescue.target (and runlevel1.target is a symbolic link to rescue.target).
Run level 3 is emulated by multi-user.target (and runlevel3.target is a symbolic link to multi-user.target).
Run level 5 is emulated by graphical.target (and runlevel5.target is a symbolic link to graphical.target).
Run level 6 is emulated by reboot.target (and runlevel6.target is a symbolic link to reboot.target).
Emergency is matched by emergency.target.


#### Mettre le systeme en veille

```bash
systemctl suspend
systemctl hibernate
systemctl hybrid-sleep
```

[Source](https://www.tecmint.com/create-new-service-units-in-systemd)
