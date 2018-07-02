# PARITY in AWS EC2 instance

### Instance details:

- ubuntu 16.04 instance
- 20gb HDD (you'll need more if you use mainnet and tracing is enabled)
- T2 unlimited enabled
- port 8545 and 8546 opened to the world
- https://www.youtube.com/watch?v=4ac5ZeTveSs for reference

### Setting up instance

- SSH into instance
- update packages
  - `$sudo apt-get update && sudo apt-get upgrade)`
- Install [parity](https://github.com/paritytech/parity) from command line:
  - `bash <(curl https://get.parity.io -Lk)`

### Running parity as a service

- `sudo mv parity.service /etc/systemd/system/parity.service`
- last version of file above can be found in [parity repo](https://github.com/paritytech/parity/blob/master/scripts/parity.service)
- note: add parity `--tracing on` to file above if needed
- `sudo systemctl daemon-reload` every time you change file above
- `sudo mkdir /etc/parity`
- `sudo mv config.toml /etc/parity/config.toml`
- change chain in file above as required (kovan, mainnet, etc)
- see https://wiki.parity.io/Configuring-Parity
  for reference, or use
	https://paritytech.github.io/parity-config-generator/

- start services
  - `sudo systemctl start parity`
  - `sudo systemctl status parity`


- to stop
  - `sudo systemctl stop parity`


- to make permanent
  - `sudo systemctl enable parity`


- see [here](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) for a nice reading about systemctl
