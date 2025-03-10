# Exercices avec LVM (Logical Volume Manager)

## Étapes d'expérimentation

1. **Ajouter un nouveau PV (Physical Volume) au VG (Volume Group)** :
   ```bash
   sudo pvcreate /dev/sdX
   sudo vgextend mon_vg /dev/sdX
Créer un nouveau VG à partir d'un ou plusieurs PV :
bash
sudo vgcreate mon_nouveau_vg /dev/sdX /dev/sdY

Ajouter un nouveau LV (Logical Volume) :
Créez le LV :

bash
sudo lvcreate -L 10G -n mon_lv mon_vg
Formatez-le avec ext4 :

bash
sudo mkfs.ext4 /dev/mon_vg/mon_lv
Montez-le temporairement :

bash
sudo mkdir /mnt/mon_lv
sudo mount /dev/mon_vg/mon_lv /mnt/mon_lv
Ajoutez-le au démarrage dans /etc/fstab :

bash
echo "/dev/mon_vg/mon_lv /mnt/mon_lv ext4 defaults 0 2" | sudo tee -a /etc/fstab
Convertir ou créer un LV en RAID 1 (mirroring) ou RAID 0 (stripping) :

RAID 1 (mirroring) :

bash
sudo lvconvert --type raid1 -m 1 mon_vg/mon_lv
RAID 0 (stripping) :

bash
sudo lvconvert --type raid0 mon_vg/mon_lv
Créer un snapshot d'un LV :

bash
sudo lvcreate --size 1G --snapshot --name snapshot_lv /dev/mon_vg/mon_lv
sudo mount /dev/mon_vg/snapshot_lv /mnt/snapshot
Supprimer un LV inutile :

Démontez d'abord le volume :

bash
sudo umount /mnt/mon_lv
Supprimez le LV :

bash
sudo lvremove /dev/mon_vg/mon_lv
