# USER

1. saya akan membuat user menggunakan ansible, pertama saya buat private instances untuk menjalankan ansible

![1](assets/01.png)

2. lakukan penginstallan ansible dan mkpasswd pada server ansible

```
sudo apt-get update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
sudo apt install whois
```

![2](assets/02.png)

3. selanjutnya, exit dari server ansible dan copy private key dari server nginx ke ansible

![3](assets/03.png)

4. buat file Inventory untuk mendefinisikan host target

![4](assets/04.png)

5. buat file ansible.cfg untuk mengatur konfigurasi apa saja yang diperlukan

![5](assets/05.png)

6. lakukan hashing password dan salin hasil outputnya

![6](assets/06.png)

7. paste hasil hash password tadi kedalam variable vars

![7](assets/07.png)

8. buat file `create_user.yml` yang nantinya akan membuat user pada server target, definisikan variable password kedalam tasks

![8](assets/07-1.png)

9. buat file hostname-change.yml untuk mengubah hostname target

![9](assets/08.png)

10. setelah itu, lakukan ping connection dengan perintah

```
ansible all -m ping
```

![10](assets/09.png)

11. apply script create-user.yml dengan perintah

```
ansible-playbook create_user.yml
```

![11](assets/10.yml)

12. apply script hostname-change.yml

![12](assets/11.png)

13. jika sudah, lakukan login dengan username dan password yang sudah dibuat tadi maka hasilnya akan berhasil

![13](assets/12.png)
