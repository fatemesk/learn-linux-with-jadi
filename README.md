# learn-linux-with-jadi
Personal Linux learning notes based on Jadi’s course

<div dir="rtl" align="right">

<span dir="rtl"><bdi>101.1</bdi> تعیین و پیکربندی تنظیمات سخت‌افزار</span>  

<span dir="rtl">سیستم‌عامل (<bdi>OS</bdi>) یک نرم‌افزار سیستمی است که سخت‌افزار کامپیوتر و منابع نرم‌افزاری را مدیریت می‌کند و سرویس‌های رایج را برای برنامه‌های کامپیوتری فراهم می‌کند. این نرم‌افزار روی سخت‌افزار قرار می‌گیرد و منابع را در صورت درخواست سایر نرم‌افزارها (که گاهی اوقات برنامه فضای کاربری (<bdi>userspace program</bdi>) نامیده می‌شود) مدیریت می‌کند.</span>  

<span dir="rtl">فریمور (<bdi>Firmware</bdi>) نرم‌افزاری است که روی سخت‌افزار شما قرار دارد و آن را اجرا می‌کند؛ آن را به عنوان یک سیستم‌عامل یا درایور داخلی برای سخت‌افزار خود در نظر بگیرید. مادربردها نیز برای کار کردن به نوعی فریمور نیاز دارند.</span>  

<span dir="rtl">فریمور نوعی نرم‌افزار است که در سخت‌افزار وجود دارد. نرم‌افزار هر برنامه یا گروهی از برنامه‌ها است که توسط یک کامپیوتر اجرا می‌شود.</span>  

</div>

<div dir="rtl" align="right">

# <bdi>BIOS</bdi>  

<span dir="rtl"><bdi>BIOS</bdi> (سیستم ورودی/خروجی پایه) از طریق یک سیستم مبتنی بر منوی متنی قابل کنترل است و با دسترسی به اولین سکتور از اولین پارتیشن هارد دیسک شما (<bdi>master boot record (MBR)</bdi>) کامپیوتر را بوت می‌کند.</span>  

<span dir="rtl">این برای سیستم‌های مدرن کافی نیست و اکثر سیستم‌ها از یک روش بوت دو مرحله‌ای استفاده می‌کنند.</span>  

</div>


<div dir="rtl" align="right">

# <bdi>UEFI</bdi>  

<span dir="rtl"><bdi>UEFI</bdi> یعنی: رابط یکپارچه توسعه‌پذیر میان‌افزار (<bdi>Unified Extensible Firmware Interface</bdi>) و یک فناوری جدیدتر از <bdi>BIOS</bdi> برای بوت کردن سیستم است.</span>  

<span dir="rtl">🔹 داستان پیدایشش: سال ۱۹۹۸ شرکت <bdi>Intel</bdi> شروع کرد روی نسخه اولیه‌ای به اسم <bdi>EFI</bdi> کار کردن. بعدها این فناوری تکامل پیدا کرد و تبدیل به استاندارد جهانی شد که الان اسمش <bdi>UEFI</bdi> است.</span>  

<span dir="rtl">🔹 تفاوت مهم با <bdi>BIOS</bdi>: برخلاف <bdi>BIOS</bdi> که مستقیم از اولین سکتور دیسک بوت می‌کرد، <bdi>UEFI</bdi> از یک پارتیشن مخصوص بوت استفاده می‌کند.</span>  

<span dir="rtl">📂 جزئیات این پارتیشن بوت: اسمش هست <bdi>EFI System Partition (ESP)</bdi>، با فرمت <bdi>FAT</bdi> (مثل فلش مموری‌ها) ساخته می‌شود و در لینوکس معمولاً در مسیر <bdi>/boot/efi</bdi> قرار دارد.</span>  

<span dir="rtl">📄 فایل‌های بوت <bdi>UEFI</bdi>: پسوند این فایل‌ها <bdi>.efi</bdi> است (مثلاً <bdi>grubx64.efi</bdi>) و هر بوت‌لودر (مثل <bdi>GRUB</bdi> یا ویندوز بوت منیجر) باید به‌صورت رسمی در <bdi>UEFI</bdi> ثبت شود تا سیستم بتواند آن را پیدا و اجرا کند.</span>  

