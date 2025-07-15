# 09_services_systemd.md — التحكم في الخدمات باستخدام systemd

## 🧠 مقدمة
`systemd` هو نظام إدارة الخدمات في معظم توزيعات Linux الحديثة.  
بيتحكم في تشغيل وإيقاف الخدمات (services) وإدارتها تلقائيًا أثناء الإقلاع.

---

## ⚙️ مفاهيم أساسية

| المصطلح       | الوصف                                                         |
|---------------|---------------------------------------------------------------|
| service       | عملية بتشتغل في الخلفية (background) مثل ssh, nginx, cron     |
| unit          | ملف تعريف الخدمة داخل systemd (غالبًا بامتداد `.service`)     |
| target        | مجموعة من الوحدات (مثل runlevels في الأنظمة القديمة)         |

---

## 🔧 أوامر إدارة الخدمات

| الأمر                               | الوظيفة                                       |
|------------------------------------|-----------------------------------------------|
| `systemctl start service`          | بدء خدمة                                       |
| `systemctl stop service`           | إيقاف خدمة                                     |
| `systemctl restart service`        | إعادة تشغيل الخدمة                            |
| `systemctl reload service`         | إعادة تحميل الإعدادات بدون إعادة تشغيل        |
| `systemctl status service`         | عرض حالة الخدمة                               |
| `systemctl is-active service`      | التحقق إذا كانت الخدمة نشطة                   |

**مثال:**
```bash
sudo systemctl restart ssh
```
---

🚀 التحكم في التشغيل التلقائي

                             	
systemctl enable service	تفعيل الخدمة لتعمل تلقائيًا عند الإقلاع

systemctl disable service	تعطيل التشغيل التلقائي

systemctl is-enabled service	التحقق إذا كانت الخدمة مفعلة تلقائيًا

---

📂 أماكن ملفات الـ Unit
                          	
/etc/systemd/system/	ملفات الخدمات المُخصصة (custom services)

/lib/systemd/system/	ملفات الخدمات الافتراضية من النظام

/etc/systemd/system/*.wants	روابط للخدمات المفعّلة عند الإقلاع


---

🔍 أوامر إضافية مهمة

                        	
systemctl list-units --type=service	 عرض كل الخدمات النشطة

journalctl -u service 	عرض لوجات خدمة معينة

systemctl daemon-reexec 	إعادة تشغيل systemd نفسه

systemctl daemon-reload	 إعادة تحميل ملفات الـ unit بعد تعديلها

---

🧪 إنشاء خدمة مخصصة (Custom Service)

أنشئ سكريبت مثل:

```bash

sudo nano /usr/local/bin/myscript.sh
```
اجعل السكريبت قابل للتنفيذ:

```bash

sudo chmod +x /usr/local/bin/myscript.sh
```
أنشئ ملف خدمة:

```bash

sudo nano /etc/systemd/system/myscript.service
```

المحتوى:
```bash

[Unit]
Description=My Custom Script

[Service]
ExecStart=/usr/local/bin/myscript.sh
Restart=always

[Install]
WantedBy=multi-user.target
```


فعّل وشغّل الخدمة:

```bash

sudo systemctl daemon-reload
sudo systemctl enable myscript
sudo systemctl start myscript
```
---

⚠️ نصائح للمحترفين

لا تعدّل مباشرة على ملفات /lib/systemd/... — انسخها إلى /etc/systemd/... قبل التعديل.

استخدم journalctl -xe لتتبع الأخطاء عند فشل تشغيل خدمة.

أضف Restart=on-failure في الوحدة لجعل الخدمة تُعاد تلقائيًا عند الفشل.
