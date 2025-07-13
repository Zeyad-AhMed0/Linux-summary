<div dir="ltr">

# 🌐 Linux Networking - أوامر الشبكات في لينكس

التحكم في الشبكات هو جزء أساسي من إدارة أي نظام Linux. لازم تكون عارف إزاي تتعامل مع الشبكة، تتتبع الاتصالات، وتفهم الـ IP Routing.

---

## 🧠 الجزء الأول: الأساسيات (Basics)

### 🔌 عنوان الـ IP
- كل جهاز في الشبكة له IP Address.
- يمكن أن يكون ثابت (Static) أو يتم توزيعه تلقائيًا (Dynamic via DHCP).

### 🌍 Network Interface
- كل كارت شبكة يسمى "Interface"، مثل:
  - `eth0`, `enp0s3`: إيثرنت
  - `wlan0`: واي فاي
  - `lo`: Local loopback (127.0.0.1)

---

## 🧾 ملفات الشبكة المهمة

| الملف | الوصف |
|-------|--------|
| `/etc/network/interfaces` | إعدادات الشبكة في بعض التوزيعات |
| `/etc/resolv.conf` | يحتوي على DNS Servers |
| `/etc/hosts` | تحويل أسماء دومينات إلى IP داخليًا |
| `/etc/hostname` | اسم الجهاز |

---

## 🛠️ أوامر الشبكات

### 📡 عرض إعدادات الشبكة


ip addr        # عرض كل الـ IPs

ip a           # اختصار

ip link        # عرض كل الكروت


ifconfig       # قديم لكنه ما زال يُستخدم

📶 مراقبة الشبكة والاتصال

ping google.com           # اختبار الاتصال

traceroute google.com     # تتبع مسار الحزم

host google.com           # الاستعلام عن DNS

nslookup google.com       # استعلام DNS

dig google.com            # أداة قوية لفحص DNS


📶 عرض الـ Routing Table

ip route       # عرض جدول التوجيه

route -n       # عرض بنفس الطريقة (أمر قديم)


🔄 إعداد IP يدويًا

sudo ip addr add 192.168.1.100/24 dev eth0

sudo ip route add default via 192.168.1.1


🔗 تشغيل/إيقاف كارت شبكة

sudo ip link set eth0 up

sudo ip link set eth0 down


🌐 إعداد DNS

cat /etc/resolv.conf


تضيف مثلاً:

nameserver 8.8.8.8

nameserver 1.1.1.1


🧪 معرفة الـ IP الخارجي

curl ifconfig.me

curl ipinfo.io/ip


🧪 أمثلة واقعية

🔍 معرفة حالة الاتصال

ping -c 4 8.8.8.8


📡 تحديد المنفذ المفتوح على سيرفر

telnet example.com 80

nc -zv example.com 80


🛡️ أوامر الشبكة والأمان


netstat -tuln        # عرض المنافذ المفتوحة (ممكن تستبدله بـ ss)

ss -tuln             # أسرع وأدق من netstat


🔧 Network Manager (GUI وCLI)

nmcli device status         # عرض الكروت وحالتها

nmcli connection show       # عرض الإعدادات

nmcli device wifi list      # عرض شبكات الواي فاي


📌 نصائح مهمة
 
استخدم ip بدل ifconfig (أكثر حداثة وموثوقية)


راقب DNS بشكل دوري لتجنب مشاكل التوجيه


تحقق دائمًا من إعدادات الـ firewall عند وجود مشكلة اتصال


🔚 خلاصة

أوامر الشبكة في لينكس أساسية لأي مدير نظام. معرفتك بـ ip, ping, ss, و traceroute هتخليك تحل أغلب مشاكل الشبكة بسهولة وكفاءة.

