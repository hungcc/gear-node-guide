# Install with pre-build binary

`wget https://builds.gear.rs/gear-nightly-linux-x86_64.tar.xz && \
tar xvf gear-nightly-linux-x86_64.tar.xz && \
rm gear-nightly-linux-x86_64.tar.xz && \
chmod +x gear-node`

# Configuration

From root directory:

`cd /etc/systemd/system
sudo nano gear-node.service`

Configure and save:

`[Unit]
Description=Gear Node
After=network.target`

`[Service]
Type=simple
User=root
WorkingDirectory=/root/
ExecStart=/root/gear-node --name 'NODE_NAME' --telemetry-url 'ws://telemetry-backend-shard.gear-tech.io:32001/submit 0'
Restart=always
RestartSec=3
LimitNOFILE=10000`

`[Install]
WantedBy=multi-user.target`

# Starting the node
Run to start the service:

`sudo systemctl start gear-node`

Automatically get it to start on boot:

`sudo systemctl enable gear-node`

How to check status of gear-node service?

`sudo systemctl status gear-node`
