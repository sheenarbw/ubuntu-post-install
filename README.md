# Ubuntu 19.10 setup guide
16 Nov 2019

# Keyboard shortcuts
- to make life faster

# Download chrome 
- just google it

# install the basics 
```
sudo apt -y update && sudo apt -y upgrade
sudo apt -y dist-upgrade
sudo apt -y install git terminator openssh-client openssh-server gitk tree
sudo apt -y install build-essential python-dev python-setuptools python-pip
sudo apt -y install libncursesw5-dev libgdbm-dev libc6-dev
sudo apt -y install zlib1g-dev libsqlite3-dev tk-dev
sudo apt -y install libssl-dev openssl
sudo apt -y install libffi-dev
sudo apt -y install curl zsh
sudo apt -y install python3.7 python3.7-dev python3.8 python3.8-dev
sudo -H pip install virtualenvwrapper
```

# Oh my zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
cd ~/.oh-my-zsh/plugins/
git submodule add  https://github.com/djui/alias-tips.git
code ~/.zshrc

```

replace the plugins line with:
```
plugins=(  git docker docker-compose per-directory-history alias-tips)
```

add this to the top of the file
```
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/workspace
source /usr/local/bin/virtualenvwrapper.sh
```

# Node (currently v 12)

See: https://github.com/nodesource/distributions/blob/master/README.md

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install -y nodejs
sudo apt install -y  gcc g++ make

curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install -y yarn


# Docker
https://docs.docker.com/install/linux/docker-ce/ubuntu/


sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"


if you are running an experimental version of ubuntu then `bionic` is a good version


sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

sudo groupadd docker
sudo usermod -aG docker $USER

docker run hello-world

sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose



# cleanup
sudo apt autoremove