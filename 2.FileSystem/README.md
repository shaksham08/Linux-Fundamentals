# File System 

Some other resources are :- 
[Understanding UNIX / Linux File Systems](https://www.cyberciti.biz/tips/understanding-unixlinux-file-system-part-i.html)

- Entire Linux Follow Tree Stucture
- on top we have **root** directory `/`
- ![file system](filesystem.png)
- Every FIle can be traced back to root directory
- One of the important directory here is home directory which contains the user and then user contains everything for that user eg , documents , desktop etc.
- [cheat sheet](File+System+Cheat+Sheet.pdf)
- this cheat explains all the Directory and why they are use.

## pwd and ls command

- shaksham@computerName:~$ => ~ tells we are in home directory  
- `pwd` tells the `**current Working Directory**
- `ls` -> it takes everything as command line arguments
- it list out the contents of the current directory or even we can giive command line arguments to give the list of a particular directory.
- `ls -F` -> it tells the different files and folders
- `ls -l` -> list in long form 
- `ls -l -h` => human redable form
- first is the directory(- for the file) and then three are read write and execute 
- `ls -a` shows whole file even the hidden one

## cd command

- `cd` command is for the change directory
- `cd` command is to go back the current users home directory
- `cd .` here dot refers to the current folder
- `cd ..` it tells above directory from where we are

## File Extensions in Linux

- `file` command tells the type of file we want to no.
- `file tuf.png` will tell about that file, here that its a png file.

## WildCards

- `ls Documents/ Downloads/ Pictures/` - it tells to show files from all folders
- `ls *` - Here star tells to look for everything so here it will show contents of all the folder inside the cwd
- Here This * is a regular expression
- `ls D*` - list out anything has D in start and then anything.
- `ls Do*`
- some resources on wildcards
- [Wildcards](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm)
- [Wildcards](http://www.linfo.org/wildcard.html)
- **?** wildcard will only match one character
- `ls ?.pdf` will only match to a.pdf or b.bdf etc
- **[]** - `ls file[1234567890].txt` - will give only file which has 1 or 2 or 3....
-  `ls file[0-9].pdf`
-  `ls file[a-z].pdf`
-  `ls file[0-9][0-90].pdf` - will look for two numbers
- `ls file[0-9][A-Z][a-z].txt`
- `ls file[0-9abc].txt`
  
## touch and mkdir command

- `touch` command creates new file
- `touch file1`
- `echo "hello" > hello.txt`
- `mkdir` - it shands for make directory
- `mkdir folder`
- `mkdir blah/thing/shaksham` it wil give error but e can use `mkdir -p blah/thing/shaksham`
- `mkdir "happy birthday"` - but try to avoid spaced and use _
- Now we want to create a lot of folders
- `mkdir {jan,feb,mar,apr......,dec}_{2017,2018,.....2022}` - it will expand how brackects expand
- `mkdir {jan,feb,mar,apr......,dec}_{2017..2022}` 
- `touch {jan,feb,mar,apr......,dec}_{2017..2022}/file{1,100}`  - in each folder create file 1 to 100
- even this can be used with `ls` command
- `touch file{A..C}.txt`
- `touch file{A,B,C}.txt`

## rm command

- `rm foldername` = this will delete the folder named **foldername**
- `rm *.txt` = will delete everything ending with txt
- `rm *2*` = will delete all files which have 2 in between

- `rm -r delfolder/` - it will delete everything recursivly
- `rm -ri deletefolder/` - it will delete something interactively and ask permission to delete something one by one.
- `rmdir` - it will remove directory which is empty only.

## cp command

- `cp file1.txt file2.txt` - this will copy content of file 1 to file 2
-  `cp file1.txt file2.txt destination/`  here we are copying both files into destination folder, last thing is always the destination.
-  `cp destination/* .` - copy everything from destination to current working directory.
-  `cp -r copy_me/ destination/` - it will copy the whole directory recursevly.
  
## moving and renaming file (mv command)

- `mv oldname.txt newname.txt` - renaming 
- `mv oldfolder/ newfolder/` - renaming
- `mv newfolder/* .` - move everything from new folder to desktop.
- `mv file* newfolder/` - move verything back
- `mv newfolder/ ~documents/` - move folders
- Now we need to move and as well rename it 
- `mv ~documents/newfolder/ ./jackpot` - move and rename it at same time.

## Nano Editor (nano command)

- `nano diary.txt` - will open editor and we can edit everything in that
- it works like everyother editors
- `nano /etc/nanorc` - this is the nano configuration file and here we can change the configuration
- tomake this writable we need to make this `sudo`

## locate command 

- `locate *.conf` - this will check for this type of file everywhere.
- Linux is case sensitive
- `locate -i *.conf` - this makes search insensitive
- `locate -i --limit 3 *.conf`
- `locate -S` - give details about the database from which we are able to search this easily
- `locate -e *conf` - this will also check if there is the file or not rather than just taking details from database.
- Now we will see how to update the database using `updatedb`
- this automatic updating of database dont happen very frequently so we may get some error when we try to find something.
- `sudo updatedb` - is used to manually update the db.
- locate just list files and not folders

## Find Command

- `find` - will list out everything folder and file.
- it dosent uses database so its a littlebit slower
- `find /etc` -  it will list everything in etc folder
- find command generally start from the current working directory.
- `find . -maxdepth 1` - only search in current directoy with only one level depth
- `find . -type f` - will only give folders
- `find . -type d` - will only give directory
- make sure togive max depth first option if want to use.
- Now we want to search things by name
- `find . -name "5.txt"`
- to search for insensitive name just use `-iname`
- we can also search with file size
- `find / -type f -size +100k`
- `find / -type f -size +100k | wc -l` -  it will count how many lines are there.
- `find / -type f -size +100k -size -5M` = greater than 100 kilobyte and less than 5 mega bytes
- Now we want to seach for all files less than 100K or greater than 5Mb
- `find / -type f -size +100k -o -size -5M`
- Now we want to **copy** the results which find command give so,we use `exec` option which tells that on each result execute something
- `find / -type f -size +100k -size -5M -exec cp {} ~Desktop/copy_here \;`
- `find / -type f -size +100k -size -5M -ok cp {} ~Desktop/copy_here \;` - this will ask everytime for each file before copying, it will be just safe option

## Viewing Files(5 New commands)

- 5 new commands to manupulate file contents
- `cat` command
- `cat file1.txt file2.txt file3.txt`
- `cat file[1-5].txt`
- it can work with mp3 and audio files as well , it can stick files together.
- `tac` command just reverse the content backwards
- `cat file[1-5].txt | tac` - it reverse the file upside down
- `rev` command is used to reverse each lines 
- `cat file[1-5].txt | rev` - reverses horizontally
- using `cat` command opening fle is pain if the file is very long.
- `less ./filetoread` - with this reading is very easy
- `cat file[1-5].txt | less` - now with this scrolling is very easy
- `cat file[1-5].txt | head` - be default it will show 10 lines
- `cat file[1-5].txt | head -n 2` = first two linnes
- `tail` command just works same as head but works from bottom.

## Sorting Data(sort command)

- How I generated 100 random numbers 
`shuf -r -i 0-10000000000 -n 100 > numbers.txt`

- How I generated 100 random numbers with values 
between 0 and 9, inclusive.

`shuf -r -i 1-10 -n 100 > numbers0-9.txt`
- How I generated 100 random words
This process involves using a bash script, which is a relatively advanced concept. If you don’t understand it yet, don’t worry; it will be crystal clear to you after you have studied the bash scripts section of the course (level 4). Here are the steps I followed:

1. First, I found a script online that does this kind of thing athttps://linuxconfig.org/random-word-generator
   
2.	Then, I copied and pasted that script into a file called word_generator.sh, saved in my home directory. You can find this script as an attachment in the resources as well. This process will be more familiar to you after you have studied the bash scripts section of the course (level 4).

3.	After making sure that I was in my home directory, I then made that   script executable by running chmod +x word_generator.sh. 

4.	I then ran the script using ./word_generator.sh 100 > ~/words.txt.   This will save 100 random words into a file called `words.txt` in my    home directory. 


- `sort word.txt`
- `sort word.txt | tac` - this will reverse the sorting
- `sort -r word.txt` - this will also reverse the content in effecient way.
- `sort -n numbers.txt` - for sorting numbers numerically
- `sort -nr numbers.txt` - for sorting numbers numerically and reverse
- to get unique result then `sort -u -n numbers.txt`
- `ls -l /etc | head -n 20 | sort -k 5n` - this will sort according to the file size here 5 is the column of that file size, we can even reverse it and add more number of options.
- `ls -lh /etc | head -n 20 | sort -k 6M` -this will sort by month


## Searching File Content(grep command)

- `grep` commands will search for the input for the lines which contains that particulat text we are searching for.
- `grep e hello.txt` - search the words which contain letter e in hellp.txt
- `grep -c e hello.txt` - will give number of lines
- `grep -ic a hello.txt` - this will give the count and also case insensitive
- `grep -v e hello.txt` - it will find all the lines which dont have the letter **e**

## File archiving and compression

- How to archive and compress  files in linux and able to create and restore backups.
- here we use tarball
- In linux file extension dosent mean anything.
- Creating a tarball is like putting our files in a bag to make them easier to store/compress.
- tarball dosent do any compression but we can compress tarball using any compression algorithm.
- `tar -cvf outarchive.tar file[1-3].txt` = c is to know that we want to create a tarball, v is to tell to ask and let us know, f tells to accept files, ourarchive.tar is the tarname.
- with this we can create out tarball.
- we can take a look at tarball using `tar -tf ourarchive.tar`
- Here t option means test label which tells whats inside 
- f is for the file and is necessary.
- Now we will see how we can get it outside our tarball.
- `tar -xvf ourarchive.tar` - here x is to extract, v for verbose
- this will extract everything in the current directory.
- There are 2 main compression algorithm **gzip** and **bzip2**.
- gzip is faster but will compress less, but bzip2 takes more time but will compress more.
- `gzip ourarchive.tar` - will compress in gzip compress data
- To `gunzip gunzip ourarchive.tar.gz`
- To unzip bzip2 we use `buzip2` command
- Now coming to how to create a zip file
- `zip outthing.zip hello.txt hello2.txt`
- to unzip `unzip` command
- Now can we do these process in one step that is creating tarball and compress it.
- `tar -cvzf ourarchive.tar.gz file[1-3].txt` - gzip
- `tar -cvjf ourarchive.tar.bz2 file[1-3].txt` - bzip2
- `tar -xvzf ourarchive.tar.gz` - uncompress
- `tar -xvjf ourarchive.tar.bz2` - uncompress
  
  [File archiving cheat sheet](File+Archiving+Cheat+Sheet.pdf)

  