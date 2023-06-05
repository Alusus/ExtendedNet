# ExtendedNet
[[English]](readme.md)

توسعة لوحدة شبكة ضمن متم

## إضافة المكتبة للمشروع

<div dir=rtl>

```
اشمل "مـحا"؛
مـحا.اشمل_ملف("Alusus/ExtendedNet"، "تـوسعة_شبكة.أسس")؛
```

</div>

```
import "Apm";
Apm.importFile("Alusus/ExtendedNet");
```

## مثال

<div dir=rtl>

```
// نقوم بتضمين المكتبات الضرورية
اشمل "مـتم/طـرفية"؛
اشمل "مـتم/طـرفية"؛
اشمل "مـتم/ذاكـرة"؛
اشمل "مـتم/شـبكة"؛
اشمل "مـحا"؛
مـحا.اشمل_ملف("Alusus/ExtendedNet"، "توسيع_شبكة.أسس")؛

دالة ابدأ {
    عرف بيانات: مؤشر؛
    عرف حجم: صـحيح؛
    عرف الرابط: "https://example.org"؛
    عرف بيانات_الأرسال: "بيانات ليتم ارسالها"؛
    
    إذا مـتم.شـبكة.أرسل(الرابط، بيانات_الأرسال, بيانات~مؤشر، حجم~مؤشر) {
        مـتم.طـرفية.اطبع("%s\ج"، بيانات)؛
        مـتم.ذاكـرة.حرر(بيانات)؛
    } وإلا {
        مـتم.طـرفية.اطبع("فشل\ج")؛
    }
}

ابدأ()؛
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
if Net.post("https://example.org","the posted data goes here", data~ptr, size~ptr) {
  Console.print("%s\n", data);
  Memory.free(data);
} else {
  Console.print("Error!\n");
}
```

## الدالات

### أرسل (post)

<div dir=rtl>

```
دالة أرسل(
    عنوان: مـؤشر_محارف،
    بيانات_الإرسال: مـؤشر_محارف،
    الناتج: مؤشر[مؤشر]،
    حجم_الناتج: مؤشر[صـحيح]،
    مصادقة: مـؤشر_محارف
): ثـنائي
```

</div>

```
func post(
    url: CharsPtr,
    postedData: CharsPtr,
    result: ptr[ptr],
    resultCount: ptr[Int],
    auth: CharsPtr
): Bool
```

هذا التابع يقوم بأرسال طلب post ويضع النتائج في المؤشر `الناتج` (`result`)

`عنوان` (`url`) عنوان الخادم الذي نريد ارسال البيانات له.

`بيانات_الإرسال` (`postedData`) البيانات التي نريد ارسالها.

`الناتج` (`result`) مؤشر لتخزين الرد من الخادم.

`حجم_الناتج` (`resultCount`) طول الرد.

`مصادقة` (`auth`) رمز المصادقة لارساله الى الخادم.

يرجع 1 عند نجاح الإرسال.

<div dir=rtl>

```
دالة أرسل(عنوان: مـؤشر_محارف, بيانات_الإرسال: مـؤشر_محارف, الناتج: مؤشر[مؤشر], حجم_الناتج: مؤشر[صـحيح]): ثـنائي
```

</div>

```
func post(url: CharsPtr, postedData: CharsPtr, result: ptr[ptr], resultCount: ptr[Int]): Bool
```

تعمل عمل الدالة السابقة لكن بدون معطى المصادقة.

<div dir=rtl>

```
دالة أرسل(عنوان: مـؤشر_محارف, بيانات_الإرسال: مـؤشر_محارف, اسم_ملف_الناتج: مـؤشر_محارف, مصادقة: مـؤشر_محارف): ثـنائي
```

</div>

```
func post(url: CharsPtr, postedData: CharsPtr, outputFilename: CharsPtr, auth: CharsPtr): Bool
```

هذه الدالة يفعل نفس عمل الدالة السابقة لكنها تخزن الناتج في ملف.

