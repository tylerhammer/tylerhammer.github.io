# Travis CI Configuration
#### Required Items
- A server with SSH access
- Github Account
- Travis-CI Account

#### Host configuration

1. SSH into the host machine via `ssh` like so:
```shell
$ ssh hammer@1.1.1.1
```
This shows that my host machine IP address is `1.1.1.1` and i'm logging in with a user `hammer`.


2. The first thing we want to do is set up an ssh key for the current user (still on the host machine) and later we'll save it on our local machine. To do this, we'll run this command:
```shell
$ cd ~/.ssh && ssh-keygen -t rsa -b 4096 -C "Project"
```
You'll get some prompt, just hit `Enter` all through to accept defaults, after that you should have your ssh key saved inside `~/.ssh/`.

3. Next, I'll add the key as an authorized key on the server like this:
```shell
$ cat Project.pub >> authorized_keys
```

4. This command is run while still in the same ~/.ssh directory. After this, let's copy the content of the public key we just generated like this:
```shell
$ cat Project.pub
```
This command will output the content of the public key on your console so you can copy the key. You'll see one long random texts on your console, mark it from the beginning to the end and copy it. Go to GitHub and add it to your account.

---

Once the key has been added to the repository in I will change directory into the directory i want to put my project (Still on my server), like so:
```shell
$ cd /var/www/html
```
Next, I will clone the repository. I'll be using SSH to clone the repository so that Password will nor be required:
```shell
$ git clone git@github.com:tylerhammer/Project.git .
```
