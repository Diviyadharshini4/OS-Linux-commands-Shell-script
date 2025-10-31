# OS-Linux-commands-Shell-scripting
Operating systems Lab exercise
# Linux commands-Shell scripting
Linux commands-Shell scripting
# NAME: A.DIVIYADHARSHINI
# REGISTER NO: 212224040080

# AIM:
To practice Linux Commands and Shell Scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Execute the following commands

### Step 3:

Testing the commands for the desired output. 

# COMMANDS:
### Create the following files file1, file2 as follows:
cat > file1
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
^d
```
cat > file2
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
^d
```
### Display the content of the files
cat < file1
## OUTPUT
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
```
cat < file2
## OUTPUT
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
```
# Comparing Files
cmp file1 file2
## OUTPUT
 ```
 file1 file2 differ: char 1, line 1
```
comm file1 file2
 ## OUTPUT
```
        anil aggarwal
        barun sengupta
        c.k. shukla
chanchal singhvi
c.k. shukla
        lalit chowdury
                s.n. dasgupta
sumit chakrobarty
```
 
diff file1 file2
## OUTPUT
```
--- file1
+++ file2
@@ -1,4 +1,5 @@
-chanchal singhvi
+anil aggarwal
+barun sengupta
 c.k. shukla
+lalit chowdury
 s.n. dasgupta
-sumit chakrobarty

```

#Filters

### Create the following files file11, file22 as follows:

cat > file11
```
Hello world
This is my world
^d
```
cat > file22
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
^d
```


cut -c1-3 file11
## OUTPUT
```
Hel
Thi
```



cut -d "|" -f 1 file22
## OUTPUT
```
1001
1002
1003
```


cut -d "|" -f 2 file22
## OUTPUT

```
Ram
tom
Joe
```
cat < newfile 
```
Hello world
hello world
^d
````
cat > newfile 
Hello world
hello world
 
grep Hello newfile 
## OUTPUT
```
Hello world
```


grep hello newfile 
## OUTPUT

```
Hello world
```


grep -v hello newfile 
## OUTPUT
```
Hello world
```


cat newfile | grep -i "hello"
## OUTPUT

```
Hello world
hello world
```


cat newfile | grep -i -c "hello"
## OUTPUT
```
2
```



grep -R ubuntu /etc
## OUTPUT

```
grep: unrecognized option: R
BusyBox v1.31.1 () multi-call binary.
 
Usage: grep [-HhnlLoqvsriwFE] [-m N] [-A/B/C N] PATTERN/-e PATTERN.../-f FILE [F
ILE]...
 
Search for PATTERN in FILEs (or stdin)
 
        -H      Add 'filename:' prefix
        -h      Do not add 'filename:' prefix
        -n      Add 'line_no:' prefix
        -l      Show only names of files that match
        -L      Show only names of files that don't match
        -c      Show only count of matching lines
        -o      Show only the matching part of line
        -q      Quiet. Return 0 if PATTERN is found, 1 otherwise
        -v      Select non-matching lines
        -s      Suppress open and read errors
        -r      Recurse
        -i      Ignore case
        -w      Match whole words only
        -x      Match whole lines only
        -F      PATTERN is a literal (not regexp)
        -E      PATTERN is an extended regexp
        -m N    Match up to N times per file
        -A N    Print N lines of trailing context
        -B N    Print N lines of leading context
        -C N    Same as '-A N -B N'
        -e PTRN Pattern to match
        -f FILE Read pattern from file

```

grep -w -n world newfile   
## OUTPUT
```
1:Hello world
2:hello world
```

cat < newfile 
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
```

cat > newfile
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
 ```
egrep -w 'Hello|hello' newfile 
## OUTPUT

```
Hello world
hello world
```

egrep -w '(H|h)ello' newfile 
## OUTPUT

```
Hello world
hello world
```

egrep -w '(H|h)ell[a-z]' newfile 
## OUTPUT

```
Hello world
hello world
```


egrep '(^hello)' newfile 
## OUTPUT

```
hello world
```

egrep '(world$)' newfile 
## OUTPUT
```
Hello world
hello world
```


egrep '(World$)' newfile 
## OUTPUT
```
Linux is best in this World

```

egrep '((W|w)orld$)' newfile 
## OUTPUT
```
Hello world
hello world
Linux is best in this World
```


