# Automation and Scheduling ( BASH SCRIPTS)

- Create a file `nano our_script.sh`
- Now we need to tell that this file is special and the interpreter has to read it.
- `#!/bin/bash` - this tells to interpret it using the bash shell
- for python its `#!/bin.python` - so now it will take it as  python script
- `#!/bin/bash`
- `echo "hello world"` - now it will run the echo command

```sh
`#!/bin/bash`

mkdir ~/Desktop/magic
cd ~/Desktop/magic
touch file{1..100}
ls -lh > ~/Desktop/magic.log
```