# SSL CONFIGURATION BACKEND

1. login ke server `reverse-proxy` dan lakukan konfigurasi SSL untuk subdomain `api.dimas.onlinecamp.id` menggunakan certbot dengan perintah

```
sudo certbot --nginx -d api.dimas.onlinecamp.id
```

![1](assets/01.png)

2. jika sudah, login ke server `frontend` dan edit file `wayshub-frontend/src/config/api.js`

![2](assets/02.png)

3. ubah pada bagian `baseURL: ` dengan subdomain api

![3](assets/03.png)

4. selanjutnya lakukan run frontend menggunakan `pm2` dengan perintah

```
pm2 start ecosystem.config.js
```

![4](assets/04.png)

5. buka browser dan masukan URL backend untuk memastikan apakah konfigurasi SSL berhasil

![5](assets/05.png)

6. selanjutnya cobalah sign up dan sign in pada aplikasi

![6](assets/06.png)

![6.1](assets/07.png)
