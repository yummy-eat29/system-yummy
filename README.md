# system yummy — تطبيق ويب (PWA) جاهز لرفعه على GitHub

هذا المجلد يحتوي على تطبيقك **كما هو تمامًا** بدون أي تعديل في التصميم أو الوظائف،
فقط تم:
1. وضع شعار **YUMMY** (نفس الصورة اللي أرسلتها) كأيقونة رسمية للتطبيق بكل المقاسات المطلوبة.
2. تجهيز ملفات PWA (manifest.json + service-worker.js) حتى يصير تطبيق حقيقي قابل للتثبيت
   على أندرويد وآيفون وويندوز مباشرة من المتصفح، بدون متجر تطبيقات.

## محتويات المجلد
```
index.html          ← نفس ملفك الأصلي (فقط تم تحديث الأيقونات)
manifest.json        ← إعدادات التطبيق (الاسم، الألوان، الأيقونات)
service-worker.js    ← يخلي التطبيق يفتح حتى لو قُطع الإنترنت بعد أول تشغيل
icons/                ← شعار YUMMY بكل المقاسات (16 إلى 512 بكسل)
```

## كيف أرفعه على GitHub وأشغّله كتطبيق حقيقي (GitHub Pages)

1. اذهب إلى https://github.com وأنشئ **مستودع (Repository) جديد** — مثلاً باسم `system-yummy`.
   اختر أنه **Public**.
2. ارفع كل محتويات هذا المجلد (index.html و manifest.json و service-worker.js ومجلد icons)
   إلى جذر المستودع مباشرة (بدون وضعها داخل مجلد فرعي).
   - إمّا بالسحب والإفلات من صفحة GitHub في المتصفح (زر "Add file" → "Upload files")،
   - أو عبر الأوامر التالية إذا كنت تستخدم git:
     ```bash
     git init
     git add .
     git commit -m "system yummy PWA"
     git branch -M main
     git remote add origin https://github.com/USERNAME/system-yummy.git
     git push -u origin main
     ```
3. من داخل المستودع في GitHub: **Settings → Pages**.
4. تحت "Build and deployment" اختر Source: **Deploy from a branch**،
   والفرع (Branch): **main**، والمجلد: **/(root)**، ثم اضغط **Save**.
5. انتظر دقيقة أو اثنتين، سيظهر لك رابط مثل:
   `https://USERNAME.github.io/system-yummy/`
6. افتح هذا الرابط من متصفح Chrome على الجوال → سيظهر خيار **"تثبيت التطبيق" / "Add to Home screen"**
   تلقائيًا (أو من قائمة المتصفح ⋮ → "تثبيت التطبيق"). بعد التثبيت سيظهر التطبيق
   بأيقونة **YUMMY** الأرجوانية في قائمة التطبيقات مثل أي تطبيق عادي، ويفتح بدون شريط المتصفح.

على آيفون: افتح الرابط من Safari → زر المشاركة (Share) → **"Add to Home Screen"**.

## ملاحظة مهمة
- لم يتم تغيير أي كود أو تصميم أو وظيفة من نظامك — فقط تم استبدال أيقونات التطبيق
  بشعار YUMMY، وإضافة ملفي manifest.json و service-worker.js اللذان كان index.html
  يشير إليهما أصلاً لكنهما لم يكونا موجودين.
- إذا رغبت لاحقًا بتطبيق APK حقيقي (ملف تثبيت مباشر على أندرويد بدل متصفح)، يمكن تحويل
  هذا الـ PWA بسهولة عبر أدوات مثل **PWABuilder** (pwabuilder.com) بعد رفعه على GitHub Pages،
  فقط ألصق رابط GitHub Pages هناك وسيولّد لك ملف APK جاهز يحمل نفس شعار YUMMY.
