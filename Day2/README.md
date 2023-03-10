# Day2

## ⛹️‍♀️ Lab - Installing nginx web server in ubuntu ansible nodes via an Ansible Playbook
```
cd ~/ansible-feb-2023
git pull

cd Day2
ansible-playbook install-nginx-playbook.yml
```

Expected output
<pre>
jegan@tektutor.org $ <b>ansible-playbook install-nginx-playbook.yml</b>

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu1]
ok: [ubuntu2]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
changed: [ubuntu1]
changed: [ubuntu2]

PLAY RECAP *****************************************************************************************************************************
ubuntu1                    : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
ubuntu2                    : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
</pre>

## ⛹️‍♀️ Lab - Limiting the playbook execution to specific machine(s)
```
cd ~/ansible-feb-2023
git pull

cd Day2
ansible-playbook install-nginx-playbook.yml --limit=ubuntu1
```

Expected output
<pre>
jegan@tektutor.org $ <b>ansible-playbook install-nginx-playbook.yml --limit=ubuntu1</b>

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu1]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
ok: [ubuntu1]

PLAY RECAP *****************************************************************************************************************************
ubuntu1                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
</pre>

## Enabling the verbosity to troubleshoot/debug the issues
```
ansible-playbook install-nginx-playbook.yml --limit=ubuntu1 -vvvv > build.yml 2>&1
cat build.yml
```

Expected output
<pre>
jegan@tektutor.org $ ansible-playbook install-nginx-playbook.yml --limit=ubuntu1 -vvvv > build.yml 2>&1

jegan@tektutor.org $ cat build.yml 
ansible-playbook [core 2.14.2]
  config file = /home/jegan/ansible-feb-2023/Day2/ansible.cfg
  configured module search path = ['/home/jegan/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.11/site-packages/ansible
  ansible collection location = /home/jegan/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.11.1 (main, Jan  6 2023, 00:00:00) [GCC 12.2.1 20221121 (Red Hat 12.2.1-4)] (/usr/bin/python3)
  jinja version = 3.0.3
  libyaml = False
Using /home/jegan/ansible-feb-2023/Day2/ansible.cfg as config file
setting up inventory plugins
host_list declined parsing /home/jegan/ansible-feb-2023/Day2/inventory as it did not pass its verify_file() method
script declined parsing /home/jegan/ansible-feb-2023/Day2/inventory as it did not pass its verify_file() method
auto declined parsing /home/jegan/ansible-feb-2023/Day2/inventory as it did not pass its verify_file() method
Parsed /home/jegan/ansible-feb-2023/Day2/inventory inventory source with ini plugin
Loading callback plugin default of type stdout, v2.0 from /usr/lib/python3.11/site-packages/ansible/plugins/callback/default.py
Skipping callback 'default', as we already have a stdout callback.
Skipping callback 'minimal', as we already have a stdout callback.
Skipping callback 'oneline', as we already have a stdout callback.

PLAYBOOK: install-nginx-playbook.yml *******************************************
Positional arguments: install-nginx-playbook.yml
verbosity: 4
connection: smart
timeout: 10
become_method: sudo
tags: ('all',)
inventory: ('/home/jegan/ansible-feb-2023/Day2/inventory',)
subset: ubuntu1
forks: 5
1 plays in install-nginx-playbook.yml

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] ***

