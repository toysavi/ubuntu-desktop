# Welcome to Ubuntu Setup Scripts!
# Instruction

## Join Domain 
After install OS to computer will require internet access to install some software/package requirement.
- Install Dependency for join Ubuntu to join domain
  ```
  sudo apt install realmd sssd sssd-tools adcli -y
  ```
- Test discover connection to domain
  ```
  realm discover -v amkdc02.amkcambodia.com
  ```
  Expected result:
  ```
  * Resolving: _ldap._tcp.amkdc02.amkcambodia.com
  * Performing LDAP DSE lookup on: 10.51.0.5
  * Successfully discovered: amkdc02.amkcambodia.com
  amkdc02.amkcambodia.com
  type: kerberos
  realm-name: amkdc02.amkcambodia.com
  domain-name: amkdc02.amkcambodia.com
  configured: no
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  ```
- Join Computer to domain
  ```
  realm join -U "User" amkdc02.amkcambodia.com
  ```
  It will prompt to input ```Password``` of the ```User``` like a below example.

      $ sudo realm join -U user1 ad1.example.com
      Password for user1: 

- Verify domain joined
  ```
  realm list
  ```
  Result would be:
 
      amkcambodia.com
        type: kerberos realm-name: AMKCAMBODIA.COM
        domain-name: amkcambodia.com 
        configured: kerberos-member 
        server-software: active-directory 
        client-software: sssd 
        required-package: sssd-tools 
        required -package: sssd 
        required-package: libnss-sss 
        required - package: libpam-sss 
        required- package: adcli
        required-package: samba-common-bin 
        login-formats: %U 
        login-policy:
  
  #### --> Completed join domain!
## Full Setup
### 1. Fresh Installation

- Intall package require
  ```
  sudo apt-get install git -y
  ```
- Download configuration file from GitHub: https://github.com/amkcambodia/ubuntu-scripts.git
  ```
  git clone https://github.com/amkcambodia/ubuntu-scripts.git /tmp/ubuntu-script
  chmod 755 -R /tmp/ubuntu-script
  cd /tmp/ubuntu-script
  ```
- Run Install
  ```./install.sh```
  ```
  ./install.sh
  ```
  - ````Choose 1 for Fresh installation````
  - Wait for a next question
  - ```Choose 2 for Teller or Bramch Setup```


## Custom Setup
  ### Custom Installation
  #### 1. Require to join domain from the above 
    Require to join domain from the above