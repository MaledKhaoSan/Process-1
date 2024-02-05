<a id="text"></a>
# :round_pushpin: Boot Process
Overview 
<br><br>
กระบวนการบูตของLinuxเป็นส่วนสำคัญของการทำงาน เนื่องจากเป็นขั้นตอนเริ่มต้นในการเริ่มระบบปฏิบัติการ ทุกครั้งที่คุณกดปุ่มเปิดเครื่อง ระบบของคุณจะใช้เวลาสักครู่ในการเตรียมความพร้อมและแสดงหน้าเข้าสู่ระบบ คุณอาจสงสัยว่าเบื้องหลังมีการดำเนินการอะไรบ้าง บทความนี้จะอธิบายว่าLinuxจัดการกระบวนการบูตระบบอย่างไร 
<br><br>
Introduction 
<br><br>
 Booting คือกระบวนการที่นำระบบจากสถานะปิดไปสู่ระบบปฏิบัติการที่กำลังทำงาน โดยขั้นตอนทั้งหมดแบ่งออกเป็น 4 ขั้นตอนหลัก มีดังนี้:
<img src="https://static.thegeekstuff.com/wp-content/uploads/2011/02/linux-boot-process.png"  width="100" height="100">

<br><br>
o Firmware stage
o Bootloader stage
o Kernel stage
o Init stage
<br><br>

1. Firmware stage:

เริ่มต้นโดย BIOS (Basic Input/Output System) ควบคุมการเริ่มต้นระบบและฮาร์ดแวร์พื้นฐาน อยู่บนชิปเมนบอร์ด
ตรวจสอบฮาร์ดแวร์พื้นฐาน เช่น CPU, RAM, อุปกรณ์ต่อพ่วง 
ค้นหาและโหลด Master Boot Record (MBR) จากฮาร์ดดิสก์
2. Bootloader stage:

โหลดและรัน MBR
MBR ค้นหาและโหลด bootloader ตัวจริง เช่น GRUB (GRand Unified Bootloader)
GRUB แสดงเมนูตัวเลือกสำหรับระบบปฏิบัติการที่จะบูต
3. Kernel stage:

โหลดเคอร์เนลของระบบปฏิบัติการ
เคอร์เนลเริ่มต้นระบบปฏิบัติการ
จัดการทรัพยากรระบบ เช่น หน่วยความจำ กระบวนการ อุปกรณ์
4. Init stage:

เริ่มต้น init system (เช่น systemd)
Init system เรียกใช้สคริปต์เพื่อเริ่มต้นบริการระบบพื้นฐาน
เตรียมพร้อมสำหรับผู้ใช้


