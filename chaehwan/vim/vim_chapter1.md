# Basic Movement

기본 이동은 화살표도 가능하지만 아래의 키를 활용하면 된다.
h j k l

h : 왼쪽
j : 아래
k : 위
l : 오른쪽

0 : 문자열의 맨 앞으로 간다. (^도 가능하다.)
$ : 문자열의 맨 끝으로 간다.

방향키와 마우스 사용하지 않기!

## 앞으로 이동

w : 다음 단어의 처음으로 이동(word를 생각하면 된다. 단어 단위의 이동)
W : 다음 단어의 처음으로 이동(구두점 기호 무시)
e : 다음 단어의 끝으로 이동(end를 생각하면 된다. 단어의 끝으로 이동)
E : 다음 단어의 끝으로 이동(구두점 기호 무시)

## 뒤으로 이동

b : 이전 단어의 처음으로 이동
ge : 이전 단어의 끝으로 이동(정확히 동시에 누르면 된다.)
gE : 

## 특정 문자로 이동

fc : c라는 문자를 앞쪽 방향으로 찾아서 이동한다.  
Fc : c라는 문자를 뒷쪽 방향으로 찾아서 이동한다.
(f의 검색 기능은 현재 행에서만 동작한다.)

tc : c라는 문자를 앞쪽 방향으로 찾아서 그 문자의 바로 한 칸 앞으로 이동한다.
(til을 생각하면 직관적이다.) 
Tc : c라는 문자를 뒷쪽 방향으로 찾아서 그 문자의 바로 한 칸 뒤로 이동한다. 

## 페이지 이동

ctrl + f : 다음 페이지로 이동(forward를 생각하면 직관적이다.) 
ctrl + b : 이전 페이지로 이동(backward를 생각하면 직관적이다.)
ctrl + u : 현재 페이지 절반만큼 다음으로 이동(up half을 생각하면 직관적이다.)
ctrl + d : 현재 페이지 절반만큼 이전으로 이동(down half을 생각하면 직관적이다.)

## 페이지 내에서의 이동

H : 현재 페이지 내에서의 최상단으로 이동(head를 생각하면 직관적이다.)
M : 현재 페이지 내에서의 가운데로 이동(middle을 생각하면 된다.)

## 전체 파일에서의 이동

gg : 전체 파일에서의 최상단으로 이동한다.
G : 전체 파일에서의 최하단으로 이동한다.
(숫자)G : 입력한 숫자에 해당하는 행으로 이동한다.

*, n : 커서가 위치한 특정단어를 앞으로 이동하면서 검색
(커서가 위치한 곳에서 *를 누르면 하이라이팅이 되는데 이 때 n을 한 번 누르면 
다음 단어로 이동하는 것을 알 수 있다. n을 누르다 보면 현재 검색된 단어로 정규표현식 
형태로 화면 하단에 나타나는 것을 볼 수 있다. asterisk 별표로 검색하려는 모든 단어를
찾고 next인 n을 눌러서 다음 단어를 찾는다고 생각하면 직관적이다.)

