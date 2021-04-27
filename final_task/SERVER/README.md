# SERVER

## SETUP VPC & SUBNET

1. buat vpc defaults baru

![1](assets/01.png)

2. tentukan subnet untuk private instances & public instances

![2](assets/02.png)

## SETUP SECURITY GROUP

3. buat security groups untuk public instances

![3](assets/03.png)

4. buat security groups untuk private instances

![4](assets/04.png)

5. terakhir buat security groups untuk NAT instances

![5](assets/04-1.png)

## SETUP NGINX SERVER

6. buat 1 public instances nginx dengan disable auto assign ip publik dan download key file nya

![6](assets/05.png)

7. buat 1 elastic ip yang nantinya akan di associate ke instances nginx

![7](assets/06.png)

8. associate elastic ip ke instances nginx

![8](assets/07.png)

9. copy file key yang sudah didownload ke instances nginx

![9](assets/08.png)

## SETUP INTERNET FOR SERVER

10. buat private instances untuk application

![10](assets/09.png)

11. jika sudah, buat NAT instances agar private instances dapat terhubung ke internet melalui NAT instances

![11](assets/10.png)

12. edit *source/destination check* pada NAT instances dengan menceklis `Stop`

![12](assets/11.png)

## SETUP ROUTE TABLE

13. buat route table baru untuk private instances

![13](assets/12.png)

14. edit routes pada route table tersebut dengan menambahkan routes menuju `0.0.0.0/0` melalui NAT instances

![14](assets/13.png)

15. associate route table tadi ke subnet private

![15](assets/14.png)

16. test ping ke internet pada server private

![16](assets/15.png)
