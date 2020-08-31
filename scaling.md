<h1 dir = 'rtl'>  آشنایی با مقیاس دهنده های مختلف</h1>
<h3 dir ='rtl'> 
MinMax Scaler:
</h3>
<p dir = rtl>
میاد همه اعداد رو از مینیمم کم میکنه و به بازه اعداد (ماکزیمم - مینیمم) تقسیم میکنه. شکل توزیع داده ها رو حفظ میکنه و توانایی رفع داده های پرت رو نداره.
</p>

<h3 dir ='rtl'> 
Robust Scaler:
</h3>
<p dir = rtl>
این میاد بجای مینیم و ماکزیمم داده ها، از Q1 , Q3 استفاده میکنه و همین باعث میشه در مقابل داده های پرت مقاوم باشه. میاد از تک تک داده ها Q1 رو کم میکنه و به Q3-Q1 تقسیم میکنه.
</p>

<h3 dir ='rtl'> 
Standard Scaler:
</h3>
<p dir = rtl>
این مقیاس دهنده برای مواقعی که توزیع داده ها بصورت نرمال میباشد مناسبه، وگرنه بهتره از مقیاس دهنده های دیگه استفاده کنیم.<br>
میاد میانگین رو از داده ها کم میکنه و به انحراف استاندارد تقسیم میکنه. در واقع هدفش اینه که توزیع داده ها رو تبدیل کنه به میانگین صفر و انحراف استاندارد 1 . 
</p>

<h3 dir ='rtl'> 
Normalizer:
</h3>
<p dir = rtl>
برخلاف چندتای بالایی که میاد روی ویژگی ها مقیاس دهی رو انجام میده، این میاد روی هر نمونه داده مقیاس دهی انجام میده. در واقع میاد هر ویژگی از یک داده رو تقسیم میکنه به نرم اون داده:<br>
</p>
norm = sqrt(x₁² + y₁² +z₁² )

x₁ₙₑw = x₁ / norm 

<h3 dir ='rtl'> 
Power Transformers:
</h3>
<p dir = rtl>
برای مواقعی که داده ها از توزیع نرمال پیروی نمیکنن، از این تبدیلات میتونیم استفاده کنیم تا داده ها تبدیل به نرمال بشن.از boxcox زمانی اسفتاده میکنیم که داده ها همگی مثبت باشن. بعضی جاها بهتره که اول داده ها رو مقیاس/استاندارد کرد بعدش این تبدیلات رو انجام داد.
</p>

<h3 dir ='rtl'> 
Quantile Transformers:
</h3>
<p dir = rtl>
این هم مثل تبدیل قبلی هست. بنظر میاد باید روی داده ها تبدیلات مختلف رو امتحان کرد و دقت رو چک کرد با هر کرد.
</p>


[source](https://benalexkeen.com/feature-scaling-with-scikit-learn/)
