
Computer Organization and Operating System Assignment 

# Table of Contents

- [Introduction](#introduction)
- [Section 1](#process-components)
    - [Subsection 1.1](#subsection-11)
    - [Subsection 1.2](#subsection-12)
- [Section 2](#section-2)
- [Conclusion](#conclusion)


# Introduction: Process
&emsp;&emsp;Process Components ใน Linux
คือส่วนหนึ่งของระบบปฏิบัติการที่จัดการกับการทำงานของกระบวนการ (Processes) ในระบบ ซึ่งรวมถึงการจัดการกระบวนการเริ่มต้น (Boot Process), การจัดการกระบวนการทั่วไป (Process Management), การจัดการบริการ (Service Management), และตัวตั้งเวลางาน (Task Scheduler) ที่มีบทบาทสำคัญในการทำงานของระบบปฏิบัติการ Linux.

# Process Components
ส่วนประกอบหลักของกระบวนการ:
1. Program: คือโค้ดของโปรแกรมที่ถูกโหลดไว้ในหน่วยความจำ.
2. Process State: ระบบติดตามสถานะของกระบวนการ, ได้แก่ กระบวนการที่กำลังทำงาน, กระบวนการที่รอ, และกระบวนการที่ถูกหยุด.
3. Process Status:
รวมถึงข้อมูลเกี่ยวกับการทำงานปัจจุบันของกระบวนการ เช่น ID ของกระบวนการ (PID), หมายเลขห้องประชุม (TTY), และเวลาที่ใช้ในการทำงาน.
4. Process Relationship: ระบบต้องการทราบว่ากระบวนการไหนเป็นโมเดลของกระบวนการไหน.

5. Stack Status: ข้อมูลที่ใช้ในการจัดการหน่วยความจำสำหรับการเรียกฟังก์ชัน.




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