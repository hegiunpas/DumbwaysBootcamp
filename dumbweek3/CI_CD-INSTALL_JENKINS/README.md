# INSTALL JENKINS

1. pertama, buat private instance untuk `jenkins` dan pastikan sudah terhubung

![1](assets/01.png)

2. login ke instances `jenkins` , lalu pastikan `Docker` & `docker-compose` sudah terinstall di server 

![2](assets/02.png)

*sebelum ke langkah-langkah, lakukan setup docker-compose auto run terlebih dahulu pada server jenkins*

3. buat direktori `jenkins` yang nantinya akan di mount volumes ke direktori `/var/jenkins_home` pada container jenkins, dan buat file `docker-compose.yml`

![3](assets/03.png)

4. edit file `/var/docker-compose/docker-compose.yml` seperti berikut

![4](assets/04.png)

5. jika sudah, `enable` service docker-compose agar berjalan secara auto run setelah booting

```
sudo systemctl enable --now docker-compose.service
```

![5](assets/05.png)

6. selanjutnya, login ke cloudflare dan buat subdomain baru untuk instances `jenkins`

![6](assets/06.png)

7. jika sudah, login ke `public-server` dan buat file config baru untuk jenkins

```
sudo touch /etc/nginx/wayshub/jenkins
sudo vim /etc/nginx/wayshub/jenkins
```

![7](assets/07.png)

8. edit file config `jenkins` seperti berikut

![8](assets/08.png)

9. lalu lakukan SSL configuration untuk subdomain `cicd.dimas.onlinecamp.id` menggunakan `certbot`

```
sudo certbot --nginx -d cicd.dimas.onlinecamp.id
```

![9](assets/09.png)

10. dan configuration file jenkins akan secara otomatis terisi SSL

![10](assets/10.png)

11. reload service nginx

```
sudo nginx -s reload
```

![11](assets/11.png)

12. kembali ke `server-jenkins` dan pastikan container sudah running. Jangan lupa untuk menyalin password authentication untuk unlock jenkins

```
docker ps
docker exec -it <container-name> cat /var/jenkins_home/initialAdminPassword
```

![12](assets/12.png)

13. buka subdomain `cicd.dimas.onlinecamp.id` pada browser dan `paste` password yang sudah disalin

![13](assets/13.png)

14. pilih `Install suggested plugins` agar beberapa plugins terinstall secara otomatis

![14](assets/14.png)

15. tunggu hingga proses instalasi selesai

![15](assets/15.png)

16. create akun user untuk login ke jenkins

![16](assets/16.png)

17. masukan URL subdomain `server-jenkins`

![17](assets/17.png)

18. dan jenkins berhasil ter-install

![18](assets/18.png)
