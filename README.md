# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0;
}
```

##OUTPUT

![Screenshot 2025-05-08 083244](https://github.com/user-attachments/assets/daaf3679-4636-46f3-b508-934a23f92863)

## C Program to create new process using Linux API system calls fork() and exit()

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>  // Needed for fork(), getpid(), getppid(), sleep()

int main() {
    int pid;
    pid = fork();  // Create a new process

    if (pid == 0) {
        // Child process
        printf("I am the child, my PID is %d\n", getpid());
        printf("My parent PID is: %d\n", getppid());
        exit(0);
    } else if (pid > 0) {
        // Parent process
        printf("I am the parent, my PID is %d\n", getpid());
        sleep(100);  // Let the parent sleep so child becomes orphan after it exits
        exit(0);
    } else {
        // fork failed
        perror("fork");
        exit(1);
    }
}
```

##OUTPUT

![Screenshot 2025-05-08 084315](https://github.com/user-attachments/assets/97586a6a-f42e-401d-8c24-ba7fe2b03ad4)

## C Program to execute Linux system commands using Linux API system calls exec() family

```
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
int main()
{
	printf("Running ps with execlp\n");
	execlp("ps", "ps", "ax", NULL);
	printf("Done.\n");
	exit(0);
}
```

##OUTPUT

![image](https://github.com/user-attachments/assets/849054d4-c50f-41bd-ac8e-6e30ba1eb566)


# RESULT:
The programs are executed successfully.