*, N : 커서가 위치한 특정단어를 뒤로 이동하면서 검색
(*, n과 같은데 뒤로 이동한다. #을 눌러도 뒤로 이동한다.)

\#, n : 커서가 위치한 특정 단어를 뒤에서부터 찾은 다음, 검색된 이전 단어로 이동하면서 검색
(*이랑 똑같은데 앞에서부터 찾는가 뒤에서부터 찾는가가 차이다. 그리고 *에서는 n을 누르면
다음 단어로 이동하는데 #에서는 이전 단어로 간다. n에서 N은 방향을 바꾼다고 생각하면 된다.)

/, n : 단어 검색 후 앞으로 이동
(/ 를 누르고 특정 단어를 입력하면 *를 눌러서 현재 커서의 단어를 선택해서 이동해 나갔던
것처럼 찾을 수 있다. 단어를 입력하면 하이라이팅이 된다.)

/, N : 단어 검색 후 뒤로 이동

?, n : / 처럼 특정 단어를 검색하지만 반대로 이동
(n을 누르면 원래 다음 단어로 이동하지만 ?로 검색하면 검색된 이전 단어로 이동한다.
N은 원래 검색된 이전 단어로 이동하지만 ?로 검색했을 경우 다음 단어로 이동한다.)   

## 함수와 클래스의 시작으로 이동

이동하는 방법에 대해 더 알고 싶다면 명령행에서 h motion.txt를 검색하면 된다.
정리가 잘 되어 있다.

]] : 다음 { (curly brace)를 찾아간다. 
(즉 블록을 사용하는 프로그래밍 언어의 다음 함수나 클래스의 시작을 찾아간다.
파이썬은 조금 아쉽게 되었다.)

[[ : 이전 { (curly brace)를 찾아간다.

][ : 다음 } (curly brace)를 찾아간다. 
(즉 블록을 사용하는 프로그래밍 언어의 다음 함수나 클래스의 끝을 찾아간다.)

[] : 이전 } (curly brace)를 찾아간다.

% : { 는 }, } 는 { 즉 각각의 짝을 찾아서 이동한다.
(이건 확인해보니 그냥 괄호에도 적용이 가능해서 파이썬에서도 짝을 찾을 때 유용하게 
사용 가능할 것 같다. matchit.vim 플러그인을 설치하면 %의 짝을 찾는 기능을 더욱 
확장해서 적용이 가능하다고 한다.)

마크 : 마크는 Vim에서 돌아갈 수 있도록 현재 위치를 저장해둔 곳이다.
아래의 명령어를 사용하면 현재 생성된 마크의 목록을 확인할 수 있다.

:marks

그리고 직접 마크를 해둘 수도 있다.

:ma 라고 입력하면 현재 위치를 a라고 마크해두는 것이다. 

'로 마크가 활성화되는데 'a 를 입력하면 내가 입력해둔 a 라는 마크 위치로 이동하게 된다.

참고) 

Jumps and marks
출처 : https://nolboo.kim/blog/2017/01/15/practical-vim/

Using marks
출처 : http://vim.wikia.com/wiki/Using_marks

# Basic Editing

## 입력모드로 전환

i : 현재 커서 위치에서 입력모드로 전환(insert라고 생각하면 직관적이다.)
I(shift + i): 현재 라인의 시작에서 입력모드로 전환(0i를 입력해도 상관은 없다.)
a : 현재 커서의 바로 뒤에서 입력모드로 전환
A(shift + a) : 현재 라인의 맨 뒤에서 입력모드로 전환(append라고 생각하면 직관적이다.)
o : 바로 아래 라인에서 입력모드로 전환
O : 바로 위 라인에서 입력모드로 전환

## 지우기

x : 현재 커서에 해당하는 문자 지우기
X(shift + x) : 현재 커서의 바로 앞에 있는 문자 지우기(Backspace와 같은 효과다.)
dd : 해당하는 라인을 전부 삭제한다.(delete를 생각하면 된다.)
dw : 해당하는 단어를 삭제한다.

## 이전 동작 반복하기

.(점/dot) : 이전에 했던 명령을 반복해서 실행한다.

## 바꾸기

cw : 현재 위치한 커서가 가리키는 단어를 바꾼다.(change)
(:set cpoptions+=$ 을 입력하면 바꾸려는 단어 끝에 $표시가 뜬다.)

r : 하나의 단어를 바꾼다.(replace)
R : replace 모드로 바뀌고 기존에 있던 텍스트들이 덮이면서 바뀌어 나간다.
(change는 현재 행에 영향을 미치기 때문에 뒤에 있던 단어들이 밀려나가지만
replace의 경우에는 그렇지 않다.)
s : s로도 바뀌는 것이 가능하다.(substitute)

## 복사하고 붙이기

:h 'virtualedit'

yy : 전체 한 라인를 복사한다. (y는 yank를 말하는데 yank는 '홱 잡아당기다'라는 뜻이 있다.)
shift + y : 전체 한 라인을 복사한다.(yy와 같다.) 
yw : 해당하는 단어를 복사한다. (yank word를 말한다.)

p : 현재 커서의 뒤에 붙이기(put or paste라고 생각하면 직관적이다.)
P : 현재 커서의 앞에 붙이기

## 이어붙이기

J : 현재 줄의 끝에 공백 하나를 두고 다음 줄을 이어 붙이기
gJ : 현재 줄의 끝에 공백 없이 이어 붙이기

## 비주얼 모드

v : 문자 단위의 지정
V : 라인 단위의 지정
ctrl + v: 블록 단위의 지정
(블록 단위로 지정한 다음 shift + i 또는 shift + a로 내용을 삽입할 수 있다.)

gv : 이전에 선택했던 비주얼 영역을 다시 선택해서 표시해준다.
(비주얼 모드를 사용하다 보면 반복적으로 같은 영역을 선택할 일이 많은데
유용하게 사용될 수 있다.)


# Working with Many Files 

## 여러 파일 한꺼번에 로드하기

먼저 vim에서 파일을 열 때 예를 들어 vim *.py 와 같이 파이썬으로 작성된 모든 파일을 연다.

그리고 아래와 같이 ls 명령어를 입력해준다.

:ls 

입력하고 나면 같이 실행된 파일들의 목록이 보인다. 그리고 각각의 파일에 대해 번호와 
%a 와 같은 표시를 확인할 수 있다. 표시의 의미가 무엇인지 궁금할 수 있는데 아래의 help
명령어로 확인하면 된다.

:h ls

%a는 현재 로드되서 창에 보이는 파일이라는 뜻이다.

## 버퍼 번호로 창 전환하기

버퍼의 번호로 창을 전환하는 방법은 다음과 같다.

:buffer (파일 번호)
ex) :buffer 2

