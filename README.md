# portainer
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

#proxy docker

Created the directory :

mkdir -p /etc/systemd/system/docker.service.d

Create the file :

nano /etc/systemd/system/docker.service.d/proxy.conf

Add the following line:

[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/"

Restart daemon:

systemctl daemon-reload

And this restart method worked:

service docker restart

and then it accepted all the env vars
