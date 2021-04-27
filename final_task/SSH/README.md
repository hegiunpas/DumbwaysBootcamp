# SSH

## SSH USER
1. lakukan generate ssh-key pada user dimas

![1](assets/01.png)

2. buat file /.ssh/config yang nantinya untuk tempat dimana private key itu diarahkan

![2](assets/02.png)

3. buat script file ssh-key.yml untuk proses transfer key dan config ke target

![3](assets/03.png)

4. apply script file tersebut di user ubuntu *jadi nanti biarkan user ubuntu yang membuat proses tersebut*

![4](assets/04.png)

5. lakukan ssh pada user yang sama menggunakan user dimas dan hasilnya tidak perlu lagi username dan password

![5](assets/05.png)

## SSH GIT

6. selanjutnya, copy public key user

![6](assets/06.png)

7. lalu salin di akun github

![7](assets/07.png)

8. lakukan ssh ke github

![8](assets/08.png)
