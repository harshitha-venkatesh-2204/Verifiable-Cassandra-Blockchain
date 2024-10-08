# Blockchain-Assisted Verifiable Cassandra

## Introduction

Outsourced Database Model (ODB) is a paradigm in cloud computing where data owners (DOs) delegate their data to a database service provider (SP) for efficient cloud services. However, the untrusted nature of SPs poses risks to data integrity. To address this, we propose a solution using Merkle Trees (MHT) and the Ethereum blockchain to authenticate queried data from SP. This proof-of-concept implementation demonstrates how the system ensures data consistency and detects alterations.

## Implementation Overview

- **Data Owner (DO)**: Prepares key-value dataset and constructs a Merkle Hash Tree (MHT) over the data.
- **Database Service Provider (SP)**: Stores data in a Cassandra database.
- **Ethereum Blockchain**: Stores the Merkle root of the MHT for data integrity verification.
- **Query Client (C)**: Issues key-value queries and verifies results using MHT.
- **Verification Results**: Detects tampered data in the case of an attack.

## Setup Instructions

### Install pip3 for package management

```bash
sudo apt-get update
sudo apt-get install python3-pip
python3 -m pip install -U pip
```

Install related packages

```bash
pip3 install cassandra-driver merkletools py-solc-x
pip3 install web3==5.31.4
```

## Project setup

1. Create a directory and upload the necessary files:

```bash
mkdir project3
cd project3
```

2. Upload all related Python files and scripts to this folder.

   Open a second terminal: Install nvm and Node.js:

```bash
touch ~/.bashrc
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
source ~/.bashrc
nvm install 16.14.2
node -v
```

Install the Solidity compiler and Ganache:

```bash
sudo add-apt-repository ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install solc
npm install ganache --global
```

Run Ganache:

```bash
ganache
```


Start the Cassandra Service

Open a third terminal: Install Cassandra

Start Cassandra:

```bash
sudo service cassandra stop
sudo service cassandra start
```

Running the Program

In the first terminal, navigate to the project folder:

```bash
cd project3
```

Run the Python driver:

```bash
python3 driver.py
```


## Verification Scenarios

- No Attack Scenario: Data is verified as untampered when the Merkle tree root matches the blockchain-stored root.
- Attack Scenario: Tampered data is detected when verification fails, demonstrating unauthorized modifications.

  
## Conclusion

This project showcases how Merkle Trees and Ethereum blockchain can be leveraged to authenticate queries and ensure data integrity in an outsourced database model. The solution effectively identifies unauthorized changes, enhancing security in cloud environments
