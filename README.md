<!-- LOGO -->
<br />
<h1>
<p align="center">
  <img src="https://cdn-icons-png.flaticon.com/512/518/518713.png" alt="Logo" width="auto" height="110">
  <br>Linux
</h1>
  <p align="center">
    how process management is handled in the Linux operating system.
    <br />
    </p>
</p>
<p align="center">
  <a href="#about">About The Project</a> •
  <a href="#table">Tables</a> •
  <a href="#contributors">Contributors</a> •
  <a href="#source">Source</a>
</p>  

---

<a id="about"></a>
## Computer Organization and Operating System Assignment  :pushpin:
รายงานฉบับนี้เป็นส่วนหนึ่งของวิชา 06016412 COMPUTER ORGANIZATION AND OPERATING SYSTEM ชั้นปีที่ 2 (2/2023) โดยมีจุดประสงค์เพื่อศึกษาความรู้ที่ได้จากเรื่อง Process ของ Linux ซึ่งรายงานนี้นำเสนอความรู้พื้นฐานเกี่ยวกับProcess ใน Linux โดยอธิบายองค์ประกอบสำคัญของโพรเซส เช่น สถานะprocess การจัดการหน่วยความจำ และการจัดตารางเวลา รวมถึงการทำงานของprocessใน Linux เป้าหมายของรายงานนี้ คือ เพื่อช่วยให้ผู้อ่านเข้าใจระบบprocess ใน Linux และสามารถจัดการprocessต่างๆ บนคอมพิวเตอร์ได้อย่างมีประสิทธิภาพ

---

<a id="overview"></a>
## Overview :pushpin:
ในระบบปฏิบัติการ Linux,  Process ใน Linux คือ เปรียบเสมือนโปรแกรมที่กำลังทำงานอยู่ เป็นหน่วยพื้นฐานของการประมวลผลในระบบ Linux แต่ละ process จะมีหน่วยความจำ พื้นที่ว่างบนดิสก์ และทรัพยากรระบบอื่นๆ ของตัวเอง ช่วยให้ผู้ใช้สามารถทำงานหลายอย่างพร้อมกัน ใช้ทรัพยากรอย่างมีประสิทธิภาพ และปรับแต่งระบบ Linux ให้ทำงานตามต้องการ

---

<a id="introduction"></a>
# :round_pushpin: Introduction: Process
Process Components ใน Linux
คือส่วนหนึ่งของระบบปฏิบัติการที่จัดการกับการทำงานของกระบวนการ (Processes) ในระบบ ซึ่งรวมถึงการจัดการกระบวนการเริ่มต้น (Boot Process), การจัดการกระบวนการทั่วไป (Process Management), การจัดการบริการ (Service Management), และตัวตั้งเวลางาน (Task Scheduler) ที่มีบทบาทสำคัญในการทำงานของระบบปฏิบัติการ Linux.


## :paperclip: ลักษณะสำคัญของ Process:
- มีเอกลักษณ์: แต่ละ process จะมี PID (Process ID) ที่ไม่ซ้ำกัน
- มีสถานะ: Process มีสถานะต่างๆ เช่น รัน (Running), รอ (Waiting), หยุด (Stopped)
- มีลำดับความสำคัญ: Process แต่ละ process จะมีลำดับความสำคัญที่กำหนดว่า process ใดควรได้รับทรัพยากรระบบก่อน
- มีทรัพยากร: Process แต่ละ process จะมีหน่วยความจำ พื้นที่ว่างบนดิสก์ และทรัพยากรระบบอื่นๆ ของตัวเอง
- มีอิสระ: Process แต่ละ process ทำงานแยกกัน ไม่รบกวนกัน

## :paperclip: ประเภทของ Process:
- Foreground process: Process ที่ผู้ใช้กำลังโต้ตอบอยู่
- Background process: Process ที่ทำงานอยู่เบื้องหลัง ไม่ได้โต้ตอบกับผู้ใช้
- Daemon: Process ที่ทำงานอยู่เบื้องหลัง โดยปกติจะเริ่มต้นเมื่อระบบบูต และทำงานต่อไปจนกว่าระบบจะปิด

