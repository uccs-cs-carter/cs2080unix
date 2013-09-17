this document's copyright allows you to do anything you want with it
the creator of this document is not responsible for any damages
to your mental stability or any disturbances in the force that
occur as a result of this documents use. giving this document to an
alien species does not violate copyrights on this document but is
in violation of the Prime-Directive and is punishable by law. 


*/-----------------------------8/22----------------------------*/

System Software
  -operating system
	-support software



Unix Structure
	The Kernel
	this is the Base OS.. operates directly with hardware, takes care of resource management

	The Shell
	is a Command Line Interpreter (CLI)
	the software that interprets what you type in
	there are a number of Shells
	Bourne -- old not used very much
	Bash --   Bourne again Shell (favorite of shub)
	C Shell -- kind of looks like C

	on Linux -- tcsh

	korn -- ksh -- david korn shell (korn shell looks alot like bash)


Utilities
	Vi, emacs, pico     ---  are all text editors
	e-mail
	date
	calender

Applications
	extras and what not

/*-----------------------------8/24----------------------------*/

when logging out using exit
it will exit you from your current shell
to see your current shell
" echo $shell "  shows your login shell
" echo $0 " shows your current shell or shell script filename or program filename
page 828 has a list of commands that can be used for unix 

homework is page 37-40 sections 1-6 not to turn in

command line:
command_name  [-switches] [argument 1] [argument 2]
command_name -- usually is the name of an executable that runs
[-switches] -- usually modifies the operation and are typically optional
[arguments] -- usually are parameters that tie to the command that you are running

in UNIX, the current directory is called "Working directory"

LS -- shows you the files in the working directory
LS -L  -- shows the files with a detailed listing
LS -A  -- shows ALL files in the working directory including hidden files (to hide a file typically rename it with a period at the name ie.. blah.exe.)
cd -- changes directory from working directory to whatever you type in as a relative directory

