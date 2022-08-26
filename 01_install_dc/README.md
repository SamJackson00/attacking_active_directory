# 01 Installing the Domain Controller


1. Use `sconfig` to:
    - Change the hostname
    - Change the IP address to static
    - Change the DNS server to our own IP address

2. Install the Active Directory Windows Feature

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

3. Deploy AD

```
import-Module ADDSDeployment
install-ADDSForest
```

- Enter a domain name
- Enter a safe mode password
- Hit Y for yes

4. Change DNS server to our own IP address again (AD deployment sets it as loopback address)

```
Get-NetIPAddress -IPAddress 192.168.195.155
```
- Take note of Interface ID

```
Set-DnsClientServerAddress -InterfaceIndex 6 -ServerAddresses 192.168.195.155
```

- Can check with 'Get-DnsClientServerAddress'

5. Take snapshot if desired


## Joining Workstation to the Domain


1. Get the current DNS address to see the interface index (can grab directly with below command but for more complex environments may need to run 'ipconfig' to grab current IP then Get-NetIPAddress -IPAddress X)

```
Get-DnsClientServerAddress
Set-DnsClientServerAddress -InterfaceIndex 4 -ServerAddresses 192.168.195.155
```

2. Add the workstation to the domain

```
Add-Computer -Domainname xyz.com -Credential xyz\Administrator -Restart -Force
```