<span dir="rtl">💡 مثال تصویری: فرض کن <bdi>UEFI</bdi> مثل یک «کتابخانه بوت» است. هر سیستم‌عامل یا بوت‌لودر باید یک کارت شناسایی (<bdi>.efi</bdi> file) داشته باشد و در قفسه مشخصی (<bdi>ESP</bdi> پارتیشن) ثبت شده باشد تا وقت روشن شدن سیستم، <bdi>UEFI</bdi> بتواند بیاید از روی آن کارت بفهمد چه چیزی را و چطور اجرا کند.</span>  

</div>


<div dir="rtl" align="right">

# دستگاه‌های جانبی (Peripheral Devices)  
دستگاه‌هایی که به مادربورد یا سیستم وصل می‌شوند تا قابلیت‌های اضافی فراهم کنند.

---

## PCI / PCIe  
- **PCI**: مخفف <bdi>Peripheral Component Interconnect</bdi>، درگاهی روی مادربورد برای افزودن قطعاتی مانند کارت صدا یا کارت شبکه.  
- **PCI Express (PCIe)**: نسخه جدیدتر و سریع‌تر PCI که امروزه در بیشتر سرورها استفاده می‌شود.

---

<div dir="rtl" align="right">

<h2>هارد داخلی (<bdi>Internal HDD</bdi>)</h2>

<p>
  <span dir="rtl"><bdi>SATA</bdi> که مخفف <bdi>Serial Advanced Technology Attachment</bdi> است، یک رابط استاندارد برای اتصال دستگاه‌های ذخیره‌سازی مانند هارد دیسک‌ها و <bdi>SSD</bdi>ها به مادربرد کامپیوتر است. این تکنولوژی امکان انتقال داده‌ها با سرعت بالا بین این دستگاه‌ها و سیستم کامپیوتری را فراهم می‌کند. به زبان ساده‌تر، <bdi>SATA</bdi> یک نوع کابل و پورت است که برای اتصال هارد دیسک‌ها و <bdi>SSD</bdi>ها به کامپیوتر استفاده می‌شود تا اطلاعات بتوانند بین این دو رد و بدل شوند.</span>
</p>

<p>
  <span dir="rtl"><bdi>PATA</bdi> که مخفف <bdi>Parallel Advanced Technology Attachment</bdi> است، یک استاندارد قدیمی برای اتصال دستگاه‌های ذخیره‌سازی مانند هارد دیسک به مادربرد کامپیوتر بود. این رابط به دلیل انتقال موازی داده‌ها، از طریق کابل‌های پهن و با سیم‌های زیاد شناخته می‌شد. به <bdi>PATA</bdi> همچنین <bdi>IDE (Integrated Drive Electronics)</bdi> نیز گفته می‌شد. این فناوری با ظهور رابط‌های سریع‌تر <bdi>SATA</bdi> منسوخ شد.</span>
</p>

<p>
  <span dir="rtl"><bdi>SCSI</bdi> یا <bdi>Small Computer System Interface</bdi>، مجموعه‌ای از استانداردهای رابط موازی برای اتصال دستگاه‌های مختلفی مانند هارد دیسک، پرینتر و اسکنر به کامپیوتر است. این فناوری امکان اتصال چندین دستگاه به یک پورت را فراهم می‌کرد و قابلیت انتقال داده‌های با سرعت بالا داشت. به‌طور سنتی، <bdi>SCSI</bdi> در سرورها و سیستم‌های حرفه‌ای که نیاز به کارکرد مداوم داشتند استفاده می‌شد. امروزه استاندارد <bdi>SAS (Serial Attached SCSI)</bdi> جایگزین <bdi>SCSI</bdi> موازی شده است و عملکرد و قابلیت‌های بیشتری ارائه می‌دهد.</span>
</p>

</div>

---

<div dir="rtl" align="right">

<h2>هارد خارجی (<bdi>External HDD</bdi>)</h2>

