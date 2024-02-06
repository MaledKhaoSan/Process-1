<a id="process-management"></a>
# :round_pushpin: What is Process Management in Linux?
Process Management ใน Linux คือกระบวนการควบคุมและตรวจสอบกระบวนการที่กำลังทำงาน การสร้าง การควบคุม และการยุติการทำงานทั้งหมดในระบบ รวมถึงการจัดสรรทรัพยากรของกระประมวลผล โดยหลักการของ Process Management ประกอบไปด้วย 3 หลักนี้
<br><br>
1. Process Initiation (การเริ่มต้นกระบวนการ):
<br>การเริ่มต้นกระบวนการใหม่, ซึ่งอาจเกิดจากการใช้คำสั่งหรือโปรแกรมที่ทำงานตลอดเวลา.
      <br><br>
2. Process Control (การควบคุมการทำงาน):
<br>การควบคุมกระบวนการที่กำลังทำงาน ลำดับการทำงาน ว่ากระบวนการใดสำคัญกว่าจึงมาก่อน การติดตามและจัดการกระบวนการที่กำลังทำงานอยู่ การจัดสรร CPU, หน่วยความจำ, ทรัพยากรอื่นๆ
      <br><br>
3. Process Termination (การหยุดกระบวนการ):
<br>การสิ้นสุดการทำงานของกระบวนการเมื่อทำงานเสร็จสิ้น หรือ การที่ผู้ใช้บังคับให้หยุด, โดยจะคืนทรัพยากรที่ใช้ไป และสิ้นสุดการทำงานของตัวเอง

> [!TIP]
> ด้วยหลักการของ Process Management ทั้งสามนี้ช่วยให้ระบบปฏิบัติการสามารถจัดการกระบวนการในระบบได้อย่างถูกต้อง 

---

<a id="process-creation"></a>
# :bulb: Process Initiation
พื้นฐานหรือหลักการทำงานของ Process Initiation จะทำหน้าที่สร้างกระบวนการใหม่ (process) เพื่อรันโปรแกรมนั้น ๆ บนระบบปฏิบัติการ คือการสร้างโปรแกรมใหม่ขึ้นมาเพื่อทำงานตามชุดคำสั่งและ Process Initiation สามารถเกิดขึ้นได้หลายวิธีตามบริบทที่ใช้ เช่น


1. ผู้ใช้รันโปรแกรม:
    - ผู้ใช้พิมพ์คำสั่งบน command line เช่น `ls`, `cd`, `mkdir`, `grep`
    - ผู้ใช้รันโปรแกรมผ่าน graphical user interface (GUI).

        ### :computer: ตัวอย่างเหตุการณ์เมื่อผู้ใช้พิมพ์คำสั่งบน Command Line
        #### `ls` - แสดงรายการ file และ directory
        > คำสั่ง `ls` จะแสดงเนื้อหาใน directory ปัจจุบัน ระบุรายการ file และ directory ทั้งหมด
        > ```ruby
        > $ ls
        > Desktop  Documents  Downloads  Music  Pictures  Videos
        > ```

        #### `cd` - เปลี่ยน directory
        > คำสั่ง `cd` จะเปลี่ยน directory ปัจจุบันเป็น "Documents."
        > ```ruby
        > $ cd Documents
        > ```

        #### `mkdir` - สร้าง directory
        > คำสั่ง `mkdir` จะสร้าง directory ใหม่ชื่อ "NewDirectory."
        > ```ruby
        > $ mkdir NewDirectory
        > ```

        #### `grep` - ค้นหาข้อความในไฟล์
        > คำสั่ง `grep` จะค้นหาข้อความที่ระบุในเนื้อหาของไฟล์ (เช่น "รูปแบบ" ใน "ชื่อไฟล์.txt").
        > ```ruby
        > $ grep "รูปแบบ" ชื่อไฟล์.txt
        > ```

