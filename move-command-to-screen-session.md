# Move a running process to a screen session
### Suspend the process
`CTRL+Z`
### Resume the process in background
`bg`
### Disown it
`disown %1`
> If you have multiple jobs running, find the correct job number:
`jobs -l`
### Enter screen session
`screen`
### Find the PID of the process
`pgrep processname`
### Attach it to current screen session
`reptyr PID`
