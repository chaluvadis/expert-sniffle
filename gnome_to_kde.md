====================================================
KDE STANDARD INSTALLATION GUIDE (Ubuntu)
====================================================

1. UPDATE SYSTEM
-----------------
sudo apt update


2. INSTALL KDE STANDARD
-----------------------
sudo apt install kde-standard

During installation:
- When asked for display manager:
  Choose "sddm" (recommended for KDE)
  OR keep "gdm3" if you still use GNOME


3. REBOOT SYSTEM
----------------
sudo reboot


4. LOGIN INTO KDE PLASMA
------------------------
At login screen:
- Click gear icon ⚙
- Select "Plasma (KDE)"
- Log in

This starts KDE Plasma desktop environment


5. FIRST-TIME SETUP
--------------------

Set default applications:
System Settings → Applications → Default Applications

Recommended:
- File Manager: Dolphin
- Terminal: Konsole
- Web Browser: your choice


Adjust appearance:
System Settings → Appearance

You can change:
- Theme
- Icons
- Fonts


6. INSTALL USEFUL KDE APPS (OPTIONAL BUT RECOMMENDED)
-----------------------------------------------------
sudo apt install kdeconnect okular gwenview filelight spectacle

What they do:
- kdeconnect  → connect phone to PC
- okular      → PDF viewer
- gwenview    → image viewer
- filelight   → disk usage analyzer
- spectacle   → screenshots tool


7. OPTIONAL: REMOVE GNOME (ONLY AFTER TESTING KDE)
--------------------------------------------------
WARNING: Do this only if you fully switch to KDE

sudo apt remove gnome-shell ubuntu-desktop
sudo apt autoremove


8. CHECK SYSTEM
----------------
Make sure:
- Plasma session works
- Dolphin opens files
- Sound and network work
- Settings open correctly


DONE
----
You now have KDE Plasma installed alongside Ubuntu.
