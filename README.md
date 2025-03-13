# LVM : Logical Volume Manager (LVM) est un ensemble d'outil permettant une gestion avancée du stockage sous Linux
## Installation de Debian avec LVM
Lors de l’installation de Debian, choisissez le partitionnement :
➡ Assisté - utiliser tout un disque avec LVM
➡ Partition /home séparée

Cela crée un groupe de volumes debian-vg contenant deux volumes logiques :

root (/)
home (/home)
Ajoutez un second disque virtuel /dev/sdb à votre machine.

1. Ajoute un nouveau disque à la machine et ajoute le au groupe de volume debian-vg pour au moins doubler l'espace du groupe de volume :
   
🔹Initialiser le disque en Physical Volume (PV)

   ![image](https://github.com/user-attachments/assets/e4b5736f-b0fb-4642-816e-275181d3994d)

🔹 Étendre le Volume Group (debianserver-vg)

   ![image](https://github.com/user-attachments/assets/9c9ed6de-8baa-4121-8098-a062c191c785)


2. La création d'un snapshot du LV home
![image](https://github.com/user-attachments/assets/5cb300c8-1725-4c73-ba16-654b031a957e)

Vérification :
![image](https://github.com/user-attachments/assets/3d63c3db-3f46-4742-a5d4-8f29905a95ec)










