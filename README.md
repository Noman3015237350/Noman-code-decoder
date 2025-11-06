align="center">
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

https://github.com/Noman3015237350/Noman-code-decoder.git/

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
# readme_generator.py
import os

def generate_readme():
    project_name = input("Project Name: ").strip()
    description = input("Project Description: ").strip()
    author_name = input("Author Name: ").strip()
    
    github_link = input("GitHub Repo Link: ").strip()
    facebook_link = input("Facebook Link: ").strip()
    whatsapp_link = input("WhatsApp Link: ").strip()
    telegram_link = input("Telegram Link: ").strip()
    
    license_type = input("License (e.g., MIT, GPL): ").strip()
    
    add_badges = input("Do you want badges? (y/n): ").lower() == "y"
    add_preview = input("Do you want live preview / GIF screenshot section? (y/n): ").lower() == "y"

    readme_lines = []

    # Project Title
    readme_lines.append(f"# {project_name}\n")
    readme_lines.append(f"{description}\n")

    # Badges
    if add_badges:
        readme_lines.append("![GitHub stars](https://img.shields.io/github/stars/{0}) "
                            "![GitHub forks](https://img.shields.io/github/forks/{0}) "
                            "![GitHub issues](https://img.shields.io/github/issues/{0})\n".format(github_link.replace("https://github.com/", "")))

    # Table of Contents
    readme_lines.append("## 📂 Table of Contents\n"
                        "1. [Setup](#setup)\n"
                        "2. [Usage](#usage)\n"
                        "3. [Owner & Author](#owner--author)\n"
                        "4. [Social Links](#social-links)\n"
                        "5. [License](#license)\n"
                        "6. [Support](#support-the-project)\n")

    # Setup
    readme_lines.append("## ⚙️ Setup\n"
                        "```bash\n"
                        "# Clone repository\n"
                        f"git clone {github_link}\n\n"
                        "# Enter project folder\n"
                        f"cd {os.path.basename(github_link)}\n\n"
                        "# Open in browser\n"
                        "# Windows\n"
                        "start index.html\n"
                        "# Linux / Termux\n"
                        "xdg-open index.html\n"
                        "# Mac\n"
                        "open index.html\n"
                        "```\n")

    # Usage
    readme_lines.append("## 🧠 JavaScript Decoder Function (Core Logic)\n"
                        "```javascript\n"
                        "function decodeBase64() {\n"
                        "    var inputBase64 = document.getElementById(\"encodedText\").value.trim();\n"
                        "    try {\n"
                        "        var decoded = decodeURIComponent(escape(atob(inputBase64)));\n"
                        "        document.getElementById(\"outputText\").textContent = decoded;\n"
                        "    } catch (e) {\n"
                        "        Swal.fire(\"❌ Error!\", \"Invalid or non-Base64 string!\", \"error\");\n"
                        "    }\n"
                        "}\n"
                        "```\n")

    # Author
    readme_lines.append(f"## 👤 Owner & Author\n\n{author_name}\n\n")

    # Social Links
    readme_lines.append("## 🌎 Social Links\n\n"
                        "| Platform | Link |\n"
                        "|----------|------|\n"
                        f"| 🔵 Facebook | {facebook_link} |\n"
                        f"| 🟢 WhatsApp | {whatsapp_link} |\n"
                        f"| 🚀 Telegram | {telegram_link} |\n")

    # License
    readme_lines.append(f"## 📝 License\n\n✅ Free to use\n❌ Don't remove author credits without permission ({license_type})\n")

    # Support
    readme_lines.append("## ⭐ Support The Project\n\n"
                        "If you like this, give it a Star ⭐ on GitHub\n\n"
                        "```bash\n"
                        "git clone → modify → share → contribute ✅\n"
                        "```\n")

    # Preview/GIF
    if add_preview:
        readme_lines.append("## 💻 Live Preview / Screenshot\n\n"
                            "![Preview](link_to_preview.gif)\n")

    # Footer
    readme_lines.append("## 💬 Need help?\n"
                        f"Inbox: Telegram Group → {telegram_link}\n\n"
                        "Always learning, always building 🚀 — {0}".format(author_name))

    # Save README.md
    with open("README.md", "w", encoding="utf-8") as f:
        f.write("\n".join(readme_lines))

    print("✅ README.md generated successfully!")

if __name__ == "__main__":
    generate_readme()
