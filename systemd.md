1 - cria o script
nano /etc/systemd/system/paulo.service

2 - conteúdo do script
[Unit]
Description= Java do Paulo

[Service]
Type=simple
User=root
ExecStart=java -jar /opt/server/myapp.jar
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target

3 - habilita e start
systemctl enable paulo.service
systemctl status paulo.service
