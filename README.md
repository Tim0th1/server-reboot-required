### server-reboot-required
### Returns list of TRUE for servers requiring reboot

Takes list from:

```
salt-ssh '*' file.file_exists /var/run/reboot-required 
```

and returns the list of servers to insert into:

```
salt-ssh -L [comma separated list of servers] system.reboot
```

```
import pandas as pd

text = input("Enter the list of servers:")

text = text.split()

servers_0 = text[0::2]

servers = []

for i in servers_0:
    serv = i.replace(':', ',')
    servers.append(serv)
    
truefalses =[]

for t in text[1::2]:
    truefalses.append(t)
    

data_tuples = list(zip(servers, truefalses))

frame = pd.DataFrame(data_tuples, columns= ['Servers', 'TrueFalses'])


df = frame[(frame['TrueFalses']=='True') ] 


print()
for items in df.Servers:
    
    print(items, end='')
```
