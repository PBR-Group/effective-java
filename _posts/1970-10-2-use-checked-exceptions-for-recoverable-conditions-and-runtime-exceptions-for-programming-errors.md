---
layout: post
title: از Checked Exception ها برای شرایط قابل اصلاح و از خطاهای زمان اجرا برای خطاهای برنامه نویسی استفاده کنید
chapter: آیتم 70
author: پانیذ علیپور
---

کلا داستان خطاها در جاوا به این شکل هست که تمام کلاس های خطا در جاوا از کلاس Throwable مشتق میشن.

کلاس ها هم به دو دسته Exception و Error تقسیم میشوند که Error جزو اون دسته از خطاهاست که در زمان اجرای برنامه رخ میده و منجر به توقف اجرای برنامه میشوند . این خطاها وقتی اتفاق میفتن تنها کاری که از دستمون برمیاد نمایش یه خطای مناسب هست .

در مقابل ، Exception ها خطاهایی هستن که قابل کنترل شدن هستن و باید تو برنامه مدیریتشون کرد .در واقع Exceptionها وضعیت ناخواسته ای هستند که در حین اجرای برنامه ممکنه اتفاق بیفتند اما قابل پیش بینی هم هستند و به همین علت می بایست شناسایی و کنترل بشوند .

Exception ها هم دو دسته هستند. RuntimeException ها و non-Runtime Exception ها که به نام Contigency Exception یا User Exception  شناخته می شوند.

اما تو کتاب توضیح میده که زیر گروه non-Runtime Exception ها همون خطاهای checked Exception هستن که همونطور که گفتم باید توشرایطی ازشون استفاده کرد که تو برنامه قابل پیش بینی هستن اما ممکنه اتفاق بیفتن

و اما خطاهای unchecked که در واقع همون خطاهای Runtime Exception و Error ها هستند.

این دو مشابه هستند ، نیاز به بلوک try-catch ندارند و باید برنامه را طوری طراحی کرد که بتونیم بگیم با اطمینان خطایی رخ نمیدهد.

یه سری از خطاهای Runtime به این شکل هستن :

<div dir="ltr" >
- ClassCastException
</div>
<div dir="ltr" >
-ArrayOutOfBoundException
</div>
<div dir="ltr" >
-NullPointerException
</div>
و...

یه نکته ای که مطرح میکنه اینه که میگه برای تشخیص checked Exception از Unchecked Exception باید ببینین اون خطایی که ایجاد شده قابل رفع و ادامه دادن برنامه هست یا نه اگه بود Checked exception هست وگرنه Unchecked Exception.
اما یه کم یه جاهایی تشخیصش سخت میشه که تو این موارد بستگی به تشخیص طراح داره که تصمیم بگیره تو کدوم دسته قرار بگیره.

مثال میزنه

تو مورد کمبود منابع که به دلایل متفاوتی میتونه اتفاق بیفته مثلا تخصیص غیر منطقی یه آرایه بزرگ یا مشکل کمبود واقعی منابع که اینجا این تصمیم توسط طراح باید گرفته بشه که این ها میتونن مرتفع بشن و برنامه ادامه کار بده یا باید متوقف بشه و رفتاری که باهاش میشه مشابه unchecked Exception باشه.

یه نکته دیگه میگه خطاهای نوع Unchecked exception می بایست از Runtime exception مشتق بشن و نباید از کلاس Error ارث بری کنن و حتی نباید خطاهای از نوع Error رو هم throw کنین که این به استثنای  AssertionError هست.

و نکته آخر هم این که موقع استفاده از Checked Exception ها حواسمون باشه متدهایی تعریف کنیم که اطلاعات لازمه و مفید رو به کاربر در زمان رخداد خطاها ارائه بده تا بدونه منشا خطا و نحوه مرتفع کردنش باید به چه شکلی باشه.