<p>
  <span dir="rtl"><bdi>Fiber</bdi>: اتصال داده پرسرعت برای انتقال اطلاعات در فواصل زیاد و با پهنای باند بالا.</span>
</p>

<p>
  <span dir="rtl"><bdi>SSD over USB</bdi>: حافظه <bdi>SSD</bdi> که از طریق پورت <bdi>USB</bdi> به سیستم متصل می‌شود و امکان جابه‌جایی آسان و سرعت بالا را فراهم می‌کند.</span>
</p>

<hr/>

<h2>کارت شبکه (<bdi>Network Cards</bdi>)</h2>

<p>
  <span dir="rtl"><bdi>RJ45</bdi>: رابط سیمی استاندارد اترنت برای اتصال کامپیوترها و تجهیزات شبکه با کابل شبکه.</span>
</p>

<hr/>

<h2>کارت بی‌سیم (<bdi>Wireless Cards</bdi>)</h2>

<p>
  <span dir="rtl"><bdi>IEEE 802.11</bdi>: استاندارد وای‌فای برای ارتباط بی‌سیم با شبکه‌های محلی.</span>
</p>

<hr/>

<h2>بلوتوث (<bdi>Bluetooth</bdi>)</h2>

<p>
  <span dir="rtl"><bdi>IEEE 802.15</bdi>: استاندارد ارتباط بی‌سیم کوتاه‌برد (معمولاً تا ۱۰ متر) برای اتصال دستگاه‌هایی مانند هدفون، گوشی و لوازم جانبی.</span>
</p>

<hr/>

<h2>شتاب‌دهنده ویدیو (<bdi>Video Accelerators</bdi>)</h2>

<p>
  <span dir="rtl">مدارهای سخت‌افزاری موجود روی کارت گرافیک که پردازش ویدیو را سریع‌تر و روان‌تر انجام می‌دهند.</span>
</p>

<hr/>

<h2>کارت صدا (<bdi>Audio Cards</bdi>)</h2>

<p>
  <span dir="rtl">سخت‌افزاری ویژه برای پردازش و پخش صدای باکیفیت و کاهش نویز در سیستم.</span>
</p>

</div>


---



## مقایسه SSD و HDD  
<div dir="rtl" align="right">

<p>
  <span dir="rtl">هر دو حافظه‌های ذخیره‌سازی اطلاعات هستند، اما تفاوت‌های اساسی در ساختار، سرعت، قیمت و کاربرد دارند. این دو به طور همزمان در یک سیستم کامپیوتری استفاده می‌شوند؛ <bdi>SSD</bdi> برای افزایش سرعت سیستم‌عامل و نرم‌افزارها و <bdi>HDD</bdi> برای ذخیره‌سازی حجم بالای داده‌ها با هزینه کمتر.</span>
</p>

<h2>تفاوت‌های اصلی <bdi>SSD</bdi> و <bdi>HDD</bdi></h2>

<h3>ساختار</h3>
<p>
  <span dir="rtl"><bdi>HDD</bdi> (<bdi>Hard Disk Drive</bdi>): از دیسک‌های چرخان و هد برای خواندن و نوشتن اطلاعات استفاده می‌کند و دارای قطعات متحرک است.</span>
</p>

<p>
  <span dir="rtl"><bdi>SSD</bdi> (<bdi>Solid State Drive</bdi>): از تراشه‌های حافظه فلش (مانند <bdi>NAND</bdi>) برای ذخیره‌سازی داده‌ها استفاده می‌کند و فاقد قطعات متحرک است.</span>
</p>

<h3>سرعت</h3>
<p>
  <span dir="rtl"><bdi>SSD</bdi>: بسیار سریع‌تر از <bdi>HDD</bdi> است؛ به دلیل نداشتن قطعات مکانیکی، زمان دسترسی به اطلاعات بسیار کمتر است.</span>
</p>

<p>
  <span dir="rtl"><bdi>HDD</bdi>: سرعت کمتری دارد؛ زیرا حرکت فیزیکی دیسک و هد باعث طولانی شدن زمان دسترسی به داده‌ها می‌شود.</span>
</p>

