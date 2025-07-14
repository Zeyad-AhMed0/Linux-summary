# 📘 01 - Introduction to Linux

## 🐧 What is Linux?

Linux is a free and open-source operating system based on Unix. It powers everything from servers, supercomputers, mobile phones (Android), to IoT devices.

---

## 🧠 Key Features
- **Open Source:** Anyone can view, modify, and distribute the code.
- **Multi-user & Multitasking:** Supports many users and processes at once.
- **Secure & Stable:** Used on over 90% of cloud infrastructure due to its reliability.

---

## 🕰️ A Brief History
- Created in **1991** by **Linus Torvalds**.
- Started as a personal project and grew into the core of the modern internet.

---

## 🏠 Common Linux Distributions (Distros)
| Distro | Description |
|--------|-------------|
| **Ubuntu** | Most beginner-friendly |
| **Debian** | Stable base for many distros |
| **Fedora** | Bleeding edge features |
| **Arch** | Customizable, for advanced users |
| **Kali Linux** | Designed for security and penetration testing |

---

## ✅ Why Learn Linux?
- 💼 Required in DevOps, Cloud, Networking, and Cybersecurity.
- 📂 Master file systems, permissions, processes.
- 🔧 Gives you true power over your system.

---
المكونات الأساسية للينكس:
1. Kernel:
   
التعريف: الـ Kernel هو قلب نظام التشغيل، والمسؤول عن إدارة الموارد المادية للجهاز (الهاردوير) مثل المعالج، الذاكرة، القرص الصلب، إلخ.

الدور الأساسي:

إدارة العمليات (Processes Scheduling)

إدارة الذاكرة (Memory Management)

التحكم في المدخلات والمخرجات (I/O Management)

التعامل مع الـ File System

ملحوظة: المستخدم لا يتفاعل مباشرة مع الـ Kernel، بل من خلال وسيط مثل الـ Shell.

 2. Terminal:
    
التعريف: الـ Terminal هو واجهة تفاعلية تسمح لك بكتابة وتنفيذ الأوامر النصية.

الوظيفة: مجرد نافذة تنقل مدخلاتك إلى الـ Shell وتعرض المخرجات.

أمثلة: GNOME Terminal، Konsole، xterm.

📝 الفرق بين Terminal وShell:

الـ Terminal هو الإطار الخارجي.

الـ Shell هو البرنامج التفاعلي اللي بيشتغل داخل الـ Terminal وينفذ الأوامر.

 3. Shell:
    
التعريف: الـ Shell هو المترجم (Interpreter) اللي بياخد الأوامر اللي بتكتبها في الـ Terminal، ويفسرها ويبعثها للـ Kernel، ثم يعرض الناتج.

أنواع Shells:


bash (Bourne Again Shell) ← الأكثر استخدامًا

sh, zsh, ksh, fish ← لكل منهم ميزات مختلفة

الوظائف:

تنفيذ الأوامر.

إدارة المتغيرات (Variables).

البرمجة النصية (Scripting).

التعامل مع الإخراج، المدخلات، الملفات، الشبكات، إلخ.

Let's continue in the next file: `02_file_system.md`.