`عنوان` (`url`) عنوان المخدم الذي نريد ارسال البيانات له.

`بيانات_الإرسال` (`postedData`) البيانات التي نريد ارسالها.

`اسم_ملف_الناتج` (`outputFilename`) عنوان الملف  لتخزين الرد من المخدم.

`مصادقة` (`auth`) رمز التحقق لارساله الى المخدم.

يرجع 1 عند نجاح الإرسال.

<div dir=rtl>

```
دالة أرسل(عنوان: مـؤشر_محارف, بيانات_الإرسال: مـؤشر_محارف, اسم_ملف_الناتج: مـؤشر_محارف): Bool
```

</div>

```
func post(url: CharsPtr, postedData: CharsPtr, outputFilename: CharsPtr): Bool
```

تعمل عمل الدالة السابقة لكن بدون معطى المصادقة.

### ضع_ملف

<div dir=rtl>

```
دالة ضع_ملف(عنوان: مـؤشر_محارف، اسم_الملف: مـؤشر_محارف، مصادقة: مـؤشر_محارف): ثـنائي؛
```

</div>

```
func putFile(url: CharsPtr, filename: CharsPtr, auth: CharsPtr): Bool;
```

هذه الدالة ترسل ملفًا إلى خادم في طلب put.

`عنوان` (`url`) عنوان المخدم الذي نريد ارسال البيانات له.

`اسم_الملف` (`filename`) مسار الملف الذي نريد ارساله.

`مصادقة` (`auth`) رمز التحقق لأرساله الى المخدم.

يرجع 1 عند نجاح الإرسال.

<div dir=rtl>

```
دالة ضع_ملف(عنوان: مـؤشر_محارف, اسم_الملف: مـؤشر_محارف): ثـنائي؛
```

</div>

```
func putFile(url: CharsPtr, filename: CharsPtr): Bool;
```

تعمل عمل الدالة السابقة لكن دون معطى المصادقة.

### أرسل_بريد

<div dir=rtl>

```
دالة ارسل_بريد(عنوان: مـؤشر_محارف, بيانات_البريد: مـصفوفة[نـص], كلمة_السر: مـؤشر_محارف): ثـنائي؛
```

</div>

```
func smtp(url: CharsPtr, emailData: Array[Srl.String], password: CharsPtr): Bool;
```

دالة لإرسال بريد الكتروني باستخدام برتكول smtp.

`عنوان` (`url`) عنوان المخدم الذي نريد ارسال البيانات له.

`بيانات_البريد` (`emailData`) بيانات الايميل الذي نرغب بأرساله والذي نحصل عليه من الدالة `هيئ_بيانات_بريد`.

`كلمة_السر` (`password`) كلمة السر الخاصة بالمرسل.

يرجع 1 عند نجاح الإرسال.

### هيئ_بيانات_بريد (prepareEmailData)

<div dir=rtl>

```
دالة هيئ_بيانات_بريد(
    المستلمون: مـصفوفة[نـص], المرسل: نـص, 
    العنوان: نـص, المتن: نـص, نوع_المتن: نـص
): مـصفوفة[نـص]؛
```

</div>

```
func prepareEmailData(
    receivers: Srl.Array[Srl.String], sender: Srl.String, 
    subject: Srl.String, body: Srl.String, bodyType: Srl.String
): Array[Srl.String]
```

هذه الدالة تهيئ بيانات البريد الإلكتروني لاستخداها في دالة `أرسل_بريد`.

`المستلمون` (`receivers`) مصفوفة لايميلات المستقبلين.

`المرسل` (`sender`) ايميل المرسل.

`العنوان` (`subject`) عنوان الايميل.

`المتن` (`body`) محتوى الايميل.

`نوع_المتن` (`bodyType`) نوع متن الايميل، إما `text` أو `html`.

يعيد مصفوفة بيانات ليتم تمريرها للدالة أرسل_بريد.