<h3>قیمت و ظرفیت</h3>
<p>
  <span dir="rtl"><bdi>HDD</bdi>: ارزان‌تر است و برای ذخیره‌سازی اطلاعات با حجم زیاد، مقرون‌به‌صرفه‌تر است.</span>
</p>

<p>
  <span dir="rtl"><bdi>SSD</bdi>: گران‌تر است اما به دلیل سرعت بالا، در سیستم‌های جدیدتر رایج شده است.</span>
</p>

<h3>کاربرد همزمان</h3>
<p>
  <span dir="rtl">می‌توانید همزمان از <bdi>SSD</bdi> و <bdi>HDD</bdi> در یک سیستم استفاده کنید. نحوه استفاده: <bdi>SSD</bdi> را برای نصب سیستم‌عامل و برنامه‌های پرکاربرد و <bdi>HDD</bdi> را برای ذخیره‌سازی فایل‌های حجیم مانند فیلم و عکس استفاده کنید.</span>
</p>

</div>

---


---

## مقایسه کارت شبکه و کارت بی‌سیم  
<span dir="rtl">- **NIC**: اتصال سیمی به شبکه از طریق پورت <bdi>RJ45</bdi>.</span>  
<span dir="rtl">- **Wireless Card**: اتصال بی‌سیم به شبکه از طریق Access Point.</span>

---

## USB  
<span dir="rtl">- **Universal Serial Bus**: رابط سریال عمومی که به اتصالات کمتری نیاز دارد.</span>

---

## GPIO  
<div dir="rtl" align="right">

<p>
  <span dir="rtl"><bdi>GPIO</bdi> مخفف "<bdi>General-purpose input/output</bdi>" و به معنی پین‌های ورودی/خروجی همه‌منظوره است. این پین‌ها رابط‌های دیجیتالی هستند که در میکروکنترلرها و دستگاه‌های الکترونیکی دیگر وجود دارند و وظیفه اصلی آن‌ها تعامل با اجزای خارجی است. رفتار این پین‌ها (ورودی یا خروجی بودن) توسط کاربر و از طریق نرم‌افزار در زمان اجرا تعیین می‌شود، که امکان کنترل یا دریافت سیگنال از قطعاتی مانند سنسورها، <bdi>LED</bdi>ها و سوئیچ‌ها را فراهم می‌آورد.</span>
</p>

<img width="600" height="491" alt="image" src="https://github.com/user-attachments/assets/86b1406d-826c-4a86-97fc-07f72b06c3a2" />


<h2>جزئیات عملکرد و کاربردها</h2>

<h3>همه‌منظوره بودن</h3>
<p>
  <span dir="rtl">این پین‌ها به صورت پیش‌فرض هدف مشخصی ندارند و می‌توان آن‌ها را برای وظایف مختلف پیکربندی کرد.</span>
</p>

<h3>پیکربندی نرم‌افزاری</h3>
<p>
  <span dir="rtl">برای استفاده از هر پین <bdi>GPIO</bdi>، لازم است تا از طریق کد و نرم‌افزار، عملکرد آن به عنوان ورودی یا خروجی تعریف شود.</span>
</p>

</div>


</div>

<br>
<div dir="rtl" align="right">
<h2>
<p>
  <span dir="rtl"> نحوه <bdi>export</bdi> کردن یک <bdi>GPIO</bdi> در لینوکس</span>
</p>
</h2>

</div>
<div dir="ltr" align="left">
<pre>
<div dir="rtl" align="right">
<p>
  <span dir="rtl">پین <bdi>GPIO</bdi> شماره 24 را <bdi>export</bdi> می‌کنیم.</span>
</p>
</div>

echo 24 > /sys/class/gpio/export
---------------------------------------------------------------------------------------------------------------------------------------------
<div dir="rtl" align="right">
<p>
  <span dir="rtl">جهت پین را روی خروجی (<bdi>out</bdi>) تنظیم می‌کنیم.</span>
</p>
</div>
echo out > /sys/class/gpio/gpio24/direction
------------------------------------------------------------------------------------------------------------------------------------------------

