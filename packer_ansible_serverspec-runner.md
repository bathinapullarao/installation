## What is this?

Image name is gcp-proxy-image-yyyyMMdd-Hmm

## Require

- packer
- ansible
- severspec-funner (needs Ruby)

## Installation

### Ansible

#### installation

```bash
sudo yum install ansible
```

#### Verification

```bash
$ ansible --version
ansible 2.9.0
  

#### Create ansible role

Create a sample as a Nginx.

```bash
mkdir nginx-playbook
cd nginx-playbook/
ansible-galaxy init nginx
```

### serverspec-runner

#### ruby installation

serverspec-runner rquires ruby.

1. install packages

```bash
sudo yum -y install gcc make zlib zlib-devel openssl openssl-devel git libffi-devel readline-devel wget bzip2
```

2. download rbenv and setting environment variables

```bash
git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
source ${HOME}/.bash_profile
```

3. download ruby-build

```bash
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
```

4. cheking ruby version

```bash
$ rbenv install --list
  :
2.6.5
  :
```
5. install ruby

```bash
rbenv install 2.6.5
rbenv rehash
rbenv global 2.6.5
```

6. verification

```bash
$ ruby --version
ruby 2.6.5p114 (2019-10-01 revision 67812) [x86_64-linux]
```

7. download and install rubygems

```bash
wget https://rubygems.org/rubygems/rubygems-3.0.6.tgz
tar zxvf rubygems-3.0.6.tgz
cd rubygems-3.0.6
ruby setup.rb
```

#### serverspec-runner installation

```bash
gem install serverspec-runner
```

#### Verification

```bash
$ gem list serverspec

*** LOCAL GEMS ***

serverspec (2.41.5)
serverspec-runner (1.3.8
```

#### initiarize serverspec-runner

```bash
serverspec-runner --activate-specroot --specroot .
```

## Packer

### Packer installation

1. Confirm and delete exist `packer` command.

```
$ which packer
/usr/sbin/packer
$ ls -l /usr/sbin/packer
lrwxrwxrwx. 1 root root 15 Oct 21  2018 /usr/sbin/packer -> cracklib-packer
$ sudo rm /usr/sbin/packer
```

2. [Dwonload page](https://www.packer.io/downloads.html) 

```bash
$ wget https://releases.hashicorp.com/packer/1.4.5/packer_1.4.5_linux_amd64.zip
```

3. unzip package and move to /usr/local/bin

```bash
unzip packer_1.4.5_linux_amd64.zip
sudo mv packer /usr/local/bin/
```

4. verification

```bash
$ which packer
/usr/local/bin/packer
$ packer --version
1.4.5
```

## Reference

[Ansible+serverspec-runner+Packer(https://qiita.com/hiracy/items/ed3ce71c2305454102d7)
[gcp-packer](https://qiita.com/smallpalace/items/9a67f613762ee38c8caa)
[GCP-Packer](https://amemo.hatenablog.jp/entry/2017/09/25/030819)
[Packer+AnsibleAMI](https://dev.classmethod.jp/server-side/ansible/build_ami_with_packer_using_ansible/)
[Packer installation](https://www.packer.io/intro/getting-started/install.html)
[Packer-GCE](https://techblog.gmo-ap.jp/2019/07/09/packer/)
[Packerー(GCE) on Ansible](https://awsbloglink.wordpress.com/2017/11/01/packer%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E4%BD%9C%E6%88%90%E6%89%8B%E9%A0%86gce-on-ansible/)
[packer  terraform  ansible ](https://qiita.com/kanagi/items/6af87a3a59e70e7e06db)
