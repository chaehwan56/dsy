# Chapter6. 보조저장장치

# 자기 디스크

우리가 흔히 말하는 하드 디스크를 말함
* 디스크는 자화될 수 있는 물질로 코팅된 플라스틱이나 금속을 이용한 원형 평판으로 만들어짐
    * 그 평판 위에 헤드라고 불리는 전도성 코일을 통하여 표면을 자화시킴으로써 데이터를 저장
    * 헤드는 디스크에 저장된 데이터를 읽을 때도 사용
* 디스크에 있는 여러 개의 동심원들을 트랙이라고 부름
    * 데이터들은 트랙 위에 저장
    * 헤드가 트랙을 지나가면서 데이터를 저장하거나 인출

참고) HDD의 짧은 역사와 동작 원리
출처 : https://www.youtube.com/watch?v=yqdme_CZo2k

디스크 쓰기 : 트랙 상에 데이터를 저장하는 동작
-> 자기장이 발생되는 전기적 성질 이용

디스크 읽기 : 데이터를 디스크 표면으로부터 감지하여 인출하는 동작

디스크 팔에 구동장치가 있어 헤드가 이동 가능 -> 이를 통해 액세스
그런데 헤드가 한 개라면 헤드가 원하는 트랙까지 이동하는데 상당한 시간이 걸림
-> 그래서 시간을 절약하기 위한 방법 고안
   * 다중 헤드 디스크
    하나의 디스크 팔에 여러 개의 헤드를 부착하여 헤드가 이동해야 하는 거리 단축
   * 고정 헤드 디스크
   각 트랙마다 헤드를 두어 헤드가 트랙 사이로 이동할 필요가 없음
   -> 시간 크게 단축 / 디스크 제작 비용 증가 (특수한 상황에 사용)

디스크 구조
* 동심원을 이루고 있는 트랙 : 헤드가 지나갈 수 있도록 연속적인 통로로 만들어짐
* 트랙은 논리적으로 여러 개의 섹터로 분리
    * 섹터 : 트랙의 분할된 각 부분 / 데이터 전송 단위인 한 블록을 저장
    * 디스크에 데이터를 저장하거나 읽는 동작 -> 블록 단위로 이루어짐
    -> 각 섹터에 저장할 수 있는 데이터 용량이 그 블록 크기에 해당
    * 섹터 들 사이에는 구분을 위해 약간의 갭을 두고 있음 -> 섹터 간 갭
* 트랙 역시도 자장 간 간섭 때문에 발생하는 오류를 방지하기 위해 약간의 
간격을 유지하고 있음 -> 트랙간 갭
* 트랙의 길이는 바깥쪽에 위치할수록 안쪽보다 더 길어짐
    * 디스크에서는 읽기 / 쓰기 동작을 간단하게 설계하기 위하여 트랙당 저장되는
    데이터 비트들의 수를 모두 같게 함 -> 바깥쪽 트랙의 저장 밀도가 안쪽 트랙의
    저장 밀도보다 낮음
    * 일정한 속도로 회전하는 상태에서도 데이터를 동일한 비율로 액세스 가능
      (등각속도 방식(CAV)) -> 저장 공간 낭비하는 것이 단점

디스크 형식화 작업
* 트랙의 시작, 섹터의 시작과 끝을 구분하기 위한 제어 데이터 -> 트랙 및 섹터의
  특정 위치에 기록

디스크 액세스 시간
* 디스크 액세스 시간 = 탐색 시간 + 회전 지연 시간 + 데이터 전송 시간
    * 탐색 시간 : 헤드를 해당 트랙으로 이동시킴
        * 현재 위치에서부터 원하는 트랙까지의 거리에 따라 달라짐
        * 기계적인 이동 -> 시동 시간 필요
        * 액세스할 데이터들의 지역성 높은 경우 탐색 시간 크게 단축
    * 회전 지연 시간 : 원하는 데이터가 저장된 섹터가 헤드 아래로 회전되어 
      올 때까지 기다림
      * 디스크의 회전 속도에 따라 결정
      * 원하는 섹터가 직전에 지나가면 한 바퀴 돌아올 때까지 기다려야 함
    * 데이터 전송 시간 : 데이터 전송 
      * 블록의 크기, 회전 속도, 트랙의 저장밀도, 버스전송률 등에 따라 결정

# RAID

배경 : 프로세서의 속도와 디스크의 속도 간의 매우 큰 불균형
-> 컴퓨터 시스템의 작업  처리 속도 궁극적으로 디스크 속도에 크게 의족하게 됨
프로세서의 속도가 더 빨라지더라도 전체 시스템의 성능 향상은 디스크 I/O에 의해
제한될 수 밖에 없음

어떻게 디스크의 성능을 높일 것인가?
여러 개의 작은 디스크들을 배열 구조로 연결하고 하나의 유니트로 패키징
-> 액세스 속도 크게 향상
-> 신뢰도 높임

RAID의 배경
디스크의 저장 밀도 증가 -> 메가바이트당 가격 인하 / 디스크 용량은 증가
                          (특히 전력 소모가 낮은 소형 디스크)