date -- shows todays date.. lots of switches available
cal -- shows the calender
who -- shows you a list of who is currently logged on to your particular system
who -h -- shows headers over columns
who -q -- quick list usernames
who -u -- shows user idle times
who -uh -- shows idle and headers
who am i -- shows who you are and additional info
whoami -- just shows your username
man -- stands for manual and is used to get info about a command (ie.. man cal -- will show options for the calender command

man -k calender -- will do a text level search through the manuals and return anything related to the topic
whatis -- will is a much watered down version of "man"
lpr -- will print a file
lpr "filename" -- without the quotes will print to the printer that is local to the computer that unix is running on, not necessarily the client


---------we are approx at chapter 1.8 at this point -------
more commands are on page 24
tty -- shows the name of the device or terminal that you are on
write user-id -- allows you to write a message to someone else
	ctrl D -- will end your write session
stty -- sets your terminal with specific settings
stty erase ^H -- will make it so your backspace key works rather than produce a ^h

ctrl + z -- will suspends a foreground job (can't log off until you take care of the process)
ctrl + c -- aborts or terminates a running foreground job
ctrl + d -- is an EOF(End Of File) command in Unix
fg - resumes a suspended foreground job
script -- record session of what is happening and all I/O of what's happening on monitor
          it's default filename is typescript
script "filename" -- make a custom filename with the above command ("exit" to exit)
script -a "filename" -- will append to an existing file (if file doesn't exist, it will get created)

______COMMAND LINE EDITING______
use up arrow to retrieve previously entered command
use left and right arrow to move about the command
use down arrows to go back through commands if you used up arrow too many times
view a file's contents---
cat "filename" -- this command will dump the files contents to the screen (cat short for concatenate)
more "filename" -- will display a file's contents (like cat) but 1 page at a time and you use spacebar to move to the next screen
less "filename" -- does everything that the "more" command does but also allows you to use the up and down arrows
head -n "filename" --  shows the first N lines of a file where N is an integer
tail -n "filename" --  shows the last N lines of a file where N is an integer
uname -- gives the name of the operating system
uname -a  -- gives lots of info about the operating system
bc -- is the calculator (we will not use this during the course) ctrl D will get out of calculator
to separate commands on the same line use a";"


// ----------------- 8/29 ------------------//
Chapter 2 text editors
VI -- is a good text editor (ascii)
vi "filename" will open a file for editing
if the file does not exist it is created
when you start, you are in command mode
press "insert key" to actually start editing (this might just be the letter "i")
pressing "esc" will put you back in command mode
in the command mode put ":w" will write to the file or save to the file
in the command mode put ":q" will quit the editor
typing ":wq" will write and then quit the editor

Chapter 3 files and file systems ~page 65ish~
File names:
	on some systems, filenames can only be upto 14 characters(ascii)
	on other systems they can go as high as 255 characters
	
File Types:
	periods can go anywhere ie "my.file.is.odd
	unix does not recognize file extensions... YOU HAVE TO KNOW WHAT TO DO WITH THEM
	other software applications still need them though (we are expected to use them
	ls -I
	-rwxrwxrwx 
	dr-xr-xr-x the first letter indicates the type of file
	types of files include:
		ascii or text file
		binary
			executable etc..
		Directories
		-----possible break ------
		Special I/O devices
			C - character special
			they read in 1 ascii character at a time
		Standard streams
			stdin -- keyboard
			stdout -- monitor
			stderr -- monitor
		(B) Block special
		these read in blocks of information at a time rather than reading in one byte at a time
		used when data is being transferred in fixed size units
			eg. 512 bytes
			great if you are reading or writing to a buffer
			AKA buffered I/O
			reading and writing to disk
		(l) is a symbolic (soft) Link
		FIFO and SOCKETS.. used for interprocess and communications
		
	for files that are only 14 characters long the other 2 characters are typically used
	for the inode numbers (this is probably how unix locates files
	directories justv contain a list of files in the given directory and their inode numbers
	
ASCII characters:
	an ascii character is only 1 byte
	0000 0001  == 1
	0000 0010  == 2
	1111 1111  == 255
	
	if a numbe3r is negative, typically the first bit will be set to signify a negative sign
	1000 0010 == -2
	65 in ascii is the letter "A"
	66 in ascii is the letter "B"
	97 in ascii is a lower case "a"

Unix directory Structures
/   --- is the Root directory (that symbols is also used as a separator from other directories
	bin -- typically has executables also shells (csh) and commands
	boot -- page 64
	dev -- where devices are kept, printers, disk drives etc... also terminals
	etc -- system files like password are kept in here
	unix -- this is where the kernel is kept (the base OS)
	home -- usually where user directories are kept
	users --they might also be in this directory
	usr -- software installed for the user are kept here (applications, very much like program files on a windows system)
	root -- System Administrator is called the "ROOT" user, this is his/her directory
	var -- variable size system files

Paths and PathNames
	absolute paths
		this means a full path starting with the "/"
		eg /bin/cat
	relative paths
		use the relative path if you want to start working with the working directory
		NEVER STARTS WITH "/"
		ls -l test/subdir, unix will start with the working directory and move down
		
		
Directory operations
	pwd -- stands for print working directory
	ls -l  -- long list of 
	ls -a  -- lists everything including hidden files
	ls -i  -- lists all files and their inode numbers
	ls -p  -- will put a "/" in front of directory names
	ls -Rp -- shows all subdirectories as well (r is for recursive also sometimes case sensitive)
			  the p makes this a readble list
	*      -- is a wild card for multiple characters (*.txt will show all files that end with .txt)
	?      -- is a wild card for a single character  ( ls ???.txt will show all files that are 3chars + .txt )
	mkdir  -- is the command to make a directory (mkdir /users/faculty/mfechner/subdir) (mkdir subdir -- just goes into the working directory )
	rmdir  -- is the remove directory command (USELESS because the directory must be empty to perform this command
	cd     -- changes directory ( if you use it with no argument it will take you to your home directory NOT root )
			  (can be used with relative paths and with absolute paths)
			  (cd ~    moves you to you $home directory )
			  (cd ~/mysubdir)
			  (cd.. will move up one parent directory )
			  (cd../.. will move up two parent directories )
			  (cd./subdir   --the "." is the working directory, )

File and Directory Operations
	cp      -- copy file or directory
	cp -i   -- Interactive, it will prompt before copying over existing items
			-- CANNOT do a wild card copy within a directory
			-- you can use absolute or relative paths with the cp command
	cp -r   -- (cp -r dira dirb will copy a directory and all of it's sub contents )
			-- if the first argument is a directory, the 2nd must also be a directory COMMON SENSE!!
			-- try to always/only use the -r tag when using directories
	mv		-- is the command to move something (page 100 )
			-- source destination
			-- mv /root/oldfilename ~/newfilename (this moves the file from root user directory to the home directory with a new filename)
			
			(we're skipping LINKS for now but we'll come back to them)
			
	rm		-- is the remove command (pg 106)
	rm -i	-- Interactive and will prompt before removing a file
	rm -r	-- recursive deletion will delete all subfiles and directories
			-- this allows wild cards and can be used with absolute path or with relative paths
	echo rm -r f* -- this will print what the remove command WOULD delete if you performed the command, doen't actually perform the command
			-- you must have the -r to delete directories that are not empty
Links
		link means Hard link, this is a way to give a file more than one name (WHAT!!!!)
		the file must be on the same disk for this to happen, it can appear in the same directory or in multiple directories
	ln		-- the command for a link
			-- ln dog cat -- means that dog and cat are the same file
			--  -rwxrwxrwx 2 ~~~~~blah~~~~ the number 2 means that there are 2 links to this file
	ls -i	1616 cat
			1616 dog
			849  cow
			--  there is only one inode number for each file on the disk, if the inodes are identical that means the files are the same file
			--  IMPORTANT!! how do you tell if 2 files are the same file?
							1. do an ls -i on the files
							2. if the inode numbers are the same number, they are the same file

	-- Unix partitions have what is called an inode table which is similar to an MFT on a windows system
	-- this contains information of inode#   # of links   address on the disk   owner of file   priveleges   dates
	
	-- IMPORTANT!! what is the inode number?
				   it is the file's unique address on the disk (not it's physical address on the disk)
				   indirectly the address of the file on the disk
			-- Aliasing, if you want to delete a file that has links, you must delete all of it's links
			-- you cannot link across drives, and cannot link to directories
	
// 9-7-11 //
	
	-- Inode tables do not actually have file names
	-- it typically has inode numbers, # of links and address on the disk
	
Symbolic Links (aka soft links)
	-- each physical device like floppy's, hard disks, flash drives ... manages it's own files and directories (in the hardware)
	-- this prevents us from hard-linking between devices
	-- instead we can use a soft link (is pretty much a shortcut)
	-- a symbolic link contains the actual pathname to the file, it can be used to link to files on different devices
	
	ln -s  -- is the command to create a symbolic link
	
	ln -s /home/cory corylink
	-- now corylink will show up in the working directory
	
	-- if you do an ls -i on the directory 
	-- the inode numbers will be different between the symbolically linked file and the original file
	-- if the original file is deleted and you try to call the symbolic link, you will get an error (link still exists but file doesn't exist anymore)
	-- deleting a symbolic link will have no effect on the original file
	
the Find command (roughly page 108)

	-- find searches a directory tree using the selected search criteria
	-- NOTE!! it tends to ignore the rules that other commands use so PAY ATTENTION!!!
	find path -criteria -criteria -criteria       -- general usage
	find /home/fechner -name myfile -print
	           |          |     |      |
	starting directory    | filename   |-> means to use stdout to print it out to the screen (not needed on linux platforms)
					indicates that your searching for a filename
	-- if you accidentally do "find ." to list all files, CTRL+C will end the search
	-- searches that include wildcards must use single quotes
	find . -name 't*.c'       = example
	
	find /home -type  -- looks for files of specified type
	-- 'd' means directory 'f' means file 'l' means SYMBOLIC link (not hard)
	find path -ntime     -- find files modified at least n days ago
	find path -size      -- finds files of size n blocks
	find path -perm      -- finds files based on octal permission code
	find path -links n    -- finds files by number of links
	find path -inum n    -- finds file based on inode number
	
	combining criteria  using -o  which kinda means or
	the criteria must be placed in parentheses
	the parens must be escaped.
	find . \( -name new.c -o -name old.c \)
				--escape characters do 2 things
					--turns off meaning of special characters and use their literal value
					--turns on the special meaning of normal characters (not all normal characters have a special meaning)
	find path criteria -exec command {} ";"
						|-> perform command on all files that were found
						
	find /home/fechner -type f -exec cp {} /home \;
	-- the above command will copy all the found files from the fechner directory to the home command
	
	-ok    -- this is just like -exec, but it asks for confirmation (Y/N) before each action
	-newer   
		find . -name file-newer path/file
									|-> find files newer than this
	
---------9/12/11-------- homework not to hand in = pg 140 sessions 14II number 9 and 13

----------------Chapter 4 - File Permissions-------------------

	aaron does an "ls -l" and gets:
	-rw-r--r-- 1 carter cs2080 120 aug28 1030 myfile
	
		-rw		r--		r--		1		carter		cs2080		120		aug28		10:30		myfile
		User	group	other	links	Owner		group		size	|------modification time-----|
		
		--user		- typically the owner (you)
		--group		- the user group, groups are set up by system administrators
		--others	- Not User and Not Group
	-- each of the above has it's own set of permissions
	rwxrwxrwx       r = read
					w = write/edit or delete
					x = execute, you can execute the file
					
	r--   means that you can read but you can't write or execute, "-" means the permission is denied
	--x   means that you can execute but you can't read or write
	
----- 4.3 setting file permissions ------
	2 methods	-symbolic (don't need to know)
				-absolute (NEED TO KNOW!!)
	both of these use the command "chmod" pronounced (cha-mod)
		symbolic
		chmod +w-x myfile
			-- adds write permission
			-- takes away execute permission
			-- read permission is unchanged
		-- "+" is to add permission
		-- "-" is to take away permission
		-- "=" is to set exactly'
		
	Directories need pass through permissions
	-- if you don't have permission for a parent (and all sub-parent) directories, you can't access the file or directory.
	
	-- giving -r permission--
	file - can look at file contents (ie cat, more, head, tail)
	directory - can list the filenames
		 -x permission should be given with read
	-- giving -w permission--
	file - can be edited
	directory - the directory it's files can be deleted, you can also add files to the directory
	-- giving -x permission--
	file - can be run if it is an executable or a shell script
	directory - can be accessed (cd to directory or through it)
	
	page 125, to reference a subdirectory or file, you MUST have execute permissions to ALL directories in the absolute path to the file or directory
	
	for chmod--
	u - set user permissions
	g - set group permissions
	o - set own permissions
	a - set all permissions
	
	examples : chmod g+rw a file		add read and write permission for group
			   chmod a=r f*				everybody gets permission for "read" for all files starting with "f"
	there is a recursive option R, will change all files and subdirectories (we do not need to know this)
				-- this is a capital R because lowercase r is for read permissions  -- (al broulliette minus 100,000 points lol)
				
	----- Absolute (octal) codes page 128 ----- (not the vodka)
	
	chmod 755 myfile
		--  7		5		5 --
		   user	  group   other
		   111		101		101
		   
		   7 = 111 = read write xecute
		   6 = 110 = read write
		   5 = 101 = read execute
		   4 = 100 = read only
		   3 = 011 = read and execute
		   2 = 010 = write only (useless lol)
		   1 = 001 = execute only
		   0 = 000 = no soup for you
	octal chmod sets all permissions wiping out permission settings
	
	
----- User Masks 4.4 ----- page 131
	is linked to both files and directories and will affect both
	default setting for directories is 777
	default setting for files is 666 ( also dan D's student number)
	but the default is combined with the user mask(umask)
	to set initial permissions.
	umask -> tells us what the umask is (or use to set the umask)
	gives you a 4/3 digit number like 0 0 0 2
									  | | | -other
									  | | ---group
									  | -----user
									  -------sticky bit
	take away these permissions for new files and directories
	unmask only takes away permissions, NOT gives permissions
	it will take away what ever permission is set (if the permission is currently not disabled)
	
	Stickybits -- sometimes umask has 4 digits, the extra digit represents special file permissions
		setuid -- set user id
		setgid -- set group id
	4 -- set user id on execution
	2 -- set user groups on execution
	1 -- stickybit - used on public directories, allow users to write files to public directories
	
----- Redirection Chapter 5 ------
										Stream descriptors only Bash and ksh
Standard input	-- stdin	--keyboard	--0
Standard output	-- stdout	--monitor	--1
Standard error	-- stderr	--monitor	--2
all of these can be redirected
	-they can be changed so input or output comes from a file
	
	REDIRECTION--
	to temporarily change these 3 stream we use redirection operators like : <,>,>>
	most commands get their input from stdin, to change use "<"
	example:
		mail -s "subject" pcarter3@uccs.edu < anytextfile
		mail -s "subject" pcarter3@uccs.edu 0< anytextfile  (use this for bash and ksh)
		this uses the contents of the text file as the body of the e-mail (input came from the file rather than from the keyboard)
	example:  (print working directory)
		pwd > working.txt
		cd < working.txt
		mv working.txt test				<-- patrick's example
		cd test
		ls -l will show the new file
		
	Input redirection
	ls -l < filelist.txt 
	
	> and >> are Output redirection operators
	
	to send a command output to a file rather than the screen
	command > outfile			--- general use of the command for csh, ksh, and bash
	To force over-write!!
	command 1>| outfile
				using the "|" character right above the enter key  ksh bash only
	command >! outfile
				this is for csh only
	To append to a file
	command >> outfile             this is true for all 3 shells
	
	NOTE ">" this will over-write existing files if noclobber option is off file is overwritten
			 if noclobber option is on it will give an error (what in the world is noclobber option)
			 
	-----roughly chapter 5.14 page 183, 184ish------
	set    (on)
	unset  (off)
	display all settings
	
	example -- set -o noclobber
			-- set +o noclobber			these are for ksh and bash
			-- set -o
			
			-- set noclobber
			-- unset noclobber			these are for csh
			-- set
	noclobber is a setting for over-write for redirection only (not anything else)
	
	COMMON OPTIONS page 183ish
	ksh			bash		|		csh		|		verbose
	-----------------------------------------------------------------------------------------------|
	noclobber				| noclobber		|	do not overwrite files when redirecting
	verbose					| verbose		|	print command before executing
	xtrace					| 				|	print command with variable values before execution
	
	csh allows yout to set xtrace but doesn't actually do anything   :(
	
	ERROR redirection
	to send errors to file, remember ksh and bash only for stream descriptors
	this means csh can only redirect errors to same file as output
	
	command 2> errorfile				-- for ksh and bash
	2>>			-- is to append
	2>&1		-- send errors to wherever you sent stdout
	
	
	send to 2 different files
	command 1> outfile 2> errorfile
	ls -l 2> errorfile 1> outfile			the order you put them in makes no difference
	
	------------9/19/11-----------------
	
	quiz on wednesday will cover redirection quoting and maybe pipes
	
	-----------PIPES chapter 5.4------------
	the "|" character is the pipe character located above the enter key
	it is used to send output from one command to another command
	the stdout of the first command becomes the stdin of the next class
	example
		pwd > filetoprint       (print working directory)
		lpr filetoprint
			instead you could type
		pwd | lpr      <-- the output of pwd becomes the input of lpr
		
		pipes can be strung together ie:
		command1 | command2 | command3 | etc......
		
	Conditions for this to work
		-the first command must produce output to "stdout"
		-the rest of the commands must be able to take input from "stdin" and have output to "stdout"
		
	----------TEE chapter 5.5 ------------
	"tee" reads from stdin
	writes to stdout, or one or more files
	"she put many "*"s on the board for this one lol
	to append to a file use -a, 
	example:    ls |tee -a list.txt
								if file doesn't exist, it is created
								if file DOES exist, it is appended to
	
	---------chapter 5.6 4 types of command execution----------'
	'
	1- Sequenced, cram all your commands on 1 line and use semicolon to separate commands
		ls -l > list.txt; cd..; ls -l >> list.txt
		commands have no dependence on eachother
	2- Grouped, commands are separated with () or {} 
		(pwd; ls -l)
		
	3- Chained, piping (output from first command becomes input for next command)
	
	4- Conditional, and "&&" or "||" commands typically execute sequentially
		if first command is false, 2nd command doesn't execute
		ls myfile && cat myfile

		
-----------------chapter 5.8 Quotes --------------------------
	Meta Characters
		they are characters that can either be text or they can have special meaning like \n, (), ;
		double quotes will allow escape characters like \n etc....
		single quotes treat everything as LITERAL  echo '\n my bag %d is missing\\'
		the output for that would be  \n my bag %d is missing\\
