# :pushpin: 귀행록 (Ghost Chronicles)
게임 플레이 영상
>https://drive.google.com/file/d/15a_SWD6fFbhL8xN9SLPNUQ7QEfSvUfnc/view

</br>

## 1. 프로젝트 정보
### **1) 제작 기간**
>2022.04.02 ~ 2024.02.01

### **2) 참여 인원**
>프로그래머 : 2명   
>그래픽 디자이너 : 2명

</br>

## 2. 개요
>귀행록은 2D 플랫포머 퍼즐 게임입니다. 플레이어는 어두운 동굴에서 탈출하기 위해 앞을 가로막는 퍼즐을 풀며 나아갑니다. 동굴을 탐험하며 아이템을 획득하고 퍼즐을 해결하는 데 사용할 수 있습니다. 배경과 오브젝트는 모두 검은색으로 표현되어, 긴장감과 미스터리한 분위기를 강조하는 미니멀리즘 아트 스타일을 특징으로 합니다.
</br>

## 3. 담당한 개발 내용
>캐릭터 조작 시스템 구현   
>몬스터 움직임 및 추격 구현  
>퍼즐 오브젝트 상호작용 구현   

</br>

## 4. 사용 기술
- Unity
- C#

</br>

## 5. 핵심 기능
- 아이템 매니저를 통해 획득 가능한 아이템 정보를 저장하고 관리합니다.
- JSON 기반의 세이브 시스템을 통해 플레이어 위치, 소지 아이템, 퍼즐 진행도, 기타 오브젝트 위치를 저장하고 불러올 수 있습니다.
- 각 퍼즐들은 설계된 구조에 맞게 작동합니다.

</br>

## 6. 핵심 트러블 슈팅
### 5.1. 플레이어 캐릭터 애니메이션 FSM 구조 문제
- 유니티에서 제공하는 '메카님'은 한 오브젝트에 적용한 복수의 애니메이션을 연결시키고 전이되도록 해주는 FSM(유한 상태 기계)입니다.
저는 플레이어 캐릭터가 이동 시의 달리는 애니메이션을 8개의 방향마다 다른 애니메이션을 적용하여 달리는 애니메이션이 부드럽게 적용되도록 구현했습니다.
- 하지만 아래와 같은 구조는 하나의 상태에서 다른 상태로 전이되기 위해 여러 상태를 거쳐야하는 경우가 생겨 전이 속도가 느려지는 문제가 발생하였다.

<details>
<summary><b>기존의 메카님</b></summary>
<div markdown="1">
  
![](https://github.com/shuby-te/Mystic-Ruins/assets/101082590/2e27b860-0649-4d1d-9cac-8f7e6a7f9bca)

</div>
</details>

- 아래의 **수정한 메카님**과 같이 달리는 애니메이션을 4방향으로 줄이고 애니메이션 전환 타이밍과 시간을 0으로 설정하여 좀 더 부드러운 움직임이 가능하도록 수정하였다.

<details>
<summary><b>수정한 메카님</b></summary>
<div markdown="1">
  
![image](https://github.com/shuby-te/Mystic-Ruins/assets/101082590/2e325fd9-0369-45a1-b129-8e7ff9e543c3)

</div>
</details>
