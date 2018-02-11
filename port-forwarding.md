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
ssh 
```
