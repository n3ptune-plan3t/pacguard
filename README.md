# pacguard

Meet **pacguard** — yes, it's pacman with a guard.  
Think of it as your package bodyguard, checking if anything in your Arch Linux system has known vulnerabilities.  

This tool is inspired by the idea behind `arch-audit`, but written simply in Python. I built it to learn, to share, and hopefully to help others keep their systems a little more secure.  

---

## Why?

Arch Linux is fast, rolling, and bleeding edge. But with speed comes the chance of pulling in packages with security issues before you've heard about them.  
**pacguard** fetches the official Arch Security Tracker feed, compares it with your installed packages, and tells you if something looks shady.  

---

## Features

- Reads your installed package list directly from pacman’s database.  
- Talks to the [Arch Security Tracker](https://security.archlinux.org/) in JSON format.  
- Flags packages that match known advisories.  
- Shows affected versions, fixed versions, severity, and CVE identifiers.  
- Suggests a quick `pacman -Syu` fix if one exists.  
- Otherwise, tells you to keep an eye on it (because sometimes there’s no fix yet).  

---

## Installation

Just type : 

```bash 
yay -S pacguard
```` 

or 

Clone the repo:

```bash
git clone https://github.com/YOUR_USERNAME/pacguard.git
cd pacguard
````

Install dependencies:

```bash
pip install requests
sudo pacman -S pyalpm
```

Make the script executable:

```bash
chmod +x pacguard
```

(Optional) move it into your `$PATH`:

```bash
sudo cp pacguard /usr/local/bin/
```

---

## Usage

Run it like this:

```bash
./pacguard
```

or, if installed system-wide:

```bash
pacguard
```

---

## Example

When something bad shows up:

```
Vulnerable packages found:

- openssl (installed 3.0.11-1)
  Advisory: ASA-2024-0001
  Affected: 3.0.0 - 3.0.11
  Fixed: 3.0.12
  Severity: Critical
  CVEs: CVE-2024-12345, CVE-2024-67890
  Suggested fix: sudo pacman -Syu openssl
```

When everything is clean:

```
No vulnerable packages detected.
```

---

## Limitations

* Arch Linux only (uses pacman’s local database + Arch Security Tracker).
* Needs internet access to pull JSON feed.
* Won’t magically fix anything — it just tells you what’s wrong.

---

## License

MIT License. See the `LICENSE` file.

---

## Notes from the me :)

This is a small project, nothing fancy — just a Python script that scratches an itch.
I know it’s simple, but I wanted to package it up for the community. If it helps even one other Arch user, I’ll call that a win.

