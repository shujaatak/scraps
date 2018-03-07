## Linux

- [Get Linux version](#get-linux-version)
- [Update packages](#update-packages)
- [Delete packages](#delete-packages)
- [Renew IP address](#renew-ip-address)

### Get Linux version

Best way:

``` bash
lsb_release -a
```

Good way:

``` bash
cat /etc/*-release
```

Kernel and stuff:

``` bash
uname -a
```

More stuff:

``` bash
cat /proc/version
```

### Update packages

``` bash
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get autoremove
```

### Delete packages

For example, we want to delete **LibreOffice**. All of its packages names start with `libreoffice`, so:

``` bash
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```
### Renew IP address

For example, if host machine has changed the network, and you need to update the IP address in your guest VM:

``` bash
dhclient -v -r
```