<div dir="rtl" align="right">
<p>
  <span dir="rtl">مقدار 1 می‌نویسیم (برای مثال روشن شدن <bdi>LED</bdi> متصل به <bdi>GPIO24</bdi>).</span>
</p>
</div>


echo 1 > /sys/class/gpio/gpio24/value
------------------------------------------------------------------------------------------------------------------------------------------------
<div dir="rtl" align="right">
<p>
  <span dir="rtl">مقدار 0 می‌نویسیم (خاموش کردن <bdi>LED</bdi>).</span>
</p>

</div>
echo 0 > /sys/class/gpio/gpio24/value
</pre>
</div>



<br>

<div dir="rtl" align="right">

## Sysfs  

<p>
  <span dir="rtl">
<bdi>Sysfs</bdi> یک فایل‌سیستم مجازی است که توسط کرنل لینوکس ارائه می‌شود و اطلاعات مربوط به زیرسیستم‌های کرنل، دستگاه‌های سخت‌افزاری و درایورهای مرتبط را به فضای کاربری منتقل می‌کند. علاوه بر نمایش اطلاعات، از فایل‌های موجود در <bdi>Sysfs</bdi> برای پیکربندی دستگاه‌ها هم استفاده می‌شود. این فایل‌سیستم در مسیر <bdi>/sys</bdi> بارگذاری (mount) می‌شود.
  </span>
</p>

</div>

<p>
  <span dir="rtl">📌 مثال:</span>
</p>

<div dir="ltr" align="left">
<pre>
jadi@funlife:~$ ls /sys
block  bus  class  dev  devices  firmware  fs  hypervisor  kernel  module  power
</pre>
</div>

<p>
  <span dir="rtl"><bdi>block</bdi>: شامل تمام دستگاه‌های بلاکی (مثل هارد)</span>
  <span dir="rtl"><bdi>bus</bdi>: شامل همه دستگاه‌های متصل (<bdi>PCI</bdi>، <bdi>USB</bdi> و …)</span>
</p>

<h2><bdi>udev</bdi></h2>

<p>
  <span dir="rtl"><bdi>udev</bdi> (مخفف <bdi>userspace /dev</bdi>) یک مدیر دستگاه برای لینوکس است. این سرویس جانشین <bdi>devfsd</bdi> و <bdi>hotplug</bdi> شده و مسئولیت‌های زیر را برعهده دارد:</span>
  <span dir="rtl">مدیریت گره‌های دستگاه در <bdi>/dev</bdi></span>
  <span dir="rtl">واکنش به رویدادهای اضافه/حذف دستگاه‌ها</span>
  <span dir="rtl">بارگذاری <bdi>firmware</bdi> در صورت نیاز</span>
</p>

<p>
  <span dir="rtl">📌 مثال: وقتی یک فلش ۱۲۸ گیگ وصل شود، سیستمی مثل <bdi>/dev/sdb2</bdi> براش ساخته می‌شه. با استفاده از قوانین <bdi>udev</bdi> می‌شه کاری کرد که همیشه با نام ثابتی مثل <bdi>/dev/mybackup</bdi> شناخته بشه یا حتی همزمان بکاپ شروع بشه.</span>
</p>

<p>
  <span dir="rtl">در نتیجه، <bdi>udev</bdi> نقش مدیر دایرکتوری <bdi>/dev</bdi> رو داره و نمایش دستگاه‌ها رو مستقل از سازنده یا مدلشون انتزاعی می‌کنه (مثلاً یک هارد همیشه <bdi>/dev/sda</bdi> یا <bdi>/dev/hd0</bdi> دیده می‌شه).</span>
</p>

<div dir="ltr" align="left">
<pre>
root@funlife:/dev# ls /dev/sda*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda5  /dev/sda6
</pre>
</div>

<h2>دستگاه‌های کاراکتری و بلاکی</h2>

