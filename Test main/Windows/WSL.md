```bash
#List all instances
wsl -l -v

#Export instance
wsl --export INSTANCE_NAME c:\wsl\backups\instance_name.tar

#Delete instance
wsl --unregister INSTANCE_NAME

#Import instance
wsl --import INSTANCE_NAME c:\wsl\installs\instance_name c:\wsl\backups\instance_name.tar

#Stop instance
wsl --shutdown INSTANCE_NAME
```