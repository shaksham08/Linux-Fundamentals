# Automation and Scheduling ( BASH SCRIPTS)

- Create a file `nano our_script.sh`
- Now we need to tell that this file is special and the interpreter has to read it.
- `#!/bin/bash` - this tells to interpret it using the bash shell
- `#!` is called as **she-bang**
- for python its `#!/bin.python` - so now it will take it as  python script
- `#!/bin/bash`
- `echo "hello world"` - now it will run the echo command

```sh
`#!/bin/bash`

mkdir ~/Desktop/magic
cd ~/Desktop/magic
touch file{1..100}
ls -lh ~/Desktop/magic > ~/Desktop/magic.log
```

- Now we can run it using `bash ourscript.sh`

- Now lets create a new bash script to do backup `nano backup.sh`
  
```sh
`#!/bin/bash`

tar -czf ~/Desktop/backup.tar.gz ~/{Documents,Downloads,Desktop,Pictures,Videos} 2>/dev/n$
```

- `2>/dev/n$` this is bit bucket so whatever send to it is deleted

- create a `bin` folder in the home directory and move all our sh file to this folder
- Now we could rename it from backup.sh to backup and then go to its properties and then permissions and then allow executing files as program 
- `chmod +x backup` - add executable permission to backup file.(this is another teminal way) - this chmod is the change mode command
- Now if we run the backup command in terminal then we will get error that it cant find the program so we need to edit the shell search path.
- `nano .bashrc` and add line `PATH="$PATH:$HOME/bin"` this at bottom
- now if we `echo $PATH` then it will also show this folder
- Now we will able to search for this folder as well.

## sheduling with Cron

- **cron** is command line tool to shedule some task
- `crontab -e` - to edit it 
- Each chron tab is broken into rows, and one row is for each command and there is 6 columns.
- Lets run the command `echo "hello world everyminute"`
- `m  h dom  mon dow  command` -m = month , h = hour , dom = day of month , mon - JAN etc , dow - 0 to 6 , 
- `*  *  *    *   *      echo "hello world" >> ~/Desktop/hello.txt`
  
- >> is for append
- Here we can also add * for every interval

- `0,15,30,45  *  *    *   *      echo "hello world" >> ~/Desktop/hello.txt`
- `*/15  *  *    *   *      echo "hello world" >> ~/Desktop/hello.txt` - this tells every 15 minutes
- 

[crontabgurulink](https://crontab.guru/)

- this crontab is generally used to do weekly backup of some database