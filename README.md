# 💬 Chit Chat CLI

A robust, secure, and colorful command-line chat application developed in C++. This project demonstrates the practical application of **Object-Oriented Programming (OOP)**, **File Handling**, and **Data Encryption** in a Windows environment.

---

## 👥 Contributors
- **Adeel Abbasi** – Project Lead, File Handling & Overall Architecture  
- **Wahab** – Encryption & Security Module  
- **Haseeb** – Chat Interface & Message Rendering  
- **Raja Tayyab** – Home Screen & Directory Setup  

---

## 📄 Description
**Chit Chat CLI** is designed to provide a secure messaging experience through a terminal interface. It features a custom encryption engine to ensure that user credentials and private conversations remain protected even if the raw data files are accessed.

---

## 🌟 Features
- ✅ **Secure Authentication:** User registration and login system.  
- ✅ **Private Messaging:** Direct peer-to-peer chat functionality.  
- ✅ **Data Privacy:** All messages and passwords are saved using a Caesar-based encryption algorithm.  
- ✅ **Persistent Storage:** Chat history is automatically saved to local text files.  
- ✅ **Dynamic UI:** Colorful and boxed layouts using the Windows API for a modern terminal feel.  
- ✅ **Auto-Folder Management:** Automatically creates a `ChatData/` directory on the first run.

---

## ⚙️ Requirements
- Windows OS (relies on `windows.h`, `SetConsoleTextAttribute`, and `_mkdir`)  
- A C++ compiler that supports C++11 or later (e.g., MinGW, MSVC)  
- No external libraries required

---

## ⚙️ Installation & Running

### Clone the repository
```bash
git clone https://github.com/adeelabbasi111/Chit-Chat-CLI.git
cd Chit-Chat-CLI
```

### Build (example with MinGW/g++)
```bash
g++ -std=c++11 -o chit_chat.exe main.cpp
```

### Run
```bash
./chit_chat.exe
```

Notes:
- The program will create a `ChatData/` folder automatically if it doesn't exist.
- `users.txt` is created/used to store registered users (encrypted).

---

## 🗂️ Project Structure
```
ChitChatCLI/
│
├── main.cpp            # Core logic, classes, and main entry point
├── users.txt           # Encrypted database of user credentials (created at runtime)
├── ChatData/           # Directory containing peer-to-peer chat logs (created at runtime)
│   ├── userA_userB.txt # Encrypted conversation between two users
│   └── ...
└── README.md           # Project documentation
```

---

## 🛠️ Technical Details

### 🔒 Encryption Module (author: Wahab)
- Uses a simple shifting algorithm (Caesar-like) over printable ASCII (characters 32–126) with a fixed shift (secret_code = 6).
- Provides basic obfuscation for on-disk data (not cryptographically secure).
- Used for encrypting usernames, passwords, and chat messages stored in files.

### 🎨 UI & UX Styling
The application uses Windows console color codes to improve user experience:
- Cyan (11): Headers and boxed UI
- Light Green (10): Messages sent by the current user (You)
- Yellow (14): Incoming messages from the recipient
- Red (12): Errors and invalid inputs

---

## 💡 How to Use
1. Launch the program and choose:
   - `1. Login` — to log in with existing credentials
   - `2. Register` — to create a new account
   - `3. Exit` — to quit
2. To register:
   - Choose `2`, provide `Username`, `Password`, and `Confirm Password`.
   - On success, you will be taken to the chat screen.
3. To log in:
   - Choose `1`, provide `Username` and `Password`.
   - On success, a list of users will be shown.
4. Chat:
   - Select a user number to open the chat with them.
   - Type a message and press Enter to send.
   - Type `exit` to return to the user selection screen.
5. Data files:
   - `users.txt` — encrypted username and password pairs (space-separated).
   - `ChatData/<userA>_<userB>.txt` — encrypted messages with `encryptedSender|encryptedText` per line.

---

## 🔧 Known Limitations
- Windows-only due to `windows.h` usage and `_mkdir`.
- Single-machine local chat (no networking).
- Simple encryption — not suitable for production use with sensitive data.
- No concurrency control — simultaneous edits to chat files may cause issues.
- Usernames with special characters may cause file naming issues.

---

## 🧭 Suggested Improvements
- Add secure password hashing (bcrypt, Argon2) for stored passwords.
- Use proper authenticated encryption for message storage if stronger privacy is required.
- Add timestamps to messages and optionally show them in the UI.
- Split code into headers and source files for better modularity and maintainability.
- Create cross-platform build options (remove or wrap Windows-specific calls).
- Add unit tests and CI to ensure reliability.
- Implement network mode (server/client) for real-time chat across machines.

---

## 📦 License
This project is open-source and free to use for educational purposes. 