-> 하나의 대형 디스크를 사용하는 것보다 크기가 작은 여러 개의 디스크들을
서로 연결하여 사용하는 것이 하나의 큰 용량을 가진 디스크 유니트로 사용하는
것보다 저렴한 가격으로 더 큰 용량을 가진 디스크 서브시스템 구축 가능

디스크 - 온라인 보조저장장치
-> 용량의 증가만큼 속도와 신뢰도 향상이 중요
-> RAID : 분산 저장 -> 여러 디스크들로부터 동시에 읽거나 쓰는 것 가능

데이터 블록들을 여러 개의 디스크들에 분산 저장하는 기술 
-> "디스크 인터리빙(disk interleaving)"
(라운드 로빈 방식으로 균등하게 분산 저장 가능)
=>  병목 현상 줄이이고 액세스 속도 향상 가능
문제는 어느 한 디스크에만 결함이 발생하여도 전체 데이터 파일이 손상되는 문제

MTTF(Mean Time To Failure) : 장치에 결함이 발생하는 평균 시간  간격
(고장이 발생하는 기간들의 평균값)

MTTF이 상당히 낮아지는 것

한 디스크만 고장나도 전체 디스크 배열을 사용할 수 없다.

이 문제를 극복하기 위한 여러 노력 끝에 오류가 발생하는 경우에도 원래의 데이터를 
복구할 수 있는 RAID 출현 -> "검사 디스크"

배열 내의 한 디스크에 결함이 발생하면 그 디스크의 사용이 중단되고, 검사 디스크에 
저장된 정보를 이용하여 원래의 정보를 신속히 재구성하여 여분 디스크에 저장

MTTR(Mean Time To Repair) : 복구 과정에 걸리는 평균 시간

내부 회로에 의해 자동적으로 다른 디스크로 대체되므로 결함이 발생하더라도 중단될 필요
없음

RAID의 종류

1) RAID-1

* 디스크 미러링 방식
    * 한 패키지 내 데이터 디스크와 미러 디스크 같이 존재
    * 데이터 디스크와 미러 디스크는 짝을 이루고 데이터 디스크의 내용은
    미러 디스크의 같은 위치에 복사됨
    * 데이터 디스크에 문제가 생겨도 미러 디스크에도 저장이 되어 있으므로
    괜찮음 -> 결함 복구에 시간을 전혀 소모하지 않고도 높은 신뢰도 확보 가능
    * 쓰기 동작은 항상 두 디스크에서 동시에 수행
    * 단점은 가격이 높다는 것 - 사용 가능한 용량이 절반으로 줄어들기 때문이다.

2) RAID-2

* 데이터를 비트 단위로 인터리빙하는 것도 가능
* 데이터 단어를 이루고 있는 비트들을 여러 개의 데이터 디스크에 한 비트씩 분산 저장
  \+ 검사 디스크를 추가하고 해밍 코드를 사용하여 비트 오류를 검출하고 정정도 가능
* 해밍 코드의 원리에 따라
  2^C - 1 >= G + C
  데이터 디스크의 수 : G
  필요한 검사 디스크들의 수 : C
* 검사 디스크에 의한 오버헤드는 전체 디스크들의 수가 증가할수록 감소
* RAID-1보다는 적은 수의 디스크들이 필요하지만, 검사 디스크의 수가 데이터 디스크의 수의
  log2값에 비례하므로 여전히 가격 높음 -> 그래서 많은 오류가 발생하는 환경에서만 사용

3) RAID-3

* RAID-2에서 사용된 검사 디스크들은 오류가 발생한 비트의 위치를 검출하기 위한 것인데,
많은 수의 검사 디스크를 사용해야 하기 때문에 낭비가 매우 큼
-> RAID-3는 한 개의 패리티 디스크만 추가
* 데이터 디스크들의 동일한 위치에 있는 비트들에 대한 패리티 비트가 패리티 디스크와
동일한 위치에 저장
* 패리티 비트와 다른 비트들 간에 XOR 연산을 수행함으로써 원래 값을 찾을 수 있다.
ex) '1001' -> 네 개의 데이터 디스크들에 한 비트씩 저장되어 있으므로 짝수 패리티 비트
p = 0 을 패리티 디스크에 저장
-> 두 번째 디스크에 오류 발생 시 b2 = 0 XOR 1 XOR 0 XOR 1 = 0
이러한 방법을 통해 어떤 데이터 디스크에 결함이 발생하더라도 다른 디스크의 데이터를 이용하여
결함 디스크의 데이터들을 복구 가능
* 쓰기 동작을 할 때마다 패리티 비트들을 갱신해야 하므로 쓰기 시간이 많이 걸림

4) RAID-4 

