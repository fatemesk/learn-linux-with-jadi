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
<span dir="rtl"><bdi>مدرن و پیشرفته</bdi></span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- یک پارتیشن مخصوص برای بوت‌لودر مشخص می‌کند؛ به آن <bdi>EFI System Partition</bdi> (<bdi>ESP</bdi>) گفته می‌شود</span>
</p>
</div>

<div dir="rtl" align="right">
<p>
<span dir="rtl">- <bdi>ESP</bdi> از نوع <bdi>FAT</bdi> است، روی <bdi>