2. การเริ่มทำงานโดยระบบปฏิบัติการ:
    - ระบบปฏิบัติการรัน scripts ที่ตั้งเวลาไว้
    - ระบบปฏิบัติการเริ่มโปรแกรม daemon ที่ทำงานพื้นหลัง
    - ระบบปฏิบัติการตอบสนองต่อ events ต่างๆ เช่น การกดปุ่มบน keyboard
        ### :computer: ตัวอย่างเหตุการณ์ Process Initiation จาก Scripts ที่ตั้งเวลาไว้

        #### สมมติว่าเรามี script ชื่อ `daily_backup.sh` 
        > ที่ใช้สำหรับสำรองข้อมูลทุกวันเวลา 12:00 นาฬิกา โดยให้ระบบปฏิบัติการเรียกใช้ script นี้ตามกำหนดเวลาที่กำหนด
        > ```bash
        > # daily_backup.sh
        > #!/bin/bash
        > 
        > # ทำงานสำหรับการสำรองข้อมูล
        > echo "Running daily backup..."
        > # คำสั่งสำหรับสำรองข้อมูล
        > # ...
        > 
        > # สิ้นสุด script
        > ```
        > จากนั้นให้กำหนดตัวแปร environment หรือ cron job ในระบบปฏิบัติการเพื่อทำงาน script ตามเวลาที่ต้องการ
        >```bash
        ># ตั้งค่า cron job เพื่อเรียกใช้ script ทุกวันที่ 2 เวลา 2 โมงเช้า
        >0 12 * * * /path/to/daily_backup.sh
        >```
        >
        > ในที่นี้เราให้ cron job ระบบปฏิบัติการเรียกใช้ `daily_backup.sh` ทุกวันเวลา 12:00 นาฬิกา เป็นตัวอย่างการเริ่มต้นกระบวนการ (Process Initiation) จาก script ที่ตั้งเวลาไว้

        <br>

        ### :computer: ตัวอย่างเหตุการณ์ Process Initiation จาก Daemon

        โปรแกรม daemon เป็นโปรแกรมที่ทำงานแบบ <a href="">background process</a> โดยไม่ต้องมีผู้ใช้เรียกใช้งานโดยตรง เรามีตัวอย่างเป็น daemon ที่เป็น web server ซึ่งทำงานตลอดเวลาเพื่อตอบรับ requests จาก clients

        > ตัวอย่างโปรแกรม daemon ของ web server (ในที่นี้เราให้ตั้งตัวอย่างเป็น Apache HTTP Server)
        > ```bash
        > # ในการเริ่ม Apache HTTP Server เป็น daemon
        > sudo service apache2 start
        > ```
        > 
        > ในที่นี้เราให้ `apache2` เป็นตัวอย่างของโปรแกรม daemon ที่ทำงานพื้นหลังโดยไม่ต้องมีผู้ใช้เรียกใช้งานโดยตรง เป็นตัวอย่างการเริ่มต้นกระบวนการ (Process Initiation) จากโปรแกรม daemon
        >
        > <p align="center"><img src="https://github.com/MaledKhaoSan/Project-Comor/blob/main/assets/process_initiation.png?raw=true" alt="Logo" width="auto" height="auto"></p>


> [!TIP]
> การสร้างกระบวนการใหม่ของ Process Initiation นั้นอาจจะใช้วิธีการ fork() และ exec() หรือวิธีการอื่น ๆ ขึ้นอยู่กับระบบปฏิบัติการและลักษณะการทำงาน
<br>

---


<a id="process-tracking"></a>
# :bulb: Process Tracking
เป็นกระบวนการที่ให้ระบบปฏิบัติการติดตามและบันทึกข้อมูลเกี่ยวกับกระบวนการที่กำลังทำงานในระบบ ซึ่งเป็นส่วนหนึ่งของ Process Management ในระบบปฏิบัติการ

1. Process ID (PID): หมายเลขที่ระบุกระบวนการเฉพาะตัว
2. Parent Process ID (PPID): หมายเลขที่ระบุกระบวนการหลักที่สร้างกระบวนการนี้ (parent process)
3. สถานะ (Status): บอกถึงสถานะปัจจุบันของกระบวนการ เช่น กำลังทำงาน (Running), หยุดชั่วคราว (Stopped), หรือ หยุด (Terminated)
4. เวลาการใช้งาน (Execution Time): ระยะเวลาที่กระบวนการทำงานจริง
5. การใช้ทรัพยากร (Resource Usage): การใช้ทรัพยากรเช่น CPU, หน่วยความจำ

---


> [!NOTE]
> ## :raising_hand: ต่อไปเราจะลงลึกในหัวข้อ Process Control (การควบคุมการทำงาน)
> ที่มีบทบาทสำคัญในการจัดการลำดับการทำงานของกระบวนการ, การติดตามและจัดการกระบวนการที่กำลังทำงานอยู่, และการจัดสรรทรัพยากรเช่น CPU และหน่วยความจำ.
>

---

# :bulb: Process Control

Process Control (การควบคุมการทำงาน) เป็นส่วนสำคัญของ Process Management ในระบบ Linux ซึ่งมีบทบาทในการควบคุมลำดับการทำงานของกระบวนการ, การติดตามและจัดการกระบวนการที่กำลังทำงาน, และการจัดสรรทรัพยากร เช่น CPU, หน่วยความจำ, และทรัพยากรอื่น ๆ ต่อไปนี้คือการทำงานที่เกี่ยวข้องกับ Process Control:

1. การสั่งรันคำสั่ง (Running a command): เมื่อผู้ใช้รันคำสั่งบนระบบ Linux, มันจะเป็นการสร้างกระบวนการ (process) เพื่อทำงานตามคำสั่งที่กำหนด.

