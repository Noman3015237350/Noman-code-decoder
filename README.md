# 🔥 Base64 & String Decoder

A Beautiful Web-Based Base64 & String Decoder Tool Built by **Noman**  
Fast • Clean UI • Mobile Friendly • 100% Free

---

## ✅ Features
- ✔ Decode Base64 text instantly  
- ✔ Built-in Error Handling (invalid string alert)  
- ✔ Neon Dark UI Theme (hacker style)  
- ✔ Social Contact Buttons (FB / WhatsApp / Telegram)  
- ✔ No server needed — runs fully in browser (HTML + JS)

---

## 🛠️ Tech Stack
| Technology | Used For |
|------------|----------|
| HTML | UI Structure |
| CSS | Glowing UI + Dark Theme |
| JavaScript | Base64 Decoder Function |
| SweetAlert2 | Error Popup UI |

---

## 🚀 Quick Start
```bash
# Clone repository
git clone https://github.com/Noman3015237350/Noman-code-decoder.git

# Open in browser
cd Noman-code-decoder
open index.html
```

---

🔍 Usage

1. Open index.html in browser
2. Paste Base64 text
3. Click Decode ✅
4. Copy decoded result

No installation required - works 100% in browser!

---

📱 Social Links

· 🔵 Facebook: https://www.facebook.com/md.norman.988
· 🟢 WhatsApp: https://whatsapp.com/channel/0029VbAkW0SATRSeAAYjNv1Z
· 🚀 Telegram: https://t.me/TNEHCHATGROUP

---

📄 License

MIT License - Free to use and modify

# base64_decoder.py

def generate_html():
    return '''
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Base64 Decoder - Noman</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: Arial; }
        body { background: #0a0a16; color: #00f7ff; padding: 20px; }
        .container { max-width: 800px; margin: 0 auto; }
        header { text-align: center; margin-bottom: 30px; }
        h1 { color: #00f7ff; margin: 20px 0; }
        .card { background: #1a1a2e; padding: 20px; border-radius: 10px; margin: 15px 0; border: 1px solid #00f7ff; }
        textarea { width: 100%; height: 100px; background: #16213e; color: white; border: 1px solid #00f7ff; padding: 10px; border-radius: 5px; }
        button { background: #00f7ff; color: #0a0a16; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; margin: 10px 5px; }
        .social { text-align: center; margin: 20px 0; }
        .social-btn { display: inline-block; padding: 10px 15px; margin: 5px; border-radius: 5px; color: white; text-decoration: none; }
        .fb { background: #3b5998; }
        .wa { background: #25D366; }
        .tg { background: #0088cc; }
        footer { text-align: center; margin-top: 30px; color: #666; }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🔓 Base64 & String Decoder</h1>
            <p>Built by <b>Noman</b> • Fast • Clean UI • 100% Free</p>
        </header>

        <div class="card">
            <h3>📥 Input Base64:</h3>
            <textarea id="inputText" placeholder="Paste Base64 string here...">SGVsbG8gV29ybGQh</textarea>
            <button onclick="decode()">🚀 Decode</button>
            <button onclick="clearText()">🗑️ Clear</button>
        </div>

        <div class="card">
            <h3>📤 Decoded Output:</h3>
            <div id="output" style="min-height: 50px; padding: 10px; background: #16213e; border-radius: 5px; color: white;">Hello World!</div>
            <button onclick="copyText()">📋 Copy Output</button>
        </div>

        <div class="social">
            <h3>🌍 Connect with Me:</h3>
            <a href="https://www.facebook.com/md.norman.988" target="_blank" class="social-btn fb">🔵 Facebook</a>
            <a href="https://whatsapp.com/channel/0029VbAkW0SATRSeAAYjNv1Z" target="_blank" class="social-btn wa">🟢 WhatsApp</a>
            <a href="https://t.me/TNEHCHATGROUP" target="_blank" class="social-btn tg">🚀 Telegram</a>
        </div>

        <footer>
            <p>© 2024 Base64 Decoder | Built with ❤️ by Noman</p>
        </footer>
    </div>

    <script>
        function decode() {
            let input = document.getElementById("inputText").value.trim();
            if (!input) {
                Swal.fire("Warning!", "Please enter Base64 text", "warning");
                return;
            }
            
            try {
                let decoded = atob(input);
                document.getElementById("output").innerText = decoded;
            } catch (e) {
                Swal.fire("Error!", "Invalid Base64 string!", "error");
            }
        }

        function copyText() {
            let output = document.getElementById("output").innerText;
            if (!output || output === "Hello World!") {
                Swal.fire("Warning!", "Nothing to copy!", "warning");
                return;
            }
            
            navigator.clipboard.writeText(output);
            Swal.fire("Success!", "Text copied to clipboard", "success");
        }

        function clearText() {
            document.getElementById("inputText").value = "";
            document.getElementById("output").innerText = "";
        }
    </script>
</body>
</html>
'''

# Save to file
with open('index.html', 'w', encoding='utf-8') as f:
    f.write(generate_html())

print("✅ Base64 Decoder generated as index.html")
print("📱 Social links added:")
print("   🔵 Facebook: https://www.facebook.com/md.norman.988")
print("   🟢 WhatsApp: https://whatsapp.com/channel/0029VbAkW0SATRSeAAYjNv1Z")
print("   🚀 Telegram: https://t.me/TNEHCHATGROUP")
```

---

Python Base64 Decoder (Command Line)

```python
# simple_base64_decoder.py
import base64
import sys

def decode_base64(encoded_text):
    """Decode Base64 string"""
    try:
        # Add padding if needed
        padding = 4 - len(encoded_text) % 4
        if padding != 4:
            encoded_text += "=" * padding
            
        decoded_bytes = base64.b64decode(encoded_text)
        decoded_text = decoded_bytes.decode('utf-8')
        return decoded_text
    except Exception as e:
        return f"❌ Error: {str(e)}"

def main():
    print("🔓 Base64 Decoder by Noman")
    print("=" * 30)
    
    while True:
        print("\nOptions:")
        print("1. Decode Base64")
        print("2. Exit")
        
        choice = input("\nEnter choice (1/2): ").strip()
        
        if choice == '1':
            encoded = input("Enter Base64 string: ").strip()
            if encoded:
                result = decode_base64(encoded)
                print(f"✅ Decoded: {result}")
            else:
                print("❌ Please enter a Base64 string")
        elif choice == '2':
            print("👋 Goodbye!")
            break
        else:
            print("❌ Invalid choice")

if __name__ == "__main__":
    main()
```

---

🚀 How to Use:

1. HTML ফাইল তৈরি করতে:

```bash
python base64_decoder.py
```

ফলে index.html ফাইল তৈরি হবে।

1. Python decoder টেস্ট করতে:

```bash
python simple_base64_decoder.py
```

1. README.md ফাইলটি GitHub এ আপলোড করুন

এখন আপনার Base64 Decoder সম্পূর্ণ তৈরি! আপনার সোশ্যাল লিংকগুলোও যোগ করা হয়েছে
