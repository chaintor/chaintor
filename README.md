# chaintor
This Tutorial Will Show You How To Run A Tor Relay On A Masternode VPS.

![1280x600](https://github.com/chaintor/chaintor/blob/master/chaintor.png "1280x600")

“The Tor Network Provides Anonymity To All Types Of Protocols!” 
As a community, we would like to support the Tor Project by setting up Tor relays.. A Chaincoin masternode has excess capacity that could, at the owner's discretion, be used to run a Tor relay.

## Installing A Tor Relay

Debian / Ubuntu:

```bash 
sudo apt-get install tor
```

CentOS:

```bash
sudo yum install epel-release
sudo yum install tor
```

## Setting Up A Tor Relay

Next, you'll need to edit the config file [ /etc/tor/torrc ] and pick a name for your Tor relay. The config file should include the following:

```bash
NickName chaincoin
ORPort 9001
AccountingMax 500 GBytes
AccountingStart month 1 00:00
DirPort 9030 
ExitPolicy reject *:*
```

Please change the NickName. If you have a bandwidth limit from your VPS provider, please edit AccountingMax. In this example it is limited to 500 GB per month. The $5 offer from Vultr.com has a limit of 1000 GB. With 500GB for Tor you should be on the safe side. Please Do Not remove »ExitPolicy reject *:*«, unless you know exactly what you are doing.

## Enable and start the Tor relay

```bash
sudo systemctl enable tor.service
sudo systemctl start tor.service
```

This will enable the Tor relay and start it.
`sudo systemctl status tor.service` should show the status »runnung«.

In a delay of 1-2 h you should be able to search for your Tor relay on this web site:

https://atlas.torproject.org/

