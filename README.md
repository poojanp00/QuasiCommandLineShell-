# QuasiCommandLineShell

## General Overview
A program for a quasi-command line shell in C called Commando which is designed to have functionalities similar to bash (default shell in many Linux machines), but also to have properties which distinguish it. 

# Usage
An example of usage for this code:

bash% make                                        # Build commando
gcc -Wall -g -c commando.c
gcc -Wall -g -c cmd.c
gcc -Wall -g -c cmdcol.c
gcc -Wall -g -c util.c
gcc -Wall -g -o commando commando.o cmd.o cmdcol.o util.o

bash% commando                                    # Start commando, prompt is @>

@> help                                                      # Show available built-ins
COMMANDO COMMANDS
help               : show this message
exit               : exit the program
list               : list all jobs that have been started giving information on each
pause nanos secs   : pause for the given number of nanseconds and seconds
output-for int     : print the output for given job number
output-all         : print output for all jobs
wait-for int       : wait until the given job number finishes
wait-all           : wait for all jobs to finish
command arg1 ...   : non-built-in is run as a job            # Runs a command as a child process
@> list
JOB  #PID      STAT   STR_STAT OUTB COMMAND
@> ls test_data/                                             # Run ls on test_data/ directory
@> list                                                      # ls now present as a running job
JOB  #PID      STAT   STR_STAT OUTB COMMAND
0    #26532      -1        RUN   -1 ls test_data/ 
@!!! ls[#26532]: EXIT(0)                                     # @!!! is an alert: job finished
@> list                                                      # list again: see exit and output size
JOB  #PID      STAT   STR_STAT OUTB COMMAND
0    #26532       0    EXIT(0)  145 ls test_data/ 
@> output-for 0                                              # show output for job 0 (ls)
@<<< Output for ls[#26532] (145 bytes):
----------------------------------------
3K.txt                                                       # actual output of ls
actual.tmp
diff.tmp
expect.tmp
gettysburg.txt
print_args
print_args.c
quote.txt
README
sleep_print.c
stuff
table.sh
temp.tmp
valgrind.tmp
----------------------------------------


## blah

## blah

