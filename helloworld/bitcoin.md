# bitcoin github주소
https://github.com/bitcoin/bitcoin

DOC 폴더에서 build-windows.md 파일을 읽어보기

wsl 설치가 되어있어야함
wsl 들어가서도 셀을 작성 할 수 있도록 환경설정

홈디렉토리에서부터 작업을 시작합니다.
cd ~ 

```
sudo apt update // 
sudo apt upgrade // 설치 좀 오래걸림
sudo apt install build-essential libtool autotools-dev automake pkg-config bsdmainutils curl git
```
build-essential: c/c++ 기본적으로 필요한 라이브러리를 제공
libtool: 라이브러리 총괄적으로 스크립트 지원하는 아이
automake: makefile을 자동적으로 생성해주는 라이브러리
pkg-config: 위랑 비슷
bsdmainutils: 유닉스계열 운영체제인 bsd의 유틸프로그램을 보음
curl: http 요청 보내주는 아이

```
sudo apt install nsis
```

현재 디렉토리 home인지 확인!
그 후 workspace
cd workspace
pwd 
~/workspace인지 확인

git clone https://github.com/bitcoin/bitcoin.git
클론 완료후

cd bitcoin
이후 
ls -al 디렉토리 확인

```
sudo apt install g++-mingw-w64-x86-64 //설치 좀 오래걸림
sudo update-alternatives --config x86_64-w64-mingw32-g++ // 1번으로 설정
```
```
PATH=$(echo "$PATH/" | sed -e 's/:\/mnt.*//g')
sudo bash -c "echo 0 > /proc/sys/fs/binfmt_misc/status"
```
sed : grep과 비슷함, 찾아서 바꿔주기

Makefile 존재하는 depends디렉토리에 들어가기
cd depends

ls -al로 확인

make HOST=x86_64-w64-mingw32 //엄청 오래걸림

* 실수내역
/bin/sh : 1: File/node.js/:/mnt/c/Program: not found
경로문제
PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')

B2_TOOL

../ depends
cd .. bicoin 폴더로 이동
ls -al 
autogen.sh 확인한뒤 폴더 실행
./autogen.sh 

```
CONFIG_SITE=$PWD/depends/x86_64-w64-mingw32/share/config.site ./configure --prefix=/  
```

make -j n   // n개씩 병렬처리 한다는 뜻

끝나면 인스톨 파일을 넣을 디렉토리를 선정

cd /mnt/c/Users/user 여기다가 넣을 예정

mkdir work //work파일 생성

cd ~/workspace/bitcoin 으로 경로 바꾸고
```
sudo make install DESTDIR=/mnt/c/Users/user/work
```

make deploy      

work 폴더에 data폴더 생성
bin폴더에 들어가서 window 터미널 열기
```
./bitcoin-qt.exe -datadir=c:\Users\user\work\data
```
