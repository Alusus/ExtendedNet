# ExtendedNet
[[English]](readme.md)

توسعة لوحدة شبكة ضمن متم
<div dir=rtl>

```
نقوم بتضمين المكتبة  كما يلي :
اشمل "مـتم/طـرفية"؛
اشمل "مـتم/نـص"؛
اشمل "مـحا"؛
مـحا.اشمل_ملف("Alusus/ExtendedNet"، "توسيع_شبكة.أسس")؛
```

</div>

```
import "Srl/Console";
import "Apm";
Apm.importFile("Alusus/ExtendedNet");
```

## مثال

<div dir=rtl>

```
// نقوم بتضمين المكتبات الضرورية
اشمل "مـتم/طـرفية"؛
اشمل "مـتم/طـرفية.أسس"؛
اشمل "مـتم/ذاكـرة.أسس"؛
اشمل "مـحا"؛
مـحا.اشمل_ملف("Alusus/ExtendedNet"، "توسيع_شبكة.أسس")؛

اشمل "مـتم/شـبكة.أسس"؛

وحدة رئـيسي
{
  دالة ابدأ
  {
    عرف بيانات: مؤشر؛
    عرف حجم: صـحيح؛
    عرف الرابط: "https://example.org"؛
    عرف بيانات_الأرسال: "بيانات ليتم ارسالها"؛
    
    إذا مـتم.شـبكة.أرسل(الرابط، بيانات_الأرسال, بيانات~مؤشر، حجم~مؤشر) {
      مـتم.طـرفية.اطبع("%s\ج"، بيانات)؛
      مـتم.ذاكـرة.حرر(بيانات)؛
    } وإلا {
      مـتم.طـرفية.اطبع("فشل\ج")؛
    }؛
  }؛
}؛

رئـيسي.ابدأ()؛


```

<div>

```
import "Srl/Console";
import "Apm";
Apm.importFile("Alusus/ExtendedNet");

use Srl;
// لجلب الرد من السيرفر
def data: ptr;
def size: Int;
//اختبر ان كان هناك مشكلة في الطلب
if Net.post("https://example.org","the posted data go here", data~ptr, size~ptr) {
  Console.print("%s\n", data);
  Memory.free(data);
} else {
  Console.print("Error!\n");
}
```

## التوابع

### تابع أرسل

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], result: ptr[ptr], resultCount: ptr[Int], auth: ptr[array[Char]]): Bool
```

هذا التابع يقوم بأرسال طلب post ويضع النتائج في المؤشر result

`url` عنوان المخدم الذي نريد ارسال البيانات له.

`postedData` البيانات التي نريد ارسالها.

`result` مؤشر لتخزين الرد من المخدم.

`resultCount` طول رد المخدم.

`auth` رمز التحقق لارساله الى المخدم.

يرجع صحيح في حالة تم الطلب بنجاح.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], outputFilename: ptr[array[Char]], auth: ptr[array[Char]]): Bool
```

هذا التابع يفعل نفس التابع السابق لكن يخزن رد المخدم ضمن ملف.

`url` عنوان المخدم الذي نريد ارسال البيانات له.

`postedData` البيانات التي نريد ارسالها.

`outputFilename` عنوان الملف  لتخزين الرد من المخدم.

`auth` رمز التحقق لارساله الى المخدم.
يرجع صحيح في حالة تم الطلب بنجاح.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], outputFilename: ptr[array[Char]]): Bool
```


هذا التابع يفعل نفس التابع السابق لكنه لا يقوم بعملية التوثيق.

`url` عنوان المخدم الذي نريد ارسال البيانات له.

`postedData` البيانات التي نريد ارسالها.

`outputFilename` عنوان الملف  لتخزين الرد من المخدم.


يرجع صحيح في حالة تم الطلب بنجاح.

```
func post(url: ptr[array[Char]], postedData: ptr[array[Char]], result: ptr[ptr], resultCount: ptr[Int]): Bool
```

هذا التابع يفعل نفس التابع السابق لكنه يخزن رد المخدم في المؤشر .


`url` عنوان المخدم الذي نريد ارسال البيانات له.

`postedData` البيانات التي نريد ارسالها.

`result` مؤشر لتخزين الرد من المخدم.

`resultCount` طول رد المخدم.

يرجع صحيح في حالة تم الطلب بنجاح.

```

### تابع أرسل_ملف

```
func putFile(url: ptr[array[Char]], filename: ptr[array[Char]], auth: ptr[array[Char]]): Bool
```

هذا التابع يرسل طلب put ويقوم بارسال ملف الى المخدم

`url` عنوان المخدم الذي نريد ارسال البيانات له.

`filename` مسار الملف الذي نريد ارساله.

`auth` رمز التحقق لأرساله الى المخدم.

يرجع صحيح في حال تم الطلب بنجاح.

```
func putFile(url: ptr[array[Char]], filename: ptr[array[Char]]): Bool
```

هذا التابع يفعل نفس التابع السابق لكنه لا يقوم بعملية التوثيق.

`url` عنوان المخدم الذي نريد ارسال البيانات له.

`filename` مسار الملف الذي نريد ارساله.



يرجع صحيح في حال تم الطلب بنجاح.

```

### تابع أرسل_بريد

```
func smtp(url: ptr[array[Char]], emailArray: Array[Srl.String], password: ptr[array[Char]]): Bool
```

هذا التابع يرسل بريد الكتروني باستخدام برتكول smtp.

`url` عنوان المخدم الذي نريد ارسال البيانات له.

'emailArray' الايميل الذي نرغب بأرساله والذي نحصل عليه من التابع  بناء_بريد.

'password' كلمة السر الخاصة بالمرسل.

يرجع صحيح في حال تم الطلب بنجاح.

```
func buildEmailString(reseviers: Srl.Array[Srl.String], sender: Srl.String, 
                        subject: Srl.String, body: Srl.String, textType: Srl.String): Array[Srl.String]
```

هذا التابع يبني الايميل ويعيد الايميل لارساله باستخدام التابع أرسل_بريد
`reseviers` مصفوفة لايميلات المستقبلين.

'sender' ايميل المرسل.

'subject' عنوان الايميل.

'body' محتوى الايميل.

'textType' نوع الايميل 'html , text'.

يعيد مصفوفة جمل ليتم ارسالها باستخدام التابع أرسل_بريد .

```


