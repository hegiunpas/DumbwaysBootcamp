# CONTINUES INTEGRATION & CONTINUES DELIVERY

1. pertama, buat script ansible untuk create dan install jenkins

![1](assets/02.png)

2. buat file docker-compose.yml jenkins yang akan di copy ke direktori `/var/docker-compose` server jenkins

![2](assets/01.png)

3. apply script ansible tersebut

![3](assets/03.png)

4. masuk ke server jenkins dan copy initial password dari container

![4](assets/04.png)

5. buka browser dan akses jenkins lalu salin password tadi

![5](assets/04-1.png)

6. pilih Install suggested plugins

![6](assets/05.png)

7. create user untuk login jenkins

![7](assets/06.png)

8. jika sudah bisa login, lalu install plugin `Publish Over SSH`

![8](assets/07.png)

9. setelah itu, tambahkan global credentials dari server jenkins

![9](assets/08.png)

10. add server untuk frontend(1 dan 2)

![10](assets/09.png)

tambahkan public key dari masing" server ke github

![10.1](assets/11.png)

11. jika sudah, create a jenkins job dan pilih Freestyle project

![11](assets/10.png)

12. pada bagian source code management, pilih git. Isikan URL repo dan pilih credentials server jenkins. lalu atur branch menjadi ke production

![12](assets/12.png)

13. pada build triggers, centang github hook trigger

![13](assets/13.png)

14. pada bagian Build , add build `send files or execute commands over ssh` dan tentukan apa yang akan dilakukan

![14](assets/14.png)

15. jika sudah, tambahkan URL jenkins ke webhook github dengan menambahkan `/github-webhook` dibagian akhir URL

![15](assets/15.png)

16. lakukan push ke repo pada branch Production

![16](assets/16.png)

17. maka jenkins akan ke trigger dan melakukan jobs nya

![17](assets/17.png)