2. Linux Manages Tasks Using Processes (Linux จัดการงานโดยใช้กระบวนการ): ในระบบปฏิบัติการ Linux, การจัดการงานหลาย ๆ อย่างเป็นไปผ่านกระบวนการ ซึ่งเป็นตัวกลางที่ช่วยจัดการทรัพยากรและควบคุมการทำงานของโปรแกรม.

3. Parent/Child Relationship (ความสัมพันธ์ระหว่าง Parent และ Child): กระบวนการสามารถเริ่มกระบวนการย่อย (subprocess) ได้ ซึ่งจะเกิดความสัมพันธ์ระหว่างกระบวนการหลัก (parent process) และกระบวนการย่อย (child process).

4. Users Can Only Control Their Processes (ผู้ใช้สามารถควบคุมกระบวนการของตนเอง): แต่ละผู้ใช้บนระบบ Linux สามารถควบคุมกระบวนการที่เป็นของตนเองได้ เขาสามารถดูข้อมูล, หยุด, หรือเรียกคำสั่งอื่น ๆ ในบริบทของกระบวนการของตน.

5. Root Can Control All System and User Processes (Root สามารถควบคุมกระบวนการทั้งระบบและผู้ใช้): ผู้ใช้ที่มีสิทธิ์ root (superuser) สามารถควบคุมทุกระบวนการในระบบ, รวมถึงกระบวนการที่เป็นของผู้ใช้ทั้งหมด. Root มีอำนาจสูงสุดในการควบคุมและจัดการทรัพยากรระบบ.
---

<div align="center">
      ตัวอย่างคำสั่ง
      <table>
      <thead>
      <tr>
      <th style="text-align:left">คำสั่ง</th>
      <th style="text-align:center">ประเภท</th>
      <th style="text-align:right">ตัวอย่าง</th>
      </tr>
      </thead>
      <tbody>
      <tr>
      <td style="text-align:left">ps</td>
      <td style="text-align:center">แสดงรายการ process ทั้งหมด</td>
      <td style="text-align:right">ps aux</td>
      </tr>
      <tr>
      <td style="text-align:left">kill</td>
      <td style="text-align:center">ยุติการทำงานของ process</td>
      <td style="text-align:right">`kill -9 1234`</td>
      </tr>
      <tr>
      <td style="text-align:left">renice</td>
      <td style="text-align:center">เปลี่ยนระดับความสำคัญของ process</td>
      <td style="text-align:right">`renice -n 10 1234`</td>
      </tr>
      <tr>
      <td style="text-align:left">job controls</td>
      <td style="text-align:center">ควบคุมการทำงานของ process ในรูปแบบ job</td>
      <td style="text-align:right">`bg %1, fg %2`</td>
      </tr>
      </tbody>
      </table>
</div>


---


1. ### :computer: Listing Processes
    #### `ps` - แสดงข้อมูลเกี่ยวกับกระบวนการที่กำลังทำงาน
    > ```ruby
    > $ ps
    > ```
    > ```
    > PID TTY           TIME CMD
    > 1234 pts/0     00:00:01 bash
    > 5678 pts/0     00:00:00 ps
    > ```

    <br>

2. ### :computer: Searching For Processes
    #### `kill` - ส่งสัญญาณให้ หยุดทำงาน
    >  คำสั่ง `kill` ใช้เพื่อหยุดการทำงาน โดยมักใช้ร่วมกับ `PID` (Process ID) ของกระบวนการ
    > ```ruby
    > $ kill [signal] PID
    > ```

3. ### :computer: Watching Processes
    #### `kill` - ส่งสัญญาณให้ หยุดทำงาน
    >  คำสั่ง `kill` ใช้เพื่อหยุดการทำงาน โดยมักใช้ร่วมกับ `PID` (Process ID) ของกระบวนการ
    > ```ruby
    > $ kill [signal] PID
    > ```

2. ### :computer: Searching For Processes
    #### `kill` - ส่งสัญญาณให้ หยุดทำงาน
    >  คำสั่ง `kill` ใช้เพื่อหยุดการทำงาน โดยมักใช้ร่วมกับ `PID` (Process ID) ของกระบวนการ
    > ```ruby
    > $ kill [signal] PID
    > ```
    
    <br>

    #### `renice` - เปลี่ยนระดับความสำคัญของกระบวนการ
    > คำสั่ง `renice` ใช้เพื่อปรับลำดับความสำคัญของ niceness ของกระบวนการ (process) บนระบบ Linux โดยมักใช้ร่วมกับ `PID` (Process ID)
    > ```ruby
    > # -n: ระบุค่า niceness ใหม่
    > # -p: ระบุ PID ของกระบวนการ
    >
    > $ renice -n 10 -p PID
    > ```

    <br>

