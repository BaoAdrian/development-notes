# Ubuntu 18.04
Used the following [resource](https://www.digitalocean.com/community/tutorials/how-to-install-go-on-ubuntu-18-04)

Navigate home and curl tarball
```
cd ~
curl -O https://dl.google.com/go/go1.10.3.linux-amd64.tar.gz
tar xvf go1.10.3.linux-amd64.tar.gz
```

Change permissions and move to recommended location
```
sudo chown -R root:root ./go
sudo mv go /usr/local
```

Set `GOROOT` and `GOPATH` variables
```
sudo nano ~/.profile

# Add the following and save
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

Activate changes
```
source ~/.profile
```

Remove tarball
```
rm go1.10.3.linux-amd64.tar.gz
```