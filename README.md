# 🔐 Understanding and Applying File Permissions with Python

This project demonstrates how to understand Unix/Linux file permissions and apply them programmatically using Python's built-in tools.

---

## 📘 What You'll Learn

- What Linux file permissions mean
- How to calculate octal permissions
- How to change file permissions using Python
- Visual logic flow for assigning permissions

---

## 🧠 File Permission Basics

Linux file permissions are divided into **three parts**:

rwxrwxr-x
│  │  └─ Others → r-x → Read & Execute
│  └──── Group  → rwx → Read, Write, Execute
└─────── User   → rwx → Read, Write, Execute

### 🧮 Octal Conversion

Each permission is a combination of values:

| Permission | Value |
|------------|-------|
| Read (r)   | 4     |
| Write (w)  | 2     |
| Execute (x)| 1     |

To convert `rwxrwxr-x`:
- **User**: rwx = 4 + 2 + 1 = **7**
- **Group**: rwx = 4 + 2 + 1 = **7**
- **Others**: r-x = 4 + 0 + 1 = **5**

➡ Final octal: `775`

---

## 🔁 Flowchart of Permission Logic

```text
START
  ↓
Is it a file or directory?
  ↓
Who needs access? (user/group/others)
  ↓
What type of access? (read/write/execute)
  ↓
Calculate octal value for each group
  ↓
Apply chmod using octal value (e.g., 775)
  ↓
DONE


⸻

🐍 Python Script to Apply Permissions

You can use Python to set these permissions using the os module:

import os

# Replace this with your target file
file_path = 'example.py'

# rwxrwxr-x = octal 775
os.chmod(file_path, 0o775)

print(f"Permissions changed to rwxrwxr-x for {file_path}")

✅ Output

Permissions changed to rwxrwxr-x for example.py


⸻

⚠️ Requirements
	•	Python 3.x
	•	File must exist at the specified path
	•	You must have permission to change the file’s mode

⸻

🔧 Run the Script

python3 set_permissions.py


⸻