<p>
  <span dir="rtl">برنامه‌ها برای خواندن یا نوشتن روی دستگاه‌ها، از فایل‌های متناظر در <bdi>/dev</bdi> استفاده می‌کنن. این فایل‌ها می‌تونن باشن:</span>
  <span dir="rtl"><bdi>Character device (c)</bdi>: انتقال داده به صورت کاراکتری (مثلاً ترمینال <bdi>tty</bdi>)</span>
  <span dir="rtl"><bdi>Block device (b)</bdi>: انتقال داده به صورت بلوک‌های داده (مثلاً هارد، <bdi>SSD</bdi>)</span>
  <span dir="rtl">📌 نشونه‌گذاری: در خروجی <bdi>ls -l</bdi>، حرف <bdi>c</bdi> یا <bdi>b</bdi> در ابتدای خط نوع دستگاه رو مشخص می‌کنه.</span>
</p>

<p>
  <span dir="rtl">📌 مثال:</span>
</p>

<div dir="ltr" align="left">
<pre>
root@ocean:~# ls -ltrh /dev/   # بخشی از خروجی
crw-rw---- 1 root tty       4,   1 Dec 15  2019 tty1
crw-rw-rw- 1 root root      1,   5 Dec 15  2019 zero
brw-rw---- 1 root disk      1,   0 Dec 15  2019 ram0
brw-rw---- 1 root disk 253,   0 Dec 15  2019 /dev/vda
</pre>
</div>


<h2><bdi>Udev VS Sysfs</bdi></h2>

<p><span dir="rtl"><bdi>Udev</bdi> و <bdi>Sysfs</bdi> هر دو مکانیزم‌هایی در لینوکس برای مدیریت دستگاه‌ها هستند اما اهداف متفاوتی دنبال می‌کنند.</span></p>

<p><span dir="rtl"><bdi>Sysfs</bdi> یک سیستم فایل مجازی است که اطلاعات هسته در مورد دستگاه‌ها و درایورهای آن‌ها را به فضای کاربر صادر می‌کند.</span></p>

<p><span dir="rtl">از سوی دیگر <bdi>Udev</bdi> یک مدیر دستگاه است که به‌صورت پویا گره‌های دستگاه را در دایرکتوری <bdi>/dev</bdi> ایجاد و حذف می‌کند و رویدادهای دستگاه را مدیریت می‌کند (و مجوزها را هم مدیریت می‌کند).</span></p>

<p><span dir="rtl">اساساً <bdi>Sysfs</bdi> داده‌ها را فراهم می‌کند و <bdi>Udev</bdi> از آن داده‌ها برای مدیریت دسترسی به دستگاه از طریق <bdi>/dev</bdi> استفاده می‌کند.</span></p>




</div>


<div dir="rtl" align="right">

<h2><bdi>دایرکتوری /proc</bdi></h2>

<div dir="rtl" align="right">
<p>
  <span dir="rtl"> جایی است که کرنل تنظیمات و ویژگی‌های خود را نگه می‌دارد.
این دایرکتوری روی رم ایجاد می‌شود و فایل‌ها ممکن است دسترسی نوشتن داشته باشند (مثلاً برای برخی پیکربندی‌های سخت‌افزاری).می‌توانید مواردی مانند موارد زیر را پیدا کنید:</</span
</p>
</div>

<ul>
  <li><span dir="rtl">IRQها (درخواست‌های وقفه)</span></li>
  <li><span dir="rtl">پورت‌های ورودی/خروجی (مکان‌هایی در حافظه که <bdi>CPU</bdi> می‌تواند با دستگاه‌ها ارتباط برقرار کند)</span></li>
  <li><span dir="rtl"><bdi>DMA</bdi> (دسترسی مستقیم به حافظه، سریع‌تر از پورت‌های ورودی/خروجی): روشی سخت‌افزاری که به دستگاه‌های جانبی اجازه می‌دهد بدون نیاز به پردازنده مرکزی (<bdi>CPU</bdi>) داده‌ها را مستقیماً بین حافظه و خود جابجا کنند.</span></li>
  <li><span dir="rtl">پردازش‌ها</span></li>
  <li><span dir="rtl">تنظیمات شبکه</span></li>
  <li><span dir="rtl"> .. </span></li>
</ul>
<br>

