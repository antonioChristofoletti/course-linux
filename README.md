# Linux

## Getting Help

-  `man`: show the command documentation;
    - example: `man pwd`.
- `help`: Bash command, depending of the command It may work or not.
- `--help`: argument that show highlights parameters about a command, It more common to work than command `work`.

## Common Commands

- `pwd`: show current folder path;
- `ls`: list folders and files;
    - `-l`: show more information;
    - `-la`: show visible and non-visible files.
- `>`: send the result to other place defined;
- `>>`: concat information;
    Example: echo "foo" >> existentFolder.txt.
- `cat file`: show a content in the terminal;
- `whoami`: show the current user
- `cd`: change directory. Just cd goes to the user root folder;
- `mkdir`: creates a dir;
- `rmdir`: delete folder;
- `rm`: delete file;
    -`-r`: param for delete recursively. Works for `cp` and `mv`.
-  `echo`: print string in the terminal or file for example;
- `cp`: copy something from one directory to anothe;
- `mv`: move something from one directory to another;
- `touch`: change the "last change date" data from the file;
- `date`: show the current system date and time;
- `head or tail`: show a certain quantity of lines in the file text;
    - example: `head -n 4 foo.txt`.
- `less`: It only print some lines of a text file, It is on demand, pressing enter the command show more lines in the terminal;
    - example: `less foo.txt`.
- `grep`: Used as a filter to find string.
    - Example: `cat google.txt | grep "Larry Page and Sergey Brin"`.
- `which`: show the location of execution file.
    - Example: `which firefox`
- `wc`: show the quantity of characters in a file
    - `-l` show quantity of lines, `-c` show quantity of characters, `-w` quantity words
    - Example: `w -lcw *.txt`

### Compacting

#### Zip

- `zip`: create a zipped file;
    - `-r`: recursively;
    - `-q`: quiet (less log);
    - example: `zip bemvindo.zip *.txt`.

- `unzip`: unzip a zipped file;
    - `-l`: show zipped files, but do not unzip.
        - Example: unzip -l file.zip;
    - `-q`: quiet (less log).

#### Tar Gz

Faster than bzip2, but It creates bigger files.

- `tar -cz workspace > work.tar.gz`: Compact
    - `c`: create
    - `z`: compaction format
- `tar -czf work.tar.gz workspace/`: Compact
    - `f`: for a file as parameter
- `tar -xz < work.tar.gz`: Extract
    - `x`: extract
    - `z`: compaction format
- `tar -vxzf work.tar.gz`: Extract
    - `v`: verbosy, optional, show more log

#### Bzip2

Lower than `gz`, but It creates smaller files.

It is used the same as `gz`, however using the parameter `z`, It is used the parameter `j`.

## Shortcuts

- `/`: linux root folder;
- `~`: user root folder;
- `.`: current folder;
- `..`: previous folder;    

## Bash Terminal WildCards

- `*`: anything after the *;
- `?`: one unique character in the ? position.

## Text File Editor: vi/vim

`Vim` is a evolution comparing with `vi`.

- Keyboard arrows to navegate;
- press `G` to go to the last file line;
    - A number + `G` goes to a specific line;
- press `$` to go to the last character of the current cursor line;
- press `0` to go to the first character of the current cursor lin;
- press `yy` copy a line. It is possible to copy more than 1 line, example, `5yy` (It will copy 5 lines);
- press `p` to past the content copied. It is possible to past more than once, example, `5p` (It will past 5 times the same content);
- press `/` + `characters` to search something;
    - press `n` to go the next found string;
    - press `N` to go the previous found string.
- press `esc` to return to navegation mode;
- press `:` to execute commands like: `q`;
- press `q` to exit;
    - press `!` to force the exit, without saving the current changes.
- press `i` to edit;
- press `a` to add after the current character;
- press `A` to add into the end of the line;
- press `x` to remove one character;
- press `dd` to remove one line;
- Obs.: 
    - the `x` and `dd` commands allow to define how many characters or lines are gonna be removed, just press the quantity and then the command: `11 + x`;
    - It is possible combine commands, like `wq` (Save and quite).

## Managing Processes

- `ps -e`: show all the processe. `-ef` show more details about each process;
- `top`: show process and resources consumided by each one;
- `pstree`: show the process in a tree scheme;
- `kill pid-number`: terminate a process, requiring to the process itself to close;
    -`-9`: kill abruptly;
    -`-TERM`: default param used if no one is passed, It terminate the process properly.
- `kilall {name}`: Kill all processes according with the name;
- `process-to-start &`: Start the process already on the background;
- `jobs`: List the processes associated with the current process (terminal);
- `ctrl + z`: put the process to sleep and unlock the terminal;
- `bg`: Send the process to the background;
    - Example: `bg firefox`.
- `fg`: send the process to the foreground;
    - Example: `fg firefox`.

## Managing Files Acess

- Each file has a configuration to the owner, user group and other users. Example: `drwxrwxr-x 8 antonio antonio 4096 Aug 22 14:51 .git`;

`d` represents a directory, if not there will be a `-` for files;
`rwx` represents the permission access for someone, if It has not a permission It gonna have just a `-`. This pattern It is repeated 3 times, one It is for the owner, the group user and other users.

`chmod`: It is used to change user permission. It has 2 ways to use it;
    - Symbolic : `chmod [permission type][operation][permission]`;
        - Example: `chmod u+rwx afile` or `chmod g-w file`.
    - Numerical: Each operation has a value, read(4), write(2) and execute(1). Each permission group type is gonna have a sum of these values, representing It access;
        - Example: `chmod 754 file` (owner has all, user group has read and execute and other users has only read).

`chown`: allows to change the owner or the user group;
    - Examples: `chown user:user-group file` (It is possible edit just the user or the group user).

- `chmod` and `chown` allow -R (Recursive).

- `sudo su`: Change to root user;
- `su {username}`: change to another user;
- `passwd`: change the password of the current user, It allows pass the user name too;
- `sudo adduser {username}`: add a new user;

## Searching for files

- `locate`: Search for a file
    - Example: `locate chrome`.
- `sudo updatedb`: the OS tracks all the file's names and keep them in a DB. It is possible to force the update with this command.

## Environment Variables

- `env`: show all the variables.
    - variables PATH keep all the paths that has executable files. It is possible to edit. Example: ``
    - It is possible edit these variables on the terminal, however, It just apply for the current terminal. Edit the `.bashrc`
        - Example editing the `.bashrc`: `PATH:$PATH:/home/anyuser/workspace/modified_scripts/`

## Managing Packages

Apt is a evolution of apt-get, better to use.

- `apt install {package-name}`: install one or more packages;
- `apt update`: update the repositories's packages references;
- `apt upgrade`: update installed packages;
- `apt remove {package-name}`: delete one or more packages;
- `apt purge {package-name}`: delete and remove all configurations of one or more packages;
- `apt autoremove`: delete packages not used anymore, especially those installed by other packages, because of dependencies.