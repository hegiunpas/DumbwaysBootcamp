# SSL CONFIGURATION

1. update system dan install certbot

```
sudo apt-get update
sudo apt-get install python-certbot-nginx
```

![1](assets/01.png)

2. masuk ke direktori `/etc/nginx/wayshub` dan masukkan perintah `sudo certbot -d dimas.onlinecamp.id` dan ikuti arahan dari output

![2](assets/02.png)
![2.1](assets/03.png)

3. jika sudah, cek file pada `/etc/nginx/wayshub/frontend` maka konfigurasi https akan otomatis diisi

![3](assets/04.png)

4. cek HTTPS SSL pada browser

![4](assets/05.png)
