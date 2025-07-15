# 🐚 Bash in Linux - ملخص شامل

الـ **Bash** (اختصارًا لـ "Bourne Again Shell") هو أشهر shell مستخدم في أنظمة لينكس. هو بيئة تنفيذ الأوامر ونقطة التفاعل الرئيسية مع النظام، وبيُستخدم كمان في كتابة سكريبتات لأداء مهام تلقائية أو معقدة.

---

## 📌 الفرق بين Bash و Shells تانية
| Shell | مميزاته |
|-------|---------|
| `sh`  | الأساسي، بسيط لكن محدود |
| `bash` | شائع جدًا، غني بالمزايا |
| `zsh` | قابل للتخصيص، مميز في الواجهة |
| `fish` | حديث وسهل الاستخدام |

---

## 🔤 المتغيرات (Variables)
```bash
name="Ziad"
echo $name
```

### 📌 أنواع المتغيرات:
- **عادية:** `var=value`
- **بيئية (Environment):** `export var=value`
- **مصفوفات (Arrays):**
```bash
arr=(apple banana cherry)
echo ${arr[1]}  # banana
```

---

## 🔁 التحكم في التدفق (Flow Control)

### ✅ if-else
```bash
if [ $x -gt 10 ]; then
  echo "Greater"
elif [ $x -eq 10 ]; then
  echo "Equal"
else
  echo "Less"
fi
```

### 🔁 for loop
```bash
for i in {1..5}; do
  echo $i
done
```

### 🔄 while loop
```bash
while [ $x -lt 5 ]; do
  echo $x
  x=$((x+1))
done
```

---

## 🧮 المقارنات في if وشرحها

### 📊 مقارنة أرقام:
| التعبير | المعنى |
|---------|--------|
| `-eq`   | equal (يساوي) |
| `-ne`   | not equal (لا يساوي) |
| `-gt`   | greater than (أكبر من) |
| `-lt`   | less than (أصغر من) |
| `-ge`   | greater or equal (أكبر أو يساوي) |
| `-le`   | less or equal (أصغر أو يساوي) |

### 📄 مقارنة نصوص:
| التعبير | المعنى |
|---------|--------|
| `=`     | يساوي |
| `!=`    | لا يساوي |
| `-z`    | هل النص فاضي؟ |
| `-n`    | هل النص غير فاضي؟ |

### 🔐 مقارنة ملفات:
| التعبير | المعنى |
|---------|--------|
| `-e file`   | هل الملف موجود؟ |
| `-d file`   | هل هو مجلد؟ |
| `-f file`   | هل هو ملف عادي؟ |
| `-x file`   | هل الملف قابل للتنفيذ؟ |
| `-r file`   | هل الملف قابل للقراءة؟ |
| `-w file`   | هل الملف قابل للكتابة؟ |

---

## 📂 التعامل مع الملفات
```bash
cd /path/to/dir
ls -l
cat file.txt
touch newfile
mkdir newdir
rm file.txt
```

---

## 🔧 العمليات الحسابية
```bash
echo $((5 + 3))   # 8
x=4
echo $((x * 2))  # 8
```

---

## 📤 Redirection و Pipelines
```bash
echo "Hello" > file.txt       # إعادة توجيه الإخراج
cat file.txt >> log.txt       # إضافة للإخراج الموجود
command < input.txt           # قراءة من ملف
ls -l | grep "txt"            # بايبلاين
```

---

## ⚙️ Functions
```bash
hello() {
  echo "Hello $1"
}

hello Ziad
```

---

## 📜 السكريبتات
- ابدأ كل سكريبت بـ:
```bash
#!/bin/bash
```
- اجعل الملف قابل للتنفيذ:
```bash
chmod +x script.sh
./script.sh
```

---

## 🧰 أوامر Bash المفيدة
| الأمر | الوظيفة |
|-------|---------|
| `echo` | طباعة للنصوص |
| `read` | قراءة إدخال من المستخدم |
| `test` | تنفيذ المقارنات |
| `exit` | إنهاء السكريبت بكود معين |
| `basename` | استخراج اسم الملف من المسار |
| `dirname` | استخراج المسار بدون اسم الملف |
| `sleep` | تأخير تنفيذ بالأوامر |
| `date` | عرض الوقت والتاريخ |
| `cut` | قطع جزء من النص |
| `awk` | معالجة ملفات نصية |
| `sed` | تعديل ملفات نصية |
| `grep` | البحث عن نصوص |

---

## 🚩 أشهر الـ Options و Flags
- `-n` : لا تنتقل لسطر جديد (echo)
- `-e` : تفسير الـ escape characters (
, 	)
- `-r` : قراءة السطر كما هو (read)
- `-f` : يعمل على الملفات
- `-v` : verbose mode (تفصيلي)
- `--help` : لعرض المساعدة

---

## 🧠 نصائح:
- دايمًا استخدم `#!/bin/bash` في أول السكريبت.
- تأكد من صلاحيات التشغيل `chmod +x`.
- جرب السكريبت خطوة بخطوة بـ `bash -x script.sh`.

---

## 📚 مصادر إضافية:
- `man bash`
- https://tldp.org/LDP/Bash-Beginners-Guide/html/
- https://www.gnu.org/software/bash/manual/bash.html