TASK [Gathering Facts] *********************************************************
task path: /home/jegan/ansible-feb-2023/Day2/install-nginx-playbook.yml:1
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'echo ~root && sleep 0'"'"''
<localhost> (0, b'/root\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'( umask 77 && mkdir -p "` echo /root/.ansible/tmp `"&& mkdir "` echo /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440 `" && echo ansible-tmp-1677560632.3023708-18094-33309568349440="` echo /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440 `" ) && sleep 0'"'"''
<localhost> (0, b'ansible-tmp-1677560632.3023708-18094-33309568349440=/root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<ubuntu1> Attempting python interpreter discovery
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'echo PLATFORM; uname; echo FOUND; command -v '"'"'"'"'"'"'"'"'python3.11'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.10'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.9'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.8'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.6'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python3.5'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/bin/python3'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/libexec/platform-python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python2.7'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'/usr/bin/python'"'"'"'"'"'"'"'"'; command -v '"'"'"'"'"'"'"'"'python'"'"'"'"'"'"'"'"'; echo ENDFOUND && sleep 0'"'"''
<localhost> (0, b'PLATFORM\nLinux\nFOUND\n/usr/bin/python3.5\n/usr/bin/python3\nENDFOUND\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'/usr/bin/python3.5 && sleep 0'"'"''
<localhost> (0, b'{"osrelease_content": "NAME=\\"Ubuntu\\"\\nVERSION=\\"16.04.7 LTS (Xenial Xerus)\\"\\nID=ubuntu\\nID_LIKE=debian\\nPRETTY_NAME=\\"Ubuntu 16.04.7 LTS\\"\\nVERSION_ID=\\"16.04\\"\\nHOME_URL=\\"http://www.ubuntu.com/\\"\\nSUPPORT_URL=\\"http://help.ubuntu.com/\\"\\nBUG_REPORT_URL=\\"http://bugs.launchpad.net/ubuntu/\\"\\nVERSION_CODENAME=xenial\\nUBUNTU_CODENAME=xenial\\n", "platform_dist_result": ["Ubuntu", "16.04", "xenial"]}\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
Using module file /usr/lib/python3.11/site-packages/ansible/modules/setup.py
<localhost> PUT /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmpx6xam0nh TO /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/AnsiballZ_setup.py
<localhost> SSH: EXEC sftp -b - -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' '[localhost]'
<localhost> (0, b'sftp> put /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmpx6xam0nh /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/AnsiballZ_setup.py\n', b'OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for \'final all\' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched \'final\'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for \'final all\' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched \'final\'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile \'~/.ssh/known_hosts\' -> \'/home/jegan/.ssh/known_hosts\'\r\ndebug3: expanded UserKnownHostsFile \'~/.ssh/known_hosts2\' -> \'/home/jegan/.ssh/known_hosts2\'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug2: Remote version: 3\r\ndebug2: Server supports extension "posix-rename@openssh.com" revision 1\r\ndebug2: Server supports extension "statvfs@openssh.com" revision 2\r\ndebug2: Server supports extension "fstatvfs@openssh.com" revision 2\r\ndebug2: Server supports extension "hardlink@openssh.com" revision 1\r\ndebug2: Server supports extension "fsync@openssh.com" revision 1\r\ndebug3: Sent message fd 3 T:16 I:1\r\ndebug3: SSH2_FXP_REALPATH . -> /root\r\ndebug3: Looking up /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmpx6xam0nh\r\ndebug3: Sent message fd 3 T:17 I:2\r\ndebug1: Couldn\'t stat remote file: No such file or directory\r\ndebug3: Sent dest message SSH2_FXP_OPEN I:3 P:/root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/AnsiballZ_setup.py M:0x001a\r\ndebug3: Sent message SSH2_FXP_WRITE I:5 O:0 S:32768\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 5 32768 bytes at 0\r\ndebug3: Sent message SSH2_FXP_WRITE I:6 O:32768 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:7 O:65536 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:8 O:98304 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:9 O:131072 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:10 O:163840 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:11 O:196608 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:12 O:229376 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:13 O:262144 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:14 O:294912 S:2920\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 6 32768 bytes at 32768\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 7 32768 bytes at 65536\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 8 32768 bytes at 98304\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 9 32768 bytes at 131072\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 10 32768 bytes at 163840\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 11 32768 bytes at 196608\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 12 32768 bytes at 229376\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 13 32768 bytes at 262144\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 14 2920 bytes at 294912\r\ndebug3: Sent message SSH2_FXP_CLOSE I:4\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n')
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'chmod u+x /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/ /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/AnsiballZ_setup.py && sleep 0'"'"''
<localhost> (0, b'', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' -tt localhost '/bin/sh -c '"'"'/usr/bin/python3 /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/AnsiballZ_setup.py && sleep 0'"'"''
<localhost> (0, b'\r\n{"invocation": {"module_args": {"gather_subset": ["all"], "gather_timeout": 10, "fact_path": "/etc/ansible/facts.d", "filter": []}}, "ansible_facts": {"ansible_processor_vcpus": 48, "ansible_chassis_asset_tag": "NA", "ansible_device_links": {"labels": {}, "masters": {}, "uuids": {}, "ids": {}}, "ansible_ssh_host_key_dsa_public": "AAAAB3NzaC1kc3MAAACBAPYRCCXbpDUwLuhhFaohfZuD1gCt7GPe4/QD+w38WZPSQUorWZMEtUBaYbrWu5G+9gAWpkK8NZM/OOs2TQpK8/d652I7iLiH45vlrfyAuHk9ECLg8Unpc5+q5wg7Sjl6ZiUeKgFGJBwviGxOzDisMZwsQYdUfRjRXD5i9yprdrAfAAAAFQDu3VCvim4YGV0yVom0/ZKLVDjJeQAAAIAiACR0VGTZ8LyaNFg45qVQ/eout36zJSkx42HeM7jc2pgteObOGcRgP72n4lstzClI1ICAfMQt3Sp81cTo98nM/E9JlxVDYu72EmZx0/WKfgHL4ZGX1qdl3BuBpXFVGv6XaYzeslNSoxLN8mDCLh0+a/vqy2WrOnGsPHmIcO+tUQAAAIBxjr/XIGf9EsQdhn6TLUjMpNTkrElPDUdUWDzHdZtWj4nHh3Wb1hV2NadmfQOGYLmsFCXI5D3KUvS/GNxIDQYPQCCcshFa5zm5XDg87qGZ0269RNv9loGyrDZ9eMaBS9rfk2Ozfw2m786bOw+w3SHGnleGZqh9EuHSFUzHQKSJXw==", "ansible_memfree_mb": 120641, "ansible_ssh_host_key_ecdsa_public_keytype": "ecdsa-sha2-nistp256", "ansible_board_vendor": "Dell Inc.", "ansible_form_factor": "Desktop", "ansible_kernel_version": "#1 SMP PREEMPT_DYNAMIC Wed Feb 15 04:35:34 UTC 2023", "ansible_devices": {"zram0": {"holders": [], "size": "8.00 GB", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "model": null, "removable": "0", "sas_device_handle": null, "virtual": 1, "sas_address": null, "sectorsize": "4096", "rotational": "0", "partitions": {}, "scheduler_mode": "", "sectors": "16777216", "host": "", "vendor": null, "support_discard": "4096"}, "sr0": {"holders": [], "size": "1024.00 MB", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "model": "DVD+-RW GU90N", "removable": "1", "sas_device_handle": null, "virtual": 1, "sas_address": null, "sectorsize": "512", "rotational": "1", "partitions": {}, "scheduler_mode": "bfq", "sectors": "2097151", "host": "", "vendor": "HL-DT-ST", "support_discard": "0"}, "sda": {"holders": [], "size": "0.00 Bytes", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "model": "SD/MMC CRW", "removable": "1", "sas_device_handle": null, "virtual": 1, "sas_address": null, "sectorsize": "512", "rotational": "1", "partitions": {}, "scheduler_mode": "bfq", "sectors": "0", "host": "", "vendor": "Generic-", "support_discard": "0"}, "nvme0n1": {"holders": [], "size": "953.87 GB", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "model": "Micron 2300 NVMe 1024GB", "removable": "0", "sas_device_handle": null, "virtual": 1, "support_discard": "512", "sas_address": null, "sectorsize": "512", "rotational": "0", "partitions": {"nvme0n1p3": {"holders": [], "sectorsize": 512, "uuid": null, "start": "3328000", "sectors": "1997080576", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "size": "952.28 GB"}, "nvme0n1p2": {"holders": [], "sectorsize": 512, "uuid": null, "start": "1230848", "sectors": "2097152", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "size": "1.00 GB"}, "nvme0n1p1": {"holders": [], "sectorsize": 512, "uuid": null, "start": "2048", "sectors": "1228800", "links": {"labels": [], "masters": [], "ids": [], "uuids": []}, "size": "600.00 MB"}}, "scheduler_mode": "none", "sectors": "2000409264", "host": "", "vendor": null, "serial": "21022C4F3E33"}}, "ansible_processor_threads_per_core": 2, "ansible_dns": {"search": ["."], "nameservers": ["192.168.1.254", "192.168.1.254"]}, "ansible_mounts": [{"inode_used": 0, "block_size": 4096, "uuid": "N/A", "block_total": 249635072, "size_total": 1022505254912, "inode_total": 0, "block_available": 239858512, "options": "rw,seclabel,relatime,compress=zstd:1,ssd,space_cache=v2,subvolid=257,subvol=/root,bind", "device": "/dev/nvme0n1p3", "mount": "/etc/hostname", "block_used": 9776560, "inode_available": 0, "fstype": "btrfs", "size_available": 982460465152}, {"inode_used": 0, "block_size": 4096, "uuid": "N/A", "block_total": 249635072, "size_total": 1022505254912, "inode_total": 0, "block_available": 239858512, "options": "rw,seclabel,relatime,compress=zstd:1,ssd,space_cache=v2,subvolid=257,subvol=/root,bind", "device": "/dev/nvme0n1p3", "mount": "/etc/hosts", "block_used": 9776560, "inode_available": 0, "fstype": "btrfs", "size_available": 982460465152}, {"inode_used": 0, "block_size": 4096, "uuid": "N/A", "block_total": 249635072, "size_total": 1022505254912, "inode_total": 0, "block_available": 239858512, "options": "rw,seclabel,relatime,compress=zstd:1,ssd,space_cache=v2,subvolid=257,subvol=/root,bind", "device": "/dev/nvme0n1p3", "mount": "/etc/resolv.conf", "block_used": 9776560, "inode_available": 0, "fstype": "btrfs", "size_available": 982460465152}], "ansible_selinux": {"status": "disabled"}, "ansible_effective_group_id": 0, "ansible_hostnqn": "", "ansible_cmdline": {"rhgb": true, "ro": true, "quiet": true, "BOOT_IMAGE": "(hd1,gpt2)/vmlinuz-6.1.12-200.fc37.x86_64", "root": "UUID=cef6f296-fcbf-41fc-b685-ea8098f7ec19", "rootflags": "subvol=root"}, "ansible_lvm": "N/A", "ansible_fips": false, "ansible_architecture": "x86_64", "ansible_bios_vendor": "Dell Inc.", "ansible_ssh_host_key_ed25519_public_keytype": "ssh-ed25519", "ansible_real_group_id": 0, "ansible_distribution_file_path": "/etc/os-release", "ansible_user_shell": "/bin/bash", "ansible_system_vendor": "Dell Inc.", "ansible_selinux_python_present": true, "module_setup": true, "ansible_chassis_serial": "22RCFD3", "ansible_product_version": "NA", "ansible_user_uid": 0, "ansible_domain": "", "ansible_kernel": "6.1.12-200.fc37.x86_64", "ansible_system_capabilities": ["cap_chown", "cap_dac_override", "cap_fowner", "cap_fsetid", "cap_kill", "cap_setgid", "cap_setuid", "cap_setpcap", "cap_net_bind_service", "cap_net_raw", "cap_sys_chroot", "cap_mknod", "cap_audit_write", "cap_setfcap+ep"], "ansible_service_mgr": "sshd", "ansible_virtualization_role": "guest", "ansible_machine": "x86_64", "ansible_processor_count": 2, "ansible_apparmor": {"status": "disabled"}, "ansible_ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQDLNs67b5TgkUTO0zcyO/JUVz2K4NdpCp8Upz9uz1YyBRTtF8X8cGaj0kSK6L6VggH2YuZOmpFoNu31vo25DaVX4MMEIkRqvhHKHRZibw8RQrIK2bcz74zJwXhJtGfSE+LgpmV8GJkDD5C13xLyk8dY95yItTCFTPWaQro5jgq6+KH51R3hkctBnKntSUH+RS2BATcayyvbbk/39L1cP6UNapng4F0XMGexxtkcCOM/aklMtsWn/62VIaLsZSpbcH07FY56m1H/4s7jhr8VRzaslG9EViAMT5nagLIVn92AEzt6AL0oRN7fJjWCE+ceD6bsP5bjl/WtMFdAxgtJA8FH", "ansible_board_serial": "/22RCFD3/CNFCW0011L00QK/", "ansible_distribution_release": "xenial", "ansible_user_id": "root", "ansible_date_time": {"iso8601": "2023-02-28T05:03:52Z", "time": "05:03:52", "second": "52", "month": "02", "tz_offset": "+0000", "date": "2023-02-28", "weekday_number": "2", "weekday": "Tuesday", "weeknumber": "09", "epoch_int": "1677560632", "epoch": "1677560632", "tz": "UTC", "iso8601_basic": "20230228T050352935538", "hour": "05", "day": "28", "tz_dst": "UTC", "minute": "03", "iso8601_basic_short": "20230228T050352", "year": "2023", "iso8601_micro": "2023-02-28T05:03:52.935538Z"}, "ansible_ssh_host_key_dsa_public_keytype": "ssh-dss", "ansible_nodename": "ubuntu1", "ansible_ssh_host_key_rsa_public_keytype": "ssh-rsa", "ansible_virtualization_type": "docker", "ansible_processor": ["0", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "1", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "2", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "3", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "4", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "5", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "6", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "7", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "8", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "9", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "10", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "11", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "12", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "13", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "14", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "15", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "16", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "17", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "18", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "19", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "20", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "21", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "22", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "23", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "24", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "25", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "26", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "27", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "28", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "29", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "30", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "31", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "32", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "33", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "34", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "35", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "36", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "37", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "38", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "39", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "40", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "41", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "42", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "43", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "44", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "45", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "46", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz", "47", "GenuineIntel", "Intel(R) Xeon(R) Silver 4214R CPU @ 2.40GHz"], "ansible_distribution": "Ubuntu", "ansible_distribution_file_variety": "Debian", "ansible_ssh_host_key_ed25519_public": "AAAAC3NzaC1lZDI1NTE5AAAAIKe6AKgLtTzzgWuGc3LtBgG+W7GRZdAUq8I4yHt3W/vu", "ansible_userspace_architecture": "x86_64", "ansible_product_uuid": "4c4c4544-0032-5210-8043-b2c04f464433", "ansible_swaptotal_mb": 8191, "ansible_distribution_major_version": "16", "ansible_local": {}, "ansible_virtualization_tech_host": ["kvm"], "ansible_bios_date": "12/15/2022", "ansible_distribution_version": "16.04", "ansible_python": {"type": "cpython", "executable": "/usr/bin/python3", "version": {"minor": 5, "major": 3, "serial": 0, "micro": 2, "releaselevel": "final"}, "has_sslcontext": true, "version_info": [3, 5, 2, "final", 0]}, "ansible_memory_mb": {"nocache": {"used": 4093, "free": 124459}, "real": {"used": 7911, "total": 128552, "free": 120641}, "swap": {"used": 0, "total": 8191, "cached": 0, "free": 8191}}, "ansible_lsb": {"major_release": "16", "release": "16.04", "description": "Ubuntu 16.04.7 LTS", "id": "Ubuntu", "codename": "xenial"}, "ansible_user_dir": "/root", "ansible_product_name": "Precision 7920 Tower", "ansible_fqdn": "ubuntu1", "ansible_memtotal_mb": 128552, "ansible_effective_user_id": 0, "ansible_virtualization_tech_guest": ["docker", "container"], "ansible_proc_cmdline": {"rhgb": true, "ro": true, "quiet": true, "BOOT_IMAGE": "(hd1,gpt2)/vmlinuz-6.1.12-200.fc37.x86_64", "root": "UUID=cef6f296-fcbf-41fc-b685-ea8098f7ec19", "rootflags": "subvol=root"}, "ansible_uptime_seconds": 7687, "ansible_processor_nproc": 48, "ansible_fibre_channel_wwn": [], "ansible_user_gecos": "root", "gather_subset": ["all"], "ansible_distribution_file_parsed": true, "ansible_os_family": "Debian", "ansible_processor_cores": 12, "ansible_swapfree_mb": 8191, "ansible_board_name": "060K5C", "ansible_env": {"_": "/bin/sh", "TERM": "xterm-256color", "PATH": "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin", "HOME": "/root", "SHELL": "/bin/bash", "SHLVL": "1", "USER": "root", "LOGNAME": "root", "SSH_CLIENT": "172.17.0.1 41782 22", "SSH_CONNECTION": "172.17.0.1 41782 172.17.0.2 22", "SSH_TTY": "/dev/pts/0", "PWD": "/root", "MAIL": "/var/mail/root"}, "ansible_chassis_version": "NA", "ansible_product_serial": "22RCFD3", "ansible_system": "Linux", "ansible_userspace_bits": "64", "ansible_user_gid": 0, "ansible_chassis_vendor": "Dell Inc.", "ansible_board_asset_tag": "NA", "ansible_hostname": "ubuntu1", "ansible_pkg_mgr": "apt", "ansible_real_user_id": 0, "ansible_system_capabilities_enforced": "True", "ansible_iscsi_iqn": "", "ansible_ssh_host_key_ecdsa_public": "AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGCCR8IgSCveC5VaLwM/LY7obseHCfYNr8GycfTvlchC+4HHadrXabOldMaf0nu+42/nC66zZYHhfz/r0K16ucg=", "ansible_bios_version": "2.29.0", "ansible_python_version": "3.5.2", "ansible_board_version": "A05", "ansible_loadavg": {"15m": 0.81, "1m": 0.68, "5m": 0.74}, "ansible_is_chroot": false}}\r\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\nShared connection to localhost closed.\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'rm -f -r /root/.ansible/tmp/ansible-tmp-1677560632.3023708-18094-33309568349440/ > /dev/null 2>&1 && sleep 0'"'"''
<localhost> (0, b'', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
ok: [ubuntu1]

TASK [Install nginx Web Server in Ubuntu] **************************************
task path: /home/jegan/ansible-feb-2023/Day2/install-nginx-playbook.yml:4
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'echo ~root && sleep 0'"'"''
<localhost> (0, b'/root\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'( umask 77 && mkdir -p "` echo /root/.ansible/tmp `"&& mkdir "` echo /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616 `" && echo ansible-tmp-1677560633.2907348-18167-11119568213616="` echo /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616 `" ) && sleep 0'"'"''
<localhost> (0, b'ansible-tmp-1677560633.2907348-18167-11119568213616=/root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
Using module file /usr/lib/python3.11/site-packages/ansible/modules/apt.py
<localhost> PUT /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmprpvn9ces TO /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/AnsiballZ_apt.py
<localhost> SSH: EXEC sftp -b - -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' '[localhost]'
<localhost> (0, b'sftp> put /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmprpvn9ces /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/AnsiballZ_apt.py\n', b'OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for \'final all\' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched \'final\'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for \'final all\' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched \'final\'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile \'~/.ssh/known_hosts\' -> \'/home/jegan/.ssh/known_hosts\'\r\ndebug3: expanded UserKnownHostsFile \'~/.ssh/known_hosts2\' -> \'/home/jegan/.ssh/known_hosts2\'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug2: Remote version: 3\r\ndebug2: Server supports extension "posix-rename@openssh.com" revision 1\r\ndebug2: Server supports extension "statvfs@openssh.com" revision 2\r\ndebug2: Server supports extension "fstatvfs@openssh.com" revision 2\r\ndebug2: Server supports extension "hardlink@openssh.com" revision 1\r\ndebug2: Server supports extension "fsync@openssh.com" revision 1\r\ndebug3: Sent message fd 3 T:16 I:1\r\ndebug3: SSH2_FXP_REALPATH . -> /root\r\ndebug3: Looking up /home/jegan/.ansible/tmp/ansible-local-18088ngg1lxvv/tmprpvn9ces\r\ndebug3: Sent message fd 3 T:17 I:2\r\ndebug1: Couldn\'t stat remote file: No such file or directory\r\ndebug3: Sent dest message SSH2_FXP_OPEN I:3 P:/root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/AnsiballZ_apt.py M:0x001a\r\ndebug3: Sent message SSH2_FXP_WRITE I:5 O:0 S:32768\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 5 32768 bytes at 0\r\ndebug3: Sent message SSH2_FXP_WRITE I:6 O:32768 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:7 O:65536 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:8 O:98304 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:9 O:131072 S:32768\r\ndebug3: Sent message SSH2_FXP_WRITE I:10 O:163840 S:17038\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 6 32768 bytes at 32768\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 7 32768 bytes at 65536\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 8 32768 bytes at 98304\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 9 32768 bytes at 131072\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: In write loop, ack for 10 17038 bytes at 163840\r\ndebug3: Sent message SSH2_FXP_CLOSE I:4\r\ndebug3: SSH2_FXP_STATUS 0\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n')
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'chmod u+x /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/ /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/AnsiballZ_apt.py && sleep 0'"'"''
<localhost> (0, b'', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' -tt localhost '/bin/sh -c '"'"'/usr/bin/python3 /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/AnsiballZ_apt.py && sleep 0'"'"''
<localhost> (0, b'\r\n{"changed": false, "cache_updated": false, "invocation": {"module_args": {"update_cache_retry_max_delay": 12, "clean": false, "state": "latest", "autoclean": false, "deb": null, "lock_timeout": 60, "cache_valid_time": 0, "allow_downgrade": false, "only_upgrade": false, "allow_unauthenticated": false, "upgrade": null, "fail_on_autoremove": false, "package": ["nginx"], "policy_rc_d": null, "dpkg_options": "force-confdef,force-confold", "allow_change_held_packages": false, "purge": false, "autoremove": false, "force_apt_get": false, "default_release": null, "name": "nginx", "install_recommends": null, "update_cache_retries": 5, "update_cache": true, "force": false}}, "cache_update_time": 1677559994}\r\n', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\nShared connection to localhost closed.\r\n")
<localhost> ESTABLISH SSH CONNECTION FOR USER: root
<localhost> SSH: EXEC ssh -vvv -C -o ControlMaster=auto -o ControlPersist=60s -o Port=2001 -o 'IdentityFile="/home/jegan/.ssh/id_rsa"' -o KbdInteractiveAuthentication=no -o PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey -o PasswordAuthentication=no -o 'User="root"' -o ConnectTimeout=10 -o 'ControlPath="/home/jegan/.ansible/cp/69ebd5c64d"' localhost '/bin/sh -c '"'"'rm -f -r /root/.ansible/tmp/ansible-tmp-1677560633.2907348-18167-11119568213616/ > /dev/null 2>&1 && sleep 0'"'"''
<localhost> (0, b'', b"OpenSSH_8.8p1, OpenSSL 3.0.8 7 Feb 2023\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: not matched 'final'\r\ndebug2: match not found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1 (parse only)\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug1: configuration requests final Match pass\r\ndebug1: re-parsing configuration\r\ndebug1: Reading configuration data /etc/ssh/ssh_config\r\ndebug3: /etc/ssh/ssh_config line 55: Including file /etc/ssh/ssh_config.d/50-redhat.conf depth 0\r\ndebug1: Reading configuration data /etc/ssh/ssh_config.d/50-redhat.conf\r\ndebug2: checking match for 'final all' host localhost originally localhost\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 3: matched 'final'\r\ndebug2: match found\r\ndebug3: /etc/ssh/ssh_config.d/50-redhat.conf line 5: Including file /etc/crypto-policies/back-ends/openssh.config depth 1\r\ndebug1: Reading configuration data /etc/crypto-policies/back-ends/openssh.config\r\ndebug3: gss kex names ok: [gss-curve25519-sha256-,gss-nistp256-sha256-,gss-group14-sha256-,gss-group16-sha512-]\r\ndebug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512]\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/jegan/.ssh/known_hosts'\r\ndebug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/jegan/.ssh/known_hosts2'\r\ndebug1: auto-mux: Trying existing master\r\ndebug2: fd 3 setting O_NONBLOCK\r\ndebug2: mux_client_hello_exchange: master version 4\r\ndebug3: mux_client_forwards: request forwardings: 0 local, 0 remote\r\ndebug3: mux_client_request_session: entering\r\ndebug3: mux_client_request_alive: entering\r\ndebug3: mux_client_request_alive: done pid = 17742\r\ndebug3: mux_client_request_session: session request sent\r\ndebug1: mux_client_request_session: master session id: 2\r\ndebug3: mux_client_read_packet: read header failed: Broken pipe\r\ndebug2: Received exit status from master 0\r\n")
ok: [ubuntu1] => {
    "cache_update_time": 1677559994,
    "cache_updated": false,
    "changed": false,
    "invocation": {
        "module_args": {
            "allow_change_held_packages": false,
            "allow_downgrade": false,
            "allow_unauthenticated": false,
            "autoclean": false,
            "autoremove": false,
            "cache_valid_time": 0,
            "clean": false,
            "deb": null,
            "default_release": null,
            "dpkg_options": "force-confdef,force-confold",
            "fail_on_autoremove": false,
            "force": false,
            "force_apt_get": false,
            "install_recommends": null,
            "lock_timeout": 60,
            "name": "nginx",
            "only_upgrade": false,
            "package": [
                "nginx"
            ],
            "policy_rc_d": null,
            "purge": false,
            "state": "latest",
            "update_cache": true,
            "update_cache_retries": 5,
            "update_cache_retry_max_delay": 12,
            "upgrade": null
        }
    }
}

PLAY RECAP *********************************************************************
ubuntu1                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
</pre>

## ⛹️‍♀️ Lab - Enabling ansible logs
We need to configure the ansible.cfg file to enable the ansible log as it is disabled by default.
```
cd ~/ansible-feb-2023
git pull

cd Day2
cat ansible.cfg

ansible-playbook install-nginx-playbook.yml --limit=ubuntu1
ansible-playbook install-nginx-playbook.yml --limit=ubuntu2
cat ansible.log
```

Expected output
<pre>
jegan@tektutor.org $ cat ansible.cfg 
[defaults]
inventory=./inventory
log_path=./ansible.log

jegan@tektutor.org $ <b>ansible-playbook install-nginx-playbook.yml --limit=ubuntu1</b>

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu1]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
ok: [ubuntu1]

PLAY RECAP *****************************************************************************************************************************
ubuntu1                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

jegan@tektutor.org $ <b>ls</b>
ansible.cfg  <b>ansible.log</b>  build.yml  install-nginx-playbook.yml  inventory  README.md

jegan@tektutor.org $ <b>ansible-playbook install-nginx-playbook.yml --limit=ubuntu2</b>

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu2]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
ok: [ubuntu2]

PLAY RECAP *****************************************************************************************************************************
ubuntu2                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   


jegan@tektutor.org $ <b>cat ansible.log</b>
2023-02-28 10:39:38,623 p=18958 u=jegan n=ansible | PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************
2023-02-28 10:39:38,631 p=18958 u=jegan n=ansible | TASK [Gathering Facts] *****************************************************************************************************************
2023-02-28 10:39:39,728 p=18958 u=jegan n=ansible | ok: [ubuntu1]
2023-02-28 10:39:39,740 p=18958 u=jegan n=ansible | TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
2023-02-28 10:39:47,218 p=18958 u=jegan n=ansible | ok: [ubuntu1]
2023-02-28 10:39:47,236 p=18958 u=jegan n=ansible | PLAY RECAP *****************************************************************************************************************************
2023-02-28 10:39:47,236 p=18958 u=jegan n=ansible | ubuntu1                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
2023-02-28 10:40:11,257 p=19396 u=jegan n=ansible | PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************
2023-02-28 10:40:11,265 p=19396 u=jegan n=ansible | TASK [Gathering Facts] *****************************************************************************************************************
2023-02-28 10:40:12,350 p=19396 u=jegan n=ansible | ok: [ubuntu2]
2023-02-28 10:40:12,364 p=19396 u=jegan n=ansible | TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
2023-02-28 10:40:16,650 p=19396 u=jegan n=ansible | ok: [ubuntu2]
2023-02-28 10:40:16,670 p=19396 u=jegan n=ansible | PLAY RECAP *****************************************************************************************************************************
2023-02-28 10:40:16,670 p=19396 u=jegan n=ansible | ubuntu2                    : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
</pre>


## ⛹️‍♀️ Lab -Installing nginx and starting the nginx web server in Ubuntu ansible nodes

```
cd ~/ansible-feb-2023
git pull

cd Day2
ansible-playbook install-nginx-playbook.yml
curl http://localhost:8001
curl http://localhost:8002
```

Expected output
```
jegan@tektutor.org $ <b>ansible-playbook install-nginx-playbook.yml</b>

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu2]
ok: [ubuntu1]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
ok: [ubuntu2]
ok: [ubuntu1]

TASK [Start the nginx web server in Ubuntu] ********************************************************************************************
changed: [ubuntu2]
changed: [ubuntu1]

PLAY RECAP *****************************************************************************************************************************
ubuntu1                    : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
ubuntu2                    : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

jegan@tektutor.org $ <b>curl http://localhost:8001</b>
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

jegan@tektutor.org $ <b>curl http://localhost:8002</b>
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

## ⛹️‍♀️ Lab -Installing nginx and starting the nginx web server in Ubuntu ansible nodes

```
cd ~/ansible-feb-2023
git pull

cd Day2
ansible-playbook install-nginx-playbook.yml
curl http://localhost:8001
curl http://localhost:8002
```

Expected output
```
jegan@tektutor.org $ ansible-playbook install-nginx-playbook.yml

PLAY [This playbook will install,configure nginx web server and will deploy a custom web page into custom web root folder] *************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [ubuntu1]
ok: [ubuntu2]

TASK [Install nginx Web Server in Ubuntu] **********************************************************************************************
ok: [ubuntu2]
ok: [ubuntu1]

TASK [Create the custom web root folder] ***********************************************************************************************
ok: [ubuntu2]
ok: [ubuntu1]

TASK [Deploy custom web page into nginx web server] ************************************************************************************
changed: [ubuntu2]
changed: [ubuntu1]

TASK [Configure nginx web server to pick the web page from our custom folder] **********************************************************
ok: [ubuntu1]
ok: [ubuntu2]

TASK [Restart the nginx web server in Ubuntu] ******************************************************************************************
changed: [ubuntu2]
changed: [ubuntu1]

PLAY RECAP *****************************************************************************************************************************
ubuntu1                    : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
ubuntu2                    : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

jegan@tektutor.org $ curl http://localhost:8001
<html>
	<head>
		<title>Welcome to DevOps!</title>
	</head>

	<body>
		<h3>Provisioned by Docker</h3>
		<h3>Configured by Ansible</h3>
		<h3>Hostname - ubuntu1</h3>
		<h3>OS -Debian - Ubuntu v16.04</h3>
		<h3>IP Address - 172.17.0.2</h3>
	</body>
</html>

jegan@tektutor.org $ curl http://localhost:8002
<html>
	<head>
		<title>Welcome to DevOps!</title>
	</head>

	<body>
		<h3>Provisioned by Docker</h3>
		<h3>Configured by Ansible</h3>
		<h3>Hostname - ubuntu2</h3>
		<h3>OS -Debian - Ubuntu v16.04</h3>
		<h3>IP Address - 172.17.0.3</h3>
	</body>
</html>
```

## 🏁 Assignment - Write a Playbook that installs apache tomcat webserver, configure tomcat to use /var/html as web root folder and deploy the custom web page on Ubuntu and CentOS using template module.

Note
1. Delete the existing containers and recreate new containers
docker rm -f $(docker ps -aq)
2. Recreate new containers
```
docker run -d --name ubuntu1 --hostname ubuntu1 -p 2001:22 -p 8001:22 tektutor/ubuntu-ansible-node:latest
docker run -d --name ubuntu2 --hostname ubuntu2 -p 2002:22 -p 8002:22 tektutor/ubuntu-ansible-node:latest
docker run -d --name centos1 --hostname centos1 -p 2003:22 -p 8003:22 tektutor/centos-ansible-node:latest
docker run -d --name centos2 --hostname centos2 -p 2004:22 -p 8004:22 tektutor/centos-ansible-node:latest
```

Ubuntu tomcat installer package is apache2
CentOS tomcat installer package is httpd

## ⛹️‍♀️ Lab - Executing the refactored ansible playbook version 2
```
cd ~/ansible-feb-2023
git pull

cd Day2/after-refactoring-v2
ansible-playbook install-nginx-playbook.yml
```

Expected output

![Refactored Playbook v2](refactored-playbook-1.png)
![Refactored Playbook v2](refactored-playbook-2.png)