<div  dir="ltr" align="left">
<pre>
$ ls /proc/
1      1249   1451   1565   18069  20346  2426  2765
10     13     146    157    18093  20681  2452  2766
1039   1321   147    1572   18243  21     2456  28
10899  13346  148    1576   18274  21021  2462  2841
</pre>
</div>
<p>
  <span dir="rtl">اعداد، شناسه‌های فرآیند هستند! فایل‌های دیگری مانند <bdi>cpuinfo</bdi>، <bdi>mounts</bdi>، <bdi>meminfo</bdi> و ... نیز وجود دارند.</span>
</p>

<p>
  <span dir="rtl"><bdi>/proc</bdi> مربوط به حافظه و اطلاعات کرنل درباره دستگاه‌ها و سخت‌افزارهاست و در عمل در آن نمی‌شود تغییراتی روی سخت‌افزارها انجام داد.</span>
  <span dir="rtl">اگر واقعاً بخواهیم تغییراتی صورت دهیم این تغییرات در <bdi>/etc/</bdi> صورت می‌پذیرد.</span>
</p>

<p>
  <span dir="rtl">یک مثال دیگر، تغییر حداکثر تعداد فایل‌های باز برای هر کاربر است:</span>
</p>
<div dir="ltr" align="left">
<pre>
root@funlife:/proc/sys/fs# cat file-max
797946
root@funlife:/proc/sys/fs# echo 1000000 > file-max
root@funlife:/proc/sys/fs# cat file-max
1000000
</pre>
</div>
<p>
  <span dir="rtl">یکی دیگر از دایرکتوری‌های بسیار مفید در اینجا، <bdi>/proc/sys/net/ipv4</bdi> است که پیکربندی‌های شبکه در لحظه (بلادرنگ) را کنترل می‌کند.</span>
</p>

<p>
  <span dir="rtl"> همه این تغییرات پس از بوت شدن به حالت اولیه برمی‌گردند. برای دائمی کردن این تغییرات، باید در فایل‌های پیکربندی موجود در<bdi>/etc/</bdi>بنویسید.</span>
 
</p>

</div>

<div dir="rtl" align="right">
<h2><bdi>D-Bus</bdi></h2>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    <bdi>D-Bus</bdi> یک سامانه‌ی <bdi>message bus</bdi> در لینوکس و سیستم‌های مشابه است که امکان برقراری ارتباط ساده و استاندارد بین برنامه‌ها (<bdi>Inter-Process Communication</bdi>) را فراهم می‌کند. این مکانیزم علاوه بر انتقال پیام، نقش مهمی در هماهنگی چرخه‌ی اجرای پردازه‌ها دارد؛ مثلاً کمک می‌کند تنها یک نمونه از یک برنامه یا سرویس اجرا شود و در صورت نیاز، برنامه‌ها یا سرویس‌های موردنیاز به‌صورت خودکار راه‌اندازی شوند. به این ترتیب، <bdi>D-Bus</bdi> توسعه‌دهندگان را قادر می‌سازد بدون پیچیدگی زیاد، ارتباط پایدار و مدیریت‌شده‌ای بین اپلیکیشن‌ها و سرویس‌های سیستم برقرار کنند.
  </span>
</p>
</div>

<br>

<div dir="rtl" align="right">
<h2> دستورات بررسی سخت‌افزار </h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lsusb</bdi>, <bdi>lspci</bdi>, <bdi>lsblk</bdi>, <bdi>lshw</bdi> درست مثل <bdi>ls</bdi> اما برای <bdi>pci</bdi>، <bdi>usb</bdi>، ...</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lspci</bdi>: دستگاه‌های <bdi>PCI</bdi> متصل به کامپیوتر را نشان می‌دهد.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lsusb</bdi>: تمام دستگاه‌های <bdi>USB</bdi> متصل به سیستم را نشان می‌دهد.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lshw</bdi>: سخت‌افزار را نشان می‌دهد. برای دریافت لیست کامل، ممکن است به وضعیت <bdi>root</bdi> نیاز باشد. آن را امتحان کنید!</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lsblk</bdi>: برای لیستی از دستگاه‌ها که می‌توانند از بلوک‌های داده بخوانند یا بنویسند، استفاده می‌شود.</span>
</p>
</div>

