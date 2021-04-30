# MONITORING

1. create instances private untuk monitoring

![1](assets/01.png)

## FILE MONITORING

2. masuk ke server ansible, dan buat file docker-compose.yml untuk running container prometheus dan grafana pada server monitoring

![2](assets/02.png)

3. buat file konfigurasi prometheus.yml untuk mendefinisikan server mana aja yang mau di monitoring

![3](assets/03.png)

## FILE SCRIPT ANSIBLE

4. buat file script ansible `monitoring.yml` yang dimana ini akan menginstall prometheus dan grafana pada server monitoring

![4](assets/04.png)

5. selanjutnya buat file `node-exporter.yml` untuk menginstall node exporter diseluruh server

![5](assets/05.png)

6. apply script ansible tersebut

![6](assets/06.png)
![6.1](assets/07.png)

7. masuk ke server monitoring untuk memastikan apakah container sudah berjalan

![7](assets/08.png)

8. selanjutnya, buka browser dan akses URL dari prometheus `prometheus.dimas.onlinecamp.id` dan kita dapat melihat server target yang akan kita monitoring

![8](assets/09.png)

9. buka juga URL dari grafana dan buat data sources

![9](assets/10.png)

10. pilih Prometheus dan isi pada bagian URL dengan ip private dan port instances dimana prometheus itu berjalan

![10](assets/11.png)

11. klik save & test

![11](assets/12.png)

12. add panel dan dashboard

![12](assets/13.png)

13. data panel ini untuk memonitor CPU server

![13](assets/14.png)

14. data panel ini untuk memonitor Memory penggunaan

![14](assets/15.png)

15. data ini untuk memonitor Input Output dari Disk server tersebut

![15](assets/16.png)

16. ini untuk memonitor jaringan server

![16](assets/17.png)

17. selesai 

![17](assets/18.png)
