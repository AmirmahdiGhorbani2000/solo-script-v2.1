# سولو اسکریپت v2.1.0

یک زبان برنامه‌نویسی مفسری با سینتکس منحصر‌به‌فرد، نوشته شده در C++17.

## ویژگی‌ها

- سینتکس ساده و خوانا با الهام از Rust و Python
- سیستم تایپ ایستا با ۸ نوع داده پایه
- شی‌گرایی با کلاس‌ها و اشیاء
- مدیریت فایل کامل
- توابع ریاضی گسترده
- سیستم تاریخ شمسی
- String Interpolation مشابه Rust
- خطایابی دقیق با نمایش خط و ستون

## نصب و اجرا

### پیش‌نیازها

- کامپایلر C++ با پشتیبانی از C++17
- CMake نسخه 3.10 یا بالاتر

### ساخت

```bash
mkdir build
cd build
cmake ..
make
```

### اجرا

```bash
./soloscript
```

پس از اجرا، نام فایل را وارد کنید:

```
FileName: program.solo
```

## سینتکس

### انواع داده


| نوع | توضیح | مثال |
|-----|--------|-------|
| `int` | عدد صحیح | `int x = 42` |
| `str` | رشته | `str name = "Solo"` |
| `float` | عدد اعشاری | `float pi = 3.14` |
| `bool` | مقدار منطقی | `bool flag = True` |
| `date` | تاریخ شمسی | `date today = @today` |
| `arr` | آرایه | `arr nums = {1, 2, 3}` |
| `dict` | دیکشنری | `dict d = ["a":1]` |
| `object` | نمونه کلاس | `object car = Car(80)` |

### متغیرها

```solo
int age = 25
str name = "Ali"
float pi = 3.14159
bool isActive = True
date today = @today
arr fruits = {"apple", "banana"}
dict person = ["name":"Ali";"age":25]
```

### عملگرها

#### حسابی

```solo
+  -  *  /  %
```

#### مقایسه‌ای

```solo
bigger  smaller  equal  not_equal  bigger_equal  smaller_equal
```

#### منطقی

```solo
and  or  not
```

### کنترل جریان

#### شرط

```solo
if x bigger 10:
    write("x is large")
else:
    write("x is small")
{end}
```

#### حلقه for

```solo
for i in 1...10:
    write(i)
{end}
```

#### حلقه while

```solo
int count = 0
while (count smaller 5, count=count+1):
    write(count)
{end}
```

### توابع

```solo
function add(a::int, b::int):
    return a+b
{end}

function factorial(n::int):
    if n smaller_equal 1:
        return 1
    {end}
    return n * factorial(n-1)
{end}
```

### شیءگرایی

```solo
class BankAccount:
    function init(~::object, owner::str, balance::int):
        ~owner = owner
        ~balance = balance
    {end}
    function deposit(~::object, amount::int):
        ~balance = ~balance + amount
    {end}
    function getBalance(~::object):
        return ~balance
    {end}
{end}

object account = BankAccount("Ali", 1000)
account.deposit(500)
write(account.getBalance())
```

### آرایه‌ها

```solo
arr nums = {1, 2, 3, 4, 5}
write(nums[0])
write(len(nums))
nums = append(nums, 6)
nums = remove(nums, 0)
```

### دیکشنری‌ها

```solo
dict person = ["name":"Ali";"age":25;"city":"Tehran"]
write(person{"name".val})
write(person{index(0).val})
write(person{25.key})
write(keys(person))
write(values(person))
```

### مدیریت فایل

```solo
write_file("output.txt", "Hello SoloScript")
str content = read_file("output.txt")
arr lines = read_lines("output.txt")
if file_exists("output.txt"):
    write("File exists")
{end}
delete_file("output.txt")
```

### توابع داخلی

#### ریاضی

```solo
abs(x)      # قدر مطلق
min(a, b, ...)  #حداقل
max(a, b, ...) # حداکثر
pow(x, y)    #توان
sqrt(x)     # جذر
floor(x)    # کف
ceil(x)     # سقف
round(x)    # گرد کردن
sin(x)      # سینوس
cos(x)     #  کسینوس
tan(x)      # تانژانت
log(x)      # لگاریتم طبیعی
log10(x)   #  لگاریتم پایه 10
exp(x)      # توان e
random()    # عدد تصادفی 0 تا 99
random(n)   # عدد تصادفی 0 تا n-1
random(a, b) #عدد تصادفی a تا b
```

#### تبدیل

```solo
int(x)       #تبدیل به عدد صحیح
str(x)       #تبدیل به رشته
float(x)     #تبدیل به عدد اعشاری
bool(x)      #تبدیل به مقدار منطقی
```

#### سایر

```solo
len(x)       #طول رشته/آرایه/دیکشنری
type(x)      #نوع متغیر
input(prompt) #دریافت ورودی
range(a, b)  #ساخت آرایه عددی
```

#### رشته‌ها

```solo
str name = "Solo"
write("Hello {}", name)
write("{} + {} = {}", 1, 2, 3)
```

### کامنت

```solo
# این یک کامنت است
```

## نمونه کد کامل

```solo
write("Hello SoloScript!")
int x = 30
str y = "a"
write("number is {} and string is {}", x, y)

for i in 1...10:
    write(i)
{end}

int z = 10
while (z bigger 0, z=z-1):
    write(z)
{end}

function add(a::int, b::int):
    return a+b
{end}

write(add(5, 3))

arr m = {8, 9, 10, "a", True}
write(m[0])
write(len(m))

dict d = ["a":5;"b":60;"c":70]
write(d{"b".val})
write(d{index(0).val})
write(d{70.key})

class Car:
    function init(~::object, speed::int):
        ~speed = speed
    {end}
    function go(~::object):
        ~speed = ~speed + 25
        write(~speed)
    {end}
{end}

object car = Car(80)
car.go()
```
## خطایابی

سیستم خطایابی SoloScript نوع خطا، شماره خط و ستون را نمایش می‌دهد:

```
Error: Parse Error at line 17, column 13
  Unexpected token: *
    *
                ^
```
## کپی‌رایت
### لایسنس
GNU General Public License v3.0

**هرگونه استفاده خودسرانه یا تغییر دادن کد و ثبت کردن به نام خود بدون اجازه سازنده از نظر شرعی حرام است.**
## حمایت
اگر این پروژه مفید بود لطفاً ستاره بدید.













