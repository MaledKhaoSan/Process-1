# cron
**cron** มีรากฐานมาจากคำว่าภาษากรีก chronos มีความหมายว่า เวลา ซึ่ง cron ก็คือ list ของคำสั่งที่ถูกตั้งเวลาไว้ล่วงหน้า

โดย มี
- **crond** หรือ **cron deamon** มีหน้าที่ในการรัน task หลายๆ task ตามเวลาที่ได้กำหนดไว้ล่วงหน้า
- **crondtab** หรือ **cron tables**  เป็นตัวแก้ไข list ของคำสั่งที่ต้องการจะจัด scheduler สามารถ แก้ไข ลบ หรือ list รายการได้
- **cron job** คือ program ที่ run ผ่าน cron

## crontab
เราจะพบ crontab files อยู่ใน 
- โดยทั่วไป มักจะพบใน ``` /etc/crontab/```  file
- ส่วนเพิ่มเติมจะอยู่ใน ```/etc/cron.d``` directory 
- directory : ```/etc/spool/cron```