<div dir="rtl" align="right">
<h2> ماژول‌های قابل بارگذاری کرنل (<bdi>Loadable Kernel Modules</bdi>) </h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">لینوکس، مثل هر سیستم‌عامل دیگری، برای کار کردن با سخت‌افزار به درایورها نیاز دارد. در سیستم‌عامل مایکروسافت ویندوز، معمولاً باید این درایورها را جداگانه نصب کنید، اما در لینوکس بیشتر درایورها به‌طور پیش‌فرض در سیستم موجود هستند.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">بااین‌حال، برای جلوگیری از این‌که کرنل همه‌ی آن‌ها را هم‌زمان بارگذاری کند (که باعث افزایش حجم و سنگین شدن کرنل می‌شود)، لینوکس از ماژول‌های کرنل استفاده می‌کند.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">ماژول‌های قابل بارگذاری کرنل (با پسوند ‎<bdi>.ko</bdi>‎) در واقع فایل‌های شیء (<bdi>object files</bdi>) هستند که برای گسترش قابلیت‌های کرنل یک توزیع لینوکس به‌کار می‌روند. این ماژول‌ها بیشتر برای پشتیبانی از سخت‌افزارهای جدید به‌کار می‌روند؛ مثل کارت‌های توسعه‌ی <bdi>IoT</bdi>، که هنوز به‌طور پیش‌فرض در توزیع لینوکس موجود نیستند.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">شما می‌توانید ماژول‌ها را با استفاده از <bdi>lsmod</bdi> بررسی کنید یا آنها را از طریق دستورات <bdi>modprobe</bdi> مدیریت کنید.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>lsmod</bdi>: ماژول‌های هسته را نشان می‌دهد. آنها در <bdi>/lib/modules</bdi> قرار دارند.</span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
root@funlife:/dev# lsmod
Module                  Size  Used by
pci_stub               12622  1
vboxpci                23256  0
vboxnetadp             25670  0
vboxnetflt             27605  0
vboxdrv               418013  3 vboxnetadp,vboxnetflt,vboxpci
ctr                    13049  3
ccm                    17731  3
dm_crypt               23172  1
bnep                   19543  2
rfcomm                 69509  8
uvcvideo               81065  0
arc4                   12608  2
videobuf2_vmalloc      13216  1 uvcvideo
intel_rapl             18783  0
iwldvm                236430  0
x86_pkg_temp_thermal    14205  0 
</pre>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">برای کسب اطلاعات بیشتر در مورد یک ماژول، از <bdi>modinfo</bdi> استفاده کنید.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">اگر نیاز به اضافه کردن یک ماژول به هسته خود دارید (مثلاً یک درایور جدید برای سخت‌افزار) یا حذف آن (یک درایور را حذف نصب کنید)، می‌توانید از <bdi>rmmod</bdi> و <bdi>modprobe</bdi> استفاده کنید.</span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
# rmmod iwlwifi
</pre>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">و این هم برای نصب ماژول‌ها:</span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
# insmod kernel/drivers/net/wireless/iwlwifi.ko
</pre>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">اما هیچ‌کس از <bdi>insmod</bdi> استفاده نمی‌کند زیرا وابستگی‌ها را درک نمی‌کند و شما باید کل مسیر فایل ماژول را به آن بدهید. در عوض، از دستور <bdi>modprobe</bdi> استفاده کنید:</span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
# modprobe iwlwifi
</pre>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">شما می‌توانید از سوئیچ <bdi>-f</bdi> برای حذف اجباری ماژول <bdi>rmmod</bdi> استفاده کنید، حتی اگر در حال استفاده باشد.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">اگر لازم است هر بار که سیستم شما بوت می‌شود، برخی ماژول‌ها بارگذاری شوند، یکی از موارد زیر را انجام دهید:</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">نام آنها را به این فایل اضافه کنید <bdi>/etc/modules</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">فایل‌های پیکربندی آنها را به <bdi>/etc/modprobe.d/</bdi> اضافه کنید.</span>
</p>
</div>







