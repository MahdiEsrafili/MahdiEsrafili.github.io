<h1 dir='rtl'>
مفاهیم در پردازش زبان طبیعی
</h1>
<h2 dir='rtl'>
1.N-Grams:
</h2>
<p dir='rtl'>
منظور توکنایز کردن جمله با پنجره به اندازه n هست.برای مثال:
 </p>
 <pre> <code>
"ali is a good boy" <br>
N=1 => ['ali', 'is', 'a', 'good','boy'] <br>
N=2 => ['ali is', 'is a', 'a good', 'good boy']
    </code></pre>
 <p dir = 'rtl'>
 از این برای استخراج ویژگی، اصلاح خطای املایی استفاده میشه
</p>

<h2 dir='rtl'>
 2.Lemmatize
 </h2>
 <p dir='rtl'>
این میاد کلمات رو به ریشه هاشون برمیگردونه. مثلا :
 </p>
 <pre><code>
 gone => go
 running => run
 apples => apple
 better => good
 </code></pre>
 <p dir = 'rtl'>
 این عمل رو برای اسم ها، فعل ها و صفت ها انجام میده و در توابعی که میخوایم این رو صدا بزنیم، مشخص میکنیم کدوم نوع منظورمونه
 </p>

<h2 dir = 'rtl'> 
 3.CountVectorize
 </h2>
 <p dir = 'rtl'>
 هدف اینه که تعداد تکرار کلمات و در بیاره و به یه ماتریس اغلب تنک sparse تبدیل کنه. مثلا:
 </p>
 <pre><code>
 'ali is a good boy a good student is ali'
 'ali' 'is' 'a' 'good' 'boy' 'student'
 2       2   2    2      1      1
</code> </pre>
<h2 dir = 'rtl'>
 4.word tokenize
</h2>
<p dir = 'rtl'>
 این عمل برای تبدیل متن به لیستی از کلمات است. مثلا:
 </p>
 <pre><code>
 'ali is a good boy and good student'
 ['ali','is','a','good','boy','and','good','student']
 </code></pre>
 <p dir ='rtl'>
 البته نوع sentence tokenizer هم هست که میاد متن رو به جملات میشکنه
 </p>
<h2 dir='rtl'>
 5.POS tagging 
 </h2>
 <p dir = 'rtl'> 
    pos یا Part of Speech tagging برای این استفاده می شود که نوع کلمات رو مشخص کند. در واقع میاد برای لیستی از کلمات توکنایز شده، مشخص میکنه نوع کلمه چیه.مثلا:           
 </p>
 <pre><code>
a= ['ali', 'go', 'best']
pos_tag(a)       
[('ali', 'RB'), ('go', 'VB'), ('best', 'JJS')]                     
 </code></pre>
