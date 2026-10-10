Qmax & Salik Software — النسخة الجديدة
======================================

محتويات الملف
- index.html: الموقع العام الأسود والأزرق.
- admin.html: لوحة الإدارة (تسجيل دخول، إضافة، تعديل، حذف).
- setup.sql: إنشاء الجداول وسياسات الأمان.

مهم: ابدأ بقاعدة بيانات Supabase للمشروع الجديد فقط. لا تستخدم أي Secret أو service_role key في ملفات HTML.

الخطوات
1) افتح مشروع Supabase الجديد > SQL Editor > New query.
2) انسخ setup.sql بالكامل والصقه ثم اضغط Run.
3) من Supabase > Authentication > Users، أنشئ مستخدمًا للمدير باستخدام بريده وكلمة مرور قوية.
4) انسخ UUID الخاص بالمستخدم من جدول Users.
5) ارجع إلى SQL Editor وشغّل الأمر التالي بعد استبدال UUID_HERE بالـ UUID الحقيقي (اترك علامات الاقتباس):
   insert into public.site_admins (user_id) values ('UUID_HERE') on conflict do nothing;
6) من Project Settings > API Keys، انسخ Publishable key فقط. لا تستخدم Secret key أو service_role.
7) من Project Settings > API، انسخ Project URL.
8) افتح index.html بمحرر نصوص وابحث عن:
   PASTE_YOUR_SUPABASE_PROJECT_URL_HERE
   PASTE_YOUR_SUPABASE_PUBLISHABLE_KEY_HERE
   واستبدل كل نص بالقيمة المناسبة مع الاحتفاظ بعلامات الاقتباس. كرر نفس الأمر في admin.html ثم احفظ الملفين.
9) ارفع index.html وadmin.html إلى جذر مستودع GitHub الجديد (نفس مستوى README.md). يمكنك كذلك رفع setup.sql وREADME.txt للاحتفاظ بهما، لكنهما ليسا مطلوبين لعمل صفحات الموقع.
10) من GitHub > Settings > Pages، اختار Deploy from a branch، ثم branch main والمجلد /(root)، واضغط Save.
11) افتح رابط GitHub Pages، واختبر لوحة الإدارة من /admin.html.

الأقسام الرئيسية:
- السوفتوير: الشكل القديم (old) والشكل الجديد (new)
- الفلاشة
- اللودر
- ملفات القنوات: DB وSDX وChmax

تنبيه: Publishable key مخصص للاستخدام بالمتصفح، والأمان يعتمد على سياسات RLS. لا تضف مفاتيح Secret أو service_role إلى أي ملف منشور. احتفظ بكلمة مرور المدير سرية.
