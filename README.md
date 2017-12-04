# BITTCLOUD-TESTED
Tested bitcloud install


- Install Bitcoin Core dependencies
‘screen -S btc

`sudo apt-get install automake libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev`

- Go to your Home folder
`cd`

- Download the BitCloud install script
`wget https://raw.githubusercontent.com/LIMXTEC/BTDX-Masternode-Setup-Ubuntu-1404/master/btdxsetup.sh`

- Run it with sudo (yes, it is needed)
`sudo bash btdxsetup.sh`

- You will be asked to press return to add a repo, obviously press return
- Now in the meantime whilst your VPS is compiling the needed binaries, grab a cup of coffee or a beer and relax. On a 2GB VPS, this will take about 15 minutes to finish.
- When it's finished compiling, it will ask you to enter a secure password. This can be used to control your node from the outside if you allow it in your firewall.
- After that, it will ask you for your Masternode PrivKey. Obviously you don't have one yet, so enter this temporary one `68SGsiitJCJgDwwM8BKiTMKjCmANfsTErUb3DzEqxYH11sZAF6x `. We will add the Masternode PrivKey in a few seconds.
- The script will launch an instance of bitcloudd and after 1 minute show you some info.


::: Get your Masternode PrivKey :::

Okay! It's time to generate your Masternode PrivKey! Type this:
` bitcloud-cli masternode genkey `
There's your Masternode PrivKey!


::: Get your wallet address :::

To get your wallet address, do this:
`bitcloud-cli getaccountaddress ""`
We chose to use account `""` here. You can generate other addresses for this wallet by adding a number like `"2"`

::: Edit the bitcloud.conf :::

Okay, final steps!
- Open bitcloud.conf with your favourite editor (yes sudo is needed since we installed with sudo):
`sudo nano .bitcloud/bitcloud.conf`

Be sure that your config has these lines, but with your variables (most of them are generated automagically by the script):

rpcuser=btdxdmasternodeservice2387645 
rpcpassword=YourVerySecurePasswordWhichYouTypedWhenTheScriptAskedYouTo 
rpcallowip=127.0.0.1
server=1 
listen=1 
daemon=1 
logtimestamps=1 
masternode=1 
promode=1 
masternodeprivkey=PLACEYOURMASTERNODEPRIVKEYHERE
masternodeaddr=127.0.0.1:8329
alertnotify=echo %s | mail -s "Alert" rob@oxycoin.io

sudo bitcloud-cli getblockcount

sudo bitcloud-cli encryptwallet eenkuttrektharderdantienpaarden

sudo bitcloudd -deamon

sudo bitcloud-cli getmininginfo

sudo bitcloud-cli getinfo

sudo bitcloud-cli stop

sudo bitcloud-cli masternode start eenkuttrektharderdantienpaarden

sudo bitcloud-cli sendtoaddress ADRESS 10000 

sudo bitcloud-cli walletpassphrase
