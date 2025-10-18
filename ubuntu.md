##### initial server setup
cf. (Digital Ocean Guide)[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu]

assuming that your ssh key was placed on the vm when it was created

1. ssh as root into server
```
ssh root@your_server_ip
```

2. create new user
```
adduser new_user
```

3. add new user to sudo group
```
usermod -aG sudo sammy
```

4. setup ufw
```
ufw allow OpenSSH
ufw enable
```

5. check that ufw allows ssh
```
ufw status
```

6. copy ssh key into new_user's home dir
```
rsync --archive --chown=sammy:sammy ~/.ssh /home/sammy
```

7. make sure password auth is disabled for ssh
in 
```
/etc/ssh/sshd_config
```
make sure the following line is uncommented and set to "no"
```
#PasswordAuthentication no
```
then 
```
service ssh restart
```


##### install file.deb
```
sudo dpkg -i file.deb
```
