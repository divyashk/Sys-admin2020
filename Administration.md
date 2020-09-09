# Administration

## Question-1

I used Google Cloud Console's Compute Engine as my IaaS provider because I have used it before and am quite familiar with how it authenticates and implements Service accounts(required for the builder, which is my own desktop).

I built the vpn-server as follows.

   * First I installed all the dependencies for the repository 'StreisandEffect/streisand' and then cloned it.
   ```
      5  sudo apt update && sudo apt install git python-pip -y
      6  git clone https://github.com/StreisandEffect/streisand.git && cd streisand
      7  ./util/venv-dependencies.sh ./venv
      8  sudo apt-get install python3-pip python3-openssl python3-dev python3-setuptools python3-venv python-cffi libffi-dev libssl-dev libcurl4-openssl-dev
      9  ./util/venv-dependencies.sh ./venv
      10  source ./venv/bin/activate
   ```
   * Once in the python virtual environment having all the dependencies installed, I ran the file streisand from the cloned repository.
   ```
      ./streisand
   ```

   * Now I was asked to create a service account on the platform and provide a service.json file . I created the service key on the platform (in the API and Services section) and downloaded the corresponding .json file.
   * Then I was prompted to enter a 'fully qualified domain' for the vpn-server, for which I used the subdomain - vpn.divyasheel.com , before doing this I set the A-record for this sub-domain on the platform and linked it to the newly created vpn-server.
  
   
The series of fatal errors that I got were something like this.
1. ```
   TASK [gpg : Refresh the Streisand GPG keyring with keyserver information] ******
   fatal: [128.199.142.41]: FAILED! =>........something bla bla
   PLAY RECAP *********************************************************************
   128.199.142.41             : ok=31   changed=22   unreachable=0    failed=1    skipped=13   rescued=0    ignored=0   
   localhost                  : ok=13   changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

   ```
   * I went onto to the github repository of 'streisand' to look for fixes and found that the author suggested changing (just a workaround,not a fix) the line 89(in my local repos, it was 88) to 
      ```when: False.``` So I made these changes and it worked!

   * I had to start the process all over again,which involved deleting the previously built server and the corresponding A-record.
   

2. ```
   Error when installing OpenVPN by Streisand:
   failed: [localhost] (item=None) => {"censored": "the output has been hidden due to the fact that 'no_log: true' was specified for this result", "changed": false}
   fatal: [localhost]: FAILED! => {"censored": "the output has been hidden due to the fact that 'no_log: true' was specified for this result", "changed": false}
   ```
   * This error really took some time to  figure out but was finally fixed by updating the OpenVPN signing keys as suggested in one of the un-merged pull request by "lvlohammadii".

   * I again had to start over the process right since the beginning, but I had done it atleast 10 times already, and this time it atleast worked.

After tackling with all these errors, I did still recieve some errors but none them halted the installation process and were simply skipped.
```
PLAY RECAP ******************************************************************************
34.126.125.129             : ok=332  changed=270  unreachable=0    failed=0    skipped=110  rescued=2    ignored=1   
localhost                  : ok=25   changed=3    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0   
```

And finally the setup ended created the directory genereated-docs inside the cloned repo.

This directory consisted of 4 .html files( primarily 2).
* vpn-server.html consisted of the user and password required for accessing the website(instructions for using) hosted on the vpn-server.
* vpn-server-firewall-information.html consists of information listing all the open ports on the newly created server.

![](./images/generated_docs.png)





## Question-2


The case discussed  in this problem is that of Vertical Privilege escalation. 
There are many ways to prevent further damage to the system but the most immediate and effective are-
* Reduce the amount of access of privileged individuals to the least possible.
*  Closely monitor all the logs of the remaining privileged users to find any suspicious activity.
* Also, warn your employees of the intrusion so that they can help in finding the source of the attack and also safe-guard their credentials from any form of social-engineering.

