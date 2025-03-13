# LVM : Logical Volume Manager (LVM) est un ensemble d'outil permettant une gestion avancée du stockage sous Linux
## Installation de Debian avec LVM
Lors de l’installation de Debian, choisissez le partitionnement :

➡ Assisté - utiliser tout un disque avec LVM

➡ Partition /home séparée

Cela crée un groupe de volumes debian-vg contenant deux volumes logiques 

root (/)

home (/home)
Ajoutez un second disque virtuel /dev/sdb à votre machine.

1. Ajoute un nouveau disque à la machine et ajoute le au groupe de volume debian-vg pour au moins doubler l'espace du groupe de volume 
   
🔹Initialiser le disque en Physical Volume (PV)

   ![image](https://github.com/user-attachments/assets/e4b5736f-b0fb-4642-816e-275181d3994d)

🔹 Étendre le Volume Group (debianserver-vg)

   ![image](https://github.com/user-attachments/assets/9c9ed6de-8baa-4121-8098-a062c191c785)


2. La création d'un snapshot du LV home
   
![image](https://github.com/user-attachments/assets/5cb300c8-1725-4c73-ba16-654b031a957e)

Vérification :

![image](https://github.com/user-attachments/assets/3d63c3db-3f46-4742-a5d4-8f29905a95ec)

3. Il y a bien création d'un dossier home-snap et montage du snapshot dans ce dossier
   🔹 Créer le point de montage
 ```bash
sudo mkdir /home-snap
 ```

🔹 Monter le snapshot
 ```bash
sudo mount /dev/debian-vg/home-snap /home-snap
 ```


🔹 Vérifier les systèmes de fichiers montés
 ```bash
df -h
 ```

![image](https://github.com/user-attachments/assets/cb804a66-ed27-4e4b-ae10-b53724aaa3ff)

4. L'affichage du contenu de /home-snap affiche un contenu identique à /home

![image](https://github.com/user-attachments/assets/31ff8da1-081f-4936-9a4e-0712198d100b)


5. L'affichage des systèmes de fichiers actuellement montés n'affiche plus /home-snap
   🔹 Démonter /home-snap
 ```bash
sudo umount /home-snap
 ```

Vérification :
 ```bash
df -h
 ```
![image](https://github.com/user-attachments/assets/d2bfb7fa-aa03-438f-9a74-7b164a8815a4)

6. L'affichage des LV n'affiche plus le snapshot et le LV home n'est plus la source d'aucun snapshot

 ![image](https://github.com/user-attachments/assets/c2d7a545-b2d8-4a9b-b099-4eab9de80fce)

Vérification :

![image](https://github.com/user-attachments/assets/6488a120-955e-4b21-b60a-291d8a753057)








