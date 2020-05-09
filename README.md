# bui
## Bind User Interface, easy to use command for making simple local dns setups

## About this program

### Who this program is for
this is a program for making the life of those who have home labs with no fancy equipment or dedicated net service boxes easier, so you can configure and change arround a local DNS without worring about reloading the service to get it to take effect inmediatly, or just want to install a ton of local web services nad just don't wanna mess arround with the complicated configuration of a DNS server.

### Features:
- support for A, PTR, CNAME records
- Adds and removes records from DNS database
- Adds and removes Authority zone's databases from Bind9 configuration using the namde.conf.local file
- Manages reverse DNS records automaticcally (Generates them and removes them autmoatically on user demad)
- Autiserializes DNS databases when there's a change (through the script obviosuly)
- Reloads bind9 configuration when there's a change.
- Auto deletes reverse DNS databases when they are no longer used by any of the current DNS databases
- No need to specify if the record you're trying to add is CNAME PTR or A the script will figure it out using the order on which you specified the parameters
- It supports deletion of multiple records at once, for example if you do bui reset -d a.example --all and you have a record that is b.a.example it will get deleted as well

### In the future could be added:
- support for MX and TXT records

### Advantages:
- Easy to use
- Not dealing with bind9
- Depends on standard system packages and commands (host, grep, sed)
- All architectures since it's all bash scripts
- works with bash associative arrays so it is easy to understand and modify

#### Disadvantages:
- Duplicates DNS database information as well as settings
- Slow for large databases.
- Rewrites files on removal operations
- Rebuilds the duplicated data when saving
- works with bash associative arrays so it is not space efficient


#### Tested on:
- Debian Buster
Should work on any debian based distribution

## Quick copy+paste installation of the latest version

### Debian and debian based
#### Just bui-common package
sudo apt update ; \
sudo apt install git -y ; \
git clone https://github.com/Reiikz/bui ; \
cd bui/bui-common ; \
make deb ; \
sudo apt install -f $( realpath bui*.deb ) -y

### Other OS
#### Just bui-common package
ensure you have installed git and make then copy+paste the following on a terminal
git clone https://github.com/Reiikz/bui ; \
cd bui/bui-common ; \
sudo make install

#### removal
to remove it when installed using make install use make uninstall

#### Warning
This program was not tested on other os than Debian Buster, you can install it anyway using the
provided makefile if you find your distribkution is compatible with this script.
If your shell is POSIX compliant it might be fine to run this on other shell than bash.
Here's a list of things your distribution has to support to be able to use this script with all the provided commands.
- /usr/local/bin location is available for installing external scripts as commands
- /usr/share/man/man8 location is used for storing manpages and your man command supports it
- /etc/bind/named.conf.local is the local DNS database configuration file for bind (if not you can change it on the script with no problems as well as the location of the database files, this is done on the bui-cfgh script you should spot theese constants in all caps at the top of the file)