ex) 우리가 파일을 총 3개를 빌드해야합니다.

hello.cpp world.cpp jihyun.cpp

build.sh

g++ -0 hello hello cpp
g++ -0 world world cpp
g++ -0 jihyun jihyun cpp


... 100개.

sh build.sh

make > 원하는대로 디렉토리 만들어서 보낼 수 있다.

./helloworld
hello.cpp
world.cpp
jihyun.cpp

빌드를 하게 된다면

./helloworld/build
hello
world
jihyun

makefile c++ 배운
빌드를 하는방법

c