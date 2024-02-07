<a id="text"></a>
# :round_pushpin: Boot Process
### Overview :
กระบวนการบูตของLinuxเป็นส่วนสำคัญของการทำงาน เนื่องจากเป็นขั้นตอนเริ่มต้นในการเริ่มระบบปฏิบัติการ ทุกครั้งที่คุณกดปุ่มเปิดเครื่อง ระบบของคุณจะใช้เวลาสักครู่ในการเตรียมความพร้อมและแสดงหน้าเข้าสู่ระบบ คุณอาจสงสัยว่าเบื้องหลังมีการดำเนินการอะไรบ้าง บทความนี้จะอธิบายว่าLinuxจัดการกระบวนการบูตระบบอย่างไร 

### Introduction :
 Booting คือกระบวนการที่นำระบบจากสถานะปิดไปสู่ระบบปฏิบัติการที่กำลังทำงาน โดยขั้นตอนทั้งหมดแบ่งออกเป็น 4 ขั้นตอนหลัก มีดังนี้:
 
- Firmware stage
 
- Bootloader stage

- Kernel stage
  
- Init stage
  
  <img src="https://www.baeldung.com/wp-content/uploads/sites/2/2022/10/boot-process-662x1024.png" >
<br><br>
<a id="text"></a>
# :round_pushpin: Firmware stage
คือ ซอฟต์แวร์ที่ฝังอยู่บนชิปฮาร์ดแวร์ ทำหน้าที่ควบคุมการทำงานพื้นฐานของอุปกรณ์ เฟิร์มแวร์จะทำงานก่อนระบบปฏิบัติการ Linux โหลดขึ้นมา ทำหน้าที่เตรียมอุปกรณ์ให้พร้อมใช้งาน เช่น การตรวจสอบฮาร์ดแวร์ การตั้งค่าคอนฟิกเบื้องต้น และการโหลดบูตโลเดอร์
<br><br>
แบ่งออกเป็น 2 ประเภทหลักๆ ดังนี้:

1. เฟิร์มแวร์ BIOS/UEFI: เป็นเฟิร์มแวร์ที่ควบคุมการทำงานพื้นฐานของเมนบอร์ด เช่น การตรวจสอบฮาร์ดแวร์ การตั้งค่าวันที่และเวลา การบูตระบบปฏิบัติการ

2. เฟิร์มแวร์อุปกรณ์: เป็นเฟิร์มแวร์ที่ควบคุมการทำงานของอุปกรณ์เฉพาะ เช่น การ์ดจอ การ์ดเสียง ไดรฟ์ Wi-Fi
<br><br>
### ลำดับการทำงานของ Firmware stage มีดังนี้:

1. POST (Power-On Self Test): เฟิร์มแวร์จะตรวจสอบฮาร์ดแวร์ว่าทำงานปกติหรือไม่

2. Initialization: เฟิร์มแวร์จะตั้งค่าคอนฟิกเบื้องต้นของอุปกรณ์ เช่น วันที่ เวลา

3. Bootloader: เฟิร์มแวร์จะโหลดบูตโลเดอร์ ซึ่งเป็นโปรแกรมที่ทำหน้าที่โหลดระบบปฏิบัติการ

4. Operating System: บูตโลเดอร์จะโหลดระบบปฏิบัติการ Linux เข้าสู่หน่วยความจำ
---
รายละเอียดของแต่ละขั้นตอน:

1. POST (Power-On Self Test):

- เฟิร์มแวร์จะตรวจสอบว่า CPU ทำงานปกติหรือไม่

- เฟิร์มแวร์จะตรวจสอบว่า RAM ทำงานปกติหรือไม่

- เฟิร์มแวร์จะตรวจสอบว่าอุปกรณ์ต่อพ่วง เช่น ฮาร์ดดิสก์ การ์ดจอ ทำงานปกติหรือไม่

2. Initialization:

- เฟิร์มแวร์จะตั้งค่าวันที่และเวลา

- เฟิร์มแวร์จะตั้งค่าคอนฟิกอุปกรณ์ต่อพ่วง

- เฟิร์มแวร์จะตั้งค่าคอนฟิก BIOS/UEFI

3. Bootloader:

- เฟิร์มแวร์จะค้นหาบูตโลเดอร์จากอุปกรณ์ต่อพ่วง เช่น ฮาร์ดดิสก์ หรือ USB drive

- เฟิร์มแวร์จะโหลดบูตโลเดอร์เข้าสู่หน่วยความจำ

