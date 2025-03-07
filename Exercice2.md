 # Exercice 2 : Manipulations pratiques sur VM Linux

Partie 1 : Gestion des utilisateurs

Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.

![image](https://github.com/user-attachments/assets/2ecc4ab2-1635-43b4-94ca-b98ab7602527)


Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?

. Ajouter l'utilisateur au groupe sudo
. Configurer SSH
. Activer 2FA
. Surveiller les logs

Partie 2 : Configuration de SSH
Un serveur SSH est lancé sur le port par défaut.
Il est possible de s'y connecter avec n'importe quel compte, y compris le compte root.

Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.

![image](https://github.com/user-attachments/assets/d7820562-64e7-4a3a-b077-3b870cbc9aff)


Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.

![image](https://github.com/user-attachments/assets/1d10b7d6-1dd7-4c9d-9251-4d6229d0cc89)


Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe

![image](https://github.com/user-attachments/assets/6eb7fab9-1811-4559-9144-375b1337942b)


Partie 3 : Analyse du stockage

Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?
devtmpfs, tmpfs, ext2, ext4

![image](https://github.com/user-attachments/assets/1b64a9b2-f34d-4ee7-aad4-ca5d53c17e11)

Q.2.3.2 Quel type de système de stockage ils utilisent ?
disque physique, raid1, LVM

![image](https://github.com/user-attachments/assets/c710461c-2df0-4c97-a094-f2229b443964)


Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID

Disque de 8go ajouté Nom sdb

![image](https://github.com/user-attachments/assets/f1005942-4136-4f66-8ba1-a33df479b4a2)


Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.

Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

Partie 4 : Sauvegardes
Le logiciel bareos est installé sur le serveur.
Les composants bareos-dir, bareos-sd et bareos-fd sont installés avec une configuration par défaut.

Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.

bareos-dir (Director) : Contrôle et coordonne l'ensemble des opérations de sauvegarde et de restauration. Il prend les décisions sur quoi sauvegarder, quand, et où stocker les données.
bareos-sd (Storage Daemon) : Gère le stockage physique des données de sauvegarde. Il écrit et lit les données sur les supports de stockage.
bareos-fd (File Daemon) : Agent client installé sur chaque machine à sauvegarder. Il est chargé d'accéder aux fichiers locaux sur la machine cliente, de les lire pour les sauvegardes et de les écrire lors des restaurations.

Partie 5 : Filtrage et analyse réseau
Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

![image](https://github.com/user-attachments/assets/fd102eeb-2608-4e1b-9f6c-384113c42d6b)

Q.2.5.2 Quels types de communications sont autorisées ?

![image](https://github.com/user-attachments/assets/8679a84a-41bc-446c-a67f-4e3a5727b15d)

tcp port 22
ICMP (IPv4)
ICMP (IPv6)

Q.2.5.3 Quels types sont interdit ?

tous les paquets entrants qui ne correspondent à aucune règle de la chaîne seront supprimés

Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.

Rappel : Bareos utilise les ports TCP 9101 à 9103 pour la communication entre ses différents composants.

Partie 6 : Analyse de logs
Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :

La date et l'heure de la tentative
L'adresse IP de la machine ayant fait la tentative



Q.2.6.1 

ok : /24
nr : 
faux : 

