# SSH Server

First we install the open ssh server:

```bash
$ sudo apt install openssh-server
```
Optionlly if you want to gove access to root etc you cn do so by editing /etc/ssh/sshd_config.
After you do so do not forget to run:

```bash
$ sudo systemctl restart sshd
```
Then we need to make sure ssh can have access through the fire wall by running:

```bash
$ sudo ufw allow ssh
```
Finally test out to see if your ssh is working:

```bash
$ ssh username@server_ip
```

Good job! If you got here you are technically done setting up the server, now it's time to start the worstation, create a new VM following the [tutorial](./VM.md) and then move on to [this step](./WS.md).