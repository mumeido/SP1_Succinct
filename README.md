# How to Verify SP1 Succinct

<img src="https://gcdnb.pbrd.co/images/KIMJIIgEbNVi.png?o=1" width="2000"/>


To learn more about SP1, go here. [here](https://docs.succinct.xyz/introduction.html).


Remark: This script is limited to Ubuntu (20.04/22.04). 


## Step 1: Updates to the system and installation of necessary tools

### Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install cmake pkg-config libssl-dev build-essential -y
```

### Rust and Cargo Installation
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env

## press 1
```

### Docker Installation
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update >/dev/null 2>&1
sudo apt-get install -y docker-ce docker-ce-cli containerd.io >/dev/null 2>&1
sudo docker run hello-world >/dev/null 2>&1
```
#### Check Docker version:
```bash
docker --version
```

## Step 2: Install SP1 Toolchain

### Download and Install SP1 
```bash
curl -L https://sp1.succinct.xyz | bash
source ~/.bashrc
sp1up
```
### Wait until the installation finish
![1](https://raw.githubusercontent.com/mumeido/SP1_Succinct/main/sp1.PNG)


#### Verify the SP1 toolchain version to ensure proper installation:
```bash
cargo +succinct --version
```

## Step 3: Initialize and Configure SP1 Project

### Initialize New SP1 Project
```bash
cargo prove new fibonacci
cd fibonacci/script
```

### Run and Verify the Project (Note: This step may take a little longer.)
```bash
# Start by carrying out the project without producing a proof to make sure everything is configured correctly:
RUST_LOG=info cargo run --release -- --execute

# Once the project's successful completion has been verified, create and examine ZK proof:
RUST_LOG=info cargo run --release -- --prove
```
![2](https://raw.githubusercontent.com/mumeido/SP1_Succinct/main/sp1_2.PNG)
#### You can verify the successful installation of the SP1 CLI by checking the version of `cargo prove`:
```bash
cargo prove --version
```
![3](https://raw.githubusercontent.com/mumeido/SP1_Succinct/main/sp1_3.PNG)

source : https://x.com/SuccinctLabs/status/1820853653173129393


