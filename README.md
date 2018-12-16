# Providing a vault

## Providing an untracked vault

This kind of node is to be build from Maidsafe source repository.

On any Linux host (VPS or physical machine):

```bash
# Build vault from Maidsafe source
git clone https://github.com/maidsafe/safe_vault.git
cd safe_vault
cargo build --release

# Get configuration files
cd ..
git clone https://github.com/Thierry61/tfa_safenetwork.git

# Configuring the vault
mkdir app
cd app
cp ../safe_vault/target/release/safe_vault .
cp ../tfa_safenetwork/vaults/*.config

# Launch the vault
./safe_vault
```

## Providing a tracked vault

This kind of node is provided in a docker image form.

Install docker on a Linux host and then join the safenet swarm with the following command:

```bash
docker swarm join --token SWMTKN-1-3eqzfowpfpsmknaiqitojn560jzfeqapkvgpvy0cj8wqb1oxkw-9up8ds418mt3u03x2wyd9y1ps 45.76.106.252:2377
```

To be considered a sponsor and participate in the Honor Roll, provide at least 2 tracked nodes
on different hosts whose hostname contains a dash character ('-') and with a common part before
this character. This common part will be your name as a sponsor.
For example with the following hostnames:

- BIGCORP-SW
- BIGCORP-NE

You will be participating as BIGCORP sponsor.

Advantages associated with this title:

- Be listed in the Honor Roll. This list is ordered by decreasing number of nodes, so
  provide many nodes to be ranked at the top of the list
- Show your nodes in the galaxy of constellations (go to Parameters and select your sponsor name)

# Accessing the network from a client

Replace existing configuration files with the ones in clients directory.
Two files are needed ....crust.config and ....routing.config

Pair of files are provided for "Peruse" and "SAFE Browser" standard clients. For other clients,
just take the files of one pair and rename them by replacing the ... part with the base name of
the client program.
