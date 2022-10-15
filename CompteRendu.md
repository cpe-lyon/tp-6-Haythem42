BELHADJ MANSOUR Haythem<br>
3ICS - CPE Lyon - 2022-2023<br>
Administration Système sous Linux

# TP 6 - Services réseau

## Exercice 1. Adressage IP (rappels)

On commence par trier les sous-réseaux en fonction du nombre de machines, puis on découpe le réseau en sous-réseaux.

* Sous-réseau 3 : 52 machines

Adresse de sous-réseau : 172.16.0.0 /26
Adresse de broadcast : 172.16.0.63 /26
Adresse de la première machine configurée : 172.16.0.1 /26
Adresse de la dernière machine configurée : 172.16.0.62 /26

* Sous-réseau 1 : 38 machines

Adresse de sous-réseau : 172.16.0.64 /26
Adresse de broadcast : 172.16.0.127 /26
Adresse de la première machine configurée : 172.16.0.65 /26
Adresse de la dernière machine configurée : 172.16.0.126 /26

* Sous-réseau 6 : 37 machines

Adresse de sous-réseau : 172.16.0.128 /26
Adresse de broadcast : 172.16.0.191 /26
Adresse de la première machine configurée : 172.16.0.129 /26
Adresse de la dernière machine configurée : 172.16.0.190 /26

* Sous-réseau 4 : 35 machines

Adresse de sous-réseau : 172.16.0.192 /26
Adresse de broadcast : 172.16.0.255 /26
Adresse de la première machine configurée : 172.16.0.193 /26
Adresse de la dernière machine configurée : 172.16.0.254 /26

* Sous-réseau 5 : 34 machines

Adresse de sous-réseau : 172.16.1.0 /26
Adresse de broadcast : 172.16.1.63 /26
Adresse de la première machine configurée : 172.16.1.1 /26
Adresse de la dernière machine configurée : 172.16.1.62 /26

* Sous-réseau 2 : 33 machines

Adresse de sous-réseau : 172.16.1.64 /26
Adresse de broadcast : 172.16.1.127 /26
Adresse de la première machine configurée : 172.16.1.65 /26
Adresse de la dernière machine configurée : 172.16.1.126 /26

* Sous-réseau 7 : 25 machines

Adresse de sous-réseau : 172.16.1.128 /27
Adresse de broadcast : 172.16.1.159 /27
Adresse de la première machine configurée : 172.16.1.129 /27
Adresse de la dernière machine configurée : 172.16.1.158 /27

Vérification sur le site https://subnettingpractice.com/vlsm.html.

## Exercice 2. Préparation de l'environnement

1 - Sur VSphere :
Pour le client : "Modifier les paramètres" -> "Adapteur réseau 1" parcourir et prendre "ICS_E5_2005" -> "OK"
Pour le serveur : "Modifier les paramètres" -> "Ajouter un périphérique" sélectionner "Adapteur réseau" -> "Adapteur réseau 2" parcourir et prendre "ICS_E5_2005" -> "OK".

Sur VirtualBox :
Pour le client : **Adapter 1** : "Configuration" -> "Réseau" -> "Mode d'accès réseau" -> "Réseau privé hôte"
Pour le serveur : **Adapter 1** : "Configuration" -> "Réseau" -> "Mode d'accès réseau" -> "Réseau privé hôte"
                  **Adapter 2** : "Configuration" -> "Réseau" -> "Mode d'accès réseau" -> "NAT"

Débrancher les câbles branchés et vérifier que les adresses MAC sont différentes.

2 - Pour vérifier la présence des interfaces réseau, on tape la commande `ip a`.On remarque la présence de 2 interfaces réseau (sans compter *lo*) : enp0s3 et enp0s8. **lo** est l'interface de loopback. (En général, on lui attribue l'adresse du localhost.)

3 - Pour supprimer complètement un paquet, on va utiliser la commande `sudo apt purge nom-paquet`. Ici, on utilisera `sudo apt purge cloud-init`. A faire sur le client et le serveur.

4 - Pour renommer le nom du serveur, on va utiliser `sudo hostname nom`. Ici, on va utiliser `sudo hostname serveur ̀. On peut ausi uiliser la commande `sudo sh -c "echo serveur > /etc/hostname"̀. On remarquera qu'après un reboot, l'hostname a bien été modifié.


## Exercice 3. Installation du serveur DHCP

1 - Pour installer le paquet isc-dhcp-server, on utilise la commande ̀sudo apt install isc-dhcp-server`.

2 - Après avoir modifié le fichier /etc/netplan/00-installer-config.yaml pour lui attribuer une adresse statique, on tape la commande `sudo netplan try` pour vérifier que la configuration soit bien correcte. En l'absence d'erreur, on peut ensuite taper la commande `sudo netplan apply` pour valider la configuration.

3 - Le **default-lease-time** correspond à la durée par défaut du bail de la configuration donnée en seconde. Le **max-lease-time** correspond quant à lui à la durée maximale du bail de la configuration donnée en seconde.

4 - On édite le fichier *isc-dhcp-erver* en ajoutant l'interface de notre réseau dans "INTERFACESv4". Dans notre cas, il vaut **enp0s3**.

5 - Après redémarrage, avec la commande `systemctl status isc-dhcp-server`, on peut remarquer que le serveur est actif.

6 - Comme précédemment avec le serveur, on reprend les mêmes commandes. Après un reboot, on remarque que tout a été modifié.

7 - 