이런 식으로 입력해주면 창이 전환되는 것을 확인할 수 있다.
꼭 버퍼의 번호로만 접근할 수 있는 것은 아니다. 

## 버퍼명으로 창 전환하기

버퍼의 이름으로 접근하는 것도 가능하다. 그리고 :buffer 명령은
:b 와 같이 줄여서 명령할 수 있다. 그래서 다른 버퍼을 열려면
다음과 같은 방식으로 여는 것이 가능하다.

:b (파일명)
ex) :b test_scheduler.py

파일명은 리눅스에서처럼 Tab 키를 누르면 파일명이 자동 완성된다.

## 가장 최근에 연 버퍼(alternative)로 창 전환하기

이렇게 창 전환한 다음 :ls 명령어를 입력하면 파일 목록 중 한 파일에 # 표시가 붙어 있는 것을
알 수 있다. #의 의미는 가장 최근에 연 파일이라는 뜻이다. 이 가장 최근에 연 파일을 
편하게 열려면 다음과 같이 입력해주면 된다.

:b#

## 파일 지우기 

다음과 같이 입력하면 파일을 목록에서 바로 지울 수 있다.
(확인해보니 실제로 지워지는 것은 아니다. 로드한 버퍼에서 지우는 명령이다.)

:bdelete

약어로 다음과 같이 입력하는 것도 가능하다.

:bd

파일 번호의 범위를 주고 지우는 것도 가능하다. 

:2,4bd

이렇게 하면 2번에서 4번 파일이 버퍼에서 지워진다.

:%bd

위와 같이 입력하면 모든 파일에서 버퍼에서 지워진다.

## 버퍼 리스트에 있는 파일 다루기

load되는 파일은 args라는 리스트 안에 담기게 된다. 다음 명령어를 입력하면
현재 load된 파일의 목록을 파악할 수 있다. 

