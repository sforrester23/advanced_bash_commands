# Advanced bash notes

## Linux is extensionless
.txt means nothing!

## Everything is a file

## Linux permisions

### Things a user can do:

- Read(r)
- Write(w)
- Execute(x)

### Users that exist

- owner
  Typically the person who creates the file. however it can be changed.
- group
  Every file belongs a single group. Groups have many users in it and give access to multiple people  
- others
  Everyone else not in a group or the owner.

### Command to change the permissions of file editing:

chmod <permissions> <path/file>

## Streams, Redirect & Piping
- STDIN
  - Standard Input
  - STDIN code is 0
- STDOUT
  - Standard Output
  - STDOUT code is 1
- STDERR
  - Standard Error
  - STDERR code is 2

### Piping & Redirects
Means we can join all of these amazing commands together :taco:

#### Redirecting:
#### This is redirecting of STDOUT
ls > list_of_ls.txt
wc words.txt > word_count.txt
cat words.txt >> word_count.txt

#### This is redirecting of STDIN
wc < words.txt

#### This is redirecting of STDERR
ls non_existing_directory 2 > ls_log.txt

the 2 is very important for logging the error.

(if the non_existing_directory doesn't exist, this will send the error to the log file)

### Piping |
We sent STDOUT and STDERR into files, but what we want is to be able to send outputs into other programs. This is very powerful and is called Piping :taco:

ls | head -3
ls | tail -3 | sort
cat example.txt | grep When


### Process management
Running an instance of a program is a process

- top: top processes
- ps: processes
- ps aux: processes auxiliary (all)
- ps aux | grep vagrant > ps_vagrant_logs.txt: gets only the processes with vagrant in them, inputs to log file for errors
- ps aux | grep vagrant sqjed 231 2 >> ps_vagrant_logerror.txt: gets the error (using 2) messages made by this command, appends it to a file

##### to kill, use kill and pid (process id)
- kill (pid) (pid = process)

### Variables
- We can store variables in bash with MY_VAR = ???
- We can call them with $MY_VAR, e.g. echo $MY_VAR, which will print whatever is stored in your variable to the command line.
- If the variables are called in a file/script, we cannot access them by running the file in bash, they will be identified as empty when this occurs.
- We need to export the variables first, then they become persistent enough for us to use. 
