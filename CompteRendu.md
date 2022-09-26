BELHADJ MANSOUR Haythem
3ICS - CPE Lyon - 2022-2023
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

2.
