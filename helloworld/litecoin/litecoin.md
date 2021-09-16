# 나만의 코인 만들기


https://github.com/litecoin-project/litecoin.git

doc 폴더
빌드-윈도우
\
라이트코인은 버전이 엄청 많다 - 0.15버전이 자주 쓰임

1. cd ~
//홈디렉토리로 이동하기

2. mkdir workspace && cd workspace
workspace

3. git clone -b 0.15 --single-branch https://github.com/litecoin-project/litecoin.git ingcoin_0.0.15

4. cd ingcoin_0.0.15

5. sudo apt update

6. sudo apt upgrade
7. sudo apt install build-essential libtool autotools-dev automake pkg-config bsdmainutils curl git 

8. sudo apt install nsis
9. sudo apt install g++-mingw-w64-x86-64
10. sudo update-alternatives --config x86_64-w64-mingw32-g++  =>> 1치고 엔터

11. find 파일 변경리스트

```

------------------- 이름 바꾸기 -------------------
find ./ -type f -readable -writable -exec sed -i "s/Litecoin/INGcoin/g" {} \;

find ./ -type f -readable -writable -exec sed -i "s/LiteCoin/ingcoin/g" {} \;
find ./ -type f -readable -writable -exec sed -i "s/litecoin/ingcoin/g" {} \;
find ./ -type f -readable -writable -exec sed -i "s/litecoind/ingcoind/g" {} \;
find ./ -type f -readable -writable -exec sed -i "s/LITECOIN/INGCOIN/g" {} \;
find ./ -type f -readable -writable -exec sed -i "s/lites/ings/g" {} \;



------------------- 단위 바꾸기 -------------------
find ./ -type f -readable -writable -exec sed -i "s/LTC/ING/g" {} \;
find ./ -type f -readable -writable -exec sed -i "s/photons/iphotons/g" {} \;



------------------- 포트 바꾸기 -------------------
find ./ -type f -print0 | xargs -0 sed -i "s/9333/9233/g"
find ./ -type f -print0 | xargs -0 sed -i "s/9332/9232/g"
find ./ -type f -print0 | xargs -0 sed -i "s/19335/19235/g"
find ./ -type f -print0 | xargs -0 sed -i "s/19332/19232/g"


```

12. code . // ingcoin_0.0.15 안에 들어간 상태에서

src폴더에 chainparams.cpp 파일 들어가기

114번째 줄부터 코드 아래와 같이 변경
        pchMessageStart[0] = 0xfd;
        pchMessageStart[1] = 0xc2;
        pchMessageStart[2] = 0xb8;
        pchMessageStart[3] = 0xdd;

133번째줄 첫번째 글자 설정
https://en.bitcoin.it/wiki/List_of_address_prefixes
102


216번째 줄부터 코드 아래와 같이 변경
        pchMessageStart[0] = 0xff;
        pchMessageStart[1] = 0xd4;
        pchMessageStart[2] = 0xca;
        pchMessageStart[3] = 0xf3;

13. 제네시스 블럭 생성
cd .. // ingcoin 나간다.
git clone https://github.com/lhartikk/GenesisH0
cd GenesisH0
ls -al
python 파일이 하나 존재함

genesis.py 파일 존재하는지 확인

파이썬을 실행하기 위해 python설치를 진행할겁니다. 
sudo apt install python2
sudo apt install python3

sudo apt install python2-pip
sudo apt install python2-pip

sudo pip install scrypt construct==2.5.2

curl https://bootstrap.pypa.io/get-pip.py --output get-pip.py
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip2.py

sudo python3 get-pip.py
sudo python get-pip2.py

sudo pip2 install scrypt          
sudo pip2 install construct          
sudo pip install scrypt construct==2.5.2

sudo python2 genesis.py -a scrypt -z "hello ingcoin" -t 1631556376


http://www.unixtimestamp.com //시간 가져오는거

---------


sudo apt-get install zsh
which zsh -> 결과물 나오는경로를 아래에 넣고
chsh -s /usr/bin/zsh/

echo $SHELL // 닫고 다시
/usr/bin/zsh

// oh my zsh 
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

cd ~/.zshrc
ZSH_THEME="agnoster" 

---------