# Secops, What Do I Know 
Getting my head around SecOps in more systematic way

I felt I needed to start writing down what I know, to not get overwhelmed by the amount of the data, 
and to serve as a recipe for whenever I have to (re)tighten up our apps.

# Primary points of interest

Aka main taxonomies.

Genres of security breaches I'm most interested in currently, from the SecOps standpoint.

Not at all definite list of what can be done to poor, little, harmless apps, nor might it be even accurate in it's description.

## Data gathering

### OSINT Roadmap

![osing overview](https://github.com/grzegorznowak/secops-what-do-I-know/blob/master/assets/osint.png "OSINT Overview")


### Finding out related and active subdomains

`python sublist3r.py -v -b -d [domain]`

### Tech Stack detection
  whatweb -v example.com
  
  
### recon-ng

https://www.blackhillsinfosec.com/whats-changed-in-recon-ng-5x/

TBD. sample uses and such

### MSF baseline reckon with Nmap

```
sudo msfdb init
msfconsole
workspace -a [domain/ip we plan scanning]
db_nmap -sV -A -T4 -Pn -p1- [domain/ip]
```

then show us what you found 

`services`

then search for usable module related to found services and their versions

`search openSSH X.Y.Z`

finaly lock and load usable exploit via

```
use [module]
info
set [PARAM] [VALUE]
exploit
```



### Load balancing detection

not very reliable, but sometimes works

`lbd example.com 443 https`

## Servers exploitation

### Useful Knowledge Sources:

#### nmap

https://www.youtube.com/watch?v=4t4kBkMsDbQ

### Tried Tools&Workflows

#### Known Vulnerabilities Workflow

#### nmap

scan ip for most common ports opened and detect their version. `-Pn` to skip host discovery
`nmap -F -sV -Pn [IP]`

scan all vuln scripts `nmap --script vuln -Pn [IP]`

more advanced and stelth(ier) flags:

`nmap --spoof-mac Cisco --data-length 24 -T paranoid --max-hostgroup 1 --max-parallelism 10 -Pn -f -D 10.1.20.5,RND:5,ME -v -n -sS -sV -oA /desktop/pentest/nmap/out -p T:1-1024 --randomize-hosts 10.1.1.10 10.1.1.15`

#### searchsploit

show me all the known exploits for openSSH (or any other service found via nmap)
`searchsploit openssh`

#### metasploit

![metasploit diagram](https://github.com/grzegorznowak/secops-what-do-I-know/blob/master/assets/metasploit.png "metasploit diagram")

boot into with `msfconsole`

* show me all the known exploits for openSSH metasploit knows about `search openSSH`

* use enumusers exploit `use auxiliary/scanner/ssh/ssh_enumusers`

* point to the server with a known vuln `set RHOST [IP]`

* show other available parameters `show options`

* try exploting `exploit`

### Promising Tools&Workflows

lorem ipsum

## Webapps exploitation

![exploitation diagram](https://github.com/grzegorznowak/secops-what-do-I-know/blob/master/assets/webapp.png "Webapp diagram")


### DB exploitation

aka webapps' backend hacking

#### Tried Tools&Workflows

lorem ipsum

#### Promising Tools&Workflows

lorem ipsum


### Stored JS exploitation

aka making sure html is being sanitized properly

#### Tried Tools&Workflows

lorem ipsum

#### Promising Tools&Workflows

lorem ipsum
