# 😈 GREMLIN — User Guide

How to install, start and use GREMLIN, your personal AI voice assistant for the desktop. Written for Windows 10/11.

**Contents**
1. [What GREMLIN is](#1-what-gremlin-is)
2. [What you need](#2-what-you-need)
3. [Install](#3-install)
4. [First launch](#4-first-launch)
5. [Tour of the screen](#5-tour-of-the-screen)
6. [Talking to GREMLIN](#6-talking-to-gremlin)
7. [The wake word](#7-the-wake-word)
8. [Everything GREMLIN can do](#8-everything-gremlin-can-do)
9. [Settings](#9-settings)
10. [Safety and undo](#10-safety-and-undo)
11. [Troubleshooting](#11-troubleshooting)
12. [Make it yours](#12-make-it-yours)
13. [Privacy and sharing](#13-privacy-and-sharing)
14. [Credits and licence](#14-credits-and-licence)

---

## 1. What GREMLIN is

GREMLIN is a voice assistant that runs as a desktop app. You talk, it talks back. It can also see your screen or webcam when you ask, and it can control your computer: open apps, change the volume, manage files, search the web, set reminders and more.

The voice and the thinking come from Google's **Gemini Live** service, so GREMLIN needs an internet connection and a Gemini API key (free to create).

**Cheat sheet**

| I want to… | Do this |
|---|---|
| Talk to it | Just speak. The microphone is open by default |
| Stop it mid-sentence | Press **Esc** or click **✋ INTERRUPT** |
| Mute my microphone | Press **F4** or click the microphone button |
| Go fullscreen | Press **F11** |
| Type instead of speak | Use the **COMMAND INPUT** box on the right |
| Give it a file | Drop it on **FILE UPLOAD**, then tell GREMLIN what to do with it |
| Change its name, voice or colour | **⚙ → ⚙ CUSTOMISE ASSISTANT** |
| Undo something it did | Say "undo" |

---

## 2. What you need

| Requirement | Details |
|---|---|
| Computer | Windows 10 or 11 (macOS and Linux also work, but this guide is for Windows) |
| Python | **3.11, 3.12 or 3.13** |
| Microphone and speakers | Both are required |
| Internet | Required. GREMLIN's voice runs on Gemini |
| Gemini API key | Free. Create one at <https://aistudio.google.com/app/apikey> |
| Graphics card | **Not needed.** The HUD is drawn in software |

The free Gemini plan has usage limits. When one model runs out, GREMLIN switches to a backup automatically, but a very heavy day can still hit the limit.

---

## 3. Install

1. **Install Python** from <https://www.python.org/downloads/>. During setup, tick **"Add python.exe to PATH"**.
2. **Get the GREMLIN folder** and put it somewhere easy, for example `C:\GREMLIN`.
3. **Open a terminal in that folder.** In File Explorer, click the address bar, type `cmd` and press Enter.
4. **Run the installer:**
   ```
   python setup.py
   ```
   It checks your Python version, installs every package GREMLIN needs, and downloads the browsers used for web control. This can take several minutes and a few hundred MB.
5. **Start GREMLIN:**
   ```
   python main.py
   ```

If setup says your Python is too old, install a version from 3.11 to 3.13 and run `py -3.12 setup.py` (use your version number).

If you see `ModuleNotFoundError: No module named 'xyz'` on launch, run `pip install xyz` and start again.

---

## 4. First launch

The first time, GREMLIN shows an **INITIALISATION REQUIRED** screen.

1. Paste your **Gemini API key** (it starts with `AIza`).
2. Check that the **operating system** shown is correct. It is detected automatically.
3. Click **▸ INITIALISE SYSTEMS**.

GREMLIN connects, and the activity log shows **GREMLIN online**. Say hello.

Your key is saved in `config/api_keys.json`. It is stored as plain text, so treat that file like a password.

**Recommended next step:** click **⚙**, then **⚙ CUSTOMISE ASSISTANT** to set your own name, a voice and a colour (see [Settings](#9-settings)).

---

## 5. Tour of the screen

| Area | What it is |
|---|---|
| **Centre** | The GREMLIN logo. It breathes while idle and pulses with the voice. The word under it shows the state: listening, thinking, speaking or muted. Videos you ask for also play here |
| **Left: SYS MONITOR** | Live CPU, memory, network, GPU and temperature, plus uptime, process count and OS. GPU and temperature show N/A if your PC doesn't report them |
| **Right: ACTIVITY LOG** | Everything said and done: what you said, what GREMLIN answered, tool actions and system messages |
| **Right: FILE UPLOAD** | Drop a file here (or click to browse) so GREMLIN can work on it |
| **Right: COMMAND INPUT** | Type a command or question and press Enter or **▸** |
| **✋ INTERRUPT [ESC]** | Stops GREMLIN talking right away |
| **🎙 MICROPHONE ACTIVE / 🔇 MICROPHONE MUTED** | Click to mute or unmute (F4) |
| **⚙ button (top left)** | Opens the **SETUP** drawer |
| **🎛 button (top left)** | Opens the **CONTROLS** drawer |
| **Top right** | Clock and date |
| **Bottom bar** | Reminds you: **[F4] Mute · [F11] Fullscreen** |

**Why is my microphone not picking me up?** Check the bottom button. If it says MICROPHONE MUTED, press F4.

---

## 6. Talking to GREMLIN

Speak naturally. You don't need a special syntax, and you can use any language; GREMLIN answers in the language you used last.

**Keyboard shortcuts**

| Key | What it does |
|---|---|
| **F4** | Mute or unmute the microphone |
| **F11** | Fullscreen on or off |
| **Esc** | Interrupt GREMLIN while it is speaking |
| **Ctrl + Space** (hold) | Talk, when **push-to-talk** is switched on. The microphone is closed unless you hold it |

**Good habits**
- Say the whole request at once: "Open Chrome and search for Lagos weather."
- You can give two tasks in one go. GREMLIN does them in the order you said.
- GREMLIN doesn't hear you while the microphone is muted, and it can't unmute itself.
- It only sees your screen or webcam when you ask it to look. Say "what's on my screen?".
- It stays quiet if it thinks you're talking to someone else in the room.

**Typing** works too. Use the COMMAND INPUT box. Typed commands are ignored while GREMLIN is asleep (see the next section).

---

## 7. The wake word

The wake word keeps GREMLIN asleep until you call it. It is optional and **off by default**, so GREMLIN listens all the time until you switch it on.

**Turn it on**
1. Click **🎛** to open the CONTROLS drawer.
2. Click **WAKE WORD**. The first time it says **⬇ WAKE WORD: DOWNLOAD**. Click it and wait; this downloads a small model once, a few MB, and works fully offline afterwards.
3. Click it again to switch it **ON**.

**Using it**
- While asleep, GREMLIN's microphone does not stream anything to the internet, and the HUD shows it sleeping.
- Say the wake phrase to wake it, or click **👂 WAKE NOW**.
- It goes back to sleep after **2 minutes of silence**, or when you click **😴 SLEEP NOW**.

**Which phrase works?**
The phrase is **"Hey Gremlin"**, but it needs a custom model file:

```
core/wake_models/hey_gremlin.onnx
```

- **With that file in place**, say **"Hey Gremlin"**. The log shows: *listening for 'Hey Gremlin'*.
- **Without it**, GREMLIN falls back to the built-in model and responds to **"Hey Jarvis"** instead. The log shows: *'Hey Gremlin' model not loaded — listening for 'Hey Jarvis' instead*.

The `.onnx` file has to be trained, because the wake-word library doesn't ship a "Gremlin" model. The openWakeWord project provides a free Colab notebook for this. Create the folder `core/wake_models` if it doesn't exist, put the file inside with exactly that name, and restart GREMLIN.

If it wakes by accident or misses you, tell whoever set it up. It has one sensitivity number in `core/wake_word.py` (`DEFAULT_THRESHOLD`, default 0.5).

---

## 8. Everything GREMLIN can do

You don't call these by name. Just ask in plain language and GREMLIN picks the right one. Example phrases are only suggestions.

### Your computer

| Ability | What it does | Try saying |
|---|---|---|
| **Open apps** | Launches an application, from a built-in list of common ones (Chrome, Edge, Spotify, VS Code, Word, Excel, Notepad, Calculator, Task Manager, Steam…) | "Open Spotify" |
| **Computer settings** | Volume (up, down, set, mute), brightness, window snapping, minimise, maximise, switch window, show desktop, close app or window, tabs, zoom, scrolling, copy and paste, dark mode, screenshot, lock screen, open Settings, File Explorer, Run | "Turn the volume up", "Take a screenshot" |
| **Power and Wi-Fi** | Restart, shutdown and Wi-Fi toggle. **These need you to press CONFIRM on screen** | "Restart the computer" |
| **Keyboard and mouse** | Types text, clicks, double and right click, hotkeys, scroll, move the mouse, copy and paste, finds things on screen | "Type my email address", "Click the Start button" |
| **Desktop** | Set the wallpaper from a file or a link, show the current wallpaper, organise the Desktop by file type or date, clean it, list its contents, show stats | "Change my wallpaper to this image" |
| **System status** | CPU, memory and other live numbers | "How is my computer doing?" |

### Files

| Ability | What it does | Try saying |
|---|---|---|
| **Files and folders** | List, create files and folders, delete (to the Recycle Bin), move, copy, rename, read, write, find by name or extension, largest files, disk usage, organise the Desktop. Works inside your user folder only | "Find all PDFs in Downloads", "Create a folder called Projects on the Desktop" |
| **Files you drop in** | Work on a file you dropped on **FILE UPLOAD**. Images (describe, read text, resize, compress, convert), PDFs (summarise, extract text, convert to Word), Word and text files (summarise, fix, reformat), CSV and Excel (analyse, filter, sort), JSON and XML, code (explain, review) | Drop a PDF, then say "Summarise this" |

### The web

| Ability | What it does | Try saying |
|---|---|---|
| **Web search** | Looks things up. Modes: search, news, research (deep answer), price, compare | "What's the latest news on AI?", "Compare the iPhone and Pixel" |
| **Browser control** | Opens sites and searches in your own browser. For clicking, typing and filling forms it uses an automation browser. Works with Chrome, Edge, Firefox, Opera, Brave, Vivaldi and Safari | "Open YouTube in Chrome", "Search Google for cheap flights" |
| **Weather** | Opens the weather for a city | "What's the weather in Lagos?" |
| **Flights** | Searches Google Flights and reads out the best options | "Find flights from Lagos to London on Friday" |

### Video

| Ability | What it does | Try saying |
|---|---|---|
| **Play on the HUD** | Plays a video in the centre of GREMLIN itself, from a YouTube link, a search description, a local file or a direct URL. It starts **muted** every time | "Play the new Dune trailer", then "Unmute" or "Stop the video" |
| **YouTube** | Play, summarise a video from its transcript, get video info, show trending | "Summarise this YouTube video" |

If you want a video to open **in the browser** on YouTube instead, say so explicitly: "Open it on YouTube".

### Time and messages

| Ability | What it does | Try saying |
|---|---|---|
| **Reminders** | Sets a timed notification using Windows Task Scheduler | "Remind me at 6 pm to call Mum" |
| **Messages** | Sends a message through WhatsApp, Telegram or another app. In this build it works by typing into the desktop app, so **check the result**, and don't use it for anything important unattended | "Send a WhatsApp to Ada saying I'm on my way" |
| **Topic watching** | Checks the news about topics you choose once a day and tells you when something new comes up | "Monitor space exploration" |

### Code and games

| Ability | What it does | Try saying |
|---|---|---|
| **Code helper** | Writes, edits, explains and runs code files | "Write a Python script that renames photos by date" |
| **Project builder** | Plans and builds a whole multi-file project, installs what it needs, opens VS Code, runs it and fixes errors. Projects go to `Desktop\GremlinProjects` | "Build a to-do list web app" |
| **Games** | Steam and Epic Games: install, update, list installed games, check download status, schedule updates | "Update all my Steam games at 3 am" |

### Seeing and remembering

| Ability | What it does | Try saying |
|---|---|---|
| **Vision** | Looks at your screen or your webcam, only when you ask. Closes the camera when done | "What's on my screen?", "Look at me and tell me how many fingers I'm holding up" |
| **Memory** | Remembers facts you tell it (your name, preferences, projects) and looks them up later. See everything it knows in **⚙ → 🧠 MEMORY**, where you can delete any item | "Remember that my sister is called Ada" |
| **Undo** | Reverses its own last change: files moved, renamed, created or written, and volume, brightness or dark mode | "Undo that", "What can you undo?" |

### Things it does by itself

| Feature | What happens |
|---|---|
| **Morning briefing** | Once each time you start GREMLIN (when it is awake), it greets you, tells you the time, mentions your last conversation if there was one, and reads out a top headline. Switch it off with **☀ MORNING BRIEF** in 🎛 |
| **Proactive check-ins** | If you've been quiet for about 15 minutes, GREMLIN may say something short and useful. It waits at least 20 minutes between check-ins |
| **Hardware alerts** | It warns you out loud when CPU or memory stay above 90%, temperature goes above 85 °C, or GPU goes above 95% |
| **Clipboard helper** | When you copy text, a small panel offers **TRANSLATE**, **SUMMARISE**, **EXPLAIN** and **FIX** (grammar and spelling) |

### Plugins

Drop a single `.py` file into the `plugins` folder and GREMLIN learns a new skill the next time it starts. Use `plugins/_template.py` as a starting point. See which are loaded in **⚙ → 🧩 PLUGINS**; settings for plugins that have them are under **⚙ PLUGIN SETTINGS**.

### Control it from your phone

1. Click **⚙**, then **◉ REMOTE CONTROL**.
2. Scan the QR code with your phone camera (or type the address and key shown on screen).
3. Your phone becomes a remote chat with GREMLIN.

Your phone must be able to reach your PC, normally the same Wi-Fi. The connection uses a certificate GREMLIN makes itself, so your phone's browser warns you the first time. Accept it once.

---

## 9. Settings

### ⚙ SETUP drawer (things you set once)

| Button | What it does |
|---|---|
| **◉ REMOTE CONTROL** | Pair your phone (see above) |
| **⊞ CREATE DESKTOP SHORTCUT** | Puts a GREMLIN shortcut on your Desktop, with the gremlin icon |
| **◉ AUTO-START: OFF / ON** | Starts GREMLIN when you log in to Windows |
| **⚙ CUSTOMISE ASSISTANT** | Name, your name, voice, colour |
| **🎧 AUDIO DEVICES** | Choose which microphone and speakers to use |
| **🧠 MEMORY** | See and delete what GREMLIN has remembered |
| **🧩 PLUGINS** | See the loaded plugins |
| **⚙ PLUGIN SETTINGS** | Settings for plugins that have them |

### 🎛 CONTROLS drawer (things you flick every day)

| Button | What it does |
|---|---|
| **⛶ FULLSCREEN [F11]** | Fullscreen on or off |
| **☀ MORNING BRIEF: ON / OFF** | The greeting and headline at start-up |
| **🎙 WAKE WORD: ON / OFF** | Sleep until the wake phrase (see section 7) |
| **👂 WAKE NOW / 😴 SLEEP NOW** | Wake or sleep GREMLIN by hand (when wake word is on) |
| **🎚 PUSH-TO-TALK** | When on, the mic is only open while you hold **Ctrl + Space** |
| **HUD** | Cycles the centre image: **GREMLIN LOGO → ANIMATED FACE → REACTOR CORE** |

Only one drawer is open at a time.

### ⚙ CUSTOMISE ASSISTANT

| Field | Notes |
|---|---|
| **ASSISTANT NAME** | What it calls itself and what the HUD shows. Default: **GREMLIN** |
| **YOUR NAME** | What it calls you. Leave blank and it uses a respectful "sir" in English or its everyday equivalent in other languages |
| **ASSISTANT VOICE** | Charon (default), Puck, Kore, Fenrir or Aoede. The change applies live |
| **UI COLOUR** | Drag the handle, or type a hex colour like `#00d4ff`. **DEFAULT** resets it |

Click **▸ APPLY CHANGES** to save, or **CANCEL**.

### Advanced options in `config/api_keys.json`

These are optional. Close GREMLIN before editing the file, and keep it valid JSON (commas, quotes).

| Key | Default | Meaning |
|---|---|---|
| `assistant_name` | `"GREMLIN"` | Assistant name |
| `user_name` | blank | How it addresses you |
| `voice_name` | `"Charon"` | Charon, Puck, Kore, Fenrir or Aoede |
| `hud_style` | `"logo"` | `logo`, `face` or `core` |
| `wake_word_enabled` | `false` | Wake word on or off |
| `push_to_talk_enabled` | `false` | Hold-to-talk on or off |
| `morning_brief_enabled` | `true` | Morning briefing |
| `proactive_audio` | `true` | Stays quiet when speech isn't aimed at it. Turn **off** if replies seem to arrive one sentence late |
| `thinking_enabled` | `false` | Lets the model "think" before answering. Smarter, slower |
| `media_resolution` | `"medium"` | Detail of screenshots and camera frames: `default`, `low`, `medium` or `high` |
| `input_device` / `output_device` | `""` (system default) | Saved microphone and speaker names |
| `ui_color` | blank | Hex colour |
| `gemini_api_key` | — | Your key |

---

## 10. Safety and undo

- **Restart, shutdown and Wi-Fi** never happen on GREMLIN's say-so alone. A **CONFIRM / CANCEL** banner appears on screen and nothing happens until *you* press CONFIRM. The banner disappears after 90 seconds.
- **Deleting a file** sends it to the **Recycle Bin**, so you can get it back.
- **File actions** only work inside your user folder (`C:\Users\<you>`).
- **Undo** reverses the most recent file or settings change. Say "undo", or "what can you undo?".
- GREMLIN stays quiet about anything it can't do, and says so instead of pretending.

---

## 11. Troubleshooting

| Problem | What to try |
|---|---|
| **The setup screen appears again** | `config/api_keys.json` is missing or has no key. Enter the key again |
| **"API key invalid"** | GREMLIN asks you to enter the key again. Create a fresh one at aistudio.google.com |
| **"Connection failed — retrying"** | No internet, or Gemini is blocked on your network (the message says a VPN may be required). It retries by itself |
| **It doesn't hear me** | Is it muted (bottom button, F4)? Is wake word on and GREMLIN asleep? Open **⚙ → 🎧 AUDIO DEVICES** and pick your microphone |
| **I can't hear it** | **⚙ → 🎧 AUDIO DEVICES**, choose your speakers, then **▸ APPLY** |
| **It says "I'm asleep"** | Wake word is on. Say the wake phrase or click **👂 WAKE NOW** |
| **"Hey Gremlin" does nothing** | The model file isn't installed yet. Say **"Hey Jarvis"** or click WAKE NOW (see section 7) |
| **WAKE WORD says DOWNLOAD** | Click it once and wait for the one-time download |
| **I see the reactor core, not the logo** | `assets/gremlin_logo.png` is missing or in the wrong folder, or the HUD button is set to another style |
| **A video plays with no sound** | It always starts muted. Say "unmute" or click **🔊 SOUND ON** on the video |
| **It says it can't see my screen** | It only looks when asked. Say "look at my screen" |
| **Phone can't connect** | Run GREMLIN as **Administrator** once (so Windows can open the firewall port), make sure both devices are on the same network, accept the certificate warning, and press **◉ REMOTE CONTROL** again for a fresh code |
| **`ModuleNotFoundError`** | `pip install <name from the error>` |
| **Anything strange after an update** | Close GREMLIN, delete the `__pycache__` folders, start again |

**Starting fresh**
- Forget settings and key: delete `config/api_keys.json`.
- Forget everything it knows about you: delete `memory/long_term.json`, or use **⚙ → 🧠 MEMORY**.

---

## 12. Make it yours

**Rename it (easy).** Open **⚙ → ⚙ CUSTOMISE ASSISTANT**, type a new **ASSISTANT NAME** and click **▸ APPLY CHANGES**. The HUD, the title and what the assistant calls itself all update straight away.

**Recolour it.** Same panel: pick a colour with the handle or type a hex code.

**Change the logo.** Replace `assets/gremlin_logo.png` with your own picture (a square image on a black background works best, and the black becomes see-through). Restart GREMLIN.

**Change its personality.** Open `core/prompt.txt`. It's plain English. The `[VOICE]` section describes how it speaks. Keep the `{curly-brace}` words exactly as they are, and keep the `[TAGGED MESSAGES]` section, because the program relies on them.

**Add skills.** Drop a plugin into the `plugins` folder (see `plugins/_template.py`).

**Rename it everywhere in the files.** A full find-and-replace in a code editor works, but some names are shared between files (for example the shutdown tool name in `main.py` and `core/prompt.txt`, and the dashboard's stored keys). Change them in **every** file together, or the matching breaks.

---

## 13. Privacy and sharing

**What leaves your PC**
- While GREMLIN is awake, your voice, and any screenshot or camera frame you ask it to look at, is sent to Google's Gemini service. While it is asleep (wake word on), nothing is streamed.
- Searches, YouTube and flights use the normal internet.

**What stays on your PC**
- `config/api_keys.json`: your key and settings (plain text).
- `memory/long_term.json`: what it remembers about you.
- `config/certs/`: the phone-dashboard certificate and private key.

**If you give GREMLIN to someone else, delete these first**
- `config/api_keys.json` (it holds **your** API key)
- `memory/long_term.json`
- `config/certs/` and `config/whatsapp_web/` (if they exist)
- All `__pycache__` folders

Each person then enters their **own** free Gemini key the first time they start it.

---

## 14. Credits and licence

**Rebranded & Customized by GREMLIN.**

GREMLIN is based on the open-source *Mark LV* project by FatihMakes, released under **Creative Commons Attribution-NonCommercial 4.0 (CC BY-NC 4.0)**. That means you may use and modify it for personal and non-commercial purposes, you must keep the credit to the original author, and you may not sell it. See the `LICENSE` file.
