```python
 
# sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo vim/etc/apt/sources.list
 
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
  
sudo apt-get update
sudo apt-get upgrade 
 
# git
git config --global user.name 'gwm'
git config --global user.email '403052870@qq.com'
ssh-keygen -t rsa -C "403052870@qq.com"
cat ~/.ssh/id_rsa.pub
git clone git@codeup.aliyun.com:5eb36f403fd198000181abcc/wisdompark.git
 
# 批量删除分支
git branch |grep -v 'master' |xargs git branch -D 
 
# git config
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.ss stash
git config --global alias.sp "stash pop"
git config --global alias.sl "stash list"
git config --global alias.sa "stash apply"
git config --global alias.cp cherry-pick
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global alias.c1 "checkout HEAD^"
git config --global alias.r1 "reset HEAD^"
 
# python
./configure --with-ssl-libs='bzip' --enable-optimizations
make
sudo make install
 
# python 位置
/usr/local/bin/python3.8
 
# 删除原来的软连接
rm -rf /usr/bin/python
rm -rf /usr/bin/pip
 
#添加 python3 和 pip3的软链接
ln -s /usr/local/bin/python3.8 /usr/bin/python
ln -s /usr/local/bin/pip3.8 /usr/bin/pip
 
# poetry
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
 
# alias 
sudo vim /etc/aliasbashrc
'''
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
alias dc=docker-compose
'''
 
 
sudo vim /etc/profile
'''
if [ -f /etc/aliasbashrc ]; then
  . /etc/aliasbashrc
fi
'''
 
 
# docker 官方 https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04 
# GPG证书
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL http://mirrors.aliyun.com/docker-ce/ubuntu/gpg | sudo apt-key add -
# 新增数据源
sudo add-apt-repository "deb [arch=amd64] https://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update && sudo apt-get install -y docker-ce 
sudo systemctl status docker
 
# 配置docker源
tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": ["https://9ytp9chd.mirror.aliyuncs.com"]
}
EOF
 
sudo systemctl restart docker
 
docker build
docker pull
docker run
# 宿主机8000:容器8000 容器名字aaa 守护态运行镜像bbb
docker run -p 8000:8000 --name aaa -d bbb 
 
# docker-compose https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04 
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```
