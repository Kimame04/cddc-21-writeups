## Massages

### Description

We have successfully obtained some of the GDC’s public IP addresses. Everybody is ready to go active! This is just the beginning of your journey.

**Target IP address: 52.220.172.156**

> Hint #1:	Perform a port scanning and try to find the service versions.

### Approach

This challenge was pretty straight-forward, apart from the fact that we overlooked finding the service version of the ports. Executing the following command would give us the flag.

```
nmap -sV 52.220.172.156
```

### Flag

```shtml
CDDC21{F1rst_Fl4G_on_THE_R04D}
```