egrep '[1-9]' newfile 
## OUTPUT

```
Linux is world number 1

```

egrep 'Linux.*world' newfile 
## OUTPUT
```
Linux is world number 1
```

egrep 'Linux.*World' newfile 
## OUTPUT
```
Linux is best in this World
```

egrep l{2} newfile
## OUTPUT
```
Hello world
hello world
```


egrep 's{1,2}' newfile
## OUTPUT 
```
Linux is world number 1
Unix is predecessor
Linux is best in this World
```

cat > file23
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR
^d
```


sed -n -e '3p' file23
## OUTPUT
```
1002 | tom |  5000 | Admin
```


sed -n -e '$p' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
```


sed  -e 's/Ram/Sita/' file23
## OUTPUT
```
1001 | Sita | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Sita | 10000 | HR
```


sed  -e '2s/Ram/Sita/' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR
```


sed  '/tom/s/5000/6000/' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  6000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR
```


sed -n -e '1,5p' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR

```


sed -n -e '2,/Joe/p' file23
## OUTPUT

```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer

```


sed -n -e '/tom/,/Joe/p' file23
## OUTPUT
```
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
```


seq 10 
## OUTPUT

```
1
2
3
4
5
6
7
8
9
10
```

seq 10 | sed -n '4,6p'
## OUTPUT

```
4
5
6
```

seq 10 | sed -n '2,~4p'
## OUTPUT
```
sed: no address after comma

```


seq 3 | sed '2a hello'
## OUTPUT

```
1
2
hello
3
```

seq 2 | sed '2i hello'
## OUTPUT
```
1
hello
2
```

seq 10 | sed '2,9c hello'
## OUTPUT
```
1
hello
10
```

sed -n '2,4{s/^/$/;p}' file23
## OUTPUT
```
$1001 | Ram | 10000 | HR
$1002 | tom |  5000 | Admin
$1003 | Joe |  7000 | Developer

```


sed -n '2,4{s/$/*/;p}' file23
## OUTPUT
```
1001 | Ram | 10000 | HR*
1002 | tom |  5000 | Admin*
1003 | Joe |  7000 | Developer*
```

#Sorting File content 
cat > file21
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
sort file21
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1004 | Sit |  7000 | Dev
1005 | Sam |  5000 | HR

```

cat > file22
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
uniq file22
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
```


#Using tr command

cat file23 | tr [:lower:] [:upper:]
## OUTPUT
```
1001 | RAM | 10000 | HR
1001 | RAM | 10000 | HR
1002 | TOM |  5000 | ADMIN
1003 | JOE |  7000 | DEVELOPER
1005 | SAM |  5000 | HR
1004 | SIT |  7000 | DEV
1003 | JOE |  7000 | DEVELOPER
1001 | RAM | 10000 | HR
```

cat < urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
^d
 ```
cat > urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
 ```
cat urllist.txt | tr -d ' '
 ## OUTPUT
```
www.yahoo.com
www.google.com
www.mrcet....com
```

 
cat urllist.txt | tr -d ' ' | tr -s '.'
## OUTPUT
```
www.yahoo.com
www.google.com
www.mrcet.com
```


#Backup commands
tar -cvf backup.tar *
## OUTPUT
```
bench.py
file1
file11
file2
file21
file22
file23
hello.c
hello.js
newfile
readme.txt
urllist.txt
```

mkdir backupdir
 
mv backup.tar backupdir

cd backupdir
 
tar -tvf backup.tar
## OUTPUT
```
drwxr-xr-x root/root         0 2024-08-16 10:12:02 backupdir/
-rw-r--r-- root/root     13312 2024-08-16 10:10:04 backupdir/backup.tar
-rw-r--r-- root/root       114 2020-07-05 23:17:07 bench.py
-rw-r--r-- root/root        61 2024-08-16 09:48:52 file1
-rw-r--r-- root/root        29 2024-08-16 09:52:03 file11
-rw-r--r-- root/root        70 2024-08-16 09:49:11 file2
-rw-r--r-- root/root       131 2024-08-16 10:06:47 file21
-rw-r--r-- root/root       155 2024-08-16 10:07:30 file22
-rw-r--r-- root/root       210 2024-08-16 10:02:59 file23
-rw-r--r-- root/root        76 2020-07-03 14:45:56 hello.c
-rw-r--r-- root/root        22 2020-06-26 14:57:33 hello.js
-rw-r--r-- root/root        96 2024-08-16 09:57:21 newfile
-rw-r--r-- root/root       151 2020-07-05 23:19:13 readme.txt
-rw-r--r-- root/root        52 2024-08-16 10:09:28 urllist.txt
```

tar -xvf backup.tar
## OUTPUT
```
backupdir/
backupdir/backup.tar
bench.py
file1
file11
file2
file21
file22
file23
hello.c
hello.js
newfile
readme.txt
urllist.txt
```
gzip backup.tar

ls .gz
## OUTPUT
 
gunzip backup.tar.gz
## OUTPUT

 
# Shell Script
```
echo '#!/bin/sh' > my-script.sh
echo 'echo Hello World‘; exit 0 >> my-script.sh
```
chmod 755 my-script.sh
./my-script.sh
## OUTPUT

 
cat << stop > herecheck.txt
```
hello in this world
i cant stop
for this non stop movement
stop
```

cat herecheck.txt
## OUTPUT


cat < scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $1#
echo 'The $$ is ' $$
ps
^d
 ```

