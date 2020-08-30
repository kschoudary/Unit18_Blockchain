# Unit18_Blockchain
Blockchain Transactions using Puppeth and Geth
KS, 8/27/2020 - Homework#18-BlockChain

Introduction: 
This document explains the detailed steps followed for submitting the Homework for the project - Unit18_Blockchain.
Detailed Steps:
Step-1: Download Software: 
-	Download and install MyCrypto app from website: https://download.mycrypto.com/
-	Download Ethereum Tools from website: https://geth.ethereum.org/downloads/
Download ‘Geth & Tools 1.9.19 for Windows 64-bit, extract it to the project folder and rename the folder name to  - KSBlockchain-Tools
Step-2: Setup a testnet blockchain
-	Open Git Bash
-	Go to Folder using CD C:/Users/kscho/Documents/github_files/Unit18_Blockchain/KSBlockchain-Tools
-	Run the following commands in sequence and note the info
-	Create node1 using ‘geth’
o	./geth account new --datadir node1
Enter PW: fintech828a
Public address of the key:   0xfEE14C1Ba13a3B379894F344aD6E375c4a605fFD
Path of the secret key file: node1\keystore\UTC--2020-08-28T21-35-06.801720700Z--fee14c1ba13a3b379894f344ad6e375c4a605ffd
-	Create node2 using ‘geth’
o	./geth account new --datadir node2
Enter PW: fintech828a
Public address of the key:   0x1Dc3F31731149b42eafefb3D110DF3A4D03f5FD6
Path of the secret key file: node2\keystore\UTC--2020-08-28T21-37-35.247089800Z--1dc3f31731149b42eafefb3d110df3a4d03f5fd6

-	Create blockchain network using ‘puppet’

o	./puppet
Enter Network name as: fintech828a
Choose option: 2. Configure new genesis
Choose option: 1. Create new genesis from scratch
Choose consensus engine to use = 2. Clique – proof-of-authority 
Hit enter for time (Default = 15)
Enter accounts for seal:  Public Address of both nodes (exclude first 2 digits)
Enter accounts for pre-funding: Public Address of both nodes (exclude first 2 digits)
Enter ‘no’ for pre-funding with 1 wei
Hit Enter
Hit Enter
Enter yes
Enter 8282 ( chain/network ID)
Hit Enter
Hit Enter

Check the folder for newly created fie: fintech828a.json file (delete the 2nd .json file)

-	Initialize the nodes
o	./geth init fintech828a.json --datadir node1
o	./geth init fintech828a.json --datadir node1
-	Run the first node, unlock the account, enable mining, and the RPC flag
o	./geth --datadir node1 --mine --minerthreads 1
o	Copy the ‘enode’
o	enode://cde1535a71815fefbeb5386fef62a6821314a0f991f523d4999762d566b93abdf1c05e75b6c15925d90ff98cf7be916877315ed41dbdd3351bb36cc30fc5edeb@127.0.0.1:30303
-	Open another Git Bash console and go the folder and Run the second node
o	./geth --datadir node2 --port 30304 --rpc --bootnodes "enode:..” --ipcdisable
o	Use the first node’s ‘enode’ in the above command

-	Open MyCrypto App
o	Change node
o	Add custom node
o	Enter Node name = fintech828a, Network = Custom,. Network name = fintech828a, Currency = ETH, Chain ID =822, URL = http://127.0.0.1:8545
o	Click on  button – Save & Use Custom Node
o	Enter node1 Keystore file details for Wallet
o	Enter Password for the node1

Wallet Info:
	Public Address: 0xfEE14C1Ba13a3B379894F344aD6E375c4a605fFD
	Public Address: 0xfee14c1ba13a3b379894f344ad6e375c4a605ffd
	Private Key:
	Balance: 0 ETH

 
-	Transfer Money from https://faucet.kovan.network/
-	Check the balance in MyCryto Wallet, Now it has ETH enough to make a transfer
-	Transfer Money from MyCrypto Wallet
	
	From Account (node1): 0xfEE14C1Ba13a3B379894F344aD6E375c4a605fFD
	To Account   (node2): 0x1Dc3F31731149b42eafefb3D110DF3A4D03f5FD6
		Amount to Transfer 15 ETH
		Your TX has been broadcast to the network. It is waiting to be mined & confirmed. During ICOs, it may take 3+ hours to confirm. Use the Verify & Check buttons below to see. TX Hash:0x50bcbfbcb124736af0664216a44a585ac583a24ee07c32aeccc1563a2f8f50a6
		Hash: 0x50bcbfbcb124736af0664216a44a585ac583a24ee07c32aeccc1563a2f8f50a6
 	Transfer Status: Pending
 
Note: As per project requirments, I used the 'proof-of-authority'. And with this option, my transaction staus of the transfer is 'Pending'. Theany confirmations or  'proof-of-authority' option is preventing node1 from mining which is why I am not getting any confirmations. This is reported to class instructor and almost all the students have similar issues with this option.

 