- บูตโลเดอร์จะทำหน้าที่โหลดระบบปฏิบัติการ Linux

4. Operating System:

- บูตโลเดอร์จะโหลดระบบปฏิบัติการ Linux เข้าสู่หน่วยความจำ

- ระบบปฏิบัติการ Linux จะเริ่มทำงาน

> [!CAUTION]
> การตั้งค่าคอนฟิก BIOS/UEFI อาจทำให้ระบบทำงานไม่เสถียร

<a id="text"></a>
# :round_pushpin: Bootloader stage
 เป็นขั้นตอนสำคัญที่เตรียมฮาร์ดแวร์ ค้นหา และโหลดระบบปฏิบัติการ Bootloader ยอดนิยม ได้แก่ GRUB, LILO  
 
 ### ทำหน้าที่หลัก ดังนี้

1. เตรียมการฮาร์ดแวร์:

- ตรวจสอบและตั้งค่าหน่วยความจำ (RAM)

- เริ่มต้นระบบ I/O เช่น คีย์บอร์ด จอภาพ

- โหลดอุปกรณ์ต่อพ่วงที่จำเป็น

2. ค้นหาและโหลดระบบปฏิบัติการ:

- ค้นหาพาร์ทิชันระบบปฏิบัติการ

- โหลด kernel ของ Linux เข้าสู่หน่วยความจำ

- ส่งต่อการควบคุมให้กับ kernel

3. แสดงเมนูตัวเลือก:

- เสนอตัวเลือกการบูทระบบปฏิบัติการ

- อนุญาตให้ผู้ใช้เลือก kernel เวอร์ชัน

- ตั้งค่าพารามิเตอร์การบูท
---
### Bootloader ที่นิยมใช้ใน Linux:

- GRUB (Grand Unified Bootloader): ตัวเลือกมาตรฐาน รองรับระบบ UEFI และ BIOS

- LILO (Linux Loader): ตัวเลือกดั้งเดิม รองรับเฉพาะ BIOS

- SYSLINUX: ตัวเลือกที่มีขนาดเล็ก รองรับระบบ UEFI และ BIOS
---
### ประเภทของ Bootloader:

- MBR (Master Boot Record): พบในระบบ BIOS เก็บข้อมูลเกี่ยวกับพาร์ทิชันและ bootloader
- GPT (GUID Partition Table): พบในระบบ UEFI เก็บข้อมูลเกี่ยวกับพาร์ทิชันและ bootloader
---
### การเรียกใช้งาน:

Bootloader stage จะถูกเรียกใช้งานโดยอัตโนมัติเมื่อเปิดเครื่องคอมพิวเตอร์ กระบวนการทำงานมีดังนี้:

- POST (Power-On Self Test): เมื่อเปิดเครื่อง คอมพิวเตอร์จะทำการ POST เพื่อตรวจสอบฮาร์ดแวร์
- BIOS/UEFI: BIOS หรือ UEFI จะค้นหาอุปกรณ์บูทที่มี bootloader
- Bootloader: Bootloader จะโหลดตัวเองเข้าสู่หน่วยความจำ
- ค้นหาพาร์ทิชัน: Bootloader จะค้นหาพาร์ทิชันระบบปฏิบัติการ
- โหลด kernel: Bootloader จะโหลด kernel ของ Linux เข้าสู่หน่วยความจำ
- ส่งต่อการควบคุม: Bootloader จะส่งต่อการควบคุมให้กับ kernel
- Kernel: Kernel จะเริ่มต้นระบบปฏิบัติการ

### ผู้ใช้สามารถ

- กดปุ่มพิเศษ (เช่น F2, F10, Esc) ระหว่าง POST เพื่อเข้าสู่ BIOS/UEFI setup
  
- เลือกลำดับการบูท (boot order) ใน BIOS/UEFI setup
  
- กำหนดค่า bootloader ใน bootloader configuration file
  
### ผลลัพธ์ที่ได้:

- ระบบปฏิบัติการจะเริ่มต้น: หาก bootloader ค้นหาพาร์ทิชันระบบปฏิบัติการและโหลด kernel สำเร็จ ระบบปฏิบัติการจะเริ่มต้น

- แสดงเมนูตัวเลือก: ผู้ใช้สามารถเลือกตัวเลือกการบูท เช่น เลือก kernel เวอร์ชัน เลือกพาร์ทิชัน

