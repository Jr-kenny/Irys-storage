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

# STEP 2. CREATE FOLDER
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

# STEP 3. UPLOADING YOUR FILE
first we need to move the file to the irys folder 
you can copy or move 
1️⃣ Locate Your Image
Find the image you want to upload. It could be in Downloads, Desktop, or another folder.
Example: myImage.png

2️⃣ Open Terminal
Open a new terminal window on Ubuntu. use the plus with arrow sign

3️⃣ Move or Copy the Image
There are two options:
Option A: Move the file (removes from original folder)
```bash
mv /path/to/your/image.png ~/irys-cli/
```
example lets say the image is in your download folder and its named bakaaa, its should be like this 
```bash
mv ~/Downloads/bakaaa.png ~/irys-cli/
```

Option B: Copy the file (keeps original in its folder)
```bash
cp /path/to/your/image.png ~/irys-cli/
```
example is still like moving but lets say its on your desktop and the name is layeredge
```bash
cp ~/Desktop/layeredge.png ~/irys-cli/
```
OR YOU CAN DO IT THIS WAY 
1. open your file explorer copy the image
2. open your linux folder/ ubuntu
3. find your home folder then select your username
4. search for irys cli a folder should appear open it
5. the paste the image ( ctrl V)

now go back to your irys cli screen
## OPEN YOUR JS FOLDER
```bash
nano upload.js
```
Then paste 

```bash
import { Uploader } from "@irys/upload";
import { Ethereum } from "@irys/upload-ethereum";

// Initialize uploader with wallet from environment variable
const getIrysUploader = async () => {
  const irysUploader = await Uploader(Ethereum).withWallet(process.env.PRIVATE_KEY);
  return irysUploader;
};

// Upload a single file
const uploadFile = async () => {
  const irysUploader = await getIrysUploader();
  const fileToUpload = "/path/to/your/file.png"; // <-- replace with your file path
  const tags = [{ name: "application-id", value: "MyNFTDrop" }];

  try {
    const receipt = await irysUploader.uploadFile(fileToUpload, { tags });
    console.log(`File uploaded ==> https://gateway.irys.xyz/${receipt.id}`);
  } catch (e) {
    console.log("Error when uploading: ", e);
  }
};

// Run the upload
(async () => {
  await uploadFile();
})();
```
EDIT THAT LINE THAT SAYS 
"const fileToUpload = "/path/to/your/file.png"; // <-- replace with your file path"
with this but 
```bash
const fileToUpload = "/home/jrkenny/irys-cli/calculator.png";
```
remove that jrkenny and add your own ubuntu username you can see on your screen like BAKAAA
also remove the calculator.png and instead add your own file you copied or moved in the step above 
THEN CTRL X THEN Y AND ENTER 

# STEP 4. Run the Upload
```bash
node upload.js
```
Expected Output: "File uploaded ==> https://gateway.irys.xyz/<transaction_id>"
<img width="1648" height="860" alt="image" src="https://github.com/user-attachments/assets/be75b49c-3ae3-4c72-b015-9dab697b99e9" />
DONE 
YOU CAN RUN IT MULTIPLE TIMES

 by [Jrkenny](https://x.com/Jrken_ny)
