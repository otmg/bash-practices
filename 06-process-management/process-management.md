# Jobs
```bash
# List all jobs
jobs

# Creating a job
sleep 10 &
# result:
# the process is running in the background
# [1]+  Running                 sleep 10 &

sleep 10 # then press Ctrl + z
# result:
# the process stopped
# [1]+  Stopped                    sleep 10

# Bring the process to the foreground
# %1 is the index of the job count from 1
fg %1

# Run it the foreground
bg %1

# Kill the job
kill %1
# result:
# [1]+ Terminated sleep 10
```

# Check which process running on specific port
```bash
lsof -i :8080
```

# Disowning background job
```bash
gzip extremelylargefile.txt &
bg
disown %1
```

# Finding information about a running process
`ps aux | grep <search-term> shows processes matching search-term`

```bash
ps aux | grep nginx
```

# Others

```bash
chroot
cron
disown
killall
pidof
pstree
pwdx
time
```