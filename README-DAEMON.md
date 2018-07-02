# Running as a daemon

- SSH into your chosen instance

- Clone this repo :
  `git clone https://github.com/ethgasstation/gasstation-express-oracle.git`

- Execute the following commands from console:   
  - `cd gasstation-express-oracle`
  - `sudo apt-get install python3-pip`


- Install gasstation express according to instructions in README, then execute commands below:
  - `sudo mv gasstation.service /etc/systemd/system/gasstation.service`
  - `sudo mv simplehttp.service /etc/systemd/system/simplehttp.service`
  - `sudo systemctl daemon-reload`
  - `sudo systemctl enable gasstation`
  - `sudo systemctl enable simplehttp`
  - `sudo systemctl start gasstation`
  - `sudo systemctl start simplehttp`


- From AWS console open port 8000 in your instance, save.

- Go to

    http://yourinstance:8000/ to see the data

    or to

    http://yourinstance:8000/ethgasAPI.json to get the raw json.