## :paperclip: ความสำคัญของ Process:
- การทำงานหลายอย่างพร้อมกัน: Process ช่วยให้ผู้ใช้สามารถทำงานหลายอย่างพร้อมกันบนระบบ Linux
- การใช้ทรัพยากรอย่างมีประสิทธิภาพ: Process ช่วยให้ระบบ Linux สามารถใช้ทรัพยากรระบบอย่างมีประสิทธิภาพ
- การปรับแต่งระบบ: Process ช่วยให้ผู้ใช้สามารถปรับแต่งระบบ Linux ให้ทำงานตามต้องการ


---

<a id="table"></a>
# :books: Table of contents

- <a href="059 l Process Management/README.md">Process Management</a>
	- <a href="059 l Process Management/#test">Process Management</a>
	* [Inline code](#inline-code)
	* [Code block](#code-block)
- [Alignments](#alignments)
- [Tables](#tables)
- [Links](#links)
	* [Inline](#inline)
	* [Reference](#reference)
	* [Relative](#relative)
	* [Auto](#auto)
	* [Section](#section)
- [Images](#images)
- [Lists](#lists)
	* [Ordered](#ordered)
	* [Unordered](#unordered)
	* [Task](#task)

---

<a id="contributors"></a>
# :briefcase: Contributors
> [!TIP]
> รายชื่อสมาชิกและหน้าที่รับผิดชอบ
>
><p align="center">
><table width="100%" gap="30px">
>    <tr gap="30px">
>      <td width="33%"><img src="https://github.com/MaledKhaoSan/Project-Comor/blob/main/assets/055.JPG?raw=true" width="auto" height="100%"/></td>
>      <td width="33%"><img src="https://github.com/MaledKhaoSan/Project-Comor/blob/main/assets/059.png?raw=true" width="100%"/></td>
>      <td width="33%"><img src="https://cdn-icons-png.flaticon.com/512/1077/1077114.png" width="100%"/></td>
>    </tr>
>    <tr>
>      <td align="center">65070055<br>นางสาวญาตาวี  ฤกษประสูต<br>duty</td>
>      <td align="center">65070059<br>นายณฏฐพล สวัสดิ์มูล<br>Process Management</td>
>      <td align="center">65070066<br>นางสาวณัฏฐณิชา  สุวรรณพยัคฆ์<br>duty</td>
>    </tr>
></table>
><br>
><table width="100%">
>    <tr>
>      <td width="33%"><img src="https://cdn-icons-png.flaticon.com/512/1077/1077114.png" width="100%"/></td>
>      <td width="33%"><img src="https://cdn-icons-png.flaticon.com/512/1077/1077114.png" width="100%"/></td>
>      <td width="33%"><img src="https://github.com/MaledKhaoSan/Project-Comor/blob/main/assets/090.jpg" width="100%"/></td>
>    </tr>
>    <tr>
>      <td align="center">65070077<br>นางสาวณัฐนันท์  งามสมุทร<br>Boots Process</td>
>      <td align="center">65070087<br>นายดราคริสต์  ปล้องไม้<br>duty</td>
>      <td align="center">65070090<br>นายธนกฤต  สิงห์สังข์<br>System Time</td>
>    </tr>
></table>
></p>

---

<a id="source"></a>
# :card_index_dividers: Source
> [!NOTE]
> Useful information that users should know, even when skimming content.
> - Book
>    - Paul Cobbau, Linux Storage - https://linux-training.be/linuxsto.pdf
>    - Richard Petersen, The Complete Reference Linux 6th Edition - https://doc.lagout.org/operating%20system%20/linux/Linux%20-%20The%20Complete%20Reference.pdf
> - Webpage
>    - Linux File System - GeeksforGeeks. https://www.geeksforgeeks.org/linux-file-system/.
>    - Linux File System: Understanding Directory Structure ... - howtouselinux. https://www.howtouselinux.com/post/linux-file-system-understanding-directory-structure-and-navigating-the-
>    - Guide to Linux Filesystems | Baeldung on Linux. https://www.baeldung.com/linux/filesystems.
>    - Partitions And Filesystems In Linux – Introduction. https://www.linuxfordevices.com/tutorials/linux/partitions-and-filesystems.
>    - Linux File System - javatpoint. https://www.javatpoint.com/linux-file-system.
