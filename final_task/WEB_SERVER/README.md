# WEB SERVER

## CLOUDFLARE

1. pertama, buat subdomain untuk beberapa server aplikasi

![1](assets/01.png)

## INSTALL NGINX & CERTBOT

2. buat script ansible untuk install nginx & cerbot

![2](assets/02.png)

## COPY FILE CONFIGURATION FOR REVERSE PROXY

3. buat script ansible untuk menyalin file konfigurasi(frontend, backend, jenkins, monitoring) ke nginx 

![3](assets/03.png)

berikut adalah isi dari file nya

![3.1](assets/03-1.png)
![3.2](assets/03.2.png)
![3.3](assets/03-3.png)
![3.4](assets/03-4.png)
![3.5](assets/03-5.png)

4. apply script untuk nginx

![4](assets/04.png)

5. jika sudah, login ke server nginx lalu edit file `/etc/nginx/nginx.conf` agar include direktori `/etc/nginx/waysgallery`

![5](assets/05.png)

6. dan lakukan konfigurasi SSL certbot letsencrypt

![6](assets/06.png)
