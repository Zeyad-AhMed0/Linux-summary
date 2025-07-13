# 👥 Linux Users & Groups - المستخدمين والجروبات في لينكس

في أنظمة Linux، كل شيء تقريبًا بيتم التحكم فيه عن طريق "مستخدمين" و"مجموعات" بهدف تنظيم الأذونات وحماية النظام.

---

### 👤 من هو المستخدم؟
- كل مستخدم (User) لديه:
  - معرف فريد **UID**
  - مجلد شخصي (Home directory)
  - نوع Shell (مثل bash أو sh)

### 👥 ما هي الجروبات؟
- الجروب (Group) عبارة عن مجموعة من المستخدمين.
- يتم استخدام الجروبات لتحديد صلاحيات الوصول لمجموعة من الأشخاص بدل كل واحد على حدة.

---

## 🧾 ملفات النظام المهمة

| الملف | الوصف |
|-------|--------|
| `/etc/passwd` | يحتوي على معلومات المستخدمين |
| `/etc/shadow` | يحتوي على كلمات السر بشكل مشفر |
| `/etc/group`  | يحتوي على معلومات الجروبات |
| `/etc/login.defs` | إعدادات افتراضية للمستخدمين الجدد |

---



### ➕ إنشاء مستخدم جديد
```bash
sudo adduser username

sudo useradd -m -s /bin/bash username

-m: إنشاء مجلد home
-s: تحديد نوع الـ shell

❌ حذف مستخدم

sudo deluser username
أو:

sudo userdel -r username
-r: لحذف المجلد الشخصي كمان

🧪 تعديل مستخدم موجود

sudo usermod -s /bin/zsh username   # تغيير الشل
sudo usermod -d /new/home username # تغيير المجلد الشخصي
sudo usermod -G groupname username # إلحاقه بجروب إضافي

🔍 عرض معلومات المستخدم
id username
groups username
getent passwd username

👥 إدارة الجروبات
➕ إنشاء جروب

sudo addgroup developers

➕ إضافة مستخدم لجروب

sudo usermod -aG developers username
-aG: تعني "أضف إلى الجروب دون إزالة الجروبات الأخرى"

❌ حذف جروب

sudo delgroup developers

🧪 مثال عملي

sudo adduser ahmed
sudo addgroup devs
sudo usermod -aG devs ahmed
groups ahmed

🔒 أنواع المستخدمين
النوع	الوصف
root	المستخدم الإداري، له كل الصلاحيات
system users	مستخدمين النظام، غالبًا لإدارة الخدمات
regular users	المستخدمين العاديين (مثل الطلاب أو الموظفين)

🧠 الفرق بين Primary Group و Secondary Groups
Primary Group: الجروب الأساسي اللي بيرتبط بالمستخدم.

Secondary Groups: جروبات إضافية ينتمي لها.

🔁 تغيير الجروب الأساسي

sudo usermod -g newgroup username
📌 نصائح للممارسات الأمنية
لا تعطي صلاحيات sudo لمستخدم إلا لو كان موثوق.

نظم الجروبات حسب الوظائف (مثلاً: devs, admins, hr)

راجع صلاحيات المجلدات المشتركة بشكل دوري.

🔚 خلاصة
فهمك العميق للمستخدمين والجروبات هو مفتاح تنظيم الصلاحيات والأمان في لينكس.
كمدير نظام، لازم تكون مرتاح جدًا مع أوامر زي adduser, usermod, groupadd, و id.