cat scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $\#
echo 'The $$ is ' $$
ps
```
 
chmod 777 scriptest.sh
 
./scriptest.sh 1 2 3

## OUTPUT

 
ls file1
## OUTPUT

echo $?
## OUTPUT 
./one
bash: ./one: Permission denied
 
echo $?
## OUTPUT 
 
abcd
 
echo $?
 ## OUTPUT


 
# mis-using string comparisons

cat < strcomp.sh 
```bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
^d
```

cat strcomp.sh 
```bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```
##OUTPUT
<img width="822" height="334" alt="image" src="https://github.com/user-attachments/assets/8cfeb2f4-71ab-4c66-bffa-c7f19da2f279" />



chmod 755 strcomp.sh
 
./strcomp.sh 
## OUTPUT
<img width="813" height="326" alt="image" src="https://github.com/user-attachments/assets/4a902842-1d68-4b0d-8ed8-3810e13da99a" />


# check file ownership
cat < psswdperm.sh 
```bash
\#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
^d
```

cat psswdperm.sh 
```bash
/#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
 ```
./psswdperm.sh
## OUTPUT
<img width="816" height="68" alt="image" src="https://github.com/user-attachments/assets/18e41194-c929-4dd8-8023-f101fc3b00ac" />

# check if with file location
cat>ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```
cat ifnested.sh 
```
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

./ifnested.sh 
## OUTPUT
<img width="821" height="236" alt="image" src="https://github.com/user-attachments/assets/dd4bf6aa-3376-4ab0-bba4-62dadead7f08" />



# using numeric test comparisons
cat > iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
^d
```


cat iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
```

$ chmod 755 iftest.sh
 
$ ./iftest.sh 
## OUTPUT
<img width="817" height="39" alt="image" src="https://github.com/user-attachments/assets/6fe9a196-6406-4531-9eb5-e6a115ebc16c" />


# check if a file
cat > ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```

cat ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

$ chmod 755 ifnested.sh
 
$ ./ifnested.sh 
## OUTPUT
<img width="820" height="81" alt="image" src="https://github.com/user-attachments/assets/7aeee427-2a45-47bf-a849-609d06a8cf17" />


# looking for a possible value using elif
cat elifcheck.sh 
```bash
\#!/bin/bash
if [ $USER = Ram ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Rahim ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Robert ]
then
echo "Special testing account"
elif [ $USER = gganesh ]
then
echo "$USER, Do not forget to logout when you're done"
else
echo "Sorry, you are not allowed here"
fi
```

$ chmod 755 elifcheck.sh
 
$ ./elifcheck.sh 
## OUTPUT
<img width="819" height="93" alt="image" src="https://github.com/user-attachments/assets/a5e6f31f-47bd-4dd4-987f-42b0df5d0fa8" />


# testing compound comparisons
cat> ifcompound.sh 
```bash
\#!/bin/bash
if [ -d $HOME ] && [ -w $HOME ]
then
echo "The file exists and you can write to it"
else
echo "I cannot write to the file"
fi
```
$ chmod 755 ifcompound.sh
$ ./ifcompound.sh 
## OUTPUT
<img width="817" height="68" alt="image" src="https://github.com/user-attachments/assets/60315a9e-960c-4e22-a104-2ff895e6a088" />

