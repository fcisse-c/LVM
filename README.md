# Exercices avec LVM (Logical Volume Manager)

Ajouter un disque et l'intégrer à debian-vg
🔹 Ajouter un disque
Ajoutez un second disque virtuel /dev/sdb à votre machine.


1. Ajoute un nouveau disque à la machine et ajoute le au groupe de volume debian-vg pour au moins doubler l'espace du groupe de volume :
   ```bash
  sudo pvcreate /dev/sdb
  ```




