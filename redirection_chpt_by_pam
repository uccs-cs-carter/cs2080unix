CS2080 Chapter 5  Page 146
Standard Streams
UNIX has the 3 usual standard streams
	Stream		Stream Descriptors
ksh and bash ONLY
standard input	stdin	keyboard	0
standard output	stdout	monitor	1
standard error	stderr	monitor	2

All of these can be redirected – changed so that their input comes from a file, or their output goes to a file.
5.3 Redirection
To temporarily change these 3 streams we use the redirection operators <, >, >>.
‘<’  Input
Most commands, be default, get their input from the stdin, to change this use  ‘<’.
command < name of file for input
ksh and bash can also use the stream descriptors.
command 0< file
example (using mail):
	mail –s “Subject Line” pcarter3@uccs.edu  < anytextfile	#the file is the message body
example using cd (thank you to Patrick Leedom)
	cd  <   text file with path
Unfortunately examples like:
	cat < filelist.txt 	works the same as	cat filelist.txt
	ls –l < filelist.txt	works the same as	ls –l filelist.txt
‘>’, ’>>’ Output Redirection Operators
To send a command’s output to a file rather than screen
	command > outfile	csh, bash, ksh
	command 1> outfile	bash, ksh
Overwrite existing
	command  1>|  outfile	bash, ksh
command   >|   outfile	bash, ksh
	command   >!  outfile	csh ONLY
Append   >>
	command    >> file	bash, ksh, and csh
command    1>>  file	bash, ksh

NOTE:  ‘>’ overwrites existing files (like >| or >!)
	If noclobber option is off, file is overwritten.
If on, you get an error and file is not overwritten.
5.14 How to turn options ON and OFF 	pg 183
page 184 table 5.10	ksh and bash	csh
set  (ON)	set –o noclobber	set noclobber
unset  (OFF)	set +o noclobber	unset noclobber
display all option settings	set -o	set

Table of some common options page 183 table 5.9
ksh and bash	csh	explanation
noclobber	noclobber	do not overwrite existing files when redirecting
verbose	verbose	print command before execution
xtrace	xtrace may not work at command line	print command with values before execution

2>, 2>>, 2>&1, >& Error Redirection
To send errors to a file.  Remember, only bash and ksh use the stream descriptors (0, 1, 2).  This means that csh can only redirect the errors to the same file as the stdout.

ksh and bash
	2>	send error messages to given file
	2>>	 append to file
	2>&1	 send error wherever you sent the stdout
csh, ksh and bash
	>&	 send errors to wherever you sent the stdout
Examples/ Explanations of Redirection of Both stderr and stdout
1)	to different files (ksh and bash only)
command 1>  outfile   2>  error file	# order makes no difference
ls file1 2>  errorfile   > outfile
2)	to send both to same file (csh, bash, ksh)
If you used method 1), the first redirection opens the file, then the second cannot access it.
Specify where you want the stdout to go and then tell it to merge the output for the stderr
                   command    >   file   >&		csh, ksh, bash
 	some other operators 
 1>&2,    >|	ksh, bash
>&!		csh only
