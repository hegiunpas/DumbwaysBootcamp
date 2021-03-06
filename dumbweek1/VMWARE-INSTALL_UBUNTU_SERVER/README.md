# INSTALL UBUNTU SERVER 18.04 IN VIRTUAL BOX

1. masuk ke halaman awal virtual box dan pilih New, lalu isikan nama, NIS, type Linux dan version. Next

![1](assets/01.png)

2. tentukan berapa banyak RAM yang akan diberikan, disini saya memberikan 1024 MB. Next

![2](assets/02.png)

3. pilih Create a virtual hard disk now

![3](assets/03.png)

4. pilih VDI

![4](assets/04.png)

5. pilih Dynamically allocated

![5](assets/05.png)

6. tentukan lokasi penyimpanan virtual hard disk file dan jumlah ukuran hard disk

![6](assets/06.png)

7. buka menu settings untuk VM yang sudah dibuat tadi, pada submenu storage tambahkan file iso ubuntu server untuk diinstal nantinya

![7](assets/07.png)

8. pada submenu system, ubah urutan boot order seperti dibawah agar proses booting berjalan baik dan tak perlu mengubah instalasi boot setelah selesai install

![8](assets/08.png)

9. pada submenu network, pilih bridged adapter dan pilih Name adapter yang mengarah ke wlan host

![9](assets/09.png)

10. setelah selesai itu, nyalakan VM yang sudah kita buat dan ikuti langkah-langkah dibawah ini

![10](assets/10.png)
![10.1](assets/11.png)
![10.2](assets/12.png)

11. pada bagian instalasi configuration interface kita ubah menjadi static agar IP tidak berubah ubah ketika VM reboot, pilih interface yang ada lalu pilih Edit IPv4

![11](assets/13.png)

12. Isikan agar satu segmen IP dengan host, disini IP host wlan saya adalah 192.168.43.246 . Jika sudah, pilih save dan Done

![12](assets/14.png)
![12.1](assets/15.png)
![12.2](assets/16.png)
![12.3](assets/17.png)

13. untuk partisi manual kita pilih custom storage layout, Done

![13](assets/18.png)

14. pilih VBOX_HARDISK yang ada, lalu pilih Add GPT Partition. berikan 1GB untuk swap dan sisanya untuk storage user. Jika sudah, enter Done dan Continue

![14](assets/19.png)
![14.1](assets/20.png)
![14.2](assets/21.png)
![14.3](assets/22.png)
![14.4](assets/23.png)

15. tentukan profile setup, pastikan untuk membuat username dan password yang mudah diingat

![15](assets/24.png)

16. Install OpenSSH server, Done

![16](assets/25.png)
![16.1](assets/26.png)

17. tunggu hingga proses instalasi selesai dan pilih reboot

![17](assets/27.png)
![17.1](assets/28.png)

18. selesai dan jangan lupa lakukan ping apakah VM terhubung ke internet atau tidak

![18](assets/29.png)
