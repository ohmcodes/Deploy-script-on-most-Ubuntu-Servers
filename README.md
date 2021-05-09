# Deploy-script-on-most-Ubuntu-Servers
Deploy script on most Ubuntu Servers

## Used codes/app
  - nano
  - touch (file creation)
  - chmod (change file permission)
  - #!/bin/bash (ask the server to run terminal script via file script content)
  - ~/  means root user folder (it will always start with [/home/user/])

## Create deploy file
```
Note: navigate to your user folder or desired dir
Note: in this tutorial were gonna use deploy_script file

touch deploy_script
chmod +x deploy_script
sudo nano deploy_script

type in:


#!/bin/bash
#desired terminal script

#add echo for logs

echo "test me"
```

## Create bash_aliases if not exist
```
touch ~/.bash_aliases
sudo nano ~/.bash_aliases

type in:
Note: alias <command_scirpt> = the file (make sure you remove spaces thats only representation)

alias deploy=~/<path_to_your_desired_dir>/deploy_script
```


## Activate bash_aliases without restarting the machine
```
source ~/.bashrc
```

## If you encounter asking a server password with sudo command
```
$echo <password> | sudo -S <command>

$./configure && make && echo <password> | sudo -S make install && halt


Note: replace <password> with your password.

OTHER Examples

echo <password> | sudo systemctl daemon-reload &&
sudo systemctl restart gunicorn &&
sudo service nginx restart
```


## Sample Bash
```
#!/bin/bash

# Define a timestamp function
timestamp=$(date +%d/%m/%Y%T)
dir=<path_to_error_logs>

echo "${timestamp} Activating source" >> ${dir}/logs/deploy/errors.log

source $dir/bin/activate

echo "${timestamp} Updating Repo..." >> ${dir}/logs/deploy/errors.log

cd ${dir}/ppem && git pull --no-edit >> ${dir}/logs/deploy/errors.log

echo "${timestamp} Applying Changes..." >> ${dir}/logs/deploy/errors.log

echo yes | python manage.py collectstatic >> ${dir}/logs/deploy/errors.log

echo "${timestamp} Restarting Engine..." >> ${dir}/logs/deploy/errors.log

sudo systemctl daemon-reload >> ${dir}/logs/deploy/errors.log

sudo systemctl restart gunicorn >> ${dir}/logs/deploy/errors.log

sudo service nginx restart >> ${dir}/logs/deploy/errors.log

echo "================================================================" >> ${dir}/logs/deploy/error>

```
