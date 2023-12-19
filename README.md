목차
- 알고리즘 프로젝트 (선형 자료구조)
  - [프로젝트 준비(미로 생성 및 오른손의 법칙](#프로젝트-준비)
    - [1. 오른손의 법칙](#1-오른손의-법칙)

# 게임 프로그래밍 공부 - 1단계 알고리즘 공부 

Algorithm 프로젝트 (기초 알고리즘)

Maze 프로젝트 (길찾기 알고리즘)
- ConsoleHelper.h, ConsoleHelper.cpp : 콘솔의 커서 조정 및 색을 입혀주기 위한 클래스로 굳이 외울필요는 없다. 한번 세팅하면 다시 안돌아봄.
- Board.h, Board.cpp : 길찾기 알고리즘을 위해서 미로를 만들어 줘야하는데, 미로를 만드는 코드들이다. 미로는 Binary Tree 미로생성 알고리즘을 통해 제작한다.
    - 바이너리 트리 미로 생성:  (x % 2 == 0) || (y % 2 == 0) 을 통해 벽을 설정해주면 대부분이 벽으로 막혀있는데 열려있는 점들을 순회하며 위, 아래로 랜덤하게 길을 뚫어주는것.
- pch.h : 미리 컴파일된 헤더로, 컴파일 시간을 단축하기 위해서 사용한다. 추후 좌표값 계산을 편하게 하기위한 연산자 오버라이딩도 구현되어있다.
- Player.h, Player.cpp : 캐릭터 이동관련. 실질적인 길찾기 알고리즘은 player클래스의 Update문에서 담당할것이다.

## 프로젝트  준비
### 1. 오른손의 법칙  
알고리즘이라 하긴 뭐하지만 미로탈출중 가장 대표적인 방법이다.  
로직은 다음과 같다.
--------------  
로직 
1. 현재 바라보는 방향을 기준으로 오른쪽으로 갈 수 있는지 확인한다
1-1. 참일시, 오른쪽 방향으로 90도 회전 후 한 보전진
1-2. 거짓일시 2번으로.
2. 현재 바라보는 방향 기준으로 전진할 수 있는지 확인.
2-1. 참일시 앞으로 한보 전진.
2-2. 거짓일시 3번으로.
3. 왼쪽으로 90도 회전,
이후 무한 루프.
---------------
구현된 코드는 ./Maze/Player.cpp 의 RightHandOnWall함수에서 확인 할 수 있으며 결과는 다음과 같다.  
![오른손법칙](./GitHubImage/RightHandOnWall.gif)
