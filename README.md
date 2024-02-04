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
  <a href="#overview">Overview</a> •
  <a href="#introduction">Introduction</a> •
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

# Process Componentss
ส่วนประกอบหลักของกระบวนการ:
1. Program: คือโค้ดของโปรแกรมที่ถูกโหลดไว้ในหน่วยความจำ.
2. Process State: ระบบติดตามสถานะของกระบวนการ, ได้แก่ กระบวนการที่กำลังทำงาน, กระบวนการที่รอ, และกระบวนการที่ถูกหยุด.
3. Process Status:
รวมถึงข้อมูลเกี่ยวกับการทำงานปัจจุบันของกระบวนการ เช่น ID ของกระบวนการ (PID), หมายเลขห้องประชุม (TTY), และเวลาที่ใช้ในการทำงาน.
4. Process Relationship: ระบบต้องการทราบว่ากระบวนการไหนเป็นโมเดลของกระบวนการไหน.

5. Stack Status: ข้อมูลที่ใช้ในการจัดการหน่วยความจำสำหรับการเรียกฟังก์ชัน.

<a id="contributors"></a>
## :briefcase: Contributors
| Image 1 | Image 2 | Image 3 | Image 4 | Image 5 | Image 6 |
|---------|---------|---------|---------|---------|---------|
| ![Alt text 1](image_url_1) | ![Alt text 2](image_url_2) | ![Alt text 3](image_url_3) | ![Alt text 4](image_url_4) | ![Alt text 5](image_url_5) | ![Alt text 6](image_url_6) |
|:------:|:------:|:------:|:------:|:------:|:------:|
| Centered Text 1 | Centered Text 2 | Centered Text 3 | Centered Text 4 | Centered Text 5 | Centered Text 6 |




<a id="source"></a>
## Source :pushpin:
FastColabCopy is a Python script for parallel (multi-threading) copying of files between two locations. Currently developed for Google-Drive to Google-Drive transfers using Google-Colab. This script frequently achieves 10-50x speed improvements when copying numerous small files.



> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
