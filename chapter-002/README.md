<div dir="rtl" align="right">

<h1>فصل دوم: بوت سیستم (<bdi>101.2 Boot the System</bdi>)</h1>

<p>
  <span dir="rtl">
    در این فصل روند بوت شدن لینوکس را مرور می‌کنیم: از فریمور مادربرد (<bdi>BIOS/UEFI</bdi>) و <bdi>POST</bdi> تا بارگذاری <bdi>Bootloader</bdi>، اجرای کرنل، آماده‌سازی فایل‌سیستم ریشه و شروع سرویس‌ها توسط <bdi>init</bdi>.
  </span>
</p>

<h2>مراحل بوت</h2>
<p>
  <span dir="rtl">
    1) فریمور مادربرد تست اولیهٔ <bdi>POST</bdi> را انجام می‌دهد.  
    2) بوت‌لودر (<bdi>Bootloader</bdi>) بارگذاری می‌شود.  
    3) بوت‌لودر، کرنل لینوکس را بر اساس تنظیماتش لود می‌کند.  
    4) کرنل سیستم را آماده کرده (مانت فایل‌سیستم ریشه) و برنامهٔ <bdi>init</bdi> را اجرا می‌کند.  
    5) برنامهٔ <bdi>init</bdi> سرویس‌هایی مانند شبکه، محیط گرافیکی و وب‌سرور را راه‌اندازی می‌کند.  
  </span>
</p>

<h2><bdi>BIOS</bdi> در برابر <bdi>UEFI</bdi></h2>
<p>
  <span dir="rtl">
    <bdi>BIOS</bdi> نسل قدیمی فریمور با محدودیت <bdi>MBR</bdi> و سکتور اول است؛ <bdi>UEFI</bdi> مدرن‌تر است، با پارتیشن <bdi>ESP</bdi> (مونت روی <bdi>/boot/efi</bdi>) و فایل‌های <bdi>.efi</bdi>. برای تشخیص <bdi>UEFI</bdi> می‌توانید مسیر <bdi>/sys/firmware/efi</bdi> را چک کنید.
  </span>
</p>

<h2>نکات تکمیلی</h2>
<p>
  <span dir="rtl">
    - <bdi>UEFI</bdi> از دیسک‌های بزرگ‌تر و پارتیشن‌بندی <bdi>GPT</bdi> پشتیبانی می‌کند و قابلیت‌هایی مثل <bdi>Secure Boot</bdi> دارد.  
    - در هر پوشهٔ این فصل، خروجی‌های ترمینال را جداگانه با قالب چپ‌چین قرار دهید.
  </span>
</p>

<!-- نمونهٔ بخش ترمینال -->
<h2>نمونهٔ ترمینال</h2>
</div>
<div dir="ltr" align="left">
<pre>
# بررسی وجود مسیر EFI (سیستم‌های UEFI)
ls /sys/firmware/efi
</pre>
</div>
<div dir="rtl" align="right">

</div>