:wn : 현재 파일을 쓰고 다음 파일로 옮겨간다.
:rewind : 다음 명령어는 첫번째 파일로 옮겨간다.
:n : 다음 파일로 넘어간다.

그리고 이 args라는 버퍼 리스트에 있는 파일들을 다루는 강력한 명령어가 있는데 
바로 bufdo 명령어다. 리스트에 있는 모든 버퍼에 대해 적용하는 명령어다.
다음과 같이 특정 패턴의 문자열을 수정하는 것도 가능하다.

:bufdo %s/pattern/replace/ge | update

참고) Run a command in multiple buffers
출처 : http://vim.wikia.com/wiki/Run_a_command_in_multiple_buffers

:wall : write all 이라는 뜻이다. 변경된 모든 버퍼에 대해 쓰기 작업을 한다.

## 창 분할하기

다음의 명령어를 입력하면 창에 대한 도움말을 볼 수 있다.

:h windows

일단 먼저 알아야 할 것이 buffer와 window에 대한 이야기다. window는 
buffer의 view일 뿐이다.

:split (파일명)

위와 같이 입력하면 창이 분할되는 것을 확인할 수 있다.

그리고 다음과 같이 입력하면 창 사이를 전환한다.

ctrl + w + x

다음과 같이 입력하면 해당 창에서 수직으로 창을 분할한다.
즉 세로로 창을 두개로 나눈다.

ctrl + w + v

## 창 사이로 이동

창을 여러 개로 분할했다면 다음 명령어로 창들 사이를 왔다갔다 하는 것이 가능하다.
방향키가 h j k l 이니 

ctrl + w + h : 왼쪽으로 이동
ctrl + w + j : 아래 창으로 이동
ctrl + w + k : 위로 이동 
ctrl + w + l : 오른쪽으로 이동 

분할된 창을 하나로 되돌리려면 다음 키들을 동시에 입력하면 된다.

ctrl + w + o 

현재 작업하고 있는 창의 위치를 옮겨주는 것도 가능하다.

ctrl + w + shift + h : 왼쪽으로 창 옮기기
ctrl + w + shift + j : 아래쪽으로 창 옮기기
ctrl + w + shift + k : 위쪽으로 창 옮기기
ctrl + w + shift + l : 오른쪽으로 창 옮기기

# How to use The Help System

vim의 help 시스템 hyperlink로 되어 있어 옮겨다니면서 도움말을 볼 수 있다.

## 도움말을 보는 방법

help 도움말을 보려면 다음과 같이 입력하면 된다.

:help

약어로 다음과 같이 입력하거나

:h

아니면 F1만 입력해주어도 상관이 없다.

j를 누르면서 내려가다 보면 tutor 등 다양한 자료들이 있는 것을 알 수 있다.
하지만 링크를 타고 들어가야 볼 수 있다. 그러므로 링크에 커서를 옮기고 다음과 같이
명령을 내려주면 된다.

ctrl + ] 

다시 원래 화면으로 돌아가려면 다음과 같이 입력하면 된다.

ctrl + t 

## 도움말 자동 완성

:help 다음의 단어는 자동 완성이 가능하다.

:set wildmenu로 wildmenu 옵션을 활성화하면 자동완성을 위해 Tab을 누를 때
그 목록을 보여줄 수 있다.

## helpgrep

helpgrep은 특정 패턴과 일치하는 단어를 찾아준다.

:helpgrep (word)

위와 같은 형식으로 입력하면 되고 다음 명령어로 일치하는 문서들을 파악할 수 있다.

:cnext
:cn

하지만 일치하는 문서가 너무 많은 경우 문제가 될 수 있다. 
이 경우 다음과 같은 명령어를 사용해서 시간을 단축할 수 있다.

:cwin

한 화면에 매치되는 단어들을 보여줘서 시간을 단축할 수 있다.

참고)
손에 잡히는 Vim - 김선영 저자
Vim Videos - Derek Wyatt 