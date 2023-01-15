
Reference:
* https://www.ruanyifeng.com/blog/2020/08/rsync.html



```
### Copy big file from one server to another

(1)rsync with root user
rsync -avhW --no-compress --progress root@10.20.42.6:/mnt2/docker_storage/volumes/git-config .
rsync -avhW --no-compress --progress root@10.20.42.6:/mnt2/docker_storage/volumes/git-data .
rsync -avhW --no-compress --progress root@10.20.42.6:/mnt2/docker_storage/volumes/git-logs .

(2) with nc
server1: nc -l 5678
server2: echo "hello" | nc 10.20.42.7 5678

nc -l 5678 | tar -xf -
tar -cf - git-* | pv | nc 10.20.42.7 5678

(3) snapshot disk from old git-lab server, and attach disk to new git-lab server, and config UUID
cat /etc/fstab
check UUID
lsblk
blkid
```
