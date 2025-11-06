p align="center">
    A Beautiful Web-Based Base64 & String Decoder Tool Built by <b>Noman</b> <br>
    Fast • Clean UI • Mobile Friendly • 100% Free
</p>

---

### ✅ Features
✔ Decode Base64 text instantly  
✔ Built-in Error Handling (invalid string alert)  
✔ Neon Dark UI Theme (hacker style)  
✔ Social Contact Buttons (FB / WhatsApp / Telegram)  
✔ No server needed — runs fully in browser (HTML + JS)

---

### 🛠️ Tech Stack
| Technology | Used For |
|------------|----------|
| HTML | UI Structure |
| CSS | Glowing UI + Dark Theme |
| JavaScript | Base64 Decoder Function |
| SweetAlert2 | Error Popup UI |

---

### 🚀 Live Demo  
🔗 **Live Website:**

https://YOUR-USERNAME.github.io/noman-code-decoder/

(Replace after hosting)

---

### 📌 Screenshot Preview

[ Add Screenshot Here ]  ← You can upload later

---

### 🔍 Usage
Just open the website → paste Base64 text → click **Decode** ✅  
No installation required.

---

### 📦 Local Run (Optional)
```bash
# Download or clone repository
git clone https://github.com/YOUR-USERNAME/noman-code-decoder.git

# Open the project folder
cd noman-code-decoder

# Run in browser
start index.html   # Windows
xdg-open index.html  # Linux / Termux
open index.html   # Mac


---

🧠 JavaScript Decoder Function (Core Logic)

function decodeBase64() {
    var inputBase64 = document.getElementById("encodedText").value.trim();
    try {
        var decoded = decodeURIComponent(escape(atob(inputBase64)));
        document.getElementById("outputText").textContent = decoded;
    } catch (e) {
        Swal.fire("❌ Error!", "Invalid or non-Base64 string!", "error");
    }
}


---

👤 Owner & Author

Noman
Full Stack Web & Python Developer


---

🌎 Social Links

Platform	Link

🔵 Facebook	https://www.facebook.com/md.norman.988
🟢 WhatsApp	https://whatsapp.com/channel/0029VbAkW0SATRSeAAYjNv1Z
🚀 Telegram	https://t.me/TNEHCHATGROUP



---

📝 License

✅ Free to use
❌ Don't remove author credits without permission


---

⭐ Support The Project

If you like this, give it a Star ⭐ on GitHub

git clone → modify → share → contribute ✅


---

💬 Need help?

Inbox: Telegram Group → https://t.me/TNEHCHATGROUP

Always learning, always building 🚀 — Noman

---

## ✅ এখন কী করতে হবে?

➜ তুমি শুধু **এই README.md কপি করে GitHub repo–তে Upload** করো  
➜ যদি চাও আমি এটাকে **আরও pro look (badges, shields, logo)** দিয়ে আপগ্রেড করি — শুধু বলো:

Add badges & logo

➜ যদি চাও আমি README–তে **GIF animation + Live Preview Image** যোগ করি — বলবে:

Add preview screenshot section fully

---

### 🔥 চাইলে আমি README + index.html + assets নিয়ে **একটা ZIP প্যাকেজও বানিয়ে দিতে পারি**  
বললেই ডাউনলোড লিঙ্ক তৈরি করে দেব ✅