# using the case command
cat >casecheck.sh 
```bash
case $USER in
Ram | Robert)
echo "Welcome, $USER"
echo "Please enjoy your visit";;
Rahim)
echo "Special testing account";;
gganesh)
echo "$USER, Do not forget to log off when you're done";;
*)
echo "Sorry, you are not allowed here";;
esac
```
$ chmod 755 casecheck.sh 
 
$ ./casecheck.sh 
 
cat > whiletest
```bash
#!/bin/bash
#while command test
var1=10
while [ $var1 -gt 0 ]
do
echo $var1
var1=$[ $var1 - 1 ]
done
```
$ chmod 755 whiletest.sh
 
$ ./whiletest.sh
 
 
cat untiltest.sh 
```bash
\#using the until command
var1=100
until [ $var1 -eq 0 ]
do
echo $var1
var1=$[ $var1 - 25 ]
done
``` 
$ chmod 755 untiltest.sh
 
 
 
cat forin1.sh 
```bash
\#!/bin/bash
\#basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
 ```
 
$ chmod 755 forin1.sh
 
 
cat forin2.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don't know if this'll work
do
echo “word:$test”
done
 ```
 
$ chmod 755 forin2.sh
 
cat forin2.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don't know if this'll work
do
echo “word:$test”
done
```
$ chmod 755 forin2.sh
 
$ ./forin2.sh 
 
cat forin3.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don\'t know if "this'll" work
do
echo "word:$test"
done
```
$ ./forin3.sh 
 
cat forin1.sh 
```bash
#!/bin/bash
# basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
```
$ chmod 755 forin1.sh

## OUTPUT
<img width="819" height="149" alt="image" src="https://github.com/user-attachments/assets/905f56bf-3a9b-4846-886a-a985daef1c08" />

cat forinfile.sh 
```bash
#!/bin/bash
# reading values from a file
file="cities"
for state in `cat $file`
do
echo "Visit beautiful $file“
done
```
$ chmod 777 forinfile.sh
$ cat cities
Hyderabad
Alampur
Basara
Warangal
Adilabad
Bhadrachalam
Khammam

## OUTPUT
<img width="819" height="307" alt="image" src="https://github.com/user-attachments/assets/1765ae7e-11af-4015-b357-7314c82a2c6b" />


cat forctype.sh 
```bash
#!/bin/bash
# testing the C-style for loop
for (( i=1; i <= 5; i++ ))
do
echo "The value of i is $i"
done
````
$ chmod 755 forctype.sh
$ ./forctype.sh 
## OUTPUT
<img width="821" height="236" alt="image" src="https://github.com/user-attachments/assets/25d722e7-c001-4d60-8dcf-e26b1c860751" />


cat forctype1.sh 
```bash
#!/bin/bash
# multiple variables
for (( a=1, b=5; a <= 5; a++, b-- ))
do
echo "$a - $b"
done
```
$ chmod 755 forctype.sh
$ ./forctype1.sh 
## OUTPUT
<img width="818" height="225" alt="image" src="https://github.com/user-attachments/assets/b2d52ea4-0fac-4b85-9b62-7cfc9e4dd299" />

cat fornested1.sh 
```bash
#!/bin/bash
# nesting for loops
for (( a = 1; a <= 3; a++ ))
do
echo "Starting loop $a:"
for (( b = 1; b <= 3; b++ ))
do
echo " Inside loop: $b"
done
done
```
$ chmod 755 fornested1.sh
 
$ ./fornested1.sh 
 ## OUTPUT
<img width="816" height="397" alt="image" src="https://github.com/user-attachments/assets/b3f70c9f-3c71-4ed2-9b34-c52ee476663e" />

 
cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
break
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```
## OUTPUT
<img width="818" height="283" alt="image" src="https://github.com/user-attachments/assets/e83c449e-dbef-410c-8de0-5fd9e2cad6ba" />

$ chmod 755 forbreak.sh
 
$ ./forbreak.sh 
 
cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
continue
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```

 
$ chmod 755 forcontinue.sh
 
