# PARITY in AWS EC2 instance

### Instance details:

- check [this post](https://ethereum.stackexchange.com/a/59038)
- using `m5d.large` at the moment
- port 8545 and 8546 opened to the world
- https://www.youtube.com/watch?v=4ac5ZeTveSs for reference

### Setting up instance

- SSH into instance
- Configure a default locale (not doing so will cause issues installing certain packages)
  - `sudo locale-gen "en_US.UTF-8"`
  - `sudo dpkg-reconfigure locales`
- update packages
  - `sudo apt-get update && sudo apt-get upgrade`
  - `sudo apt-get autoremove`
- Install [parity](https://github.com/paritytech/parity) from command line:
  - `bash <(curl https://get.parity.io -L)` for latest beta
  - or `<(curl https://get.parity.io -L) -r stable` for latest stable

### Running parity as a service
- Clone this repo.
  - `git clone https://github.com/andres3months/gasstation-express-oracle.git`
  - `cd gasstation-express-oracle`
- `sudo mv parity.service /etc/systemd/system`
- last version of file above can be found in [parity repo](https://github.com/paritytech/parity/blob/master/scripts/parity.service)
- note: add parity `--tracing on` to file above if needed
- `sudo systemctl daemon-reload` every time you change file above
- `sudo mkdir /etc/parity/`
- `sudo mv config.toml /etc/parity`
- change chain in file above as required (kovan, mainnet, etc)
- see https://wiki.parity.io/Configuring-Parity
  for reference, or use
	https://paritytech.github.io/parity-config-generator/

- `sudo systemctl start parity` to start service
- `sudo systemctl stop parity` to stop service
- `sudo systemctl status parity` to check service
- `sudo systemctl enable parity` to make service persistent

- see [here](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) for a nice reading about systemctl
