# Ansible Docker Netshare

Installs Docker and Netshare plugin along with other dependencies on Debian / Ubuntu

## Setup

Install ansible
```bash
# Install python packages
apt-get update
apt-get install -y python3 python3-apt python3-setuptools python3-testresources

# Update symlinks
ln -sf /usr/bin/python3 /usr/bin/python
ln -sf /usr/local/bin/pip3 /usr/bin/pip

# Install pip from source
curl -skL https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
python /tmp/get-pip.py --no-setuptools

# Installs ansible along with other components
pip install --upgrade --ignore-installed --requirement ./requirements.txt

# Display current ansible version
ansible --version
```
Install third-party roles
```bash
ansible-galaxy install -r roles/requirements.yml
```

## Generating passwords for users 

Using ansible
```bash
ansible all -i localhost, -m debug -a "msg={{ 'mypassword' | password_hash('sha512', 'mysecretsalt') }}"
```

Using mkpasswd (Ubuntu/Debian)
```bash
sudo apt-get install -y whois
mkpasswd --method=sha-512 # prompts password to be hashed
```
