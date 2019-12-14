---
title: Hadoop 常见错误
date: 2019-12-12 19:12:48
top: 1
tags:
- Hadoop
categories: 
- code
---

# Hadoop 常见错误

## `subprocess failed with code` 类型的错误

<!-- more -->

```
PipeMapRed.waitOutputThreads(): subprocess failed with code X 
error code 1: Operation not permitted
error code 2: No such file or directory
error code 3: No such process
error code 4: Interrupted system call
error code 5: Input/output error
error code 6: No such device or address
error code 7: Argument list too long
error code 8: Exec format error
error code 9: Bad file descriptor
error code 10: No child processes
error code 11: Resource temporarily unavailable
error code 12: Cannot allocate memory
error code 13: Permission denied
error code 14: Bad address
error code 15: Block device required
error code 16: Device or resource busy
error code 17: File exists
error code 18: Invalid cross-device link
error code 19: No such device
error code 20: Not a directory
error code 21: Is a directory
error code 22: Invalid argument
error code 23: Too many open files in system
error code 24: Too many open files
error code 25: Inappropriate ioctl for device
error code 26: Text file busy
error code 27: File too large
error code 28: No space left on device
error code 29: Illegal seek
error code 30: Read-only file system
error code 31: Too many links
error code 32: Broken pipe
error code 33: Numerical argument out of domain
error code 34: Numerical result out of range
error code 35: Resource deadlock avoided
error code 36: File name too long
error code 37: No locks available
error code 38: Function not implemented
error code 39: Directory not empty
error code 40: Too many levels of symbolic links
error code 42: No message of desired type
error code 43: Identifier removed
error code 44: Channel number out of range
error code 45: Level 2 not synchronized
error code 46: Level 3 halted
error code 47: Level 3 reset
error code 48: Link number out of range
error code 49: Protocol driver not attached
error code 50: No CSI structure available
error code 51: Level 2 halted
error code 52: Invalid exchange
error code 53: Invalid request descriptor
error code 54: Exchange full
error code 55: No anode
error code 56: Invalid request code
error code 57: Invalid slot
error code 59: Bad font file format
error code 60: Device not a stream
error code 61: No data available
error code 62: Timer expired
error code 63: Out of streams resources
error code 64: Machine is not on the network
error code 65: Package not installed
error code 66: Object is remote
error code 67: Link has been severed
error code 68: Advertise error
error code 69: Srmount error
error code 70: Communication error on send
error code 71: Protocol error
error code 72: Multihop attempted
error code 73: RFS specific error
error code 74: Bad message
error code 75: Value too large for defined data type
error code 76: Name not unique on network
error code 77: File descriptor in bad state
error code 78: Remote address changed
error code 79: Can not access a needed shared library
error code 80: Accessing a corrupted shared library
error code 81: .lib section in a.out corrupted
error code 82: Attempting to link in too many shared libraries
error code 83: Cannot exec a shared library directly
error code 84: Invalid or incomplete multibyte or wide character
error code 85: Interrupted system call should be restarted
error code 86: Streams pipe error
error code 87: Too many users
error code 88: Socket operation on non-socket
error code 89: Destination address required
error code 90: Message too long
error code 91: Protocol wrong type for socket
error code 92: Protocol not available
error code 93: Protocol not supported
error code 94: Socket type not supported
error code 95: Operation not supported
error code 96: Protocol family not supported
error code 97: Address family not supported by protocol
error code 98: Address already in use
error code 99: Cannot assign requested address
error code 100: Network is down
error code 101: Network is unreachable
error code 102: Network dropped connection on reset
error code 103: Software caused connection abort
error code 104: Connection reset by peer
error code 105: No buffer space available
error code 106: Transport endpoint is already connected
error code 107: Transport endpoint is not connected
error code 108: Cannot send after transport endpoint shutdown
error code 109: Too many references: cannot splice
error code 110: Connection timed out
error code 111: Connection refused
error code 112: Host is down
error code 113: No route to host
error code 114: Operation already in progress
error code 115: Operation now in progress
error code 116: Stale NFS file handle
error code 117: Structure needs cleaning
error code 118: Not a XENIX named type file
error code 119: No XENIX semaphores available
error code 120: Is a named type file
error code 121: Remote I/O error
error code 122: Disk quota exceeded
error code 123: No medium found
error code 124: Wrong medium type
error code 125: Operation canceled
error code 126: Required key not available
error code 127: Key has expired
error code 128: Key has been revoked
error code 129: Key was rejected by service
error code 130: Owner died
error code 131: State not recoverable
error code 132: Old database file
error code 133: No record read before update
error code 134: Record was already deleted (or record file crashed)
error code 135: No more room in record file
error code 136: No more room in index file
error code 137: No more records (read after end of file)
error code 138: Unsupported extension used for table
error code 139: Too big row
error code 140: Wrong create options
error code 141: Duplicate unique key or constraint on write or update
error code 142: Unknown character set used
error code 143: Conflicting table definitions in sub-tables of MERGE table
error code 144: Table is crashed and last repair failed
error code 145: Table was marked as crashed and should be repaired
error code 146: Lock timed out; Retry transaction
error code 147: Lock table is full; Restart program with a larger locktable
error code 148: Updates are not allowed under a read only transactions
error code 149: Lock deadlock; Retry transaction
error code 150: Foreign key constraint is incorrectly formed
error code 151: Cannot add a child row
error code 152: Cannot delete a parent row
```

