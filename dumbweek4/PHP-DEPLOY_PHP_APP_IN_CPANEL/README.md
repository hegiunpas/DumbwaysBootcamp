# DEPLOY PHP APPLICATION IN CPANEL

*untuk cpanel saya menggunakan* [byet.host](https://byet.host) *dan akan mendeploy aplikasi PHP* [Simple Machine Forum](https://www.simplemachines.org/)

1. pertama, buat akun cpanel melalui `byet.host` 

![1](assets/01.png)

2. download simple machine forum

![2](assets/03.png)

3. download FileZilla untuk melakukan transfer file ke cpanel

![3](assets/04.png)

4. jika sudah, login ke [cpanel.byethost6.com](cpanel.byethost6.com)

![4](assets/02.png)

5. create mysql database pada cpanel

![5](assets/05.png)

6. jalankan filezilla dan remote ftp cpanel untuk transfer file instalasi simple machine forum

*pastikan file sudah diekstrak*

![6](assets/06.png)

7. buka subdomain untuk melakukan proses install SMF dan isikan username, pass, name, server database yang sudah kita buat

![7](assets/07.png)

8. biarkan defaults

![8](assets/08.png)

9. create user administrator baru 

![9](assets/09.png)

10. jika sudah selesai, buka kembali subdomain pada tab baru dan SMF sudah terinstall

![10](assets/10.png)
