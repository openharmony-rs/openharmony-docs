# Seccomp-Provided System Call List
<!--Kit: Common-->
<!--Subsystem: Security-->
<!--Owner: @ren_ze_hua-->
<!--Designer: @JerryH1011-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## Overview

Secure Computing Mode (seccomp) is a lightweight system call filtering mechanism provided by the Linux kernel. Since its introduction in Linux 2.6.12, seccomp has evolved from a simplified form that supports only the strict mode to a mainstream form that is centered on Berkeley Packet Filter (seccomp-BPF).

OpenHarmony uses the seccomp-BPF mode, which allows you to customize system call filtering rules using BPF. This mode precisely restricts the range of system calls that can be invoked by processes, reducing the risks posed by malicious code exploiting kernel vulnerabilities and improving the security isolation of processes, containers, and applications.

This topic focuses on the system call lists provided by seccomp for different device types in the OpenHarmony environment. It aims to help you:

1. Quickly understand the differences in system call control under seccomp for different devices.

2. Select appropriate APIs based on service scenarios to avoid function exceptions caused by system call restrictions.

## Introduction to the Seccomp Mechanism

- Basic mechanism

    Seccomp policies exist in the form of policy files. During compilation and building, a policy file is parsed to generate a source file that contains the BPF instruction policies, and then the source file is compiled into a dynamic policy library. During the startup of a user-space process, seccomp system calls are invoked to load the BPF instruction policies into the kernel.

- Basic features
    - A child process inherits the seccomp policies of its parent process.
    - After a seccomp policy is loaded to the kernel during process running, the policy is stored in the memory as a singly linked list and cannot be modified.
    - Seccomp policies can be set for a process for multiple times. When a process executes a system call, the kernel traverses the policies specified for the nodes in the singly linked list and compares the policies to obtain the policy with the highest priority.

## Determining Whether a Process Is Terminated Due to the Seccomp Mechanism

Check the process fault logs. If the error cause is **signal:SIGSYS** and the stack top is in the ld-musl-{architecture}.so.1 library, the process termination may be caused by the seccomp mechanism.

```shell
cat /data/log/faultlog/faultlogger/cppcrash-xxxx
```
Incorrect example:
```txt
Process name:com.example.myapplication
Reason:Signal:SIGSYS(UNKNOWN)
Fault thread Info:
Tid:13893, Name:e.myapplication
#00 pc 000a5d30 /system/lib/ld-musl-arm.so.1(sethostname+16)(584c9d0a0e9000497bb0d66799a9526a)
#01 pc 00002f68 /data/storage/el1/bundle/libs/arm/libentry.so(test()+64)
```

## Seccomp Symbols

