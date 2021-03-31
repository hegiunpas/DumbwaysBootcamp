# SETUP NETWORK STATIC IP ON VM

1. buka virtual box, masuk ke menu settings VM yang dipilih. Pada submenu Network, ubah network adapter menjadi Bridge Adapter dan pilih interface host yang terhubung ke internet

![1](assets/02.png)
![1.2](assets/01.png)

2. selanjutnya, login ke VM dan edit file `/etc/netplan/00-installer-config.yaml`

![2](assets/03.png)

3. tuliskan konfigurasi file seperti dibawah ini

![3](assets/04.png)

4. ketikkan perintah `sudo netplan apply` untuk menerapkan perubahan network dan perintah `ip a` untuk melihat informasi pada setiap interfaces. Lakukan perintah `ping -c 4 8.8.8.8` untuk mengetahui apakah VM terhubung ke internet atau tidak

![4](assets/05.png)

5. terakhir, lakukan percobaan ssh pada sisi host ke VM dengan menggunakan perintah `ssh -l <username> <ip tujuan>`

![5](assets/06.png)
