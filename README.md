# NYU HPC short setting guide

## Log in hpc greene:

For more detail, please check [NYU High Performance Computing website](https://sites.google.com/nyu.edu/nyu-hpc)

### 1. use vpn connect to nyu internet if you acces greene remotely

### 2. run the command line in the Termianl on your laptop
```bash
ssh NYUNetID@greene.hpc.nyu.edu
```
### 3. Then a prompt will ask you to enter your password(don't worry about the blank while typing)

<br>

- Two main repository: \home and \scratch

\home: data permanently saved but space is small (50 GB)

\scratch: data would be purged (The file that have been access for 60 days) but space is larger(5 TB)

Recommand to work with scratch

<br>

- Some time you will get the error messange ``` WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! ```
One way to solve this issue is to remove the old key
```bash
ssh-keygen -R greene.hpc.nyu.edu
```

## Use SSH Keys for Authentication:
Setting SSH keys can avoid entering your password every time while accessing to hpc(only do this on the computer you trust)

For more information, see [ssh.com](https://www.ssh.com/academy/ssh/keygen)
### 1. Run the command in the Terminal on your local machine to generate ssh key in your local computer.

NYUNetID@nyu.edu should be your email address
```bash
ssh-keygen -t rsa -b 4096 -C "NYUNetID@nyu.edu"
```
- Press enter to accept the default file location.(would probably be ```~/.ssh/id_rsa```)
- Then, Press enter again to skip the secure passphrase

### 2. Display the public SSH key in the Termianl of your local computer
```bash
cat ~/.ssh/id_rsa.pub
```
- Copy the whole thing(it should be like "ssh-rsa ...... == your_email_address")

### 3. Log into your hpc account and put the copy public key in the file "authorized_keys":
- Ensure .ssh directory exists and set the right permission by the following command line
```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```
- Open the authorized_keys file with a text editor on HPC(you can use "nano" or "vi")
```bash
nano ~/.ssh/authorized_keys
```
Then the text editor will open the file.

- Paste the public key you just copied in local computer.

- Press control+x (exit and save)
- Press y (commit the change you make)
- Press enter(no need to change the file name here, so just press enter)

### 4. Check if you can log in without typing password
- Log out the hpc account
```bash
exit
```
- Log in again
```bash
ssh NYUNetID@greene.hpc.nyu.edu
```
You should be logged in without typing password