| System Call       | Supported Architecture     |Supported Device    |Remarks    |
| ------------ | ----------------- | ----------------- | ----------------- |
| mbind | all | PC|- |
| mmap | arm64 | All platform devices|- |
| mmap | riscv64 | All platform devices|- |
| mmap2 | arm | All platform devices|- |
| munmap | all | All platform devices|- |
| mremap | all | All platform devices|- |
| mprotect | all | All platform devices|- |
| msync | all | All platform devices|- |
| mlock | all | All platform devices|- |
| munlock | all | All platform devices|- |
| mlockall | all | All platform devices|- |
| munlockall | all | All platform devices|- |
| mincore | all | All platform devices|- |
| madvise | all | All platform devices|- |
| mlock2 | all | All platform devices|- |
| membarrier | all | All platform devices|- |
| brk | all | All platform devices|- |
| remap_file_pages | arm | All platform devices|- |
| fork | arm | All platform devices|- |
| vfork | arm | All platform devices| -|
| exit | all | All platform devices| -|
| exit_group | all | All platform devices| -|
| waitid | all | All platform devices|- |
| wait4 | all | All platform devices|- |
| set_tid_address | all | All platform devices| -|
| setpgid | all | All platform devices|- |
| getpgid | all | All platform devices|- |
| getsid | all | All platform devices|- |
| setsid | all | All platform devices|- |
| getpid | all | All platform devices| -|
| getppid | all | All platform devices|- |
| gettid | all | All platform devices|- |
| uname | all | All platform devices|- |
| personality | all | All platform devices|- |
| execve | all | All platform devices|- |
| execveat | all | All platform devices| -|
| clone | all | All platform devices| Only calls that do not contain the following namespace flags are allowed:<br>**CLONE_NEWNS**,<br>**CLONE_NEWPID**,<br>**CLONE_NEWNETCLONE_NEWCGROUP**,<br>**CLONE_NEWUTS**,<br>**CLONE_NEWIPC**,<br>and **CLONE_NEWUSER**.<br>If the conditions are met, **ALLOW** is returned. Otherwise, **TRAP** is returned.|
| io_setup | all | All platform devices|- |
| io_destroy | all | All platform devices|- |
| io_submit | all | All platform devices|- |
| io_cancel | all | All platform devices|- |
| io_getevents | all | All platform devices|- |
| openat | all | All platform devices|- |
| open | arm | All platform devices|- |
| close | all | All platform devices|- |
| creat | arm | All platform devices|- |
| read | all | All platform devices|- |
| write | all | All platform devices|- |
| readv | all | All platform devices|- |
| writev | all | All platform devices|- |
| pread64 | all | All platform devices|- |
| pwrite64 | all | All platform devices|- |
| preadv | all | All platform devices|- |
| pwritev | all | All platform devices|- |
| preadv2 | all | All platform devices|- |
| pwritev2 | all | All platform devices|- |
| lseek | all | All platform devices|- |
| _llseek | arm | All platform devices|- |
| truncate | all | All platform devices|- |
| ftruncate | arm64 | All platform devices|- |
| ftruncate | riscv64 | All platform devices|- |
| truncate64 | arm | All platform devices|- |
| ftruncate64 | arm | All platform devices|- |
| fallocate | all | All platform devices|- |
| fcntl | all | All platform devices|- |
| fcntl64 | arm | All platform devices|- |
| flock | all | All platform devices|- |
| mknodat | all | All platform devices|- |
| mkdirat | all | All platform devices|- |
| mkdir | arm | All platform devices|- |
| rmdir | arm | All platform devices|- |
| unlinkat | all | All platform devices|- |
| unlink | arm | All platform devices|- |
| symlinkat | all | All platform devices|- |
| symlink | arm | All platform devices|- |
| linkat | all | All platform devices|- |
| link | arm | All platform devices |- |
| renameat | arm | All platform devices|- |
| renameat | arm64 | All platform devices|- |
| rename | arm | All platform devices|- |
| renameat2 | all | All platform devices|- |
| chdir | all | All platform devices|- |
| fchdir | all | All platform devices|- |
| faccessat | all | All platform devices|- |
| access | arm | All platform devices|- |
| faccessat2 | all | All platform devices|- |
| getcwd | all | All platform devices|- |
| getdents64 | all | All platform devices|- |
| getdents | arm | All platform devices |- |
| readlinkat | all | All platform devices|- |
| readlink | arm | All platform devices|- |
| newfstatat | arm64 | All platform devices|- |
| newfstatat | riscv64 | All platform devices|- |
| fstatat64 | arm | All platform devices|- |
| fstat | arm64 | All platform devices|- |
| fstat | riscv64 | All platform devices|- |
| stat64 | arm | All platform devices|- |
| lstat64 | arm | All platform devices|- |
| fstat64 | arm | All platform devices|- |
| statfs | arm64 | All platform devices|- |
| statfs | riscv64 | All platform devices|- |
| statfs64 | arm | All platform devices|- |
| fstatfs | arm64 | All platform devices|- |
| fstatfs | riscv64 | All platform devices|- |
| fstatfs64 | arm | All platform devices|- |
| sync | all | All platform devices|- |
| fsync | all | All platform devices|- |
| fdatasync | all | All platform devices|- |
| syncfs | all | All platform devices|- |
| sync_file_range | arm64 | All platform devices|- |
| sync_file_range | riscv64 | All platform devices|- |
| sync_file_range2 | arm | All platform devices |- |
| utimensat | all | All platform devices|- |
| utimensat_time64 | arm | All platform devices|- |
| pipe2 | all | All platform devices|- |
| pipe | arm | All platform devices|- |
| dup | all | All platform devices|- |
| dup3 | all | All platform devices|- |
| dup2 | arm | All platform devices |- |
| sendfile | all | All platform devices|- |
| sendfile64 | arm | All platform devices|- |
| copy_file_range | all | All platform devices|- |
| vmsplice | all | All platform devices|- |
| splice | all | All platform devices|- |
| tee | all | All platform devices|- |
| readahead | all | All platform devices|- |
| fadvise64 | arm64 | All platform devices|- |
| fadvise64 | riscv64 | All platform devices|- |
| fadvise64_64 | arm | All platform devices|- |
| quotactl | all | All platform devices|- |
| pivot_root | riscv64 | All platform devices|- |
| statx | all | All platform devices|- |
| setxattr | all | All platform devices|- |
| lsetxattr | all | All platform devices|- |
| fsetxattr | all | All platform devices|- |
| getxattr | all | All platform devices|- |
| lgetxattr | all | All platform devices|- |
| fgetxattr | all | All platform devices|- |
| listxattr | all | All platform devices|- |
| llistxattr | all | All platform devices|- |
| flistxattr | all | All platform devices|- |
| removexattr | all | All platform devices|- |
| lremovexattr | all | All platform devices|- |
| fremovexattr | all | All platform devices|- |
| fchownat | all | All platform devices|- |
| fchown | arm64 | All platform devices|- |
| fchown | riscv64 | All platform devices|- |
| fchown32 | arm | All platform devices|- |
| lchown32 | arm | All platform devices|- |
| chown32 | arm | All platform devices|- |
| getuid | all | All platform devices|- |
| getuid32 | arm | All platform devices|- |
| geteuid | arm64 | All platform devices|- |
| geteuid | riscv64 | All platform devices|- |
| geteuid32 | arm | All platform devices|- |
| getgid | arm64 | All platform devices|- |
| getgid | riscv64 | All platform devices|- |
| getgid32 | arm | All platform devices|- |
| getegid | arm64 | All platform devices|- |
| getegid | riscv64 | All platform devices|- |
| getegid32 | arm | All platform devices|- |
| setresuid | arm64 | All platform devices|- |
| setresuid | riscv64 | All platform devices|- |
| setresuid32 | arm | All platform devices|- |
| getresuid | arm64 | All platform devices|- |
| getresuid | riscv64 | All platform devices|- |
| getresuid32 | arm | All platform devices|- |
| getresgid | arm64 | All platform devices|- |
| getresgid | riscv64 | All platform devices|- |
| getresgid32 | arm | All platform devices|- |
| getgroups | arm64 | All platform devices|- |
| getgroups | riscv64 | All platform devices|- |
| getgroups32 | arm | All platform devices|- |
| setpriority | all | All platform devices|- |
| getpriority | all | All platform devices|- |
| capget | all | All platform devices|- |
| capset | all | All platform devices|- |
| umask | all | All platform devices|- |
| getrlimit | arm64 | All platform devices|- |
| getrlimit | riscv64 | All platform devices|- |
| ugetrlimit | arm | All platform devices|- |
| setrlimit | all | All platform devices|- |
| prlimit64 | all | All platform devices|- |
| fchmod | all | All platform devices|- |
| fchmodat | all | All platform devices|- |
| chmod | arm | All platform devices|- |
| kill | all | All platform devices|- |
| tkill | all | All platform devices|- |
| tgkill | all | All platform devices|- |
| sigaltstack | all | All platform devices|- |
| rt_sigsuspend | all | All platform devices|- |
| rt_sigaction | all | All platform devices|- |
| sigaction | arm | All platform devices|- |
| rt_sigprocmask | all | All platform devices|- |
| rt_sigpending | all | All platform devices|- |
| rt_sigtimedwait | all | All platform devices|- |
| rt_sigtimedwait_time64 | arm | All platform devices|- |
| rt_sigqueueinfo | all | All platform devices|- |
| rt_sigreturn | all | All platform devices|- |
| sigreturn | arm | All platform devices|- |
| signalfd4 | all | All platform devices|- |
| timerfd_create | all | All platform devices|- |
| timerfd_settime | all | All platform devices|- |
| timerfd_gettime | all | All platform devices|- |
| timerfd_gettime64 | arm | All platform devices|- |
| timerfd_settime64 | arm | All platform devices|- |
| timer_create | all | All platform devices|- |
| timer_gettime | all | All platform devices|- |
| timer_gettime64 | arm | All platform devices|- |
| timer_getoverrun | all | All platform devices|- |
| timer_settime | all | All platform devices|- |
| timer_settime64 | arm | All platform devices|- |
| timer_delete | all | All platform devices|- |
| clock_gettime | all | All platform devices|- |
| clock_gettime64 | arm | All platform devices|- |
| clock_settime64 | arm | All platform devices|- |
| clock_getres | all | All platform devices|- |
| clock_getres_time64 | arm | All platform devices|- |
| clock_nanosleep | all | All platform devices|- |
| clock_nanosleep_time64 | arm | All platform devices|- |
| clock_adjtime64 | arm | All platform devices|- |
| getitimer | all | All platform devices|- |
| setitimer | all | All platform devices|- |
| nanosleep | all | All platform devices|- |
| futex | all | All platform devices|- |
| futex_time64 | arm | All platform devices|- |
| rt_tgsigqueueinfo | all | All platform devices|- |
| semtimedop_time64 | arm | All platform devices|- |
| pidfd_send_signal | all | All platform devices|- |
| shmget | all | PC |- |
| socket | all | All platform devices|- |
| socketpair | all | All platform devices|- |
| bind | all | All platform devices|- |
| listen | all | All platform devices|- |
| accept | all | All platform devices|- |
| accept4 | all | All platform devices|- |
| connect | all | All platform devices|- |
| getsockname | all | All platform devices|- |
| getpeername | all | All platform devices|- |
| sendto | all | All platform devices|- |
| recvfrom | all | All platform devices|- |
| setsockopt | all | All platform devices|- |
| getsockopt | all | All platform devices|- |
| shutdown | all | All platform devices|- |
| sendmsg | all | All platform devices|- |
| recvmsg | all | All platform devices|- |
| recvmmsg | all | All platform devices|- |
| recvmmsg_time64 | arm | All platform devices|- |
| sendmmsg | all | All platform devices|- |
| sched_setparam | all | All platform devices|- |
| sched_setscheduler | all | All platform devices|- |
| sched_getscheduler | all | All platform devices|- |
| sched_getparam | all | All platform devices|- |
| sched_setaffinity | all | All platform devices|- |
| sched_getaffinity | all | All platform devices|- |
| sched_yield | all | All platform devices|- |
| sched_get_priority_max | all | All platform devices|- |
| sched_get_priority_min | all | All platform devices|- |
| sched_rr_get_interval | all | All platform devices|- |
| sched_rr_get_interval_time64 | arm | All platform devices|- |
| sched_setattr | all | All platform devices|- |
| sched_getattr | all | All platform devices|- |
| ioprio_set | arm64 | All platform devices|- |
| ioprio_set | riscv64 | All platform devices|- |
| ioprio_get | arm64 | All platform devices|- |
| ioprio_get | riscv64 | All platform devices|- |
| perf_event_open | all | All platform devices|- |
| getcpu | all | All platform devices|- |
| getrusage | all | All platform devices|- |
| times | all | All platform devices|- |
| process_vm_readv | all | All platform devices|- |
| process_vm_writev | all | All platform devices|- |
| process_madvise | all | All platform devices|- |
| ioctl | all | All platform devices|- |
| inotify_init1 | all | All platform devices|- |
| inotify_init | arm | All platform devices|- |
| inotify_add_watch | all | All platform devices|- |
| inotify_rm_watch | all | All platform devices|- |
| eventfd2 | all | All platform devices|- |
| eventfd | arm | All platform devices|- |
| epoll_create1 | all | All platform devices|- |
| epoll_create | arm | All platform devices|- |
| epoll_ctl | all | All platform devices|- |
| epoll_pwait | all | All platform devices|- |
| epoll_wait | arm | All platform devices|- |
| pselect6 | all | All platform devices|- |
| pselect6_time64 | arm | All platform devices|- |
| _newselect | arm | All platform devices|- |
| ppoll | all | All platform devices|- |
| ppoll_time64 | arm | All platform devices|- |
| poll | arm | All platform devices|- |
| ptrace | all | All platform devices|- |
| restart_syscall | all | All platform devices|- |
| prctl | all | All platform devices|- |
| seccomp | all | All platform devices|- |
| getrandom | all | All platform devices|- |
| memfd_create | all | All platform devices|- |
| userfaultfd | all | All platform devices|- |
| gettimeofday | all | All platform devices|- |
| sysinfo | all | All platform devices|- |
| pidfd_open | all | All platform devices|- |
| pidfd_getfd | all | All platform devices|- |
| set_robust_list | all | All platform devices|- |
| cacheflush | arm | All platform devices|- |
| set_tls | arm | All platform devices|- |
