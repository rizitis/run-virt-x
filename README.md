# 🏃‍♂️-virt-x

`🏃‍♂️-virt-x` is a lightweight 🖥️📜 to 🏃 apps in a 🖼️ X 🌍 (`Xvfb`) on 🐧 Slackware. This 📜 cleans stale X ⚙️, starts a 🆕 `Xvfb` ⚙️, & runs the 🏁 app in the 🖼️ display 🌍.

## ✨ Features

- **🧹 Auto-Cleanup**: Stops active X ⚙️ on the chosen display.
- **🚮 Resource 🧹**: Clears `.X<DISPLAY>-lock` & `/tmp/.X11-unix/X<DISPLAY>` 🗂️.
- **📝 Error Logging**: Logs 🛑s to a 📂.
- **🔢 Custom Display**: Run 🖥️ on various 🌍s.
- **🤝 Graceful Exit**: Ends `Xvfb` post-app exit.

---

## 📋 Requirements

- `Xvfb` must exist 🛠️.
- 📦-free 📜 since Slackware 🐧 all ⚒️.

---

## 🛠️ Install

1️⃣ Move `🏃‍♂️-virt-x` 📜 to `/usr/local/bin`:
   ```bash
   cp 🏃‍♂️-virt-x.sh /usr/local/bin/🏃‍♂️-virt-x
   chmod +x /usr/local/bin/🏃‍♂️-virt-x
   ```

2️⃣ Confirm `Xvfb` is 🐧:
   ```bash
   slackpkg install xvfb
   ```

---

## 🖱️ Usage

```bash
🏃‍♂️-virt-x [🔧] -- 🖥️ [🎛️]
```

### 🔧 Options:

- `-n NUM`, `--server-num=NUM`: Set X display 🌍 (`99`).
- `-e FILE`, `--error-file=FILE`: Send 🛑s to (`/tmp/xvfb.log`).
- `-h`, `--help`: 📖 usage & 🛑.

### Examples:

1️⃣ **🏃 Firefox on `:101`**:
   ```bash
   🏃‍♂️-virt-x -n 101 -- firefox
   ```

2️⃣ **🏃 VLC on 🚀**:
   ```bash
   🏃‍♂️-virt-x -- vlc
   ```

3️⃣ **🔍 🛑s in `/tmp/xvfb.log`**:
   ```bash
   cat /tmp/xvfb.log
   ```

---

## ⚙️ How It Works

1️⃣ **X ⚙️ Check**:
   - Stops 🏃⚙️ on 🌍, clears `.X<DISPLAY>-lock` & `/tmp/.X11-unix/X<DISPLAY>`.

2️⃣ **Start `Xvfb`**:
   - Boots virtual 🖥️ `Xvfb`.
   - 📝 outputs 🛑 to 🔍.

3️⃣ **Run App**:
   - Exports `DISPLAY`.
   - 🏃 user 🎛️.

4️⃣ **🧹 Cleanup**:
   - Ends `Xvfb` post-app & removes 🚮.

---

## 🛠️ Troubleshooting

1️⃣ **Server 🛑**
   - ❌ = 🖥️ conflict. Verify:
     ```bash
     ps aux | grep Xvfb
     kill <PID>
     rm -f /tmp/.X<DISPLAY>-lock
     rm -f /tmp/.X11-unix/X<DISPLAY>
     ```

2️⃣ **`Xvfb` Launch Fail**
   - 🔍 `/tmp/xvfb.log` 🛑.
   - Ensure `Xvfb` 🛠️.

---

## 🪪 License

🎁 [unlicense](https://unlicense.org). ⚠️ No ⛑️.

---

## ✍️ Author

✒️ For 🐧 Slackware fans 🛠️ stable graphical X ⚙️s.

---

