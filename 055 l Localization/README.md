# LOCALIZATION 📂

**Locale**  หรือ รูปแบบข้อมูลท้องถิ่น เป็นส่วนหนึ่งของระบบ Internationalization (i18n) และ Localization (l10n) เพื่อให้โปรแกรมต่าง ๆ สามารถที่จะแสดง และจัดการข้อมูลในแต่ละภาษาและท้องถิ่น ได้อย่างถูกต้องเหมาะสม Locale ต่าง ๆ ของแต่ละภาษาและท้องถิ่นจะมีลักษณะเป็น ส่วน ๆ ซึ่งสามารถเพิ่มเข้าไปในระบบ Localization ต่าง ๆ ได้ และแต่ละ Locale จะเป็น อิสระจากกัน รูปแบบข้อมูลท้องถิ่นอาจจะรวมไปถึงข้อมูลสำหรับจัดการข้อความที่ซับซ้อน เช่นการจัดเรียง การตัดคำ และอื่น ๆ

ระบบ **Localization ใน Linux** ส่วนใหญ่จะอาศัยระบบหลัก ๆ คือ POSIX Locale ซึ่งอยู่ใน C Library เช่น GLIBC ซึ่งใน POSIX Locale การทำงานจะใช้ค่าตัวแปรระบบ (LC_...) ซึ่ง จะประกอบด้วยส่วนต่าง ๆ ดังนี้


# Install the Localize CLI

With Python and pip installed, use pip to install the Localize CLI :
<table>
<tr>
<th>Windows</th>
</tr>
<tr>
<td>
<pre lang="js">
pip install localize
</pre>
</td>
</tr>
</table>

<table>
<tr>
<th>Linux, OS X, or Unix</th>
</tr>
<tr>
<td>
<pre lang="js">
sudo pip install --ignore-installed localize
</pre>
</td>
</tr>
</table>

<table>
<tr>
<th>To upgrade an existing Localize CLI installation, use the --upgrade option :</th>
</tr>
<tr>
<td>
<pre lang="js">
pip install --upgrade localize
</pre>
</td>
</tr>
</table>

