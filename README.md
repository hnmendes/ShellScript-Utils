# ShellScript-Utils
A repository with some commands that i want to learn about it.

# → How to work the logics in bash.

&&	Logical AND	if [ "$foo" -ge "0" ] && [ "$foo" -le "9"]

||	Logical OR	if [ "$foo" -lt "0" ] || [ "$foo" -gt "9" ] (not in Bourne shell)

^	Start of line	grep "^foo"

$	End of line	grep "foo$"

=	String equality (cf. -eq)	if [ "$foo" = "bar" ]

!	Logical NOT	if [ "$foo" != "bar" ]

$$	PID of current shell	echo "my PID = $$"

$!	PID of last background command	ls & echo "PID of ls = $!"

$?	exit status of last command	ls ; echo "ls returned code $?"

$0	Name of current command (as called)	echo "I am $0"

$1	Name of current command's first parameter	echo "My first argument is $1"

$9	Name of current command's ninth parameter	echo "My ninth argument is $9"

$@	All of current command's parameters (preserving whitespace and quoting)	echo "My arguments are $@"

$*	All of current command's parameters (not preserving whitespace and quoting)	echo "My arguments are $*"

-eq	Numeric Equality	if [ "$foo" -eq "9" ]

-ne	Numeric Inquality	if [ "$foo" -ne "9" ]

-lt	Less Than	if [ "$foo" -lt "9" ]

-le	Less Than or Equal	if [ "$foo" -le "9" ]

-gt	Greater Than	if [ "$foo" -gt "9" ]

-ge	Greater Than or Equal	if [ "$foo" -ge "9" ]

-z	String is zero length	if [ -z "$foo" ]

-n	String is not zero length	if [ -n "$foo" ]

-nt	Newer Than	if [ "$file1" -nt "$file2" ]

-d	Is a Directory	if [ -d /bin ]

-f	Is a File	if [ -f /bin/ls ]

-r	Is a readable file	if [ -r /bin/ls ]

-w	Is a writable file	if [ -w /bin/ls ]

-x	Is an executable file	if [ -x /bin/ls ]

( ... )	Function definition	function myfunc() { echo hello }

# → Permissions

⇝ Changing file and folder permissions

⇝ Use the following commands to change file or folder permissions:

chmod (change file modes)
chown (change file owner)
chgrp (change file group owner)

⇝ The following letters represent

* " u " - user/owner
* " g " - group owner
* " o " - all other users
* " a " - for all: user/owner, group owner and all other users
* " r " - read permission
* " w " - write permission
* " x " - execute permission

⇝ Examples of replacing and setting new permissions

(Note: Do not use space between any of the statements.
Example DO NOT TYPE: u = rwx)

 * chmod u=rwx filename
 * chmod u=rwx directoryname
 * chmod -R u=rwx directoryname

 * chmod g=rx filename
 * chmod g=rx directoryname
 * chmod -R g=rx directoryname

 * chmod o=r filename
 * chmod o=r directoryname
 * chmod -R o=r directoryname

 * chmod u=rwx,g=rx,o=r filename
 * chmod u=rwx,g=rx,o=r directoryname
 * chmod -R u=rwx,g=rx,o=r directoryname
 * "-R" - means recursively change permissions of directories and their contents.
 * chmod a=rwx filename
 * "a" - for all: user/owner, group owner and all other users.

⇝ Examples of adding or taking away permissions from the current permissions

 * chmod u+w filename
 * chmod u+w directoryname
 * chmod -R u+w directoryname

 * chmod g+w filename
 * chmod g+w directoryname
 * chmod -R g+w directoryname

 * chmod o-r filename
 * chmod o-r directoryname
 * chmod -R o-r directoryname
 
⇝ Modifying multiple permissions examples:

* chmod u+w,g+x,o-r filename
* chmod ug+rwx filename
* chmod ugo+rwx filename
* chmod u+w,g+x,o-r directoryname
* chmod ug+rwx directoryname
* chmod ugo+rwx directoryname
* chmod -R u+w,g+x,o-r directoryname
* chmod -R ug+w,o-r directoryname
* chmod -R ugo+rwx directoryname
* "-R" - means recursively change permissions of directories and their contents.

⇝ Examples of changing user/owner:

* chown username filename
* chown -R username directoryname

⇝ Examples of changing user/owner:

* chown username filename
* chown -R username directoryname

⇝ Examples of changing user/owner:

* chgrp groupname filename
* chgrp -R groupname directoryname

* "-R" - means recursively change permissions of directories and their contents.

⇝ Here is some more examples:

* chmod u=rwx,g=rw,o=rx myfile.txt

⇝ Now view the result:

* ls -l myfile.txt

-rwxrw-r-x 1 user group 9482 Jan 16 16:29 myfile.txt

* chmod -R u=rwx,g=rx,o=r directoryname

⇝ Now view the result:

ls -l directoryname

drwxr-xr-- 6 user group 204 Dec 30 06:37 images

-rwxr-xr-- 1 user group 5754 May 20 2005 index.html

-rwxr-xr-- 1 user group 9482 Jan 16 16:29 mypage.html

* chown -R www directoryname

⇝ Now view the result:

ls -l directoryname

drwxr-xr-- 6 www group 204 Dec 30 06:37 images

-rwxr-xr-- 1 www group 5754 May 20 2005 index.html

-rwxr-xr-- 1 www group 9482 Jan 16 16:29 mypage.html

* chgrp -R www directoryname

⇝ Now view the result:

* ls -l directoryname

drwxr-xr-- 6 www www 204 Dec 30 06:37 images

-rwxr-xr-- 1 www www 5754 May 20 2005 index.html

-rwxr-xr-- 1 www www 9482 Jan 16 16:29 mypage.html 
