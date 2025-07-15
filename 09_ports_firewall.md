
# 🧱 البورتات والفايروول في لينكس

التحكم في حركة المرور الداخلة والخارجة من نظام لينكس شيء أساسي لتأمين السيرفر وضمان أدائه. في الجزء ده هنغطي إزاي نفحص البورتات المفتوحة والخدمات اللي بتسمع عليها، وكمان إزاي نتحكم في الوصول عن طريق أدوات الفايروول زي `ufw` و `iptables`.

---

## 🔌 أوامر فحص البورتات

### 🔍 عرض البورتات اللي بتسمع
```bash
ss -tuln       # عرض البورتات TCP/UDP اللي بتستقبل
netstat -tuln  # بديل قديم لأمر ss
lsof -i        # عرض السوكتس المفتوحة
```

### 🧠 معاني الفلاجز:
- `t` → بروتوكول TCP
- `u` → بروتوكول UDP
- `l` → Listening (يعني بيسمع)
- `n` → عرض رقمي (من غير ترجمة DNS)

---

## 🧯 إدارة الفايروول

### 1. أداة UFW (Uncomplicated Firewall)
أداة سهلة الاستخدام لإدارة الجدار الناري، وغالبًا بتكون موجودة في توزيعات Ubuntu وDebian.

#### 📌 أوامر أساسية لـ UFW
```bash
sudo ufw status                               # عرض حالة الفايروول
sudo ufw enable                               # تفعيل الفايروول
sudo ufw disable                              # تعطيل الفايروول
sudo ufw allow 22                             # السماح ببورت SSH
sudo ufw deny 80                              # منع بورت HTTP
sudo ufw allow from 192.168.1.0/24 to any port 22  # السماح من شبكة معينة
```

#### 📌 حذف القواعد
```bash
sudo ufw delete allow 22
```

---

### 2. أداة iptables (للتحكم المتقدم)
أداة قوية للتحكم الدقيق في الترافيك الداخل والخارج.

#### ✅ أوامر أساسية
```bash
sudo iptables -L                                     # عرض القواعد الحالية
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT   # السماح ببورت SSH
sudo iptables -A INPUT -j DROP                       # حظر باقي الترافيك
```

#### 🔄 حفظ القواعد وإعادة تحميلها:
- في توزيعات Debian/Ubuntu:
```bash
sudo iptables-save > /etc/iptables/rules.v4
```
- في توزيعات RedHat/CentOS:
```bash
sudo service iptables save
```

---

## 🛡️ نصائح مهمة:
- دايمًا تأكد إن بورت SSH (عادة 22) مفتوح علشان تقدر تدخل على السيرفر.
- جرب تعديلات الفايروول في جلسة `screen` أو `tmux` علشان لو حصل مشكلة تقدر ترجع بسرعة.
- استخدم أداة `nmap` من جهاز تاني لفحص البورتات المفتوحة:
```bash
nmap <your-ip>
```

---

## 📚 مصادر إضافية:
- `man ufw`, `man iptables`, `man ss`, `man lsof`
- https://wiki.ubuntu.com/UFW
- https://linux.die.net/man/8/iptables
