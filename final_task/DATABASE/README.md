# DATABASE

1. pertama, buat script ansible yang dimana untuk menginstall docker ke server

![1](assets/01.png)
![1.1](assets/02.png)

2. buat file docker-compose.yml untuk postgres 

![2](assets/03.png)

3. buat file docker-compose.service untuk memproses layanan docker-compose

![3](assets/04.png)

4. buat script ansible lagi untuk membuat docker-compose running di systemd

![4](assets/05.png)

5. apply script install docker

![5](assets/06.png)
![5.1](assets/07.png)

6. apply script deploy postgres

![6](assets/08.png)

7. jika sudah, remote ke server databases dan login ke postgres lalu buat database baru yaitu `waysgallery`

![7](assets/09.png)

8. buat user database baru dan berikan akses privileges ke databse waysgallery

![8](assets/09-1.png)

9. lalu edit file *config/config.json* pada repo backend dibagian production yang nantinya akan kita migrate

![9](assets/10.png)

10. buat file docker file untuk builds images backend

![10](assets/11.png)

11. buat script ansible untuk build, push, and run images backend

![11](assets/11-1.png)

12. apply script nya

![12](assets/12.png)

13. remote ke server backend dan container backend sudah berjalan

![13](assets/13.png)

14. lakukan migrate database pada environment production  didalam container

![14](assets/14.png)




