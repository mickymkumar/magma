# Deploy Magma Core AGW

## Run AGW Installation

To get started login into your ubuntu box and login into rootu user.

```
sudo su
```

Now, you can run the following command to install magma:

```
wget https://raw.githubusercontent.com/magma/magma/v1.8/lte/gateway/deploy/agw_install_ubuntu.sh

bash agw_install_ubuntu.sh
```

Start running the following script below. The script begins with a pre-check to identify potential modifications to your system. It then seeks your approval for these changes. If you consent by replying "yes," the script will proceed with installing Magma. Conversely, if you reply "no," the installation will be halted.

> **Warning:** The machine will reboot, but the installation is not finished yet; the script is still running in the background.

After the reinstallation, you can check the status of AGW with the following command.

```
service 'magma@*' status

```









