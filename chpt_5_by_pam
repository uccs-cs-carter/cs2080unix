5.10 Jobs
A job is a USER executed process (i.e. a command is entered at the prompt by the user). This distinguishes them from the generic idea of a process. (jobs are a subset of processes.)

Foreground Jobs
Foreground jobs must be run sequentially, because they take control of the keyboard (stdin) and the monitor (stdout), and don’t release them until they are completed (or suspended).

For foreground jobs, the user can:

<ctrl>+z   – suspend/interrupt
fg 		– resume
<ctrl>+c 	– cancel or terminate job

Background Jobs
A job can be made to execute in the ‘background,’ allowing the user to use the terminal for other things. This is done by placing an ampersand (&) at the end of the command.

$ lpr file &

Problems: If a background job generates output, it will come up on the screen, so you could redirect the output (including errors to a file(s)).

$ cat myfile >& outfile &  //Send errors and output to outfile

When a job is placed in the background, UNIX comes back and gives the user a Job Number and a Process ID (PID) number.

$ sleep 200 &
[1] 568		//Job#, PID

The process id (PID) is the number the system uses. The job number is a “shortcut” that the user can use instead of the pid. If you are running 3 jobs, then they will be numbered 1, 2, and 3, but their pids will be larger and probably out of sequence. Eg. 1549, 1600, 1602.

Background job commands:

stop %n – interrupt/.suspend
bg %n – resume suspended
kill %n – terminate job
fg %n – move background job to foreground



To move a foreground job to the background:
<ctrl>+z	//Suspend it
$ bg 		//Send it to the bg

jobs command
Use jobs to get a list of your jobs, job numbers, and their status

$ jobs
[1] – Running lpr bigfile
[2] + Running sleep 200

Currency flags
Appear after job number

+ 	Usually the first job started
-	Next job started
If a job is suspended, it will become +. The most recently suspended job is +. If you enter a job control command with no job #, the + job is used.

fg %+
kill %%
stop %-
bg %4

Remember, job numbers are only relevant to the particular user and their current session. 

Process ID (pid)
Each process, even if it is a child, is assigned a unique process ID number (pid).

The ps command
Ps will show you the processes and their pids that are running on your terminal.

ps –a shows processes for all users
ps –l long form
ps –e all processes including system and user
ps –f full listing (shows process id of parent (ppid) for child processes)





5.11 Aliases
Allows you to create custom commands – you choose their names.

ksh, bash:
alias chosenName=command
alias copy=cp
alias dir=’ls –l’

csh:
alias aliasName command
alias dir ‘ls –l’

In C shell we can put in placeholders for arguments (filenames, directories, etc). ksh and bash don’t have this.

\!* 	position of only argument
\!^ 	first
\!$ 	last
\!:n nth

alias whofile “who tee \!x”
alias copier “cp \!:1 \!$”

Viewing / Removing Aliases
alias 	– to see a listing of all aliases

unalias 	– to remove an alias
unalias alias1 alias2

-a removes all aliases (REMOVES SYSTEM ALIASES, DO NOT USE)














5.12 Variables p. 176
Variable names start with an alpha character, or an underscore.
The value of a variable is ALWAYS A STRING. You need to use quotes when setting a value, if it contains spaces or special characters.

ksh and bash:
variable=value (no spaces)
myVar=6
x=”Hello Student”

csh
set variable = value (spaces)
set myVar = 6
Set y = “Hello Student”

To see the variable’s contents:
echo $varname
echo the var is $myVar

Note: User defined variables are typically lower case. Also, if you fork a new shell, your variables will now be available in the new shell (they only exist in the instance of the shell they were defined in).

 
5.13 Predefined Variables (System Defined)

Shell variables
These apply only to the current shell (sub-process) you are in. They customize the shell. In csh they are lowercase and can be listed, along with user-defined variables by typing:

$ set

Environmental variables
These are typically set at login (they can be changed at runtime) and stay with you as you move from shell to shell.

ksh and bash:

$ set

csh:

$ setenv


Examples:

$CDPATH ($cdpath in csh)

CDPATH=:$HOME:/bin/usr/files

This variable is used to find a directory when a relative path name is used.

cd directoryName

1.	First the working directory is searched for a matching name. If not found there:
2.	Then it searches your home directory. If not found:
3.	Then it searches the last directory.
$HOME (environmental) (also $home in csh) holds your home directory.

csh:

setenv HOME /home/pcarter

ksh and bash: 

HOME=/home/pcarter

$PATH (Environmental) (also $path in csh)
	When you type in a command (e.g. ls, cat,…), the shell looks through the directories listed in the PATH var, until it finds the executable for that command (so there directories usually end in /bin). $PATH works much like $CDPATH

PATH=/bin:/user/local/bin:/home/pcarter/bin

csh:

setenv PATH /bin:/usr/bin::
setenv PATH $PATH:$HOME/bin
set path = ($path $home/bin . )

$SHELL (environmental) (also shell in csh)
	echo $SHELL (Shows login shell)

$TERM (environmental) (also term in csh)
	Shows terminal type e.g. xterm, vt100

Setting, unsetting, and viewing variables

ksh and bash:
var=value
unset varName
set

csh:
set var = value
setenv VAR value
unset var
unsetenv var
set
setenv

 
5.14 Options
We have already looked at 
	noclobber (don’t automatically overwrite existing files when redirecting)

Two other useful options are (for shell script) 
	verbose – print command before executing
	xtrace – print the command and its arguments’ values before executing

bash:
ON: 			set –o xtrace
OFF: 			set +o xtrace
Show all options: 	set –c

 
5.15 Shell/Environmental Customization

Temporary
	When we set an option, alias, or variable at the command line or in a shell script that we run outselves. Once we log off, theses settings are lost.

Permanent
	Putting special commands, setting predefined variable, and setting options in startup and shutdown files (login and logoff) will create “permanent” changes. 

Here is a rundown of these files:

ksh: (no logout file)
	System 	/etc/profile
	Personal 	~/.profile

These run at login. Personal settings run right after the system profile.

Environmental – environmental files will be run each time the korn shell is 
started. The korn shell’s environmental file does not have a 
standard name, or directory. Its path (with name) is stored 
in the environmental variable $ENV (so you would 
want to set this in ~/.profile.

bash: (uses same system file as ksh)
	System		/etc/profile
	Personal 	~/.bash-profile
			~/.bash_login
			~/.profile	

	Environmental – same as ksh, but filename is in $BASH_ENV

	Logout		~/.bash_logout

Csh:
	Login		~/.login
	Environmental	~/.cshrc
	Logout		~/.logout

	Other (these may or may not exist on your system)		
 		/etc/csh.cshrc
			/etc/csh.login
			/etc/csh.logout
