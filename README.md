# 🔓 Password Cracking Lab – Kali Linux

This is a beginner-friendly cybersecurity lab focused on password cracking using tools like **John the Ripper** and **Hashcat** inside a Kali Linux virtual machine. The goal is to demonstrate an understanding of password hashing, weak password exploitation, and the importance of strong credential hygiene.

---

## 🧰 Tools Used

- [Kali Linux](https://www.kali.org/)
- [John the Ripper](https://www.openwall.com/john/)
- [Hashcat](https://hashcat.net/hashcat/)
- Wordlist: `rockyou.txt` (pre-installed in Kali)
- `openssl`, `md5sum`, `sha256sum`

---

## ⚙️ Setup

### 1. Create Sample Password Hashes

```bash
# SHA-512 hash (similar to /etc/shadow format)
openssl passwd -6 -salt randomsalt mypassword
