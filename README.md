# 🔓 Password Cracking Lab – Kali Linux

This is a beginner-friendly cybersecurity lab focused on password cracking using tools like **John the Ripper** and **Hashcat** inside a Kali Linux virtual machine. The goal is to demonstrate an understanding of password hashing, weak password exploitation, and the importance of strong credential hygiene.

## 🧰 Tools Used

- [Kali Linux](https://www.kali.org/)
- [John the Ripper](https://www.openwall.com/john/)
- [Hashcat](https://hashcat.net/hashcat/)
- Wordlist: `rockyou.txt` (pre-installed in Kali)
- `openssl`, `md5sum`, `sha256sum`

## ⚙️ Setup

### 1. Create Sample Password Hashes

\`\`\`bash
# SHA-512 hash (similar to /etc/shadow format)
openssl passwd -6 -salt randomsalt mypassword
\`\`\`

Save hashes like this in a file called `hashes.txt`.

### 2. Create an MD5 Hash

\`\`\`bash
echo -n "mypassword" | md5sum
\`\`\`

Save the output (just the hash) into a file called `md5hash.txt`.

## 🚀 Cracking with John the Ripper

\`\`\`bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
john --show hashes.txt
\`\`\`

To crack real shadow hashes (on your Kali VM only):

\`\`\`bash
sudo unshadow /etc/passwd /etc/shadow > combined.txt
john combined.txt
\`\`\`

## ⚡ Cracking with Hashcat

\`\`\`bash
# Mode 0 = MD5, Attack 0 = Dictionary
hashcat -m 0 -a 0 md5hash.txt /usr/share/wordlists/rockyou.txt
\`\`\`

To check supported hash modes:

\`\`\`bash
hashcat --help
\`\`\`

## 📸 Sample Output

![Sample John output](screenshots/john_output.png)

## 🛡️ Disclaimer

This project is for educational purposes only. Do **not** attempt these techniques on any system you do not own or have explicit permission to test.

## 📁 Project Structure

\`\`\`
├── hashes.txt
├── md5hash.txt
├── combined.txt        # Optional: For real Linux shadow/passwd testing
├── screenshots/
│   └── john_output.png
├── commands.sh         # Optional: All CLI commands used
└── README.md
\`\`\`

## ✨ Next Steps

- Try cracking salted SHA hashes  
- Create your own custom wordlist  
- Test performance on GPU vs CPU (if hardware supports it)  
- Build a small Bash script that automates the cracking process
