# Commands used in __Learning Linux Command Line__ from LinkedIn Learning

## Navigating command line
           ctrl A --> move to beginning of line
           ctrl E --> move to end of line
           ctrl U --> delete from cursor to line start
           ctrl K --> delete from cursor to line end
           ctrl shift C --> copy 
           ctrl shive V --> paste
           ctrl C --> cancle command
           ctrl R --> search command history of a command

## 02_04 - Finding help for commands

`man ls`
    returns manual of how to use command and options associated
    
`ls --help`
  
`apropos list`
    looks up a command by its description rather than its name
    
## 02_05 - Helpful keyboard shortcuts in the terminal

`ls -l Do` followed by the Tab key twice
  returns list of items in directory with letters do in directory
  
`ls -l Doc` followed by the Tab key
  returns document if only path that contains 'Doc' is document
  
Tab completion autocompletes your command based on the first letters of the command. --> 'user/docu' + tab  = user/documents


  
`clear` (used throughout the course)
    clears terminal window
## 03_01 - The Linux file system

`ls -l` --> display list of every path in directory

`file Documents` --> classifies a file (i.e what type? Directory, png, executable?)

`stat Documents` --> display file status 

## 03_03 - Navigating the file system

 for directories with titles with spaces, we can use escape the space to ensure the shell treats the word as a single argument 
  --> Directory: home/tyler/documents/"exercise file" can be written as home/tyler/documents/exercise\file for convience
  
`pwd` --> Prints working directory

`cd Exercise Files` (invalid command)

`cd Exercise\ Files`

`pwd`--> prints absolute directory

`ls`

`ls -R departments/`

`cd departments/hr/policies`

`..` refers to parent directory or working directory 

`cd ..`

`cd hr/policies`

`cd ../../finance/documents`
     --> leave top 2 directories, then go into finance directory and then into documents directory  

`cd -` can be used to switch between the two most recently used working directories

`cd` returns back to home directory

## 03_04 - Exploring the output of the ls command

`ls` returns content of a directory

`ls --color=always` returns content of a directory to ensure different types of paths have different colors 

`ls -l`
      returns additional file content like permissions and type of file you are working with and byte size of files
  
## 03_05 - Create and remove directories

`mkdir newfolder` makes a new folder in working directory

`mkdir departments/customerservice/documents departments/customerservice/cases departments/customerservice/awards`
        makes new folder in dep/cust/doc, dep/cust/cas/, and dep/cus/awards 
        
`mkdir -p departments/legal/contracts` -p option stants for parent, usually a error will arise if parent directory of new directory being made doesnt exist. Here, that parent directory is created.  

`rmdir departments/legal/contracts/` remove departments

`rmdir departments/customerservice` will give me a error because customerservice is not empty in this case. Only empty directories can be deleted

## 03_06 - Copy, move, and delete files and directories

`cp poems.txt poems2.txt` --> copy contents of poems to poems2

`cp simple_data.txt departments/hr/employee\ info/` copies simple_data contents to a new file called simple_data in employeeinfo

`mv poems2.txt departments/marketing`  --> Move between directories 

`mv departments/marketing/poems2.txt departments/marketing/literature.txt` rename file literature.txt by moving the contents of a file poem2.txt to another literature.txt

`mv departments/marketing/literature.txt .`  moves literature.txt to current working directory AWAY from specified PATH

---
wildcards are used to match a bunch of files together with known patterns. Here are wild cards
---

 - * (Asterisk): Matches zero or more characters.
- Example: ls *.txt lists all files ending in .txt.
- ? (Question mark): Matches exactly one character.
- Example: ls file?.txt would match file1.txt, file2.txt, but not file10.txt.
- [] (Square brackets): Matches any single character within the brackets.
- Example: ls file[123].txt matches file1.txt, file2.txt, and file3.txt.

- [^] (Negation in square brackets): Matches any character NOT listed inside the brackets.

---

`mv *.txt departments/marketing/` --> Move ALL .txt files in working directory to departments/marketing

`mv departments/marketing/* .` --> move all files in departements/marketing to working directory

`rm literature.txt` --> delete literature file



`rm poems?.txt`
     --Context: poems2 and poems3 exist-- 
         --> removes  poems2, and poems3

`rm departments/customerservice/` cannot work because customersevice is a directory and is not empty

`rm -r departments/customerservice/` deletes all contents of customer service, then customer service itself

## 03_07 - Find files from the command line

`find . -name "do*"` --> find all file and directory titles starting with the word 'do' in working directory and sub directories

`find . -name "*d*"` --> find all file and directory titles with the letter 'd' present in the their titles in working directory and sub directories

`find ~/Documents -name "*d*"` --> finds all file and directory tittles with 'd' present in documents and sb directories



## 03_08 - Understand user roles and sudo
super users can make system wide changes, normal users cannot. super user perms can be granted temporatily using sudo commands

`ls /root` --> trying to access the root directory, which is a system directory not specific to any user. Therefore, since we are normal users, access will be denied

`sudo ls /root`  --> First time using sudo, will be asked to enter password for user currently on system
    return snap
