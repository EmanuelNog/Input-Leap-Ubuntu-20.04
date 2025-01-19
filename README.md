# BUILD for Ubuntu 20.04


### Important:

- tests where disabled on CMakeLists.txt so it's not necessary to install gtest, etc...
- it's modified to get qt from a hard path `~/Qt/6.5.2/gcc_64/`, change CMakeLists.txt if you wish to install qt in a differen folder
- done on python 3.8.10, not that I think it matters

### What is it?

 Build guide to ubuntu 20.04 since author dropped official build.

 InputLeap it's to share mouse and keeb like Barrier.

### What to do?

 Install Qt 6.5.2
 ```shell
pip install aqtinstall
mkdir ~/Qt
cd ~/Qt
aqt install-qt linux desktop 6.5.2
```
 Add Qt to ~/.bashrc
```shell
vim ~/.bashrc
export Qt6_DIR=~/Qt/6.5.2/gcc_64/lib/cmake/Qt6
```

 Download repo and try to build
 (on repo folder)
```shell
rm -rf build
mkdir  build
cd build
cmake ..
```
 Install the required packages that cause build errors, always delete and recreate build folder

 Some pacakges that where missing for me
- avahi
```shell
sudo apt update
sudo apt install -y libavahi-compat-libdnssd-dev
```
- xtst
```shell
sudo apt install -y libxtst-dev
```

 When cmake .. runs, just make
```shell
make -j4
```

Don't forget the Network Ip addres off input leap should be the server current ip address
```shell
ifconfig
```
current wifi address is 192.168.0.8, lock it on router if possible

some stupid problems where caused by not having qt path on CMakeLists but it should be solved
