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

# Redirection & Pipelines in Linux

## مقدمة
Redirection و Pipelines من أهم مميزات الـ shell في لينكس.  
بيتحكموا في تدفّق البيانات بين الـ commands، سواء بإعادة توجيه الـ input/output أو ربط أوامر ببعض في سلسلة واحدة.

---

# 1. Redirection  
Redirection معناها إنك تغيّر مكان الـ **input** أو **output** بتاع أي command بدل ما يروح للـ terminal.

## 1.1 Output Redirection
إخراج الـ output لملف بدل الشاشة.

### الكتابة فوق الملف (overwrite):
```bash
command > file.txt
الإضافة لنهاية الملف (append):
bash
نسخ الكود
command >> file.txt
1.2 Input Redirection
استخدام ملف كمدخل للـ command:

bash
نسخ الكود
command < file.txt
1.3 Error Redirection
Standard Error بيبقى رقم 2.

إرسال الأخطاء فقط لملف:
bash
نسخ الكود
command 2> errors.log
دمج الـ Output + Error في ملف واحد:
bash
نسخ الكود
command > output.log 2>&1
أو:

bash
نسخ الكود
command &> output.log
(حسب نوع الشيل)

1.4 دمج Input + Output
توجيه output لملف، وأخذ input من ملف:

bash
نسخ الكود
command1 < in.txt > out.txt
2. Pipelines
Pipeline (الرمز |) بيستخدم لربط commands ببعض.
الـ Output بتاع command يدخل كـ Input للّي بعده من غير ملفات وسيطة.

أمثلة:
مثال 1: تصفية الملفات بالـ grep
bash
نسخ الكود
ls -l | grep ".txt"
مثال 2: عدّ السطور
bash
نسخ الكود
cat access.log | wc -l
مثال 3: فرز ثم اختيار أول 10 سطور
bash
نسخ الكود
sort bigfile.txt | head
2.1 إرسال الـ Error مع Output للـ Pipeline
عشان الـ pipe بياخد الـ Standard Output بس…
لو عايز تبعت الـ errors كمان، استخدم:

bash
نسخ الكود
command 2>&1 | other_command
3. أوامر إضافية مفيدة
3.1 The tee Command
بيكتب الـ output في ملف وفي نفس الوقت يعرضه على الشاشة.

bash
نسخ الكود
command | tee output.txt
لإضافة المحتوى بدل الكتابة فوقه:

bash
نسخ الكود
command | tee -a output.txt
3.2 Heredoc (<<)
طريقة تدي command input من النص اللي تكتبه في نفس اللحظة.

bash
نسخ الكود
cat << EOF
Hello world
This is a heredoc
EOF
Quick Notes
> → كتابة output لملف

>> → إضافة output لملف

< → إدخال من ملف

2> → توجيه errors

2>&1 → دمج error مع output

| → ربط output ل command بالـ input للّي بعده

tee → حفظ output في ملف + عرضه

<< → Heredoc لإرسال input مباشر للـ command

خلاصة
Redirection بيغير مسار الـ input/output،
والـ pipeline بيربط commands ببعض كأنها stages في خط إنتاج.
الاتنين مع بعض بيخلّوا الشيل قوة جبارة في معالجة البيانات والتحكم في الـ commands.


---

لو عايز أضيف شرح للـ **process substitution `<( )`** أو **named pipes (FIFOs)** عشان الريبو يبقى “full coverage”، قولّي وهكمّل الملف.

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