- แสดงข้อความแสดงข้อผิดพลาด: หาก bootloader พบปัญหา อาจแสดงข้อความแสดงข้อผิดพลาด

### ตัวอย่าง:

- GRUB: ผู้ใช้สามารถกดปุ่ม C ระหว่างการบูทเพื่อเข้าสู่ GRUB command line interface

- LILO: ผู้ใช้สามารถแก้ไขไฟล์ /etc/lilo.conf เพื่อกำหนดค่า bootloader
  
> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

<a id="text"></a>
# :round_pushpin: Kernel stage
Kernel stage เป็นหนึ่งในขั้นตอนหลักของการบูตระบบปฏิบัติการ Linux มันเป็นช่วงเวลาหลังจาก POST (Power-On Self Test) เสร็จสิ้น และก่อนที่จะเริ่ม init system

### หน้าที่หลักของ Kernel stage มีดังนี้:

1. โหลดเคอร์เนล

- BIOS โหลดเคอร์เนลจากฮาร์ดดิสก์หรืออุปกรณ์อื่นๆ

- เคอร์เนลจะเริ่มทำงานในโหมดพิเศษเรียกว่า "protected mode"

- เคอร์เนลจะตั้งค่า stack และ heap ของตัวเอง

2. ตรวจสอบฮาร์ดแวร์

- เคอร์เนลจะตรวจสอบและระบุฮาร์ดแวร์ทั้งหมดที่มีในระบบ

- ตรวจสอบ CPU, RAM, อุปกรณ์ต่อพ่วง ฯลฯ

- เก็บข้อมูลเกี่ยวกับฮาร์ดแวร์ในโครงสร้างข้อมูลต่างๆ

3. ตั้งค่าระบบ

- เคอร์เนลจะตั้งค่าระบบต่างๆ เช่น หน่วยความจำ การจัดการกระบวนการ และระบบไฟล์

- ตั้งค่าตารางเวลาสำหรับการทำงานของ CPU

- กำหนดค่าหน่วยความจำเสมือน

- เริ่มต้นระบบไฟล์

4. เริ่มต้นอุปกรณ์

- เคอร์เนลจะโหลดไดรเวอร์อุปกรณ์

- เริ่มต้นอุปกรณ์ต่างๆ เช่น ฮาร์ดดิสก์, เครือข่าย, อุปกรณ์ต่อพ่วง ฯลฯ

- ตั้งค่า IRQ สำหรับอุปกรณ์ต่างๆ
  
5. เริ่มต้น init system

- เคอร์เนลจะเริ่ม init system

- init system รับผิดชอบในการเริ่มต้นบริการระบบและโปรแกรมอื่นๆ

- ผู้ใช้สามารถกำหนดค่า init system ได้
---
### ขั้นตอนของ Kernel stage มีดังนี้:

1.POST (Power-On Self Test): BIOS ตรวจสอบฮาร์ดแวร์พื้นฐาน

2.Bootloader: โหลดเคอร์เนลเข้าสู่หน่วยความจำ

3.Kernel stage:

- เคอร์เนลเริ่มทำงานในโหมดพิเศษเรียกว่า "protected mode"

- ตรวจสอบและระบุฮาร์ดแวร์ทั้งหมดที่มีในระบบ

- ตั้งค่าระบบต่างๆ เช่น หน่วยความจำ การจัดการกระบวนการ และระบบไฟล์

- โหลดไดรเวอร์อุปกรณ์

- เริ่มต้นอุปกรณ์ต่างๆ

- เริ่มต้น init system

4.Init system: เริ่มต้นบริการระบบและโปรแกรมอื่นๆ

5.ระบบพร้อมใช้งาน: ผู้ใช้สามารถเข้าสู่ระบบและใช้งานโปรแกรมต่างๆ

### ผลลัพธ์ที่ได้:

- ระบบปฏิบัติการ Linux จะบูตขึ้นและพร้อมใช้งาน

- บริการระบบและโปรแกรมต่างๆ จะเริ่มต้นทำงาน

- ผู้ใช้สามารถเข้าสู่ระบบและใช้งานโปรแกรมต่างๆ
---
### Command ที่เกี่ยวข้องกับ Kernel stage 

Command:
`dmesg`

Options/Arguments:

- `c` ล้างข้อความทั้งหมดใน buffer

- `-T`: แสดง timestamp ของข้อความ

- `-l`: แสดงข้อความทั้งหมด (ไม่จำกัดจำนวน)

