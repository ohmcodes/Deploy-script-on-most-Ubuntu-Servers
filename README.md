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

alias testme=~/<path_to_your_desired_dir>/deploy_script
```
