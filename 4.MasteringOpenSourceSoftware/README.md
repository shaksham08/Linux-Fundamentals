# Mastering OpenSource Software in Linux

## The GNU project

- Rechard Stallman began development of the GNU os.
- Idea was to create unix like os with free softwares.
- THis is provided by GNU liscence
- THis os needeed kernel so Linux torvalds released Linux Kernel.

## How to donwload and modify source code

[GNUORG](gnu.org)

- Lets download the coreutils package.
- We will download the latest version of .xz version
- Here xz is one of the compression algorithm
- `tar -xJf coreutils-8.28.tar.xz` -  to uncompresss
- Now We go to the src directory of the folder extracted.
- There we will find all files written in c , there we will find ls.c file so we can open it as `nano ls.c`
- So we can add any print statement to it and then save now then we need to compile the updated code , so for that we need to use gcc
- `sudo apt-get install gcc`
- this will install the comiler.
- now go to the  folder we extracted.
- then do `bash configure`
- It will configure the program.
- this will create a new MakeFile.
- Now we need to use a **make** command
- `sudo apt-get install make`
- Now just run the `make` command
- this will compile everything into binary.
- Now we need to install thode binary or machine code using `sudo make install`
- Now it will install all the programs that come with that package.

## The software Repositories

- [ubunturepositories](https://help.ubuntu.com/community/Repositories/Ubuntu)
- [ubuntupackagesearch](https://packages.ubuntu.com/)
- `lsb_release` - print all the detail about the ubuntu distribution

## apt package manager

- `apt-cache searh docx` -  to search for the package
- `apt-cache show docx2txt` - get details of the package
- This information is installed in cache so we even dont need the internet to get that. 
- But we need to update the cache reglarly.
- it located in `cd /var/lib/apt/lists`
- Now we will how to update cache uptodate
- `sudo apt-get update` -  it tells the cache to update
- Now we have updated the cache but we need to update the software
- `sudo apt-get upgrade` - this will upgrade our programs on linux.
- Now coming to installing a new software/Packages
- `sudo apt-get install x11-apps` - it will install x11-apps package.
- Now Downloading the source code of the packages
- `sudo nano /etc/apt/sources.list`  - now uncomment all
- Now it will download all the source code, before that we need to update the apt.
- `sudo apt-get install dpkg-dev`
- `sudo apt-get source x11-apps`
- now we can go to its downloaded directory in cwd and see the cource code of it.
- Now coming to uninstalling packages.
- `sudo apt-get remove <packagename>` - But this is not the preffered way, sometime the configuration files remain left behind the system and it takes place in system.
- `sudo apt-get purge <packagename>` - this will remove everything regarding that package , so this is most used.
- there may be still some dependency which are not used so we can use `sudo apt-get autoremove` to remove those not used dependencies.
- Whenever we download or install new softare it create a copy of the project, i.e the compressed version of it so this may take some space. 
- Lets Free that space!!
- `cd /var/cache/apt/archive` - here all compressed archives are stored.
- so to clean this we can use `sudo apt-get clean`
- `sudo apt-get autoclean` will only remove those which cannot be downloaded from repository now
- [CheatSheet](Software+Management+Cheatsheet.pdf)