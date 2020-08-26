# shell-lab


### This is a simple Unix Shell that supports foreground and background processes and job control.

#### To run this project in command line:
1. type `make` to compile the code

2. then, type `./tsh` to run the project

3. after the prompt `tsh> `, you can type any command that tsh supports

#### Here is an overview of tsh features:
* The command line typed by the user should consist of a name and zero or more arguments, all separated by one or more spaces. 
If name is a built-in command, then tsh will handle it immediately and wait for the next command line. 
Otherwise, tsh will assume that name is the path of an executable file, which it loads and runs in the context of an initial child process.

* Typing ctrl-c (ctrl-z) will cause a `SIGINT (SIGTSTP)` signal to be sent to the current foreground
job, as well as any descendents of that job. If there is no foreground job, then the signal will have no effect.

* If the command line ends with an ampersand &, then tsh will run the job in the background. Otherwise, it will run the job in the foreground.

* Each job can be identified by either a process ID (PID) or a job ID (JID), which is a positive integer
assigned by tsh. JIDs will be denoted on the command line by the prefix `%`. For example, `%5`
denotes JID 5, and `5` denotes PID 5.

* tsh supports the following built-in commands:

  * The quit command terminates the shell.
  
  * The jobs command lists all background jobs.
  
  * The `bg <job>` command restarts `<job>` by sending it a `SIGCONT` signal, and then runs it in
the background. The `<job>` argument can be either a PID or a JID.

  * The `fg <job>` command restarts `<job>` by sending it a `SIGCONT` signal, and then runs it in
the foreground. The `<job>` argument can be either a PID or a JID.
  
* tsh reaps all of its zombie children. If any job terminates because it receives a signal that
it didn’t catch, then tsh will recognize this event and print a message with the job’s PID and a
description of the offending signal.

* tsh does not support pipes (`|`) or I/O redirection (`<` and `>`).
