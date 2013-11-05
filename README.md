forkprocs.c
===========

一个测试fork()返回值并区分父子进程的简单程序

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
    pid_t  child_pid;
    int i = 1;
    printf("the main program process ID is %d\n", (int)getpid());
    child_pid = fork();/* 创建子进程 */
    if(child_pid != 0)/* child_pid 不为0说明在父进程中 */
    {
        i = 0;
        printf("this is the parent process , with id %d and i = %d\n" , (int)getpid(), i);
        printf("the child's process ID is %d\n", (int)child_pid);
    }
    else /* child_pid 为0说明在子进程中 */
    {
        printf("this is the child process , with id %d and i = %d\n",(int)getpid(), i);
    }
    return 0;
}
