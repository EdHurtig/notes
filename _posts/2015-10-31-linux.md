
# Linux Notes

## Signals

### Send Signal to Proc

`kill -s SIGHUP 12345`

### Common Signals

SIGABRT		6	Terminate (core dump)	Process abort signal
SIGALRM		14	Terminate				Alarm clock
SIGBUS		10	Terminate (core dump)	Access to an undefined portion of a memory object
SIGCHLD		18	Ignore [9]				Child process terminated, stopped,
SIGCONT		25	Continue				Continue executing, if stopped.
SIGFPE		8	Terminate (core dump)	Erroneous arithmetic operation.
SIGHUP		1	Terminate				Hangup.
SIGILL		4	Terminate (core dump)	Illegal instruction.
SIGINT		2	Terminate				Terminal interrupt signal.
SIGKILL		9	Terminate				Kill (cannot be caught or ignored).
SIGPIPE		13	Terminate				Write on a pipe with no one to read it.
SIGQUIT		3	Terminate (core dump)	Terminal quit signal.
SIGSEGV		11	Terminate (core dump)	Invalid memory reference.
SIGSTOP		23	Stop					Stop executing (cannot be caught or ignored).
SIGTERM		15	Terminate				Termination signal.
SIGTSTP		20	Stop					Terminal stop signal.
SIGTTIN		26	Stop					Background process attempting read.
SIGTTOU		27	Stop					Background process attempting write.
SIGUSR1		16	Terminate				User-defined signal 1.
SIGUSR2		17	Terminate				User-defined signal 2.
SIGPOLL		22	Terminate				Pollable event.
SIGPROF		29	Terminate				Profiling timer expired.
SIGSYS		12	Terminate (core dump)	Bad system call.
SIGTRAP		5	Terminate (core dump)	Trace/breakpoint trap.
SIGURG		21	Ignore					High bandwidth data is available at a socket.
SIGVTALRM	28	Terminate				Virtual timer expired.
SIGXCPU		30	Terminate (core dump)	CPU time limit exceeded.
SIGXFSZ		31	Terminate (core dump)	File size limit exceeded

### Useful Links

* http://en.wikipedia.org/wiki/Unix_signal

## Processes

### Listing Proccesses

`ps aux` 

> Show all Processes

`ps aux | grep docker`

> Find all processes that match docker in their details, also matches the grep command.  Not great for automated use but good for manual debugging

`pgrep docker`

> Returns the PIDs which have commands that match the specified string (only searches the first xx characters of the command)

### Killing Processes

`pkill docker`

> Will kill proccesses matching docker (see pgrep)

`kill 12345`

> Sends SIGTERM (?) to the process with the given ID.  Proccess might ignore this, see next

`kill -9 12345`

> Sends SIGKILL to the proccess, This WILL kill the proccess no matter what.

`killall docker`

> Kills all procces with exact name matches


### Useful Links

* 
* http://www.linux.org/threads/kill-commands-and-signals.4423/
