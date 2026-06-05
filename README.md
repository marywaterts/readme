# 📧 Gmail Dot Generator Bot

Bot Telegram untuk generate variasi alamat Gmail menggunakan **Gmail Dot Trick**. Semua variasi email yang dihasilkan akan masuk ke inbox yang sama!

[![Python Version](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Telegram Bot](https://img.shields.io/badge/Telegram-Bot-blue.svg)](https://t.me/YourBotUsername)

---

## 🌟 Fitur Utama

- ✨ **Single Generation** - Generate variasi untuk 1 email
- 📦 **Bulk Generation** - Process hingga 10 email sekaligus
- 💾 **Export Files** - Download hasil dalam format TXT, CSV, atau ZIP
- 🚀 **Multi-User Support** - Bot bisa dipakai banyak user bersamaan
- 🔒 **Privacy Focused** - Tidak menyimpan data user secara permanen
- ⚡ **Fast & Efficient** - Generate ratusan variasi dalam hitungan detik

---

## 📋 Apa itu Gmail Dot Trick?

Gmail mengabaikan titik (.) dalam username email. Artinya:

```
john.doe@gmail.com
johndoe@gmail.com
j.o.h.n.d.o.e@gmail.com
```

**Semuanya adalah EMAIL YANG SAMA!** ✅

### 🎯 Kegunaan:

- 🔍 **Filter Email** - Buat filter otomatis berdasarkan variasi
- 🕵️ **Track Email Leaks** - Identifikasi siapa yang jual/bocorkan email Anda
- 📝 **Multiple Accounts** - Daftar di website yang butuh unique email
- 📊 **Email Analytics** - Track dari mana email masuk

---

## 🚀 Quick Start

### Prerequisites

- Python 3.9 atau lebih baru
- Telegram Bot Token dari [@BotFather](https://t.me/BotFather)

### Installation

1. **Clone Repository**
```bash
git clone https://github.com/yourusername/gmail-dot-bot.git
cd gmail-dot-bot
```

2. **Install Dependencies**
```bash
pip install -r requirements.txt
```

3. **Setup Environment Variables**
```bash
# Copy template .env
cp .env.example .env

# Edit .env dan isi BOT_TOKEN
nano .env
```

4. **Run Bot**
```bash
python bot.py
```

Bot akan running dan siap menerima requests! 🎉

---

## 📁 Project Structure

```
gmail-dot-bot/
├── bot.py              # Main entry point
├── handlers.py         # Command & callback handlers
├── generator.py        # Dot variation algorithm
├── validator.py        # Email validation
├── keyboards.py        # Inline keyboard layouts
├── exporter.py         # File export (TXT/CSV/ZIP)
├── utils.py            # Helper functions
├── config.py           # Configuration & settings
├── requirements.txt    # Python dependencies
├── .env                # Environment variables (create this!)
├── .env.example        # Template for .env
├── .gitignore          # Git ignore rules
└── README.md           # Documentation (you're here!)
```

---

## 🎮 Usage Guide

### Command List

| Command | Description |
|---------|-------------|
| `/start` | Mulai bot dan tampilkan main menu |
| `/generate` | Shortcut ke single generation mode |
| `/bulk` | Shortcut ke bulk generation mode |
| `/help` | Panduan lengkap cara pakai |
| `/about` | Informasi tentang Gmail dot trick |
| `/cancel` | Batalkan operasi yang sedang berjalan |

### Single Mode Flow

1. Klik **"Generate Single"** atau ketik `/generate`
2. Kirim alamat Gmail Anda (contoh: `john@gmail.com`)
3. Bot akan generate semua variasi possible
4. Pilih **Export TXT** atau **Export CSV** untuk download

### Bulk Mode Flow

1. Klik **"Generate Bulk"** atau ketik `/bulk`
2. Kirim multiple emails (satu per baris, max 10)
3. Bot akan process semua email dengan progress bar
4. Download hasil dalam **ZIP file**

### Example Input/Output

**Input:**
```
john@gmail.com
```

**Output (8 variations):**
```
1. john@gmail.com
2. j.ohn@gmail.com
3. jo.hn@gmail.com
4. joh.n@gmail.com
5. j.o.hn@gmail.com
6. j.oh.n@gmail.com
7. jo.h.n@gmail.com
8. j.o.h.n@gmail.com
```

---

## ⚙️ Configuration

Edit `config.py` untuk customize settings:

```python
# Limits
MAX_BULK_EMAILS = 10              # Max emails per bulk request
MAX_VARIATIONS_DISPLAY = 20       # Max variations di chat
MAX_USERNAME_LENGTH = 30          # Max Gmail username length
MIN_USERNAME_LENGTH = 3           # Min Gmail username length

# File Settings
EXPORT_DIR = 'exports/'           # Directory untuk export files
FILE_RETENTION_HOURS = 1          # Auto-delete setelah 1 jam

# Rate Limiting
MAX_REQUESTS_PER_MINUTE = 10      # Max requests per user per menit
MAX_BULK_PER_5MIN = 3             # Max bulk requests per 5 menit
```

---

## 🔐 Security & Privacy

- ✅ **No Data Storage** - Email tidak disimpan secara permanen
- ✅ **Auto Cleanup** - Export files dihapus otomatis setelah 1 jam
- ✅ **In-Memory Sessions** - Semua processing di memory
- ✅ **Input Validation** - Strict validation untuk prevent injection
- ✅ **Rate Limiting** - Protect dari spam/abuse

---

## 🧮 Algorithm Explanation

Bot menggunakan **binary pattern algorithm** untuk generate variasi:

```
Username: "john" (4 characters)
Formula: 2^(n-1) = 2^(4-1) = 8 variations

Binary Pattern → Email Variation
000 → john@gmail.com
001 → joh.n@gmail.com
010 → jo.hn@gmail.com
011 → jo.h.n@gmail.com
100 → j.ohn@gmail.com
101 → j.oh.n@gmail.com
110 → j.o.hn@gmail.com
111 → j.o.h.n@gmail.com
```

**Complexity:** O(2^n) where n = username length

---

## 📊 Performance

- **Generate Speed:** ~10,000 variations per second
- **Max Variations:** Limited to 100 per email (prevent spam)
- **Concurrent Users:** Unlimited (session-based isolation)
- **Memory Usage:** ~50MB for typical workload

---

## 🐛 Troubleshooting

### Bot tidak respond?

1. Check BOT_TOKEN di `.env` file
2. Check internet connection
3. Check logs di `bot.log`

### Error "Invalid email format"?

- Hanya @gmail.com yang didukung
- Username min 3 karakter
- Username hanya boleh huruf dan angka

### File export gagal?

- Check directory `exports/` exists
- Check disk space available
- Check file permissions

---

## 🛠️ Development

### Setup Development Environment

```bash
# Create virtual environment
python -m venv venv

# Activate venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Run bot
python bot.py
```

### Testing Checklist

- [ ] Test `/start` command
- [ ] Test single generation dengan email valid
- [ ] Test single generation dengan email invalid
- [ ] Test bulk generation (1-10 emails)
- [ ] Test export TXT, CSV, ZIP
- [ ] Test session timeout & cleanup
- [ ] Test concurrent users (min 5 users)
- [ ] Test cancel operation di setiap state

---

## 📝 Deployment

### Deploy ke VPS (Ubuntu/Debian)

```bash
# 1. Install Python 3.9+
sudo apt update
sudo apt install python3 python3-pip

# 2. Clone project
git clone https://github.com/yourusername/gmail-dot-bot.git
cd gmail-dot-bot

# 3. Install dependencies
pip3 install -r requirements.txt

# 4. Setup .env
nano .env
# Paste BOT_TOKEN

# 5. Run dengan screen/tmux
screen -S gmail-bot
python3 bot.py
# Ctrl+A+D untuk detach

# 6. Optional: Setup systemd service
sudo nano /etc/systemd/system/gmail-bot.service
```

### Systemd Service Template

```ini
[Unit]
Description=Gmail Dot Generator Bot
After=network.target

[Service]
Type=simple
User=yourusername
WorkingDirectory=/path/to/gmail-dot-bot
ExecStart=/usr/bin/python3 /path/to/gmail-dot-bot/bot.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```bash
# Enable & start service
sudo systemctl enable gmail-bot
sudo systemctl start gmail-bot
sudo systemctl status gmail-bot
```

---

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot) - Awesome Telegram Bot framework
- [Gmail Dot Trick](https://support.google.com/mail/answer/7436150) - Official Gmail documentation

---

## 📞 Contact & Support

- **Telegram:** [@YourTelegramUsername](https://t.me/YourTelegramUsername)
- **Issues:** [GitHub Issues](https://github.com/yourusername/gmail-dot-bot/issues)
- **Email:** your.email@gmail.com

---

## 📈 Roadmap

- [ ] Add pagination untuk hasil > 100 variations
- [ ] Support Google Workspace custom domains
- [ ] Add database support (PostgreSQL/MongoDB)
- [ ] Web dashboard untuk analytics
- [ ] Multi-language support (EN, ID, etc)
- [ ] API endpoint untuk integration

---

## ⚠️ Disclaimer

Bot ini dibuat untuk tujuan **edukasi dan productivity**. Penggunaan untuk spam, fraud, atau aktivitas ilegal **DILARANG KERAS**. Developer tidak bertanggung jawab atas penyalahgunaan bot ini.

Gmail Dot Trick adalah fitur resmi Gmail dan 100% legal untuk digunakan.

---

<div align="center">

**Made with ❤️ by [Your Name](https://github.com/yourusername)**

⭐ Star this repo if you find it useful!

</div>
