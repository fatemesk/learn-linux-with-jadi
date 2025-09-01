# learn-linux-with-jadi
Personal Linux learning notes based on Jadi’s course

<div dir="rtl" align="right">

<span dir="rtl"><h1><bdi>101.2</bdi>  بوت کردن سیستم   </h1></span>  
<br>
<div dir="rtl" align="right">
<h2> فرآیند بوت </h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">درک این مرحله اهمیت زیادی دارد، زیرا در این زمان کنترل بسیار کمی بر سیستم دارید و نمی‌توانید دستورات زیادی برای عیب‌یابی صادر کنید. بنابراین باید به‌خوبی بدانید که چه اتفاقی در حال رخ دادن است.</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">1. <bdi>Firmware</bdi> مادربورد یک تست خودکار روشن شدن (<bdi>PowerOnSelfTest</bdi> یا <bdi>POST</bdi>) انجام می‌دهد</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">2. مادربورد بوت‌لودر را بارگذاری می‌کند</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">3. بوت‌لودر کرنل <bdi>Linux</bdi> را بر اساس تنظیمات و دستورات خود بارگذاری می‌کند</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">4. کرنل سیستم را بارگذاری و آماده می‌کند (از جمله فایل‌سیستم روت) و برنامه‌ی راه‌اندازی (<bdi>init</bdi>) را اجرا می‌کند</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">5. برنامه‌ی <bdi>Init</bdi> سرویس‌ها را راه‌اندازی می‌کند؛ مثل وب‌سرور، رابط گرافیکی، شبکه و غیره</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">همان‌طور که در بخش قبل (101.1) بحث شد، <bdi>Firmware</bdi> روی مادربورد می‌تواند <bdi>BIOS</bdi> یا <bdi>UEFI</bdi> باشد.</span>
</p>
</div>

<div dir="rtl" align="right">
<h2> BIOS </h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>Basic Input Output System</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>قدیمی‌تر</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- محدود به یک سکتور از دیسک است و نیاز به بوت‌لودر چندمرحله‌ای دارد</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- می‌تواند بوت‌لودر را از <bdi>HDD</bdi> داخلی/خارجی، <bdi>CD/DVD</bdi>، <bdi>USB Flash drive</bdi> یا سرور شبکه اجرا کند</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- اگر بوت از <bdi>HDD</bdi> باشد، از <bdi>Master Boot Record</bdi> استفاده می‌شود (یک سکتور)</span>
</p>
</div>


<br>

<div dir="rtl" align="right">
<h2> UEFI </h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>Unified Extensible Firmware Interface</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl"><bdi>مدرن و شیک</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- یک پارتیشن مخصوص برای بوت‌لودر مشخص می‌کند؛ به آن <bdi>EFI System Partition</bdi> (<bdi>ESP</bdi>) گفته می‌شود</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- <bdi>ESP</bdi> از نوع <bdi>FAT</bdi> است، روی <bdi>/boot/efi</bdi> مونت شده و فایل‌های بوت‌لودر پسوند <bdi>.efi</bdi> دارند</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- می‌توانید با بررسی مسیر <bdi>/sys/firmware/efi</bdi> ببینید که سیستم شما <bdi>UEFI</bdi> است یا نه</span>
</p>
</div>



<div dir="rtl" align="right">
<h2>بوت‌لودر</h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
بوت‌لودر حداقل سخت‌افزار مورد نیاز برای بوت سیستم را مقداردهی اولیه می‌کند. سپس سیستم‌عامل را پیدا کرده و اجرا می‌کند. از نظر فنی می‌توانید <bdi>UEFI</bdi> خود را برای اجرای هر چیزی که می‌خواهید تنظیم کنید، اما معمولاً در سیستم‌های <bdi>GNU/Linux</bdi> از <bdi>GRUB</bdi> استفاده می‌کنیم. <bdi>GRUB</bdi> می‌تواند برای اجرای هر برنامه خاصی که نیاز دارید استفاده شود، اما به طور کلی سیستم‌عامل را اجرا می‌کند.
</span>
</p>
</div>

<div dir="rtl" align="right">
<h2>کرنل</h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
کرنل، هستهٔ اصلی سیستم‌عامل شماست. اساساً خود <bdi>LINUX</bdi> است. بوت‌لودر کرنل را در حافظه بارگذاری کرده و اجرا می‌کند. اما کرنل برای شروع به برخی اطلاعات اولیه نیاز دارد؛ چیزهایی مانند درایورهایی که برای کار با سخت‌افزار ضروری هستند. این درایورها در <bdi>initrd</bdi> یا <bdi>initramfs</bdi> در کنار کرنل ذخیره می‌شوند و در طول بوت استفاده می‌شوند. همچنین می‌توانید در طول بوت با استفاده از پیکربندی‌های <bdi>Grub</bdi>، پارامترهایی به کرنل ارسال کنید. به عنوان مثال، ارسال ۱ یا <bdi>S</bdi> باعث می‌شود سیستم در حالت تک‌کاربره (بازیابی) بوت شود. یا می‌توانید با ارسال <bdi>vga=792</bdi> به کرنل در هنگام بوت، گرافیک خود را مجبور کنید در حالت 1024×768x24 کار کند.
</span>
</p>
</div>

