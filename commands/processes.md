# Processes

Look process by name
```
pgrep
```

Kill process by name
```
pkill
```

Process tree
```
pstree
```

Show what process use device
```
fuser -m /mnt
```

Kill process by name
```
killall atom
```

Kill all user processes
```
killall -u user
```

Process information pseudo-filesystem
```
/proc
```

Show information about PID
```
top -p <PID>
```


## Priority
IO priority
```
ionice -c3 coommand
```

Start with priority
```
nice -n 15 command
```

Change the priority
```
renice renice -n 15 -p pid
```

## PS
Sort by RAM
```
ps aux | sort -nk 4
ps aux —sort=%mem | grep -v 'root' | head -n 35
```

Sort by CPU
```
ps aux | sort -nk 3
ps aux —sort=%cpu | grep -v 'root' | head -n 35

Show processes
ps -ef
```

Show pids of process
```
ps -ef | grep -v grep | grep <process_name> | awk '{ print $2 }'
```
