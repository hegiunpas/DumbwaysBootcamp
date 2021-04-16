# AUTO RUN DOCKER-COMPOSE AFTER BOOTING

1. pertama, buat working direktori pada `/var/<nama-direktori>` untuk `docker-compose`

![1](assets/01.png)

2. jika sudah, copy/create file `docker-compose.yml` ke working direktori 

```
sudo cp wayshub-frontend/docker-compose.yml /var/<nama-direktori>
```

![2](assets/02.png)

3. lalu buat file pada `/etc/systemd/system/docker-compose.service` untuk service docker-compose

![3](assets/03.png)

4. edit file service tersebut seperti dibawah ini

![4](assets/04.png)

5. terakhir, enable docker-compose dengan perintah

```
sudo systemctl enable --now docker-compose
```

![5](assets/05.png)


