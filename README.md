# Secops, What Do I Know 
Getting my head around SecOps in more systematic way

I felt I needed to start writing down what I know, to not get overwhelmed by the amount of the data, and to serve as a recipie for whenever
I had to (re)tighten up our apps.

# Primary points of interest

Aka main taxonomies.

Genres of security breaches I'm most interested in currently, from the SecOps standpoint.

Not at all definite list of what can be done to poor, little, harmless apps, nor might it be even accurate in it's description.

## Data gathering

### Tech Stack detection
  whatweb -v example.com
  
  
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

#### searchsploit

show me all the known exploits for openSSH (or any other service found via nmap)
`searchsploit openssh`

#### metasploit

boot into with `msfconsole`

* show me all the known exploits for openSSH metasploit knows about `search openSSH`

* use enumusers exploit `use auxiliary/scanner/ssh/ssh_enumusers`

* point to the server with a known vuln `set RHOST [IP]`

* show other available parameters `show options`

* try exploting `exploit`

### Promising Tools&Workflows

lorem ipsum


## DB explotation

aka webapps' backend hacking

### Tried Tools&Workflows

lorem ipsum

### Promising Tools&Workflows

lorem ipsum


## Stored JS exploitation

aka making sure html is being sanitized properly

### Tried Tools&Workflows

lorem ipsum

### Promising Tools&Workflows

lorem ipsum
