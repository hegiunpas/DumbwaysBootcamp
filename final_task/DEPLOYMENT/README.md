# DEPLOYMENT

## DEPLOYMENT WAYSGALLERY FRONTEND

1. pertama, lakukan clone repository frontend ke local computer kita, lalu buat dan pilih branch Production

![1](assets/00.png)

2. tambahkan `Dockerfile` pada repo untuk frontend

![2](assets/00-1.png)

3. jika sudah, lakukan push ke github pada branch Production

![3](assets/00-2.png)

4. lalu masuk ke server ansible dan tambahkan variable frontend & backend yang nantinya akan kita definisikan pada file script ansible fronted

*~/vars/defaults.yml*

![4](assets/01.png)

5. setelah itu, tambahkan file script frontend.yml yang dimana ini akan mengclone repo ke server target, edit file setAuthToken.jsx, melakuakan login ke docker hub, build custom images dan push, dan copy file docker-compose.yml lalu restart service docker-compose

![5](assets/02.png)

6. jangan lupa membuat file docker-compose.yml untuk frontend

![6](assets/03.png)

7. apply script ansible untuk frontend

![7](assets/04.png)

8. dan sudah ter-deploy

![8](assets/05.png)

## DEPLOYMENT WAYSGALLERY BACKEND

9. clone repo dan setup to branch Production

![9](assets/06.png)

10. buat Dockerfile untuk backend

![10](assets/07.png)

11. lakukan push ke github pada branch production

![11](assets/08.png)

12. jika sudah, masuk lagi ker server ansible dan buat script untuk build backend

![12](assets/09.png)

13. buat docker-compose.yml untuk backend

![13](assets/10.png)

14. apply script backend.yml

![14](assets/11.png)

15. cek di backend pada file `config/config.json` dan pastikan sudah mengarah ke variable database waysgallery

![15](assets/12.png)

16. lakukan migrate database

![16](assets/13.png)

17. jika sudah, coba untuk membuat akun dan login pada aplikasi

![17](assets/14.png)
![17.1](assets/15.png)


