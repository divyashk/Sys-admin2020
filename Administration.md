# Administration

## Question-1

* created an account on [digitalocean](https://www.digitalocean.com).
* cloned [streisand](https://github.com/StreisandEffect/streisand) and installed all its dependencies.

```
git clone https://github.com/StreisandEffect/streisand.git && cd streisand
./util/venv-dependencies.sh ./venv
sudo apt-get install python3-openssl python-cffi libssl-dev libcurl4-openssl-dev\n
dir
./util/venv-dependencies.sh ./venv

```
* when installing the linking streisand to my digitalocean server account and further setting up the service, I encountered an error in my terminal as follows-
```
TASK [gpg : Refresh the Streisand GPG keyring with keyserver information] ******
fatal: [128.199.142.41]: FAILED! =>........something bla bla
PLAY RECAP *********************************************************************
128.199.142.41             : ok=31   changed=22   unreachable=0    failed=1    skipped=13   rescued=0    ignored=0   
localhost                  : ok=13   changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```
* I went onto to the github repository to find the fixes and found that the author suggested changing (just a workaround,not a fix) the line 89(in my local repos, it was 88) to 
   ```when: False.``` So I made these changes and it worked.