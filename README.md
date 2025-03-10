# Exercices avec LVM (Logical Volume Manager)

## Étapes d'expérimentation

1. **Ajouter un nouveau PV (Physical Volume) au VG (Volume Group)** :
   - Utilisez la commande `pvcreate` pour transformer une partition ou un disque en volume physique.
   - Associez ce PV au VG existant avec `vgextend`.

2. **Créer un nouveau VG à partir d'un ou plusieurs PV** :
   - Regroupez plusieurs PV pour créer un VG en utilisant `vgcreate`.

3. **Ajouter un nouveau LV (Logical Volume)** :
   - Créez un LV avec `lvcreate`.
   - Formatez-le avec un système de fichier comme ext4 (via `mkfs.ext4`).
   - Montez-le au démarrage en configurant `/etc/fstab`.

4. **Convertir ou créer un LV en RAID 1 (mirroring) ou RAID 0 (stripping)** :
   - Configurez le RAID avec `lvconvert`.

5. **Créer un snapshot d'un LV** :
   - Capturez l'état actuel d'un volume logique avec `lvcreate --snapshot`.
   - Montez ce snapshot pour accéder à une copie.

6. **Supprimer un LV inutile** :
   - Démontez le volume logique, puis supprimez-le avec `lvremove`.

## Astuces
- Toutes ces opérations nécessitent les droits administratifs (`root`).
- Si vous utilisez une machine virtuelle pour vos expérimentations, créez un snapshot de la VM avant de commencer afin de revenir à l'état initial en cas de problème.

Ces exercices sont parfaits pour explorer les nombreuses fonctionnalités de LVM et tester votre maîtrise des commandes liées au stockage sous Linux. N'hésitez pas à demander plus de détails sur une commande ou étape particulière !
