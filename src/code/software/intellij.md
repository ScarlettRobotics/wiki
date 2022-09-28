# Installing Intellij

Intellij is the IDE (Integrated Development Environment) that we will be using to write code for the robot. The Download links and installtion steps can be found per platform below:
+++ Windows
1. Download the installer from: https://www.jetbrains.com/idea/download/#section=windows
 (*If you have a ultimate license, you can use the ulimate edition. If not, use the community edition.*)
2. Launch the installer and follow the graphical installation steps.
+++ MacOS
1. Download the installer from: https://www.jetbrains.com/idea/download/#section=mac. Make sure you downlaod the correct DMG version depending whether you are using an Alple Silicon Mac or an intel Mac.
 (*If you have a ultimate license, you can use the ulimate edition. If not, use the community edition.*)
2. Open the DMG file and drag the icon to the applications folder. 
+++ Linux
If you are using one of the following distros, simply install the following packages using your package manager or AUR helper of choice:
* Ubuntu Classic Snap: `intellij-idea-community`
* Arch Linux (AUR): `intellij-idea-ce`

Other Distros:
1. Download the tarball at: https://www.jetbrains.com/idea/download/#section=linux (not wget or curl friendly)
2. Extract the tarball on your system `tar -xzf idea-(version).tar.gz`
3. Ensure idea.sh has execute permissions `chmod +x idea.sh`
4. Run idea.sh `./idea.sh`
+++