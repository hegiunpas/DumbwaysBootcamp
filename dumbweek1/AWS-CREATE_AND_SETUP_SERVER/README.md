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

20. tambahkan user baru untuk jaga-jaga apabila key pair hilang. Jalankan perintah 

```
sudo adduser nama-user
```

![20](assets/21.png)

21. tambahkan akses sudo untuk user baru tersebut dengan menjalankan perintah

```
sudo usermod -aG sudo nama-user
```

![21](assets/22.png)

22. edit pada file `/etc/ssh/sshd_config` dan ubah pada bagian `PasswordAuthentication no` menjadi `PasswordAuthentication yes`

![22](assets/23.png)

23. jika sudah, restart service sshd

```
sudo systemctl restart sshd
sudo systemctl status sshd
```

![23](assets/24.png)

24. lakukan remote ssh ke server public tanpa menggunakan key pair

```
ssh nama-user@ip-public
```

![25](assets/25.png)

25. Selanjutnya kita akan mencoba remote SSH server private dari server public

pertama, lakukan transfer key pair dari local ke server public

```
scp key-pair.pem nama-user@ip-public:/server/directory/key-pair.pem
```

![25](assets/26.png)

26. buka kembali aws management console dan masuk ke `EC2 > Instances > private-server` lalu salin Private IPv4 address

![26](assets/27.png)

27. selanjutnya, lakukan remote SSH ke server public lalu ke server private. Dan buat user baru seperti sebelumnya

![27](assets/28.png)

# SETUP VPC (Virtual Private Cloud)

28. pertama, buka aws management console dan masuk ke `service > VPC > subnets`

![28](assets/30.png)

29. beri nama subnet milik public server menjadi `subnet-id-public-server` dan private server `subnet-id-private-server`

![29](assets/31.png)

# CREATE & SETUP NAT INSTANCE FOR PRIVATE SERVER

* Supaya private server aman, jangan diberi public ip yang dapat diakses langsung melalui internet. Tapi nantinya akan diakses melalui server public __revers proxy__ . Namun, dengan begitu server private tidak terhubung ke internet, oleh karena itu kita akan membuat NAT intances agar server private dapat terhubung ke internet.

30. Pertama, Launch Instances dan pilih AMI nat

![30](assets/32.png)

31. disini saya memilih tipe Instance yang sederhana yaitu t2.micro

![31](assets/33.png)

32. pada Configure Instance Details yang perlu diubah yaitu Subnet, pilih public subnet dan `enable Auto-assign Public IP` 

![32](assets/34.png)

33. pada Security Group, tambahkan 1 rule dengan setup type __all traffic__ dan source ip dari network/subnet-server-private

![33](assets/35.png)

34. selanjutnya masuk ke list instances, centang NAT instances dan klik `Action > Networking > Change source/destination check`

![34](assets/36.png)

35. pada settingan ini ceklis __stop__ dan klik save

![35](assets/37.png)

36. jika sudah, masuk ke `service > VPC > Route Tables` lalu klik `Create route table`

![36](assets/38.png)

37. kita bikin route table baru untuk private server, pilih VPC dari Subnet ID private server. klik Create

![37](assets/39.png)

38. selanjutnya `Edit routes` dari route table yang telah kita buat

![38](assets/40.png)

39. `Add route` dan pilih `Target` NAT Instance. __Save routes__

![39](assets/41.png)

40. jika sudah, pergi ke `VPC > Subnets > subnet-private-server` lalu klik `Edit route table association`

![40](assets/42.png)

41. lalu associate route table tadi dengan subnet private. klik __Save__

![41](assets/43.png)

42. test ping ke internet dari private server

![42](assets/44.png)

 

