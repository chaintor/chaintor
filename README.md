# chaintor
Tutorial to run a tor relay on a masternode vps.

![1280x600](https://github.com/chaintor/chaintor/blob/master/chaintor.png "1280x600")

As a community we like to support the Tor Project by running a view Tor relays. The tor network provides anonymity to all kind of protocols. A chaincoin masternode does not use a lot of resources on a vps. So that could be used to run a Tor relay.

## Installing a Tor relay

Debian / Ubuntu:

```bash 
sudo apt-get install tor
```

CentOS:

```bash
sudo yum install epel-release
sudo yum install tor
```

## Setup a Tor relay

Next you need to edit the config file `/etc/tor/torrc` and pick a name for your Tor relay.
The config file should include the following: 

```bash
NickName chaincoin
ORPort 9001
AccountingMax 500 GBytes
AccountingStart month 1 00:00
DirPort 9030 
ExitPolicy reject *:*
```

Please change the Nickname.
If you have a bandwidth limit from your vps provider please edit AccountingMax. In this example it is limited to 500 GB per month. The 5$ offer from Vultr.com has a limit of 1000 GB. With 500GB for Tor you should be on the save side. Please dont remove »ExitPolicy reject \*:\*«, unless you know what you are doing.

## Enable and start the Tor relay

```bash
sudo systemctl enable tor.service
sudo systemctl start tor.service
```

This will enable the Tor relay for start at booting and start it.
`sudo systemctl status tor.service` should show the status »runnung«.

In a delay of 1-2 h you should be able to search for your Tor relay on this web site:

https://atlas.torproject.org/

