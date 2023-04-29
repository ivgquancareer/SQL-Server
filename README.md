# DATA ANALYST: USING SQL SERVER

![image](https://user-images.githubusercontent.com/131565885/235278658-88b9a873-6bdb-4db8-9796-ab472db0a115.png)


![image](https://user-images.githubusercontent.com/131565885/235118578-69a9b4e5-33a8-4571-9d60-7d2051d779fa.png)

# 1. Data Overview
**The table structure of 5 different Data marts in a Data warehouse is as follows :**
![212323928-120f0473-7d88-4bef-85ca-afbab466228d](https://user-images.githubusercontent.com/131565330/233814482-85df9454-802d-4f3b-8adf-307d42963737.png)
![212324165-3173bba9-35f2-4caf-85e2-f6aa6c711e37](https://user-images.githubusercontent.com/131565330/233814486-3be93411-fc56-488a-ba33-171b288eba25.png)
![212324274-254a80d4-37a7-4602-bfa8-88298acfa453](https://user-images.githubusercontent.com/131565330/233814491-fefc91cd-b84f-45e9-96fe-7184b5eed8b4.png)
# 2. Tạo các Table
**Use Database**
```php
USE ivgquan_data_analyst
```
**Create Table 'NHANVIEN'**
```php
CREATE TABLE NHANVIEN(
        MANV char(4) PRIMARY KEY ,
        HOTEN VARCHAR(40),
        DTHOAI VARCHAR(20),
        NGVL Date)
```
**Create Table 'KHACHHANG'**
```php
CREATE TABLE KHACHHANG(
    MAKH char(4) PRIMARY KEY,
    HOTEN varchar(40),
    DCHI VARCHAR(50),
    SODT VARCHAR(20),
    NGSINH Date,
    NGDK Date, 
    DOANHSO money)
```
**Create Table 'SANPHAM'**
```php
CREATE TABLE SANPHAM(
    MASP char(4) PRIMARY KEY,
    TENSP VARCHAR(40),
    DVT VARCHAR(20),
    NUOCSX VARCHAR(40),
    GIA money)
```
**Create Table 'HOADON'**
```php
CREATE TABLE HOADON(
    SOHD int PRIMARY KEY,
    NGHD Date,
    MAKH char(4) REFERENCES KHACHHANG (MAKH),
    MANV char(4) REFERENCES NHANVIEN (MANV),
    TRIGIA money)
```
**Create Table 'CTHD'**
```php
CREATE TABLE CTHD(
    SOHD int references HOADON (SOHD),
    MASP char(4) REFERENCES SANPHAM (MASP),
    SL int )
```
**Add Data vào Table 'NHANVIEN'**
```php
insert into NHANVIEN values ('NV01','Nguyen Nhu Nhut','0927345678','04/13/2006')
insert into NHANVIEN values ('NV02','Le Thi Phi Yen','0987567390','04/21/2006')
insert into NHANVIEN values ('NV03','Nguyen Van B','0997047382','04/27/2006')
insert into NHANVIEN values ('NV04','Ngo Thanh Tuan','0913758498','06/24/2006')
insert into NHANVIEN values ('NV05','Nguyen Thi Truc Thanh','0918590387','07/20/2006')
```
**Add Data vào Table 'KHACHHANG'**
```php
insert into KHACHHANG VALUES ('KH01','NGUYEN VAN A','731 TRAN HUNG DAO, Q5, TPHCM','08823451','10/22/1960','10/22/1960',13000000)
insert into KHACHHANG values ('KH02','Tran Ngoc Han','23/5, Nguyen Trai, Q 5, Tp HCM','0908256478','04/03/1974','07/30/2006',280000)
insert into KHACHHANG values ('KH03','Tran Ngoc Linh','45, Nguyen Canh Chan, Q 1, Tp HCM','0938776266','06/12/1980','08/05/2006',3860000)
insert into KHACHHANG values ('KH04','Tran Minh Long','50/34 Le Dai Hanh, Q 10, Tp HCM','0917325476','03/09/1965','10/02/2006',250000)
insert into KHACHHANG values ('KH05','Le Nhat Minh','34, Truong Dinh, Q 3, Tp HCM','08246108','03/10/1950','10/28/2006',21000)
insert into KHACHHANG values ('KH06','Le Hoai Thuong','227, Nguyen Van Cu, Q 5, Tp HCM','08631738','12/31/1981','11/24/2006',915000)
insert into KHACHHANG values ('KH07','Nguyen Van Tam','32/3, Tran Binh Trong, Q 5, Tp HCM','0916783565','04/06/1971','12/01/2006',12500)
insert into KHACHHANG values ('KH08','Phan Thi Thanh','45/2, An Duong Vuong, Q 5, Tp HCM','0938435756','01/10/1971','12/13/2006',365000)
insert into KHACHHANG values ('KH09','Le Ha Vinh','873, Le Hong Phong, Q 5, Tp HCM','08654763','09/03/1979','01/14/2007',70000)
insert into KHACHHANG values ('KH10','Ha Duy Lap','34/34B, Nguyen Trai, Q 1, Tp HCM','08768904','05/02/1983','01/16/2007',67500)
```
**Add Data vào Table 'SANPHAM'**
```php
insert into SANPHAM values ('BC01','But chi','cay','Singapore',3000)
insert into SANPHAM values ('BC02','But chi','cay','Singapore',5000)
insert into SANPHAM values ('BC03','But chi','cay','Viet Nam',3500)
insert into SANPHAM values ('BC04','But chi','hop','Viet Nam',30000)
insert into SANPHAM values ('BB01','But bi','cay','Viet Nam',5000)
insert into SANPHAM values ('BB02','But bi','cay','Trung Quoc',7000)
insert into SANPHAM values ('BB03','But bi','hop','Thai Lan',100000)
insert into SANPHAM values ('TV01','Tap 100 giay mong','quyen','Trung Quoc',2500)
insert into SANPHAM values ('TV02','Tap 200 giay mong','quyen','Trung Quoc',4500)
insert into SANPHAM values ('TV03','Tap 100 giay tot','quyen','Viet Nam',3000)
insert into SANPHAM values ('TV04','Tap 200 giay tot','quyen','Viet Nam',5500)
insert into SANPHAM values ('TV05','Tap 100 trang','chuc','Viet Nam',23000)
insert into SANPHAM values ('TV06','Tap 200 trang','chuc','Viet Nam',53000)
insert into SANPHAM values ('TV07','Tap 100 trang','chuc','Trung Quoc',34000)
insert into SANPHAM values ('ST01','So tay 500 trang','quyen','Trung Quoc',40000)
insert into SANPHAM values ('ST02','So tay loai 1','quyen','Viet Nam',55000)
insert into SANPHAM values ('ST03','So tay loai 2','quyen','Viet Nam',51000)
insert into SANPHAM values ('ST04','So tay ','quyen','Thai Lan',55000)
insert into SANPHAM values ('ST05','So tay mong','quyen','Thai Lan',20000)
insert into SANPHAM values ('ST06','Phan viet bang','hop','Viet Nam',5000)
insert into SANPHAM values ('ST07','Phan khong bui','hop','Viet Nam',7000)
insert into SANPHAM values ('ST08','Bong bang','cai','Viet Nam',1000)
insert into SANPHAM values ('ST09','But long','cay','Viet Nam',5000)
insert into SANPHAM values ('ST10','But long','cay','Trung Quoc',7000)
```
**Add Data vào Table 'HOADON'**
```php
insert into HOADON values (1001,'07/23/2006','KH01','NV01',320000)
insert into HOADON values (1002,'08/12/2006','KH01','NV02',840000)
insert into HOADON values (1003,'08/23/2006','KH02','NV01',100000)
insert into HOADON values (1004,'09/01/2006','KH02','NV01',180000)
insert into HOADON values (1005,'10/20/2006','KH01','NV02',3800000)
insert into HOADON values (1006,'10/16/2006','KH01','NV03',2430000)
insert into HOADON values (1007,'10/28/2006','KH03','NV03',510000)
insert into HOADON values (1008,'10/28/2006','KH01','NV03',440000)
insert into HOADON values (1009,'10/28/2006','KH03','NV04',200000)
insert into HOADON values (1010,'11/01/2006','KH01','NV01',5200000)
insert into HOADON values (1011,'11/04/2006','KH04','NV03',250000)
insert into HOADON values (1012,'11/30/2006','KH05','NV03',21000)
insert into HOADON values (1013,'12/12/2006','KH06','NV01',5000)
insert into HOADON values (1014,'12/31/2006','KH03','NV02',3150000)
insert into HOADON values (1015,'01/01/2007','KH06','NV01',910000)
insert into HOADON values (1016,'01/01/2007','KH07','NV02',12500)
insert into HOADON values (1017,'01/02/2007','KH08','NV03',35000)
insert into HOADON values (1018,'01/13/2007','KH08','NV03',330000)
insert into HOADON values (1019,'01/13/2007','KH01','NV03',30000)
insert into HOADON values (1020,'01/14/2007','KH09','NV04',70000)
insert into HOADON values (1021,'01/16/2007','KH10','NV03',67500)
insert into HOADON values (1022,'01/16/2007',null,'NV03',7000)
insert into HOADON values (1023,'01/17/2007',null,'NV01',330000)
```
**Add Data vào Table 'CTHD'**
```php
insert into CTHD values (1001,'TV02',10)
insert into CTHD values (1001,'ST01',5)
insert into CTHD values (1001,'BC01',5)
insert into CTHD values (1001,'BC02',10)
insert into CTHD values (1001,'ST08',10)
insert into CTHD values (1002,'BC04',20)
insert into CTHD values (1002,'BB01',20)
insert into CTHD values (1002,'BB02',20)
insert into CTHD values (1003,'BB03',10)
insert into CTHD values (1004,'TV01',20)
insert into CTHD values (1004,'TV02',20)
insert into CTHD values (1004,'TV03',20)
insert into CTHD values (1004,'TV04',20)
insert into CTHD values (1005,'TV05',50)
insert into CTHD values (1005,'TV06',50)
insert into CTHD values (1006,'TV07',20)
insert into CTHD values (1006,'ST01',30)
insert into CTHD values (1006,'ST02',10)
insert into CTHD values (1007,'ST03',10)
insert into CTHD values (1008,'ST04',8)
insert into CTHD values (1009,'ST05',10)
insert into CTHD values (1010,'TV07',50)
insert into CTHD values (1010,'ST07',50)
insert into CTHD values (1010,'ST08',100)
insert into CTHD values (1010,'ST04',50)
insert into CTHD values (1010,'TV03',100)
insert into CTHD values (1011,'ST06',50)
insert into CTHD values (1012,'ST07',3)
insert into CTHD values (1013,'ST08',5)
insert into CTHD values (1014,'BC02',80)
insert into CTHD values (1014,'BB02',100)
insert into CTHD values (1014,'BC04',60)
insert into CTHD values (1014,'BB01',50)
insert into CTHD values (1015,'BB02',30)
insert into CTHD values (1015,'BB03',7)
insert into CTHD values (1016,'TV01',5)
insert into CTHD values (1017,'TV02',1)
insert into CTHD values (1017,'TV03',1)
insert into CTHD values (1017,'TV04',5)
insert into CTHD values (1018,'ST04',6)
insert into CTHD values (1019,'ST05',1)
insert into CTHD values (1019,'ST06',2)
insert into CTHD values (1020,'ST07',10)
insert into CTHD values (1021,'ST08',5)
insert into CTHD values (1021,'TV01',7)
insert into CTHD values (1021,'TV02',10)
insert into CTHD values (1022,'ST07',1)
insert into CTHD values (1023,'ST04',6)
```

# 3.1. Xử lí các Requests về Sản phẩm
**REQUEST 1: Lập danh sách các sản phẩm do Viet Nam sản xuất**
```php
SELECT MASP, TENSP
FROM SANPHAM
where NUOCSX = 'Viet Nam'
```
**REQUEST 2: Lập danh sách các sản phẩm có đơn vị tính là “cay”, ”quyen”**
```php
SELECT MASP, TENSP
FROM SANPHAM
where DVT in ( 'cay ', 'quyen' )
```
**REQUEST 3: Lập danh sách các sản phẩm có mã sản phẩm bắt đầu là “B” và kết thúc là “01”**
```php
SELECT MASP, TENSP
FROM SANPHAM
where MASP like 'B%01'
```
**REQUEST 4: Lập danh sách các sản phẩm do Việt Nam sản xuất có giá từ 20.000 đến 35.000**
```php
SELECT MASP, TENSP, GIA
FROM SANPHAM
where NUOCSX ='Viet nam' and GIA >= 20000 AND GIA <= 35000
/*hoặc*/
Select MASP, TENSP, GIA
from (SELECT MASP, TENSP, GIA FROM SANPHAM where NUOCSX ='Viet nam') as a
where GIA >= 20000 AND GIA <= 35000
```
**REQUEST 5: Lập danh sách các sản phẩm do Trung Quốc hoặc Việt Nam sản xuất có giá từ 30.000 đến 40.000**
```php
SELECT MASP, TENSP, GIA
FROM SANPHAM
where NUOCSX in ('Viet nam','Trung Quoc') and GIA >= 30000 AND GIA <= 40000
```
**REQUEST 6: Lập danh sách các sản phẩm do Trung Quốc sản xuất hoặc các sản phẩm được bán ra trong ngày 1/1/2007**
```php
SELECT sp.MASP, tensp, NUOCSX, NGHD
from (SANPHAM as sp join CTHD as ct on sp.MASP=ct.MASP join HOADON as hd on ct.SOHD=hd.SOHD)
where NUOCSX='Trung Quoc' and NGHD = '1/1/2007'
```
**REQUEST 7: Lập danh sách các sản phẩm không bán được**
```php
select *
from SANPHAM 
where MASP not in (Select MASP from CTHD where SL>0)
```
**REQUEST 8: Lập danh sách các sản phẩm không bán được trong năm 2006**
```php
select *
from SANPHAM 
where MASP not in (Select MASP from CTHD as ct join HOADON as hd on ct.SOHD=hd.SOHD where SL>0 and YEAR(NGHD)='2006')
```
**REQUEST 9: Lập danh sách các sản phẩm do Trung Quốc sản xuất không bán được trong năm 2006**
```php
select *
from SANPHAM 
where MASP not in (Select MASP from CTHD as ct join HOADON as hd on ct.SOHD=hd.SOHD where SL>0 and YEAR(NGHD)='2006') and NUOCSX='Trung Quoc'
```
**REQUEST 10: Có bao nhiêu sản phẩm khác nhau được bán ra trong năm 2006**
```php
SELECT count(distinct ct.MASP) as 'Số sản phẩm khác nhau được bán ra trong năm 2006'
from SANPHAM as sp join CTHD as ct on sp.MASP = ct. MASP join HOADON as hd on ct.SOHD=hd.SOHD
where YEAR(NGHD)=2006
```
**REQUEST 11: Lập danh sách các sản phẩm có giá bán bằng 1 trong 3 mức giá cao nhất**
```php
SELECT masp, tensp
from SANPHAM
where gia in (SELECT top 3 SUM(gia) from SANPHAM group by masp order by SUM(gia)  desc)
```
**REQUEST 12: Lập danh sách các sản phẩm do Thai Lan sản xuất có giá bằng 1 trong 3 mức giá cao nhất (của tất cả các sản phẩm)**
```php
SELECT masp, tensp
from SANPHAM
where gia in (SELECT top 3 SUM(gia) from SANPHAM group by masp order by SUM(gia)  desc) and NUOCSX='Thai Lan'
```
**REQUEST 13: Lập danh sách các sản phẩm do Trung Quoc sản xuất có giá bằng 1 trong 3 mức giá cao nhất (của sản phẩm do Trung Quoc sản xuất)**
```php
SELECT masp, tensp
from SANPHAM
where gia in (SELECT top 3 SUM(gia) from SANPHAM where NUOCSX='Trung Quoc' group by masp order by SUM(gia)  desc) and NUOCSX='Trung Quoc'
```
# 3.2. Xử lí các Requests về Hóa đơn
**REQUEST 1: Lập danh sách các số hóa đơn, trị giá hóa đơn bán ra trong ngày 1/1/2007 và ngày 2/1/2007**
```php
select SOHD, TRIGIA 
from HOADON
where NGHD in ('1/1/2007','1/2/2007')
```
**REQUEST 2: Lập danh sách các số hóa đơn, trị giá hóa đơn trong tháng 1/2007, sắp xếp theo ngày (tăng dần) và trị giá của hóa đơn (giảm dần)**
```php
select NGHD, SOHD, TRIGIA  
from HOADON
where NGHD BETWEEN '1/1/2007' and  '1/31/2007'
order by NGHD asc, TRIGIA DESC
/*hoặc*/
select NGHD, SOHD,TRIGIA
from HOADON
where YEAR(NGHD)= '2007' AND MONTH(NGHD)= '01'
order by NGHD asc , TRIGIA DESC
```
**REQUEST 3: Lập danh sách các số hóa đơn, trị giá các hóa đơn do nhân viên có tên “Nguyen Van B” lập trong ngày 28/10/2006**
```php
SELECT HOADON.SOHD,TRIGIA
from NHANVIEN LEFT JOIN HOADON
on NHANVIEN.MANV = HOADON.MANV
where NGHD = '10/28/2006' and HOTEN= 'Nguyen Van B'
```
**REQUEST 4: Lập danh sách các số hóa đơn đã mua sản phẩm có mã số “BB01” hoặc “BB02”**
```php
SELECT distinct SOHD
from CTHD
where MASP = 'BB01' or MASP ='BB02'
```
**REQUEST 5: Lập danh sách các số hóa đơn đã mua sản phẩm có mã số “BB01” hoặc “BB02”, mỗi sản phẩm mua với số lượng từ 10 đến 20**
```php
SELECT distinct SOHD, MASP, SL
from CTHD
where (MASP in ('BB01','BB02')) and SL BETWEEN 10 and 20
```
**REQUEST 6: Lập danh sách các số hóa đơn mua cùng lúc 2 sản phẩm có mã số “BB01” và “BB02”, mỗi sản phẩm mua với số lượng từ 10 đến 20**
```php
SELECT SOHD
from CTHD as ct1
where MASP='BB01' and ct1.SL BETWEEN 10 and 20 and exists (select * from CTHD as ct2 where MASP= 'BB02' and ct2.SL BETWEEN 10 and 20 and ct1.SOHD=ct2.SOHD)
```
**REQUEST 7: Lập danh sách các số hóa đơn đã mua tất cả các sản phẩm do Singapore sản xuất**
```php
SELECT SOHD, count(TENSP) as 'Số sản phẩm do Singapore sản xuất'
from CTHD as ct join SANPHAM as sp on ct.MASP = sp.MASP
where NUOCSX ='singapore'
GROUP by SOHD, TENSP
having count(TENSP) = (select count(TENSP) from SANPHAM where NUOCSX='singapore')
```
**REQUEST 8: Có bao nhiêu hóa đơn không phải của khách hàng đăng ký thành viên mua?**
```php
SELECT COUNT(SOHD) as 'Số hóa đơn không phải của khách hàng đăng ký thành viên mua'
from hoadon 
where mAKH is null
```
**REQUEST 9: Cho biết trị giá hóa đơn cao nhất, thấp nhất là bao nhiêu**
```php
SELECT MAX(TRIGIA) as 'Trị giá HD cao nhất', MIN(TRIGIA) as 'Trị giá HD thấp nhất'
from HOADON
```
**REQUEST 10: Trị giá trung bình của tất cả các hóa đơn được bán ra trong năm 2006 là bao nhiêu?**
```php
SELECT AVG(TRIGIA) as 'Trị giá trung bình của tất cả các hóa đơn được bán ra trong năm 2006'
from hoadon
where YEAR(NGHD)=2006
```
**REQUEST 11: Tìm số hóa đơn có trị giá cao nhất trong năm 2006**
```php
SELECT SOHD as 'Số hóa đơn có trị giá cao nhất trong năm 2006'
from hoadon
where TRIGIA >= all (SELECT MAX(TRIGIA) from HOADON)
```
**REQUEST 12: Lập danh sách các hóa đơn có mua ít nhất 4 sản phẩm khác nhau**
```php
select SOHD, COUNT(distinct MASP) as 'Số Sản phẩm trong đơn'
from CTHD
group by SOHD
HAVING COUNT(distinct MASP) >= 4
```
**REQUEST 13: Lập danh sách các hóa đơn có mua 3 sản phẩm do Viet Nam sản xuất (3 sản phẩm khác nhau)**
```php
SELECT SOHD,  COUNT(ct.MASP) as 'Số sản phẩm do Viet Nam sản xuất '
from CTHD as ct join SANPHAM as sp 
on ct.MASP=sp.MASP
where NUOCSX='Viet Nam'
GROUP by SOHD
HAVING COUNT(ct.MASP) >= 3
```
# 3.3. Xử lí các Requests về Khách hàng
**REQUEST 1: Lập danh sách các khách hàng đã mua hàng trong ngày 1/1/2007**
```php
SELECT KHACHHANG.MAKH, HOTEN
FROM KHACHHANG join HOADON 
on KHACHHANG.MAKH = HOADON.MAKH
where NGHD = '1/1/2007'
```
**REQUEST 2: Lập danh sách các sản phẩm được khách hàng có tên “Nguyen Van A” mua trong tháng 10/2006**
```php
SELECT HOTEN, ct.MASP, TENSP
from (KHACHHANG as kh join HOADON as hd on kh.MAKH=hd.MAKH join CTHD as ct on hd.SOHD = ct.SOHD join SANPHAM as sp on ct.MASP= sp.MASP)
where MONTH(NGHD) = '10' AND YEAR(NGHD)='2006' AND HOTEN='Nguyen Van A' 
```
**REQUEST 3: Tìm họ tên khách hàng đã mua hóa đơn có trị giá cao nhất trong năm 2006**
```php
SELECT SOHD, HOTEN
from hoadon as hd join KHACHHANG as kh on hd.MAKH=kh.MAKH
where TRIGIA >= all (SELECT MAX(TRIGIA) from HOADON)
```
**REQUEST 4: Lập danh sách 3 khách hàng có doanh số cao nhất**
```php
SELECT top 3 *
from KHACHHANG
order by DOANHSO desc
```
**REQUEST 5: Lập danh sách 3 khách hàng có doanh số cao nhất (sắp xếp theo kiểu xếp hạng)**
```php
select MAKH,HOTEN,doanhso, RANK() OVER(ORDER BY DOANHSO desc) as' Xếp hạng'
from KHACHHANG
```
**REQUEST 6: Tìm khách hàng (MAKH, HOTEN) có số lần mua hàng nhiều nhất**
```php
SELECT hd.MAKH,HOTEN, count(distinct SOHD) as 'Số lần mua hàng'
from KHACHHANG as kh join hoadon as hd on kh.MAKH=hd.MAKH
GROUP by hd.MAKH, HOTEN
ORDER by count(distinct SOHD) desc
```
# 3.4. Xử lí các Requests về Doanh thu, Số sản phẩm
**REQUEST 1: Tính doanh thu bán hàng trong năm 2006**
```php
SELECT SUM(TRIGIA) as 'Doanh thu bán hàng trong năm 2006'
from hoadon
where YEAR(NGHD)=2006
```
**REQUEST 2: Tính doanh thu bán hàng mỗi ngày**
```php
select NGHD, sum(trigia) as 'Doanh thu bán hàng'
from HOADON
GROUP by NGHD
```
**REQUEST 3: Tính tổng số sản phẩm do “Trung Quoc” sản xuất**
```php
SELECT COUNT(MASP) as 'Tổng số sản phẩm do Trung Quoc sản xuất'
from sanpham
where nuocsx='Trung Quoc'
```
**REQUEST 4: Tính tổng số sản phẩm của từng nước sản xuất**
```php
SELECT NUOCSX, COUNT(MASP) as 'Tổng số sản phẩm của từng nước sản xuất'
from SANPHAM
GROUP by NUOCSX
```
**REQUEST 5: Với từng nước sản xuất, tìm giá bán cao nhất, thấp nhất, trung bình của các sản phẩm**
```php
/*QUESTION 33: Với từng nước sản xuất, tìm giá bán cao nhất, thấp nhất, trung bình của các sản phẩm*/
SELECT NUOCSX, max(GIA) as 'Giá bán cao nhất ', MIN(GIA) as 'Giá bán cao nhất' , AVG(GIA) as 'Giá bán trung bình'
from SANPHAM
GROUP by NUOCSX
```
**REQUEST 6: Tính tổng số lượng của từng sản phẩm bán ra trong tháng 10/2006**
```php
select ct.MASP, sum(SL) as 'Tổng số lượng của từng sản phẩm bán ra'
from hoadon as hd join cthd as ct on hd.SOHD=ct.SOHD join SANPHAM as sp on ct.MASP=sp.MASP
where MONTH(NGHD)='10' and YEAR(NGHD)='2006'
group by ct.MASP
```
**REQUEST 7: Tính doanh thu bán hàng của từng tháng trong năm 2006**
```php
SELECT MONTH(NGHD) as ' Tháng', SUM(TRIGIA) as 'Doanh thu bán hàng của từng tháng'
from HOADON
where YEAR(NGHD)='2006'
GROUP by MONTH(NGHD)
```
**REQUEST 8: Tháng mấy trong năm 2006, doanh số bán hàng cao nhất ?**
```php
SELECT MONTH(NGHD) as Tháng, SUM(TRIGIA) as ' Doanh số bán hàng'
from hoadon
where YEAR(NGHD)='2006'
GROUP by MONTH(NGHD)
order by SUM(TRIGIA) desc
```
**REQUEST 9: Tìm sản phẩm có tổng số lượng bán ra thấp nhất trong năm 2006**
```php
SELECT ct.MASP, SUM(SL) as 'Số lượng sản phẩm bán ra'
from SANPHAM as sp join CTHD as ct on sp.MASP = ct.MASP join HOADON as hd on ct.SOHD=hd.SOHD 
where YEAR(NGHD)='2006'
GROUP BY ct.MASP
order by SUM(SL) asc
```
**REQUEST 10: Mỗi nước sản xuất, tìm sản phẩm (MASP,TENSP) có giá bán cao nhất**
```php
SELECT nuocsx,masp,tensp, MAX(GIA) as 'Giá bán cao nhất'
from SANPHAM as sp1
group by nuocsx,masp,tensp
having max(GIA) >= all (select MAX(GIA) from sanpham as sp2 where sp1.NUOCSX=sp2.nuocsx GROUP by nuocsx)
```
**REQUEST 11: Tìm nước sản xuất sản xuất ít nhất 3 sản phẩm có giá bán khác nhau**
```php
SELECT NUOCSX, count(distinct GIA) as 'Số mức giá'
from sanpham
group by nuocsx
having  count(distinct GIA) >=3
```
**REQUEST 12: Trong 10 khách hàng có doanh số cao nhất, tìm khách hàng có số lần mua hàng nhiều nhất**
```php
SELECT top 1 *
from (SELECT hd.MAKH, HOTEN, COUNT(distinct SOHD) as 'Số lần mua hàng'
      from khachhang as kh join hoadon as hd on kh.MAKH=hd.MAKH
      group by hd.MAKH, HOTEN) as c
```