$ ./forcontinue.sh 
## OUTPUT
 <img width="818" height="314" alt="image" src="https://github.com/user-attachments/assets/28df3ed0-367a-499e-8400-5c77d0fa3be9" />

cat exread.sh 
```bash
#!/bin/bash
# testing the read command
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program. "
 ```
 
$ chmod 755 exread.sh 
 
$ ./exread.sh 
## OUTPUT


 cat exread1.sh
```bash
#!/bin/bash
# testing the read command
read -p "Enter your name: " name
echo "Hello $name, welcome to my program. “
``` 
$ chmod 755 exread1.sh 

## OUTPUT

<img width="816" height="155" alt="image" src="https://github.com/user-attachments/assets/429ac674-e8c5-42f7-ba2f-4c699f0ae2e5" />


$ ./exread1.sh 
 
cat funcex.sh
```bash
#!/bin/bash
# trying to access script parameters inside a function
function func {
echo $[ $1 * $2 ]
}
if [ $# -eq 2 ]
then
value=`func $1 $2`
echo "The result is $value"
else
echo "Usage: badtest1 a b"
fi
```
## OUTPUT
<img width="819" height="293" alt="image" src="https://github.com/user-attachments/assets/4590d4b2-5bef-427e-9fb8-c827973e6b74" />

 ./funcex.sh 

 
 ./funcex.sh 1 2

 
cat argshift.sh
```bash
#!/bin/bash 
 while (( "$#" )); do 
  echo $1 
  shift 
done
```
$ chmod 777 argshift.sh

## OUTPUT
$ ./argshift.sh 1 2 3
<img width="818" height="174" alt="image" src="https://github.com/user-attachments/assets/cbabb94f-9e18-4a9b-a7c0-6503be8d79fb" />

 cat argshift1.sh
```bash
 #/bin/bash 
 # store arguments in a special array 
args=("$@") 
# get number of elements 
ELEMENTS=${#args[@]} 
 # echo each element in array  
# for loop 
for (( i=0;i<$ELEMENTS;i++)); do 
    echo ${args[${i}]} 
done
```
$ chmod 777 argshift.sh
## OUTPUT
$ ./argshift.sh 1 2 3
<img width="814" height="258" alt="image" src="https://github.com/user-attachments/assets/196ad658-d797-4889-95c0-069c55e33ad9" />

 
cat argshift.sh
```bash
#!/bin/bash 
set -x 
while (( "$#" )); do 
  echo $1 
  shift 
done
set +x
```
## OUTPUT
 ./argshift.sh 1 2 3
 <img width="817" height="362" alt="image" src="https://github.com/user-attachments/assets/57497b6d-627f-42d3-bdaf-49209a9acf06" />

 
 
cat > nc.awk
```bash
BEGIN{}
{
print len=length($0),"\t",$0 
wordcount+=NF
chrcnt+=len
}
END {
print "total characters",chrcnt 
print "Number of Lines are",NR
print "No of Words count:",wordcount
}
 ```
cat>data.dat
```bash
bcdfghj
abcdfghj
bcdfghj
ebcdfghj
bcdfghj
ibcdfghj
bcdfghj
obcdfghj
bcdfghj
ubcdfghj
```
awk -f nc.awk data.dat
## OUTPUT 
<img width="819" height="582" alt="image" src="https://github.com/user-attachments/assets/170e0bc4-31c5-4106-9bca-74bf42864aa6" />

 
cat > palindrome.sh
```bash
#num=545
echo "Enter the number"
read num
s=0
rev=""
temp=$num
while [ $num -gt 0 ]
do
	# Get Remainder
	s=$(( $num % 10 ))
	# Get next digit
	num=$(( $num / 10 ))
	# Store previous number and
	# current digit in reverse
	rev=$( echo ${rev}${s} )
done
if [ $temp -eq $rev ];
then
	echo "Number is palindrome"
else
	echo "Number is NOT palindrome"
fi
```
## OUTPUT 
<img width="818" height="720" alt="image" src="https://github.com/user-attachments/assets/613fe067-57c1-4731-b1e5-095c744297b7" />
<img width="815" height="72" alt="image" src="https://github.com/user-attachments/assets/d0583937-4560-4780-967b-97fe5b30396b" />


# RESULT:
The Commands are executed successfully.
