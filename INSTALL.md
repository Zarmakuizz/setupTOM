# Install

To install TOM on Linux, you need to follow multiple steps.

## Prerequisite

Install the latest Java JDK from Oracle: https://www.oracle.com/uk/java/technologies/downloads/

## Download the TOM Mac Installer

The current easiest way to get the TOM files is to get the Mac installer.

- Go to https://www.pokemon.com/
- Login
- You must be a Pokémon Professor with the Organizer certification
- Go to https://www.pokemon.com/us/pokemon-trainer-club/play-pokemon-tournaments/software/ (this link will not work if you aren't an Organizer)
- Download the Mac installer (it's a ZIP file)

## Extract files from the TOM Mac Installer

- Extract the Mac installer ZIP file.
- Inside the extracted files, locate a .dmg file.
- Extract files from the .dmg file
 - This step depends on your Linux environment.
 - Solution tested on Ubuntu:
 - Requirements: install p7zip-full and dmg2img
 - in a terminal, use `dmg2img Tournament.Operations.Manager-[version].dmg tom.img`
 - in the same terminal, use `7z x tom.img`
 - The folder Tournament Operation Manager appears and contains multiple folders.
 
## Organize TOM files on your computer

- Create a folder where you want your TOM setup. This folder will be called "TOM root folder" for the rest of the instructions
 - Personal suggestion: name your folder with the TOM version you are about to install, for example TOM174 for TOM version 1.74. This helps a lot when upgrading a new version of TOM (more on that later).
- Inside your TOM root folder, create a lib folder
- From the TOM extracted files, locate a folder containing multiple .jar files.
 - It should be there: `Tournament Operations Manager.app/Contents/app/`
- copy all these files, paste them in the _lib_ folder before
- Inside your TOM root folder, create a `script.sh` file with the following content: `java -Xms256m -Xmx2048m -cp "lib/file1.jar:lib/file2.jar:...:lib/lastfile.jar" com.tcg.pokemon.op.tom.Main`
 - Yes, you must list every file inside the lib/ folder, separated by :.
 - These files change at every TOM version. More on that later.


### Installation only: create your TOM_DATA folder

You need to do this step when you first install TOM. You don't need to do this step when you update TOM.
- Inside your TOM root folder, create a TOM_DATA folder
- inside TOM_DATA, create the following folders:
 - data/
 - data/reports/
 - data/profiles/
 - inside data/profiles/ , create a `profiles.xml` file with the following content: 
```
<?xml version="1.0" encoding="UTF-8"?>
<profiles>
</profiles>
```
- Inside your home directory, create a file called `.tom_install`
 - On Linux systems, your home directory usually is `/home/yourusername/`.
- Inside that file, write the path from the root to the TOM_DATA location
 - example: `/home/yourusername/folder/to/TOM/TOM_DATA`
 - **Warning** Make sure you only use simple letters and numbers. Do not use any accents or special characters (like é ê è ç ...) in the path leading to TOM_DATA. You will encounter bugs otherwise.

# Start TOM

Run the _script.sh_ file from the Terminal.

# Install notes:

You need to declare where is TOM\_DATA. The first time you run TOM, you choose the location, which is stored in your home folder inside a .tom_install file. 

# Update TOM

Follow these instructions to upgrade your TOM version.

## Download the TOM Mac Installer

Do the same step than for the Installation.

## Extract files from the TOM Mac Installer

Do the same step than for the Installation.

## Organize TOM files on your computer

Do every step, except the _Installation only_ part.

# Troubleshooting

I wrote these instructions on a computer that already found workaround for older TOM versions. I don't know if those workaround are still needed nowadays. Please let me know!

## TOM doesn't open any pairings or match slips

TOM opens pairings and match slips in the browser. If you don't see any browser opening those files, then you need this workaround.

In a terminal, enter the following command:

```
sudo ln -s /usr/bin/xdg-open /usr/bin/netscape
```

Explanation: A very old, outdated way for Java to open a link, is to open Netscape. However, the Netscape browser doesn't exist anymore. With this redirection, you will open your default browser instead.
