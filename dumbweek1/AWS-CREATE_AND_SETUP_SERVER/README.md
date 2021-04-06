# CREATE & SETUP PUBLIC SERVER FOR REVERSE PROXY

1. masuk ke AWS Management Console & masuk ke `service > EC2 > Instances` lalu pilih Launch instances

![1](assets/01.png)

2. pilih OS yang akan dibuat untuk instances, disini saya memilih Ubuntu Server 18.04 LTS

![2](assets/02.png)

3. pilih spesifikasi type Instance, saya memilih t2.micro

![3](assets/03.png)

4. pada step Configure Instance Details, yang perlu diubah disini yaitu `Auto-assign Public IP = Disable` untuk yang lainnya biarkan default

![4](assets/04.png)

5.untuk storage server, saya memberikan sebesar 10 GiB

![5](assets/05.png)

6. pada Configure Security Group, tambahkan 3 rule `SSH (22), HTTP(80), HTTPS(443)`

![6](assets/06.png)

7. Lalu pilih Review and Launch, jangan lupa membuat key pair untuk login ke instance nantinya. Pilih `Create a new key pair` dan isikan nama key pair dan `Download Key Pair` . Jika sudah, Launch Instances

![7](assets/07.png)

8. dan instance untuk public telah dibuat

![8](assets/08.png)

9. selanjutnya, buat elastic IP static untuk dialokasikan ke Instance public 

![9](assets/09.png)
![9.1](assets/10.png)

10. lalu associate elastic ip dengan instance public. Centang Elastic IP yang ada, pilih `Actions > Associate Elastic IP address`

![10](assets/11.png)

11. pilih `Resource type = Instance` dan pilih `Instance = public-instance` . klik Associate

![11](assets/12.png)

# CREATE & SETUP PRIVATE SERVER FOR APPLICATION

12. buat lagi instance untuk private server. Pilih OS yang sama yaitu ubuntu server 18.04 LTS

![12](assets/13.png)

13. pilih t2.micro

![13](assets/14.png)

14. pada Configure Instance Details, masih sama seperti sebelumnya

![14](assets/15.png)

15. Tambahkan Storage sebesar 10 Gib

![15](assets/16.png)

16. pada Configure Security Group disini berbeda dari sebelumnya, yaitu tambahkan rule untuk mengizinkan semua traffic yang masuk

![16](assets/17.png)

17. jika sudah, Review and Launch lalu pilih key pair yang sebelumnya sudah dibuat.

Setelah instance private dibuat, tidak perlu diberi Elastic IP

![17](assets/18.png)

# SETUP USER & SSH PUBLIC INSTANCE

18. setelah mendownload key pair untuk kedua instance, ubah permission dari file key pair tersebut

```
sudo chmod 400 key_pair.pem
```

![18](assets/19.png)

19. lakukan SSH ke server public dengan menggunakan key pair

```
ssh -i key_pair.pem ubuntu@ip-public
```

![19](assets/20.png)

 

