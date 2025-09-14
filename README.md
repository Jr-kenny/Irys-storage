# Irys-storage
## Just an easy fun way of testing out irys storage 

## 1️⃣ Minimal Requirements
RAM	2 GB is enough; 4 GB recommended
Storage	~200 MB for Node.js, packages, and files
OS	Ubuntu 20.04+, any Linux distro, macOS, or Windows with Node.js
Network	Stable internet connection (uploads require network to Irys testnet)
TESTNET TOKENS
ETH Sepolia faucet (get free tokens from [Alchemy](https://www.alchemy.com/faucets/ethereum-sepolia) Faucet)
IRYS faucet ([here]([https://irys.xyz/faucet])
PLEASE DON'T USE YOUR MAIN WALLET

## 2️⃣ Recommended for Comfort
RAM: 4–8 GB (for handling multiple uploads or large files)
Storage: 1 GB+ if you store multiple files locally
Network: 10 Mbps+ for faster uploads

## 3️⃣ Notes
Node.js handles the uploads; it’s not GPU-intensive.
Large bulk uploads (hundreds of files) may be limited by RAM and internet speed, but typical single-file or small batch uploads run fine on any laptop.
No special hardware like GPUs or SSDs is required.

# STEP 1. Installations:
## install dependencies
```bash
sudo apt-get update && sudo apt-get upgrade -y
```
```bash
sudo apt install curl iptables build-essential git wget lz4 jq make protobuf-compiler cmake gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen ufw -y
```
## Install nodejs & npm :
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt install -y nodejs
```
for mac

      brew install node

## Check version :
```bash
node -v
npm -v
```

# STEP 2 CREATE FOLDER
```bash
mkdir ~/irys-cli
cd ~/irys-cli
```
## Initialize Node project :
```bash
npm init -y
```

## Install Irys SDK packages:
```bash
npm install @irys/upload @irys/upload-ethereum
```
## Mark project as ES module
Add "type": "module" to package.json
```bash
nano package.json
```
just input at the end
```bash
{
  "type": "module"
}

```
to go down use your arrow keys 
after adding the file use ctrl X then Y and enter 

## SET WALLET
Export your testnet wallet private key in the terminal
```bash
export PRIVATE_KEY="your_testnet_wallet_private_key_here"
```
Ensure your wallet has some testnet tokens for gas. sepolia, holesky etc

3️⃣ Uploading a Single File