- `-n`: แสดงหมายเลขบรรทัด

- `p` แสดงชื่อ PID ของกระบวนการที่ส่งข้อความ

- `-s`: แสดงข้อความสั้นๆ

- `-t`: แสดง timestamp ของข้อความในรูปแบบ HH:MM:SS

- `-w`: รอให้มีข้อความใหม่ปรากฏ

ตัวอย่าง:

```
dmesg | grep -i "error"
```
---
Command: `klog`

Options/Arguments:

- `-c`: ล้างข้อความทั้งหมดใน buffer
- `-T`: แสดง timestamp ของข้อความ
- `-l`: แสดงข้อความทั้งหมด (ไม่จำกัดจำนวน)
- `-n`: แสดงหมายเลขบรรทัด
- `-p`: แสดงชื่อ PID ของกระบวนการที่ส่งข้อความ
- `-s`: แสดงข้อความสั้นๆ
- `-t: แสดง timestamp ของข้อความในรูปแบบ HH:MM:SS
- `-w`: รอให้มีข้อความใหม่ปรากฏ
  
ผลลัพธ์:

- แสดงข้อความเคอร์เนลในรูปแบบที่กรองแล้ว

- ผู้ใช้สามารถกรองข้อความ

ตัวอย่าง:
```
klog | grep -i "kernel"
```
> [!CAUTION]
> ผู้ใช้ควรหยุดการติดตามการเรียกระบบเมื่อไม่ใช้งาน การติดตามการเรียกระบบอาจทำให้ระบบทำงานช้าลง
<a id="text"></a>
# :round_pushpin: Init stage

Init stage คือ กระบวนการเริ่มต้นระบบปฏิบัติการLinux  ทำหน้าที่ควบคุมกระบวนการเริ่มต้นระบบปฏิบัติการ ประกอบด้วยชุดของสคริปต์และบริการที่รันตามลำดับเพื่อเตรียมระบบให้พร้อมใช้งานสำหรับผู้ใช้  

### init stage แบ่งออกเป็น 7 ระดับ ดังนี้:

1. S - Single-user mode:

- เริ่มต้นเคอร์เนล Linux
  
- ตั้งค่าฮาร์ดแวร์พื้นฐาน
  
- เปิดใช้งานคอนโซลผู้ใช้ตัวเดียว
  
2. S - Multi-user mode without NFS:

- เริ่มต้นบริการระบบพื้นฐาน เช่น syslog, network
  
- ตรวจสอบระบบไฟล์
  
- เปิดใช้งาน getty บนคอนโซลเสมือน

3. S - Full multi-user mode with NFS:

- เริ่มต้นบริการ NFS
  
- เปิดใช้งาน NIS (Network Information Service)
  
- เปิดใช้งานบริการเพิ่มเติมตามต้องการ
  
4. s - Shutdown:

- ปิดบริการระบบอย่างปลอดภัย
  
- ถอดส่วนประกอบฮาร์ดแวร์
 
5. S - Power-off:

- ปิดเครื่อง
  
6. S - Reboot:

- เริ่มต้นระบบใหม่
  
7. S - Halt:

- หยุดการทำงานของระบบ (ไม่ปิดเครื่อง)
<div align="center">
      ตารางสรุป
      <table>
      <thead>
      <tr>
      <th style="text-align:left">ระดับ</th>
      <th style="text-align:center">คำอธิบาย</th>
      <th style="text-align:right">ผลลัพธ์</th>
      </tr>
      </thead>
      <tbody>
      <tr>
      <td style="text-align:left">0</td>
      <td style="text-align:center">Shutdown</td>
      <td style="text-align:right">ปิดเครื่อง</td>
      </tr>
      <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:center">Single-user mode</td>
      <td style="text-align:right">เริ่มต้นระบบในโหมดผู้ใช้เดี่ยว</td>
      </tr>
      <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:center">Multi-user mode without NFS</td>
      <td style="text-align:right">เริ่มต้นระบบในโหมดผู้ใช้หลายคน (ไม่มี NFS)</td>
      </tr>
      <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:center">	Full multi-user mode with NFS</td>
      <td style="text-align:right">เริ่มต้นระบบในโหมดผู้ใช้หลายคน (มี NFS)</td>
      </tr>
       <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:center">Shutdown</td>
      <td style="text-align:right">ปิดระบบ</td>
      </tr>
       <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:center">Power-off</td>
      <td style="text-align:right">ปิดเครื่อง</td>
      </tr>
       <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:center">	Reboot</td>
      <td style="text-align:right">รีบูตเครื่อง</td>
      </tr>
       <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:center">Halt</td>
      <td style="text-align:right">	หยุดการทำงานของระบบ</td>
      </tr>
      </tbody>
      </table>
</div>

---

### การตั้งค่า init stage:

- ไฟล์ `/etc/inittab` กำหนดค่า init stage เริ่มต้น

- ไฟล์ `/etc/rc.d/rc?.d` เก็บสคริปต์สำหรับแต่ละ init stage
---
### หลักการทำงาน:

1.การเริ่มต้น:

- เมื่อเปิดเครื่อง BIOS จะโหลด bootloader

- Bootloader โหลดเคอร์เนล Linux

- เคอร์เนลเริ่มต้น init process

- Init process อ่านค่าจากไฟล์ `/etc/inittab`

- Init process รันสคริปต์สำหรับ init stage เริ่มต้น
  
2.การเปลี่ยน init stage:

- ผู้ใช้สามารถเปลี่ยน init stage ได้โดยใช้คำสั่ง `init`

- ตัวอย่าง: `init 3` เริ่มต้นระบบใน multi-user mode
  
3.การปิดระบบ:

- ผู้ใช้สามารถปิดระบบได้โดยใช้คำสั่ง `shutdown`

- Shutdown process เรียกใช้สคริปต์ shutdown

- สคริปต์ shutdown ปิดบริการระบบอย่างปลอดภัย

- สุดท้าย ปิดเครื่องหรือ halt ระบบ
---
### การเรียกใช้งานและผลลัพธ์ที่ได้

ผู้ใช้สามารถเรียกใช้งาน init stage ได้โดยใช้คำสั่ง `init`

- รูปแบบ: `init <level>`

- `<level>` คือหมายเลขของ init stage (0-6)

#### คำสั่งที่เกี่ยวข้องกับ Init stage ใน Linux
1. init:

- Options:

    - `n`: ไม่เปลี่ยน init stage จริง แสดงผลลัพธ์ที่จะเกิดขึ้น
  
    - `q`: เงียบ ไม่แสดงข้อความใด ๆ
  
    - `s`: shutdown
  
    - `t`: seconds รอ seconds วินาทีก่อน shutdown
      
- Arguments:

    -`<level`>: ระดับ init stage (0-6)
  
ตัวอย่าง:

- `init -n 3`: แสดงผลลัพธ์ที่จะเกิดขึ้นหากเปลี่ยน init stage ไปที่ 3

- `init -q 0`: ปิดเครื่องเงียบ ๆ

- `init -s`: shutdown

- `init -t 60 0`: รอ 60 วินาทีก่อน shutdown

2. shutdown:

- Options:

    - `-h`: shutdown
  
    - `-r`: reboot
  
    - `-c`: ยกเลิก shutdown
  
    - `-t`: seconds รอ seconds วินาทีก่อน shutdown
  
- Arguments:

    -`<message>`: ข้อความแจ้งเตือนผู้ใช้ก่อน shutdown
  
ตัวอย่าง:

`shutdown -h now`: shutdown

`shutdown -r`: reboot

`shutdown -c`: ยกเลิก shutdown

`shutdown -t 60 "System will shutdown in 60 seconds"`: รอ 60 วินาทีก่อน shutdown

3. systemctl:

- Options:

    - `-h`: แสดง help

    - `-l`: แสดงรายชื่อ services

    - `i`: แสดง information เกี่ยวกับ service

    - `-s`: shutdown

    - `-r`: reboot

- Arguments:

    - `<command>`: คำสั่ง systemctl
  
    - `<service>`: ชื่อ service
  
ตัวอย่าง:

`systemctl -h`: แสดง help

`systemctl -l`: แสดงรายชื่อ services

`systemctl -i ssh.service`: แสดง information เกี่ยวกับ ssh service

`systemctl -s`: shutdown

`systemctl -r`: reboot

> [!CAUTION]
> การเปลี่ยน init stage โดยไม่ได้ตั้งใจอาจทำให้ระบบหยุดทำงาน
> การปิดระบบโดยไม่ปิดบริการอย่างปลอดภัยอาจทำให้ข้อมูลเสียหาย
> การใช้คำสั่ง init กับ options หรือ arguments ที่ไม่ถูกต้องอาจทำให้เกิดผลลัพธ์ที่ไม่คาดคิด
