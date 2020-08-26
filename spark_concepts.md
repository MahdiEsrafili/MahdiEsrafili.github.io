<h1 dir= 'rtl'> Apache Spark </h1>
<h2 dir = 'rtl'> Session, Context</h2>
<p dir = 'rtl'>
این دو تا نقطه ورود هر اپلیکیشن اسپارک هستن. یعنی باید قبل از هر کاری، اینا رو صدا زد و آبجکت ازشون تولید کرد. Session جدیدتره و بقیه چیزا رو هم شامل میشه. این رو از کلاس sql صدا میزنیم. ولی Context رو از خود اسپارک میتونیم صدا بزنیم.<br>
با استفاده از context  ایجاد شده میتونیم هر آبجکتی رو به RDD تبدیل کنیم.مثلا یه آرایه داریم، با استفاده از parallelize میتونیم اونو به یه rdd تبدیل کنیم:<br>
</p>

```python
sc = SparkContext('local', 'app_name')
arr = [1,2,3,4,5]
rdd_arr = sc.parallelize(arr)
```
<h2 dir = 'rtl'> map, reduce, flatMap, reduceByKey</h2>
<p dir = 'rtl'> 
map, reduce از توابع خود پایتون هستن. از map استفاده میکنیم برای اعمال یه تابعی روی یه لیست و از reduce استفاده میکنیم برای اعمال یه تابع بصورت متوالی. مثلا:
</p>

```python
from functools import reduce
arr = [1,2,3,4,5]
arr_transed = list(map(lambda x: x**2, arr))
'output' : [1,4,9,16,25]
arr_transed = reduce(lambda x,y:x+y, arr)
'output': 1+2+3+4+5=15
```

<p dir = 'rtl'>
این دو تا تابع توی اسپارک هم همین کاربرد رو دارن. حالا این flatMap تفاوتش اینه که لیست خروجی رو یک بعدی میکنه:
</p>

```python
arr = [[1,2],[3,4]] # its a RDD
arr.flatMap(lambda x: x[0]+x[1])
'output' : [3,7]
```
<p dir = 'rtl'>
reduceByKey هم میاد عنصر اول یه تاپل رو به عنوان کلید در نظر میگیره و عمل reduce رو روی عنصر دوم انجام میده. مثلا:
</p>

```python
arr = ['ali', 'ali','mahdi','ali','mahdi']
arr.map(lambda x: (x,1)).reduceByKey(lambda x,y:x+y)

#output:
[('ali',1), ('ali',1), ('mahdi',1), ('ali',1), ('mahdi',1)] =>
[('ali',3), ('mahdi',2)]
```