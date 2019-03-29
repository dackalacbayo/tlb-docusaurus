---
id: install
title: Install Hugo
sidebar_label: Installation
---
_____
The following aims to be a complete guide to installing Hugo on your Windows PC.

## Assumptions
1.  You will use **C:\Hugo\Sites** as the starting point for your new project.
2.  You will use **C:\Hugo\bin** to store executable files.

## Set up Your Directories
You’ll need a place to store the Hugo executable, your content, and the generated Hugo website:

1. Open Windows Explorer.
2. Create a new folder: C:\Hugo, assuming you want Hugo on your C drive, although this can go anywhere
3. Create a subfolder in the Hugo folder: **C:\Hugo\bin**
4. Create another subfolder in Hugo: **C:\Hugo\Sites**

## Technical Users
1. Download the latest zipped Hugo executable from [Hugo Releases.](https://github.com/gohugoio/hugo/releases/ "Hugo Releases")
2. Extract all contents to your **..\Hugo\bin folder**.
3. The hugo executable will be named as hugo_hugo-version_platform_arch.exe. Rename the executable to **hugo.exe** for ease of use.
4. In PowerShell or your preferred CLI, add the hugo.exe executable to your PATH by navigating to C:\Hugo\bin (or the location of your hugo.exe file) and use the command **set PATH=%PATH%;C:\Hugo\bin**. If the hugo command does not work after a reboot, you may have to run the command prompt as **administrator**.

## Less-technical Users
1. Go to the [Hugo Releases.](https://github.com/gohugoio/hugo/releases/ "Hugo Releases") page.
2. The latest release is announced on top. Scroll to the bottom of the release announcement to see the downloads. They’re all ZIP files.
3. Find the Windows files near the bottom (they’re in alphabetical order, so Windows is last) – download either the 32-bit or 64-bit file depending on whether you have 32-bit or 64-bit Windows. (If you don’t know, see here.)
4. Move the ZIP file into your **C:\Hugo\bin folder**.
5. Double-click on the ZIP file and extract its contents. Be sure to extract the contents into the same **C:\Hugo\bin** folder – Windows will do this by default unless you tell it to extract somewhere else.
5. You should now have three new files: The **hugo executable (hugo.exe)**, **LICENSE**, and **README.md**.

>Now you need to add Hugo to your Windows PATH settings:

## For Windows 10 Users:
1. Right click on the **Start** button.
2. Click on **System**.
3. Click on **Advanced System Settings** on the left.
4. Click on the **Environment Variables…** button on the bottom.
5. In the **User variables** section, find the row that starts with **PATH (PATH will be all caps)**.
6. Double-click on **PATH**.
7. Click the **New…** button.
8. Type in the folder where hugo.exe was extracted, which is **C:\Hugo\bin** if you went by the instructions above. The PATH entry should be the folder where Hugo lives and not the binary. Press **Enter** when you’re done typing.
9. Click **OK** at every window to exit.
