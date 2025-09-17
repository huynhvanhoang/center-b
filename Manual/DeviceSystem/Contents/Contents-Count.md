# 카운트 장치


![Contents-Count_Accomplished.png](./media/images/Contents-Count_Accomplished.png) {width="200"}

## 장치 개요

게임이 진행하는 중에 카운트를 더하거나 빼는 컨텐츠 장치입니다.    
장치를 연결하여 점수를 집계(**Plus** 혹은 **Minus**)할 수 있습니다

##장치의 특징
카운트 장치는 Flow Message를 받아서 작동하지 않습니다.
장치와 장치 연결을 통해 장치를 사용하고, 이벤트를 받았을 때 숫자 카운트를 집계하는 장치입니다.

## 장치 위치와 구분
1. 팔레트 > 공식 탭 > Contents Device 폴더
2. 장치 분류와 이름
    - 마이너스 카운트 장치 : CD_Count_Survival
      - Survival에서 사용하기 좋은 카운트 장치입니다.
      - **-1** 카운트를 집계합니다.
    - 라운드 종료 장치 : CD_Round_End
    - 게임 종료 장치 : CD_Game_End
