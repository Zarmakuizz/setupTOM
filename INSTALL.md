This document explains a setup process collected through Trial&Error.

**Reminder**: As per README.md, TOM is officially UNSUPPORTED on Linux systems. These instructions are provided "as is" with NO WARRANTIES. Any tournament created and/or completed using that setup may be flagged as INVALID.

# Install

To install TOM on Linux, you need to follow multiple steps.

## Prerequisite

Install the latest Java JDK from Oracle: https://www.oracle.com/uk/java/technologies/downloads/

Note: TOM has not been tested with the latest OpenJDK releases (so far).

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
  - Requirements: install `p7zip-full` and `dmg2img`
  - in a terminal, use `dmg2img Tournament.Operations.Manager-[version].dmg tom.img`
  - in the same terminal, use `7z x tom.img`
  - The folder `Tournament Operation Manager` appears and contains multiple folders.
 
## Organize TOM files on your computer

- Create a folder where you want your TOM setup. This folder will be called "TOM root folder" for the rest of the instructions
  - Personal suggestion: name your folder with the TOM version you are about to install, for example TOM174 for TOM version 1.74. This helps a lot when upgrading a new version of TOM (more on that later).
- Inside your TOM root folder, create a lib folder
- From the TOM extracted files, locate a folder containing multiple .jar files.
  - It should be there: `Tournament Operations Manager.app/Contents/app/`
- Copy all these files, paste them in the _lib_ folder before
- Inside your TOM root folder, create a `script.sh` file with the following content: `java -Xms256m -Xmx2048m -cp "lib/file1.jar:lib/file2.jar:...:lib/lastfile.jar" com.tcg.pokemon.op.tom.Main`
  - Yes, you must list every file inside the lib/ folder, separated by :.
  - These files change at every TOM version. More on that later.


### Installation only: create your TOM_DATA folder

You need to do this step when you first install TOM. You don't need to do this step when you update TOM.
- Inside your TOM root folder, create a TOM_DATA folder
- Inside TOM_DATA, create the following folders:
  - data/
  - data/reports/
  - data/profiles/
  - Inside data/profiles/ , create a `profiles.xml` file with the following content: 
```
<?xml version="1.0" encoding="UTF-8"?>
<profiles>
</profiles>
```
- Inside your home directory, create a file called `.tom_install`
  - On Linux systems, your home directory usually is `/home/yourusername/`.
- Inside that file, write the path from the root to the TOM_DATA location
  - Example: `/home/yourusername/folder/to/TOM/TOM_DATA`
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

Find below reported issues, and if a solution exists.

## Can't use TOM's Import Profile feature

When you start TOM, a pop-up opens where you are supposed to create a profile, import a profile, or enter your Play!Pokémon ID to use your profile. 

The Import Profile doesn't seem to work.

**Workaround** : Ignore the feature and create a new profile from scratch.

## I can't see the Verify popup's buttons

When you create a tournament, you have a step to verify your tournament before you start it.

When you click Verify, the pop-up appears.

Under certain conditions, the pop-up content may be too tall, and parts of the content are hidden. However, you can't resize the pop-up. As a consequence, you don't see the buttons.

Example: tested with a Custom TCG Swiss tournament that has 4 Juniors, 7 Seniors and 6 Masters, thus JR/SR Combined and Masters.

**Workaround** : Click on the pop-up content, then press Tab twice, then press Enter, to confirm you want to start the tournament. Click on the pop-up's Close icon in the pop-up's window corner to cancel.
