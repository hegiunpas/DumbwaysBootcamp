# SETUP MONITORING SERVER

1. pertama, launch sebuah instances untuk `monitoring` & `automation ansible` di AWS

![1](assets/01.png)

2. lakukan instalasi ansible dan library yang dibutuhkan pada instances ansible

```
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

3. buat file `Inventory` untuk mendefinisikan host yang akan menjadi target host lalu tambahkan ip target kedalam file tersebut dan buat file `ansible.cfg`

![3](assets/02.png)
![3.1](assets/02-1.png)

4. jalankan perintah dibawah untuk memastikan apakah host tujuan sudah dapat terhubung

```
ansible all --key-file <location-file> -i Inventory -m ping
```

![4](assets/03.png)

5. buat file `docker-install-monitoring.yml` untuk menginstall docker & docker-compose ke instances monitoring dan menjalankan container prometheus grafana menggunakan docker-compose yang berjalan di `systemd`

![5](assets/04.png)
![5.1](assets/05.png)

6. buat file `hosts-monitoring.yml` untuk add host ke path dir `/etc/hosts` yang ada pada instances monitoring

![6](assets/06.png)

7. buat lagi file `node-exporter.yml` untuk penginstallan node-exporter ke seluruh instance

![7](assets/07.png)

8. persiapkan konfigurasi prometheus yaitu `prometheus.yml` 

![8](assets/08.png)

9. persiapkan file `docker-compose.yml` untuk menjalankan container prometheus & grafana

*jadikan lokasi satu file dengan prometheus.yml*

![9](assets/09.png)

10. setelah itu, jalankan seluruh script configuration ansible

```
ansible all --key-file <location-key> -i Inventory -m ping
ansible-playbook <config-file-name.yml> 
```

![10](assets/10.png)
![10.1](assets/11.png)
![10.2](assets/12.png)

11. masuk ke server nginx dan buat file config baru untuk subdomain `prometheus.dimas.onlinecamp.id` & `monitoring.dimas.onlinecamp.id`

    lalu lakukan konfigurasi SSL untuk https

```
sudo certbot -d monitoring.dimas.onlinecamp.id -d prometheus.dimas.onlinecamp.id
```

![11](assets/13.png)

12. buka browser dan akses `monitoring.dimas.onlinecamp.id` login menggunakan user defaults `username: admin` `password: admin`

![12](assets/14.png)

13. pilih data source

![13](assets/15.png)

14. add data sources dan pilih prometheus. Masukan URL subdomain dari prometheus

![14](assets/16.png)

15. save & test

![15](assets/17.png)

16. create dashboard and add panel

![16](assets/18.png)

17. setelah itu, cek prometheus

*server ansible & mysql tidak up karena belum saya install docker*

![17](assets/19.png)

 

