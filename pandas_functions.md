<h1 dir= 'rtl'> برخی توابع مهم در پانداس </h1>
[notebook link](https://github.com/MahdiEsrafili/MahdiEsrafili.github.io/blob/master/pandas_functions_notebook/pandas_functions.ipynb)
<h2 dir = 'rtl'>
تعریف دیتافریم
</h2>
<p dir = 'rtl'>
یه مدل اینه که داده های رو بصورت دیکشنری بدیم، اینطوری که کلید ها اسم ستون ها باشه و مقادیرشون، مقادیر هر ستون
</p>
<pre><code>
df = pd.DataFrame({'A': ['A0', 'A1', 'A2','A3'],
                      'B': ['D0', 'D0', 'D2','D0']},
                     index=['K0', 'K1', 'K2','K3'])
 
</code></pre>
<p dir ='rtl'>
یه مدل هم اینطوریه که داده ها رو بصورت سطر به سطر بدیم و در آخر بنویسیم اسم هر ستون چیه
</p>
<pre><code>
df = pd.DataFrame([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9],
                   [np.nan, np.nan, np.nan]],
                  columns=['A', 'B', 'C'])
</code></pre>
<h2 dir='rtl'>
merge
</h2>
<p dir='rtl'>
با پارامتر on مشخص میکنیم که کدام ستون کلید است
با how نیز مشخص میکنیم چه نوعی. مثلا inner,outer,left,right
<br>
با کلیدهای left_on , right_on میتونیم مشخص کنیم از هر طرف کدوم معیار هستن
</p>
<pre><code>
res = pd.merge(left,right,on='customerID')
</code></pre>
<p dir = 'rtl'>
اگه میخوایم دو تا دیتافریم رو بر اساس ایندکس هاشون اتصال بدیم، پارامترهای right_index, left_index رو برابر True قرار میدیم.
</p>
<h2 dir ='rtl'> join</h2>
<p dir='rtl'>  
این هم مانند merge دو دیتافریم را به همدیگه ارتباط میده. با توجه به how اون سطرهایی که در دو دیتافریم مشترک نیستن، NaN می شوند.
<br>
البته بصورت پیش فرض روی ایندکس جوین میکنه
</p>
<pre><code>
result = left.join(right,how='outer')
</code></pre>

<h2 dir='rtl'> map</h2>
<p dir ='rtl'> 
وقتی که بخوایم یه تغییری توی یه سری از ستون ها اعمال بکنیم، از این استفاده میکنیم.
</p>
<pre><code>
def gender_convert(g):
    if g=='Male':
        return 0
    elif g=='Female':
        return 1

</code></pre>
<pre><code>
data.gender = data.gender.map(gender_convert)
</code></pre>
<p dir = 'rtl'>
البته میشه اینو ساده تر هم نوشت:
</p>
<pre><code>
data.gender = data.gender.map({'Male':0,'Female':1})
</code></pre>
<p dir = 'rtl'>
البته این رو میشه با apply هم نوشت
</p>
<pre><code>
data.gender = data.gender.apply(gender_convert)
</code></pre>
<p dir = 'rtl'>
applymap هم میاد یه تابعی رو روی همه داده های موجود در دیتافریم اعمال میکنه
</p>
<h2 dir='rtl'> aggregate </h2>
<p dir = 'rtl'>
aggregate یعنی تجمیع. یعنی یه سری توابع آماری مثل مجموع، میانگین، مینیمم و ماکزیمم رو روی دیتافریم اعمال کنیم.
</p>
<pre><code>
df = pd.DataFrame([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9],
                   [np.nan, np.nan, np.nan]],
                  columns=['A', 'B', 'C'])

df.agg(['sum', 'min','std'],axis=0)
df.agg({'A' : ['sum', 'min'], 'B' : ['min', 'max']})
# axis =0 : for each column, axis=1: for each row
</code></pre>
<h2 dir='rtl'>
group by
</h2>
<p dir= 'rtl'>
همونطور که از اسمش پیداست، برای دسته بندی استفاده میشه.مثلا در دیتاستی، به اسم یه نفر چند تا تراکنش موجود هست، میایم بر اساس اسم ها دسته بندی میکنیم و میانگین مبلغ تراکنش ها رو بدست میاریم(به ازای هر نفر)
</p>
<pre><code>
df = pd.DataFrame({'name':['ali','ali','ali','mahdi'],
                   'score':[10,12,9,15],
                   'rankk':[4,3,2,1]})
df.groupby('name').max()
df.groupby('name').score.mean()                   
</code></pre>