# Ethereum-IoT

This tutorial will give you a full details about how to setup a private Ethereum network in your home using your Local Machine and Raspberry Pi. And also you can able control the Raspberry Pi using the smart contracts. In this tutorial I am going to control the  Blinking of Led bulb in Raspberry pi using smart contracts.

First step is installation of Go-Ethereum client in your Local Machine.

Installation from PPA

$sudo apt-get install software-properties-common
$sudo add-apt-repository -y ppa:ethereum/ethereum
$sudo apt-get update
$sudo apt-get install ethereum

This command will install Ethereum client and other dependencies which are required to run the ethereum network in your local machine.

Installation of geth and go in Raspberry pi

Download the tar file from the link given below
https://storage.googleapis.com/golang/go1.8.3.linux-armv6l.tar.gz

Extract it in your /usr/local/ 

Add /usr/local/go/bin to the PATH environment variable. You can do this by adding this line to your /etc/profile (for a system-wide installation) or $HOME/.bashrc
export PATH=$PATH:/usr/local/go/bin

This will install the latest stable version of Golang in your raspberry pi.

You can check the version of Golang installed in your system using the command

$go version

Now we are ready to install Ethereum client in our Raspberry pi. 

Download the binary files from the link mentioned below
https://geth.ethereum.org/downloads/

Extract the downloaded tar file in your Desktop and make the file using the command make
$cd go-ethereum
$make geth 

This will install the Go-Ethereum client geth in our raspberry pi
We can check the version of the geth version using the command
$geth version

Make sure that you are installing stable version of go and geth in your system.
Install the same version of go and geth in your Local Machine and Raspberry pi. This will avoid some confilts which will arise while connecting to them.

Now your sytem was ready to create the Ethereum Private Network.

Initialise the first node using the geth command 
$geth --datadir "etherum/node1" init "../genesis.json"
--datadir - specify the path where your node needs to be saved.
After init command specify the path to your genesis file.

Enter into to node using the command 
$geth --datadir "ethereum/node1" --networkid 1234 --port 30303 console

This will allow us to enter into the geth console. 
First we need to create the account to save your Eth. This can be done using the command
$personal.newAccount("pwd")

Now we have to generate Ether by using mining fucntion or by allocating using the genesis file. 
Mining can be start using the command 
$miner.start(1) -- starts the mining with thread one
$eth.mining --- gives the status of mining 
$miner.stop() --- stops the mining process.
$eth.blocknumber -- gives the last block number in our network.
$eth.getBalance("Account Hash") --- This will display the avaiable ether in our account.


