# cron
**cron** มีรากฐานมาจากคำว่าภาษากรีก chronos มีความหมายว่า เวลา ซึ่ง cron ก็คือ list ของคำสั่งที่ถูกตั้งเวลาไว้ล่วงหน้า

โดย มี
- <ins>**crond**</ins> หรือ **cron deamon** มีหน้าที่ในการรัน task หลายๆ task ตามเวลาที่ได้กำหนดไว้ล่วงหน้า
- <ins>**crondtab**</ins> หรือ **cron tables**  เป็นตัวแก้ไข list ของคำสั่งที่ต้องการจะจัด scheduler สามารถ แก้ไข ลบ หรือ list รายการได้
- <ins>**cron job**</ins> คือ program ที่ run ผ่าน cron

## crontab
เราจะพบ crontab files อยู่ใน 
- <ins>โดยทั่วไป</ins> มักจะพบใน ``` /etc/crontab/```  file
- ส่วน<ins>เพิ่มเติม</ins>จะอยู่ใน ```/etc/cron.d``` directory 
- directory : ```/etc/spool/cron```

แต่ก่อนที่เราจะแก้ไข จัดการ crontab ได้นั้น จะต้องมีสิทธิ์พิเศษของผู้ดูแลระบบก่อน (มีสืทธิ์ที่จะแก้ไข)

### syntax ของ crontab
ในการที่จะติดตั้ง cron job นั้น เราต้องทำการ สร้างบรรทัดที่แสดงด้านลง ลงใน crontab file
```
  <minute> <hour> <day of the month> <month> <day of week> comand
```

|     field      |            value            |
|:--------------:|:---------------------------:|
|     minute     |           0 - 59            |
|      hour      |           0 - 23            |
|day of the month|           1 - 31            |
|     month      |           1 - 12            |
|  day of week   |       0 (Sunday) - 6        |
|     comand     |คำสั่งที่เราต้องการจะ execute|


ใช้
- <ins>เครื่องหมายดอกจันท์ *</ins> แทนตัวเลขนั้น ก็หมายความว่า ใช้ทุกค่าที่เป็นไปได้ของ ตำแหน่งงนั้น เช่น * ตรง minute ก็คือเอาทุกช่วง ตั้งแต่ 0 - 59 หรือเรียกง่ายๆ ก็คือ ทำทุกรอบ ทุก 1 นาที แต่ถ้า */5 ก็จะเป็น ทุกๆ 5 นาที
-  <ins>เครื่องหมาย - </ins>  ก็คือบอกช่วง เช่น 10 - 15
- <ins>เครื่องหมาย , </ins> ในการแยก value

เช่น
```
*/5 * * * * root /usr/root/bkup.sh -> ทำงานทุกๆ 5 นาที
30 22 * * * dev /usr/dev/ant_build.sh -> ทำงานทุกวัน เวลา 22:30 น.
```
ตัวอย่างข้างต้น จะเป็น system crontab แต่ถ้าเป็น user crontab ก็สามารถทำได้ โดยการเปลี่ยนจาก command เป็น user name
