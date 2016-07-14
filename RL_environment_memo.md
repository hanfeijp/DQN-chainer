#### Python environment

```
cd ~
wget https://3230d63b5fc54e62148e-c95ac804525aac4b6dba79b00b39d1d3.ssl.cf1.rackcdn.com/Anaconda2-2.5.0-Linux-x86_64.sh
chmod +x Anaconda2-2.5.0-Linux-x86_64.sh

./Anaconda2-2.5.0-Linux-x86_64.sh -b -p /home/ubuntu/anaconda
echo 'export PATH="/home/ubuntu/anaconda/bin:$PATH"' >> ~/.bashrc

source ~/.bashrc

```


#### VNC install for Ubuntu

```
sudo apt-get update
sudo apt-get -y install lxde
sudo start lxdm

sudo apt-get -y install vnc4server
vncserver

rm ~/.vnc/xstartup
ln -s /etc/X11/Xsession ~/.vnc/xstartup

vncserver -kill :1
vncserver

```

### DQN environment

```
pip install chainer
```

```
sudo apt-get update
sudo apt-get -y install git
sudo apt-get -y install cmake
sudo apt -y install g++
sudo apt-get install unzip

export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

```
RL_glue 導入
```
cd
wget http://rl-glue-ext.googlecode.com/files/rlglue-3.04.tar.gz
tar xfv rlglue-3.04.tar.gz
cd rlglue-3.04
./configure
make
sudo make install

```
RL_glue python codec導入
```
cd
wget http://rl-glue-ext.googlecode.com/files/python-codec-2.02.tar.gz
tar xfv python-codec-2.02.tar.gz
cd python-codec/src
python setup.py install

```
ALE導入
```
mkdir ~/github
cd ~/github
git clone https://github.com/mgbellemare/Arcade-Learning-Environment.git
cd Arcade-Learning-Environment

sudo apt-get -y install libsdl1.2-dev
sudo apt-get -y install libsdl-image1.2-dev
sudo apt-get -y install libsdl-mixer1.2-dev

cmake -DUSE_SDL=ON -DUSE_RLGLUE=ON -DBUILD_EXAMPLES=ON .
sudo make -j 4

# Pong Rom download
wget http://atariage.com/2600/roms/VideoOlympics.zip
unzip VideoOlympics.zip
mv Vid_olym.bin pong.bin
```

DQN-chainer for cpuダウンロード
```
cd ~/github
git clone https://github.com/matsuken92/DQN-chainer.git
```

複数のターミナルを立ち上げ、それぞれでコマンドを実行  


ターミナル1

```
rl_glue
```

ターミナル2
```
:~/github/DQN-chainer
python dqn_agent_nature_cpu.py
```

ターミナル3
```
:~/github/DQN-chainer
python experiment_ale.py
```


ターミナル4
```
cd ~/github/Arcade-Learning-Environment
./ale -game_controller rlglue -use_starting_actions true -random_seed time -display_screen true -frame_skip 4 ./pong.bin
```
画面表示をしない時は`-display_screen false` とする。