<div dir="rtl" align="right">
<h2>dmesg</h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
در طول بوت، <bdi>Linux</bdi> لاگ‌های فرایند بوت را نمایش می‌دهد. بعضی از سیستم‌های دسکتاپ این را پشت یک صفحهٔ گرافیکی مخفی می‌کنند که می‌توانید با کلید <bdi>Esc</bdi> یا ترکیب <bdi>Ctrl+Alt+F1</bdi> آن را ببینید. به دلایل مختلفی که خارج از محدودهٔ این دوره است، کرنل لاگ‌های خود را در "Kernel Ring Buffer" ذخیره می‌کند. پس از تکمیل فرایند بوت، <bdi>syslog daemon</bdi> لاگ‌ها را جمع‌آوری کرده و در <bdi>/var/log/dmesg</bdi> ذخیره می‌کند. برای مشاهدهٔ تمام لاگ‌ها، از جمله آنچه پس از بوت ثبت شده، از دستور <bdi>dmesg</bdi> استفاده می‌کنیم. همچنین می‌توان از <bdi>journalctl -k</bdi> برای مشاهدهٔ لاگ‌های کرنل یا <bdi>journalctl -b</bdi> برای لاگ‌های بوت استفاده کرد (یا حتی <bdi>journalctl -u kernel</bdi> برای مشاهدهٔ تمام لاگ‌های قبلی).
</span>
</p>
</div>

<div dir="rtl" align="right">
<h2>/var/log/messages</h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
بعد از شروع فرایند <bdi>init</bdi>، <bdi>syslog daemon</bdi> پیام‌ها را ثبت می‌کند. این پیام‌ها شامل زمان‌بندی هستند و در طول راه‌اندازی مجدد سیستم حفظ می‌شوند. کرنل همچنان پیام‌های خود را در Kernel Buffer Ring ثبت می‌کند. در بعضی سیستم‌ها ممکن است این فایل <bdi>/var/log/syslog</bdi> نامیده شود و فایل‌های لاگ دیگر نیز در <bdi>/var/log</bdi> وجود دارند.
</span>
</p>
</div>

<div dir="rtl" align="right">
<h2>init</h2>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
وقتی مقداردهی اولیهٔ کرنل تمام شد، نوبت به اجرای برنامه‌های دیگر می‌رسد. برای این کار، کرنل فرایند <bdi>Initialization Daemon</bdi> را اجرا می‌کند که مسئول راه‌اندازی دیگر دیمون‌ها، سرویس‌ها، زیرسیستم‌ها و برنامه‌هاست. با استفاده از سیستم <bdi>init</bdi> می‌توان گفت: "من سرویس A را نیاز دارم و سپس سرویس B. بعد سرویس‌های C و D و E را نیاز دارم اما D را اجرا نکن مگر اینکه A و B در حال اجرا باشند." مدیر سیستم می‌تواند از سیستم <bdi>init</bdi> برای توقف و راه‌اندازی سرویس‌ها بعداً استفاده کند.
</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">
سیستم‌های مختلف <bdi>init</bdi> وجود دارند:  

</span>
</p>
</div>

<div dir="rtl" align="right">
<ul>
  <li>
    <span dir="rtl">
      <bdi><b>SysVinit</b></bdi> بر اساس <bdi>Unix System V</bdi> است. دیگر زیاد استفاده نمی‌شود اما مردم آن را دوست داشتند زیرا فلسفه‌های یونیکس را دنبال می‌کرد. ممکن است آن را روی ماشین‌های قدیمی یا حتی سیستم‌های تازه نصب شده ببینید.
    </span>
  </li>
  <li>
    <span dir="rtl">
      <bdi><b>upstart</b></bdi> جایگزینی مبتنی بر رویداد برای دیمون سنتی <bdi>init</bdi> بود که توسط <bdi>Canonical</bdi> (توسعه‌دهندگان <bdi>Ubuntu</bdi>) ساخته شد. هدف پروژه ساخت جایگزینی برای <bdi>SysVinit</bdi> هنگام انتشار آن در سال ۲۰۰۷ بود. نهایتاً پروژه به دلیل پذیرش گستردهٔ <bdi>Systemd</bdi> متوقف شد. حتی این روزها <bdi>Ubuntu</bdi> از <bdi>Systemd</bdi> استفاده می‌کند، اما upstart هنوز در <bdi>ChromeOS</bdi> گوگل یافت می‌شود.
    </span>
  </li>
  <li>
    <span dir="rtl">
      <bdi><b>Systemd</b></bdi> جایگزین جدید است. این سیستم توسط بعضی علاقه‌مندان به لینوکس به دلیل نادیده گرفتن اصول یونیکس مورد انتقاد است، اما به طور گسترده توسط توزیع‌های اصلی پذیرفته شده است. می‌تواند سرویس‌ها را به صورت موازی اجرا کرده و امکانات پیشرفتهٔ زیادی ارائه دهد.
    </span>
  </li>
