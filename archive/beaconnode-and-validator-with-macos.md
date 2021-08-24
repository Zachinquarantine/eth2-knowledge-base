---
description: A guide for getting set up on the Prater testnet with the Lighthouse Client.
---

# Medalla Testnet: Lighthouse Client - macOS

[Official Lighthouse docs  
](https://lighthouse-book.sigmaprime.io/become-a-validator-source.html)[Lighthouse Discord server](https://discord.gg/8mFMS7G)

#### Requirements:  A synced Goerli node \([Guide](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2#step-1) till step 3.\)

#### 

#### 1. Step 

#### Installing Rust

Open a terminal window and paste the following in:

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

_"Current installation options"_  
Press **"1"** and confirm with Enter.

![](../.gitbook/assets/image%20%28130%29.png)

_"Next time you log in this will be done automatically"_  
**Close** this terminal window and **open a new one.**

#### 2. Downloading and building Lighthouse

`git clone https://github.com/sigp/lighthouse.git  
cd lighthouse`

and then run `make`

![](../.gitbook/assets/image%20%28133%29.png)

_Wait a few minutes_  
Once the process is done it will look like the following

![](../.gitbook/assets/image%20%28128%29.png)

#### 3. Find the binary file

Open **Finder** and head over to `~/.cargo/bin/`

![](../.gitbook/assets/image%20%28132%29.png)

**Copy** the Lighthouse file to a more convenient folder.

#### 4. Start the beaconnode

_Make sure the goerli node \(ETH1\) is running as mentioned in the_ [_requirements_](https://kb.beaconcha.in/archive/outdated-lighthouse-client-guides/beaconnode-and-validator-with-macos#requirements-a-synced-goerli-node-guide-till-step-3)_._

Drag and drop the **Lighthouse** file and add `--network prater beacon --eth1 --http --graffiti "beaconcha.in<3"` 

![](../.gitbook/assets/image%20%28160%29.png)

#### 5. Create ETH2 Wallet

_**Lighthouse** allows you to create an ETH2 wallet and attach your validator keys._

Open a new Terminal window, drag and drop the Lighthouse file and **add**  
`account wallet create --name my-validators --passphrase-file my-validators.pass`

**The 12 word mnemonic phrase can restore the ETH2 wallet - write the words down.**

![](../.gitbook/assets/image%20%28134%29.png)

The wallet is located in `$HOME/lighthouse`

![](../.gitbook/assets/image%20%28123%29.png)

#### 6. Create ETH2 Keys

Use the same Terminal window, drag and drop the Lighthouse file and **add**   
`lighthouse account validator create --wallet-name my-validators --wallet-passphrase my-validators.pass --count 1`

![](../.gitbook/assets/image%20%28131%29.png)

#### 7. Depositing to Ethereum 2.0

First, find the deposit data of the newly created ETH2 Key , which is located in `.lighthouse/validators/`   
  
There are two lighthouse folders, `.lighthouse` is a hidden folder.  
**Enable hidden folders with** **`CMD + Shift + .`**

Open the `eth1-deposit-data.rlp` file with a **text editor.   
Copy** the 842 long text sequence and **follow these** [**steps**](https://kb.beaconcha.in/ethereum-2.0-and-depositing-process/depositing-to-ethereum-2.0#depositing)**.  
  
Prater Deposit Contract address:** `0xff50ed3d0ec03aC01D4C79aAd74928BFF48a7b2b`

The deposit will be recognised by the beacon-chain in 8.5 hours.

![](../.gitbook/assets/image%20%28127%29.png)



#### 8. Starting the validator

Open a new terminal window, drag and drop the **Lighthouse** file and add `validator --auto-register`

In total there are **three** terminal windows running simultaneously!   
[Track](https://prater.beaconcha.in/dashboard?validators=) your validator performance.

![](../.gitbook/assets/image%20%28122%29.png)