`sudo -k` --> kills superuser privilages, will need to enter password to use sudo again

`sudo -s` --> login to the root shell. Default logged into user shell

`exit` --> kill root shell access. Now working in user shell

## 03_10 - Modify file permissions

File permissions will look similar to this.
rwxrwxrwx filename when you ls -l filename
r = read
w = write
x = execute

first 3 characters define user permissions
characters 3-6 define group permissions (defined collection of users)
characters 7-9 define other users permissions

chmod changes permissions of mode string
chown and chgrp changes file owner(s)

`ls`

`./test.sh`

`ls -l test.sh`

`stat test.sh`

`chmod 644 test.sh` followed by Ctrl+C

`chmod -x test.sh`

`./test.sh`

`bash test.sh`

`cat test.sh`

`chmod u-r test.sh`

`chmod 244 test.sh` followed by Ctrl+C

`cat test.sh`

`chmod 755 test.sh`

`./test.sh`

`cat test.sh`

`touch newfile`

`stat newfile`

`ls -l`

`nano test.sh`

`sudo chown root test.sh`

`nano test.sh`

`ls -l test.sh`

`sudo chown [username] test.sh` (replace `[username]` with your user name)

## 03_11 - Create hard and symbolic links

`ln -s poems.txt writing.txt`

`ls -l`

`cat writing.txt`

`ln poems.txt words.txt`

`ls -l`

## 04_02 - Use pipes to connect commands together

`echo "Hello"`

`echo "Hello" | wc`

`echo "Hello world from the command line" | wc`

## 04_03 - View text files with cat, head, tail, and less

`cat poems.txt`

`head poems.txt`

`head -n5 poems.txt`

`tail -n3 poems.txt`

`cat poems.txt | cat -n | tail -n5`

`cat poems.txt | tail -n5 | cat -n`

`less poems.txt`

`cat poems.txt | less`

## 04_04 - Search for text in files and streams with grep

`grep "the" poems.txt`

`grep -n "the" poems.txt`

`grep -n "The" poems.txt`

`grep -in "The" poems.txt`

`grep -vi "the" poems.txt``grep -E "\w{6.}" poems.txt`

## 04_05 - Manipulate text with awk, sed, and sort

`cat simple_data.txt`

`awk '{print $2}' simple_data.txt`

`awk '{print $2 "\t" $1}' simple_data.txt`

`awk '{print $2 "\t" $1}' simple_data.txt | sort -n`

`cat simple_data.txt`

`sort simple_data.txt`

`sort -k2 simple_data.txt`

`cat dupes.txt`

`sort -u dupes.txt`

## 04_06 - Edit text with Vim

`vi`

`vi poems.txt`

## 04_07 - Edit text with nano

`nano`

`nano poems.txt`

## 04_08 - Working with tar and zip archives

`cd ..`

`tar -cvf myfiles.tar Exercise\ Files/`

`ls -l`

`tar -caf myfiles.tar.gz Exercise\ Files/`

`tar -caf myfiles.tar.bz2 Exercise\ Files/`

`ls -lh`

`mkdir unpack1`

`mv myfiles.tar.bz2 unpack1/`

`cd unpack1/`

`tar -xf myfiles.tar.bz2`

`ls -l`

`cd Exercise\ Files`

`ls`

`cd ~/Documents/`

`mkdir unpack2`

`tar -xf myfiles.tar.gz -C unpack2`

`ls unpack2`

`zip -r exfiles.zip Exercise\ Files/`

`ls -lh`

`mkdir unpack3`

`mv exfiles.zip unpack3`

`cd unpack3`

`unzip exfiles.zip`

`ls -l`

`cd ..`

`mkdir unpack4`

`unzip unpack3/exfiles.zip -d unpack4`

`ls -l unpack4`

## 04_11 - Output redirection

`cd Exercise\ Files`

`ls`

`ls 1> filelist.txt`

`cat filelist.txt`

`ls > filelist2.txt`

`cat filelist2.txt`

`ls notreal`

`ls notreal > filelist3.txt`

`ls notreal 2> filelist4.txt`

`cat filelist4.txt`

`>filelist4.txt`

`cat filelist4.txt`

`ls > filelist5.txt`

`echo "some appended text" >> filelist5.txt`

`cat filelist5.txt`

## 04_12 - Exploring environment variables and PATH

`env`

`echo $PATH`

`which ls`

`which less`

`ls -a`

`nano ~/.bash_profile`

## 05_01 - Find information about your Linux distribution

`ls -l /etc/*release`

`cat /etc/lsb-release`

`cat /etc/os-release`

`cat /etc/*release`

`uname -a`

`uname -r`

## 05_02 - Find system hardware and disk information

`free -h`

`cat /proc/cpuinfo`

`lscpu`

`df -h`

`sudo du -hd1 /`

`sudo lshw | less`

`ip a`

## 05_03 - Install and update software with a package manager

`apt search tree`

`apt show tree`

`tree`

`sudo apt update`

`sudo apt install tree`

`tree`

`man tree`

`sudo apt update`

`sudo apt upgrade`