3. ### :computer: Managing Jobs
    #### `renice` - เปลี่ยนระดับความสำคัญของกระบวนการ
    > เป็นกระบวนการควบคุมและจัดการกับกระบวนการ (process) ที่กำลังทำงานหรือหยุดทำงานในระบบปฏิบัติการ Linux หรือ UNIX-like systems โดยใช้เทคนิคที่เรียกว่า Job Control.

    #### `Job Control`
    > คำสั่ง bg (<a href="">Background</a>) และ fg (<a href="">Foreground</a>) ใช้เพื่อควบคุมการทำงานของ jobs (งาน) ในระบบปฏิบัติการ Linux หรือ UNIX-like systems. นี่คือตัวอย่างคำสั่ง:

---

### Foreground และ Background Processes

- **Foreground Processes:**
    - การทำงานที่อยู่เบื้องหน้าสามารถสื่อสาร หรือ รับคำสั่งผู้ใช้ และ แสดงผลลัพธ์บนหน้าจอได้ทันที
    - คือกระบวนการที่ป้องกันผู้ใช้ไม่ให้ใช้ shell จนกว่ากระบวนการนั้นจะเสร็จสิ้น.
    - มี parent process และกระบวนการใหม่เรียกว่า child process

- **Background Processes:**
    - การทำงานที่อยู่บนพื้นหลัง โดยไม่รบกวน หน้า console และผู้ใช้สามารถป้อนคำสั่งอื่นได้ในขณะที่กระบวนการนี้กำลังทำงาน.
    - เพื่อให้คำสั่งทำงานเป็น background process, ให้เพิ่มเครื่องหมาย ampersand (&) หลังคำสั่ง

> [!CAUTION]
> **ข้อควรระวัง**
> - โปรแกรม background อาจทำงานไม่เสร็จสิ้น หากผู้ใช้ logout ออกจากระบบ
> - โปรแกรม background อาจใช้ทรัพยากรระบบมากเกินไป


> [!NOTE]
> ## :raising_hand: ต่อไปเราจะพูดถึง Process Termination (การหยุดกระบวนการ)
> ซึ่งเป็นขั้นตอนสุดท้ายใน Process Management ที่เกี่ยวข้องกับการสิ้นสุดกระบวนการทำงานของกระบวนการ.
>

---


# :bulb: Process Termination

Process Termination (การหยุดกระบวนการ) เป็นขั้นตอนสุดท้ายใน Process Management ในระบบ Linux ซึ่งมีบทบาทในการสิ้นสุดกระบวนการทำงานของกระบวนการ โดยมีลักษณะการทำงานดังนี้:

## 3. บทบาทหรือหน้าที่บน Linux

### 3.1 พื้นฐานหรือหลักการทำงาน
- **Process Termination (การหยุดกระบวนการ):**
    - **หน้าที่หลัก:** การสิ้นสุดกระบวนการทำงานของกระบวนการ.
    - **สาเหตุของการหยุด:**
        - การทำงานเสร็จสิ้น: กระบวนการทำงานของโปรแกรมเสร็จสิ้นโดยปราศจากข้อผิดพลาด.
        - การถูกบังคับให้หยุด: กระบวนการถูกส่งสัญญาณจากโปรแกรมหรือผู้ใช้ให้หยุดทำงาน.
    - **ผลลัพธ์:**
        - การหยุดกระบวนการทำงาน.
        - คืนทรัพยากรที่ใช้ไป, เช่น หน่วยความจำ, CPU, และทรัพยากรอื่น ๆ.

### 3.2 การสิ้นสุดกระบวนการ
- **การสิ้นสุดกระบวนการ:**
    - `kill`: ส่งสัญญาณให้กระบวนการหยุดทำงาน.
    - `pkill`: หยุดกระบวนการที่มีชื่อที่ตรงกับคำที่กำหนด.
    - `killall`: หยุดกระบวนการที่มีชื่อที่ตรงกับคำที่กำหนด.

### 3.3 การคืนทรัพยากร
- **การคืนทรัพยากร:**
    - `wait`: รอจนกระบวนการลูกค้าทำงานเสร็จ.
    - `exit`: สิ้นสุดการทำงานของกระบวนการและส่งค่ากลับ.

---

> [!TIP]
> ## :raising_hand: สรุป
> Process Termination (การหยุดกระบวนการ) เป็นขั้นตอนสุดท้ายของ Process Management ที่เกี่ยวข้องกับการสิ้นสุดกระบวนการทำงานของกระบวนการ โดยมีการใช้คำสั่ง `kill`, `pkill`, `killall` เพื่อส่งสัญญาณหยุดทำงานแก่กระบวนการ และใช้ `wait` และ `exit` เพื่อรอและคืนทรัพยากรต่าง ๆ ที่ใช้งานของกระบวนการก่อนหน้า.
>

---


REF
job control: https://linuxcommand.org/lc3_lts0100.php
