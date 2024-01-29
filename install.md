# Install Documetation
This is the install documentation for the project. It will contain all the information needed to install the project. This includes the following:
- [Requirements](#requirements)
- [Install](#install)


## Requirements
This project requires the following:
- [Ubuntu 20.04](https://ubuntu.com/download/desktop)
- [Docker](https://docs.docker.com/engine/install/ubuntu/)



## Install
To install this project, follow these steps:
1. Install Docker by running the following command:
```
$ sudo apt-get update
$ curl -sSL https://get.docker.com/ | CHANNEL=stable bash
$ sudo systemctl enable --now docker

```

2. Run the following command:
```
$ mkdir /var/lib/shikendo
$ curl -L -o /usr/local/bin/shinkendo https://github.com/groep11shikendo/go/releases/download/Version1/shinkendo
$ chmod +x /usr/local/bin/shinkendo
```
3. Create a file at /etc/systemd/system/shinkendo-file.service with the following content:
```
[Unit]
Description=Shinkendo File Server
After=docker.service
Requires=docker.service
PartOf=docker.service

[Service]
User=root
LimitNOFILE=4096
ExecStart=/usr/local/bin/shinkendo
Restart=on-failure
StartLimitInterval=180
StartLimitBurst=30
RestartSec=5s

[Install]
WantedBy=multi-user.target
```
4. Run the following command:
```
$ systemctl daemon-reload
$ systemctl enable shinkendo-file.service
$ systemctl start shinkendo-file.service
```
5. The server is now running on port 9999. You can access it by going to http://localhost:9999 in your browser.
6. To stop outside access to the server, run the following command:
```
$ ufw enable
$ ufw deny 9999
```

## Contributers
- [DahRealPandaaa](https://github.com/DahRealPandaaa)
- [Geerten123](https://github.com/Geerten123)
- [mikeee1](https://github.com/mikeee1)
- [MitchvdG](https://github.com/MitchvdG)
- [Rick van der Spek](https://github.com/S142500)