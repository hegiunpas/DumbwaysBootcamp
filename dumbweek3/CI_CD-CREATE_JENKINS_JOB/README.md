# CREATE JENKINS JOB

1. login ke server jenkins, lakukan generate ssh-keygen dan salin public-key

```
ssh-keygen -t rsa -b 4096 -C "jenkins@cicd.dimas.onlinecamp.id"
cat .ssh/id_rsa.pub
```

![1](assets/01.png)

2. masukan public-key server jenkins yang sudah disalin ke akun github

![2](assets/02.png)

3. login ke server-frontend, dan buat file `.ssh/authorized_keys` , salin lagi public-key jenkins ke file tersebut

![3](assets/03.png)
![3.1](assets/04.png)

4. masuk ke jenkins pada browser, dan install plugin yang dibutuhkan yaitu `Publish Over SSH`

![4](assets/04-1.png)

5. masuk ke `Manage Jenkins` dan pilih `Manage Credentials`

![5](assets/05.png)

6. pilih `jenkins`

![6](assets/06.png)

7. pilih `Global credentials`

![7](assets/07.png)

8. klik `Add Credentials`

![8](assets/08.png)

9. isikan `ID`, `Description` , `Username` , `Private-key` yang ada pada server jenkins

![9](assets/09.png)

10. sealnjutnya, masuk ke `Manage Jenkins` > `Configure System` 

![10](assets/10.png)

11. pilih `Add server` dan tambahkan server untuk frontend

*exec timeout set : 0*

![11](assets/12.png)

12. kembali ke halaman utama jenkins lalu create a job

![12](assets/13.png)

13. isikan nama dan pilih `Freestyle project`

![13](assets/14.png)

14. isi sebuah description bebas

![14](assets/15.png)

15. pada bagian `Source Code Management` , pilih `Git` lalu isikan repo URL SSH dan pilih credentials yang sudah dibuat sebelumnya lalu pilih branch master

![15](assets/16.png)

16. pada bagian `Build Triggers`, ceklis `Github hook trigger for GITscm polling` untuk mentrigger jenkins ketika ada push baru dari repo 

![16](assets/17.png)

17. pada bagian `Build` , add build `send files or execute commands over ssh` dan tentukan apa yang akan dilakukan

![17](assets/18.png)

18. pergi ke `Github` dan masuk ke menu `Repository` > `Settings` > `Webhooks` , lalu isikan subdomain dari server jenkins itu sendiri

![18](assets/19.png)

19. pastikan server frontend dapat terhubung ke repo karena nanti akan dilakukan `git pull origin master` , coba lakukan push

![19](assets/20.png)

20. maka jenkins akan melakukan proses job nya secara otomatis jika ada push terbaru pada repo

![20](assets/21.png)