</ul>
</div>





<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    فرآیند <bdi>init</bdi> شناسه‌ای معادل ۱ دارد و می‌توانید آن را با اجرای دستورات زیر پیدا کنید:
  </span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
# which init
/sbin/init
# readlink -f /sbin/init
/usr/lib/systemd/systemd
# ps -p 1
PID TTY TIME     CMD
1   ?   00:00:06 systemd
</pre>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    شما می‌توانید سلسله مراتب فرآیندها را با استفاده از دستور <bdi>pstree</bdi> مشاهده کنید:
  </span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
pstree
systemd
</pre>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    <bdi>Systemd</bdi> جدید است، هم دوست داشته می‌شود و هم مورد انتقاد قرار می‌گیرد. ایده‌های زیادی دارد اما برخی اصول محبوب <bdi>UNIX</bdi> را دنبال نمی‌کند (مثلاً لاگ‌ها را در فایل متنی ذخیره نمی‌کند یا هنگام اجرای دستورات بدون <bdi>sudo</bdi> درخواست رمز <bdi>root</bdi> می‌کند). این سیستم به شما اجازه می‌دهد سرویس‌ها را در صورت اتصال سخت‌افزار، در بازه‌های زمانی مشخص یا پس از شروع سرویس دیگر اجرا کنید.
  </span>
</p>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    <bdi>Systemd</bdi> حول مفهومی به نام <bdi>unit</bdi> ساخته شده است. یک <bdi>unit</bdi> می‌تواند سرویس، گروهی از سرویس‌ها یا یک عمل باشد. هر <bdi>unit</bdi> دارای نام، نوع و فایل پیکربندی است. ۱۲ نوع <bdi>unit</bdi> وجود دارد: <bdi>automount</bdi>، <bdi>device</bdi>، <bdi>mount</bdi>، <bdi>path</bdi>، <bdi>scope</bdi>، <bdi>service</bdi>، <bdi>slice</bdi>، <bdi>snapshot</bdi>، <bdi>socket</bdi>، <bdi>swap</bdi>، <bdi>target</bdi> و <bdi>timer</bdi>.
  </span>
</p>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    ما از <bdi>systemctl</bdi> برای مدیریت این <bdi>unit</bdi>ها و از <bdi>journalctl</bdi> برای مشاهده لاگ‌ها استفاده می‌کنیم.
  </span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
# systemctl list-units
# systemctl list-units --type=target
# systemctl get-default
# systemctl list-unit-files
# systemctl cat ntpd.service
# systemctl cat graphical.target
# systemctl stop sshd
# systemctl start sshd
# systemctl status sshd
# systemctl is-active sshd
# systemctl is-failed sshd
# systemctl restart sshd
# systemctl reload sshd
# systemctl daemon-reload sshd
# systemctl enable sshd
# systemctl disable sshd
# systemctl is-system-running
# systemctl --failed
# journalctl
# journalctl --no-pager
# journalctl -n 10
# journalctl -S -1d
# journalctl -xe
# journalctl -u ntp
# journalctl _PID=1234
</pre>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    <bdi>SysV</bdi> سیستم <bdi>init</bdi> قدیمی‌تر است و هنوز روی بسیاری از سیستم‌ها قابل استفاده است. فایل‌های کنترل آن در <bdi>/etc/init.d/</bdi> قرار دارند و بیشتر شبیه اسکریپت‌های <bdi>bash</bdi> هستند. در بسیاری از موارد می‌توانید مانند نمونه‌های زیر آن‌ها را اجرا کنید:
  </span>
</p>
</div>

<div dir="ltr" align="left">
<pre>
/etc/init.d/ntpd status
/etc/init.d/ntpd stop
/etc/init.d/ntpd start
/etc/init.d/ntpd restart
</pre>
</div>

<div dir="rtl" align="right">
<p>
  <span dir="rtl">
    درباره <bdi>runlevels</bdi> در بخش ۱۰۱.۳ بیشتر صحبت خواهیم کرد.
  </span>
</p>
</div>




