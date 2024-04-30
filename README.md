# Connect to OpenVPN Server step

Establish a VPN connection with the specified OpenVPN server.


## How to use this Step

In your `bitrise.yml`, add this step to your workflow. This will pull the step from github and insert 
the step into your workflow. 

Example:
```yml
- git::https://github.com/hatchedlabs/bitrise-step-open-vpn.git@master:
    title: OpenVPN
    inputs:
    - host: your-openvpn-server
    - fqdns: |-
        www.google.com
        www.something.com
```

The way that this differs from the original openvpn step is that you can have the split tunnel based on passed in 
FQDNs. In the client.ovpn that it generates in `step.sh`, it will add in new routes for the split tunnel to route to.
Good news is that if the FQDN routes to different IPs, the step will grab all IPs and route them in the `client.ovpn` file.

Example:

```
# client.ovpn
...
route 142.251.116.106 255.255.255.255 # www.google.com
route 142.251.116.103 255.255.255.255 # www.google.com
...
```

## How to contribute to this Step

Create a Pull Request :D

You can test your branch by updating the branch from the above example of the step

```yml
- git::https://github.com/hatchedlabs/bitrise-step-open-vpn.git@YOURBRANCH:
    title: OpenVPN
    inputs:
    - host: your-openvpn-server
    - fqdns: |-
        www.google.com
        www.something.com
```

## Credits

Based off of https://github.com/justice3120/bitrise-step-open-vpn