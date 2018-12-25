# Providing a vault

There are 2 kinds of vaults: standard ones (in binary or source form) and tracked ones (only in binary form).

## Providing a standard vault

### Get binary from Maidsafe release

Download zip file from [Maidsafe release](https://github.com/maidsafe/safe_vault/releases/tag/0.17.2) corresponding to
your platform, extract the vault executable and configure it with the set of configuration files defined in
["vaults" directory](https://github.com/Thierry61/tfa_safenetwork/tree/master/vaults).

For example on linux platform:

```bash
# Download zip file
wget https://github.com/maidsafe/safe_vault/releases/download/0.17.2/safe_vault-v0.17.2-linux-x64.zip

# Unzip file
unzip safe_vault-v0.17.2-linux-x64.zip

# Get configuration files
git clone https://github.com/Thierry61/tfa_safenetwork.git

# Configure vault
mkdir app
cd app
cp ../safe_vault-v0.17.2-linux-x64/safe_vault .
cp ../tfa_safenetwork/vaults/*.config .

# Launch vault
./safe_vault
```

### Compile source from Maidsafe repository

This kind of node is to be build from [safe_vault](https://github.com/maidsafe/safe_vault.git) Maidsafe repository
and configured with the set of configuration files defined in
["vaults" directory](https://github.com/Thierry61/tfa_safenetwork/tree/master/vaults).

On a Linux host with rust 1.30.1 (NOT THE LATEST VERSION!):

```bash
# Build vault from Maidsafe source
git clone https://github.com/maidsafe/safe_vault.git
cd safe_vault
cargo build --release

# Get configuration files
cd ..
git clone https://github.com/Thierry61/tfa_safenetwork.git

# Configure vault
mkdir app
cd app
cp ../safe_vault/target/release/safe_vault .
cp ../tfa_safenetwork/vaults/*.config .

# Launch vault
./safe_vault
```

## Providing a tracked vault

This kind of node is provided in binary form (as a docker image). It uses an out of band network that collects data from
participating vaults. Aggregate data are displayed on [this site](http://116.203.42.154/).

Install docker on a Linux host and then join the network with the following command:

```bash
docker swarm join --token SWMTKN-1-3eqzfowpfpsmknaiqitojn560jzfeqapkvgpvy0cj8wqb1oxkw-9up8ds418mt3u03x2wyd9y1ps 116.203.25.212:2377
```

To be considered a sponsor and participate in the Honor Roll, provide at least 2 tracked nodes
on different hosts whose hostname contains a double dash sequence ('--') with a common string before
this sequence. This common string will be your name as a sponsor.
For example with the following hostnames:

- BIGCORP--SW
- BIGCORP--NE

You will be participating as BIGCORP sponsor.

Advantages associated with this title:

- Be listed in the Honor Roll. This list is ordered by decreasing number of nodes, so
  provide many nodes to be ranked at the top of the list
- Show your nodes in the galaxy of constellations
- Monitor your own nodes in the dashboard

To stop your vault, issue following command:

```bash
docker swarm leave
```

# Accessing the network from a client

Replace existing crust configuration file with the one in
["clients" directory](https://github.com/Thierry61/tfa_safenetwork/tree/master/clients).

The file is provided for "SAFE Browser". For other clients, just rename it
by replacing "SAFE Browser" part with the base name of the client program.