* RAID-2, RAID-3이 데이터를 비트 단위로 분산 저장해서 모든 데이터 디스크들을 동시에 액세스
해야 했다면 RAID-4의 경우 필요한 데이터 블록을 어느 한 디스크에 모두 저장
-> 각 액세스 요구를 서로 다른 디스크들에서 독립적으로 처리 가능
* 문제는 어떤 블록의 내용을 변경하게 되면 해당 패리티 블록도 그에 따라 갱신되어야 함
  이 때 다른 디스크에 같은 위치에 저장된 데이터 블록들도 사용해서 패리티 블록을 갱신할 
  수 있음
  -> 같은 위치의 데이터 블록들을 읽고 패리티 블록을 다시 쓰는 등 동작에 걸리는 시간이
  매우 길어지므로 성능이 현저히 저하됨
  -> 이 과정의 연산은 줄일 수 있지만 여전히 패리티 디스크에 액세스들이 집중되는 병목
  현상으로 성능이 저하되는 문제가 발생함

5) RAID-5

* 모든 설계 개념은 RAID-4와 동일하지만, 패리티 블록들을 모든 디스크들에 분산 저장한다는 
  점이 차이점이다.
* 분산 저장 방식으로 패리티 갱신을 위한 액세스들이 분산되어 패리티 디스크에 대한 
  병목 현상이 완화될 뿐 아니라, 쓰기 동작들을 병렬로 수행하는 것도 가능함
* 여러 블록을 동시에 쓰는 '큰 쓰기'의 경우에는 별 문제가 없지만, 어느 한 블록만 쓰는
  작은 쓰기의 경우 매 쓰기 동작마다 성능이 현저히 떨어짐(작은 쓰기의 문제)


# 플래시 메모리와 SSD

DRAM의 문제 : 휘발성 / 용량

그런데 주기억장치와 보조저장장치 간에는 빈번한 정보 전송 발생
* 시스템 초기화 : OS -> 프로그램, 주기억장치로 적재
* 응용프로그램이 처음 수행 : From 디스크 -> 주기억장치로 적재
* 새로 생성되거나 수정된 데이터 : 보조저장장치에 영구 저장
* 주기억장치 공간이 부족할 경우 : 적재되어 있던 블록은 swap-out / 새로운 블록은 swap-in

그리고 하드디스크는 기계장치를 많이 포함하고 있기 때문에 속도가 매우 느림 

최근 디스크의 단점을 보완할 수 있는 새로운 유형의 보조저장장치 출현
-> SSD(솔리드 스테이트 드라이브)
SSD : 기계장치가 아닌, 반도체 기억장치 칩들을 이용하여 구성한 대용량 저장장치
* 이 장치에 사용되는 반도체 기억장치는 EEPROM의 한 유형인 플래시 메모리
* RAID가 여러 개의 소형 디스크들을 배열로 구성한 것처럼 SSD도 여러 개의 플래시
메모리 칩들을 한 패키지 내에 배열로 설치하여 대용량 저장장치를 개발한 것

참고) SSD가 빠른 이유
https://www.youtube.com/watch?v=s4ZSL35WhfU

애초에 EEPROM은 비휘발성 반도체 기억장치로 전기적으로 삭제 가능하지만,
가격과 저장 밀도 측면에서 디스크를 대체할 수 있는 저장장치로 보기는 힘들었음
-> 그런데 EEPROM의 개선된 변형으로, 한 개의 트랜지스터를 이용하여 한 비트를
저장할 수 있고, 전력 소모가 낮으며 신뢰성이 뛰어난 플래시 메모리가 개발되면서
대체 가능한 자원으로 부각됨

플래시 메모리의 동작원리

플래시 메모리에는 셀(기억소자)가 존재하고 그 셀 안에는 전력을 스위칭하는 데 
사용되는 트랜지스터가 있는데 트랜지스터에는 게이트라는 것이 존재

게이트는 다시 제어 게이트와 부동 게이트로 구성되는데 부동 게이트는 정보 저장의 
핵심적인 역할을 하고 제어 게이트에 충분히 높은 전압을 인가하면 강력한 자기장이
발생하여 N-채널의 전자들이 부동 게이트로 흘러 들어감(터널링 효과)
이 후 전압을 인가하지 않으면 터널링 효과 사라지고 부동 게이트에 들어간 전자들은
그 안에 갇힘 
-> 이것이 플래시 메모리의 쓰기 동작의 원리

이후 별도의 단자를 통해 충분히 높은 전압을 인가하면 전기장의 영향으로 전자들이 
산화막을 통과하여 빠져나오게 되고 부동 게이트는 비게 됨
-> 삭제 동작의 원리

SLC, MLC 및 TLC
* 플래시 메모리에서는 기본적으로 셀당 한 비트씩 저장됨
    * SLC(single level cell) : 한 비트씩 저장하는 셀
    * MLC(multi level cell) : 셀당 두 비트씩 저장하는 셀
    * TLC(triple level cell) : 셀당 세 비트씩 저장하는 셀
* 저장밀도는 MLC와 TLC가 높지만 셀의 데이터를 읽어들이면서도
구분이 쉽지 않은 등의 문제로 속도가 느려지고 오류도 발생 가능


# 광 저장장치

1) CD-ROM
2) CD-R/RW
3) DVD
4) 블루레이 디스크
