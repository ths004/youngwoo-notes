## Python 문법정리
### 자료형
- int : 숫자정수
- float : 숫자실수
- str : 문자
- bool : 논리형
- list : 배열-리스트
- tuple : 배열-리스트인데 수정못함(반복 처리 시 고정값이기 때문에 연산 속도가 리스트보다 빠르다는 장점)
- dict : 배열-키밸류.
- nohting
#### 특징
Python 에서는 자료형도 클래스로 되어있음,
파이썬의 특징 중 하나가 어떤 변수라도 서로 다른 자료형으로 값을 바꾸고 설정할 수 있습니다. 
이것은 파이썬이 변수를 값만 넣는 것이 아닌, 값을 가진 하나의 클래스를 생성하고 그 포인터를 저장하고 있기 때문, 
```
    x = 30
    print(type(x))
    y = 0.134
    print(type(y))
    s = 'string'
    print(type(s))
    bool = True
    print(bool, type(bool))
    li = [10, -324.33, 'a', "bbb"]
    print(type(li))
    print(li)
    tup = (10, -233.33, '안녕', "KK")
    print(type(tup))
    print(tup, tup[0])
    dict = {"a": 1, "b": "둘", 'c': "3"}
    print(type(dict))
    print(dict, dict['a'])
    nothing = None
    print(nothing)
```
### 인덱스

### 연산자
#### 기본 연산
```
    +	더하기	1 + 3, 10 + 30.5
    -	빼기	100 - 10, 55.5 - 30.3
    * 	곱하기	10 * 5, 20.5 * 2.3, '안녕' * 5
    / 	나누기	55 / 4, 100 / 3.3
    %	나머지	100 % 6 = 4
    //	소수점 이하 절삭 ( 몫의 정수값 )	7 // 2 = 3
    **	거듭제곱	2 ** 4 ( 2의 4승 )
```
#### 논리연산
```
    and a == 1 and b == '김치'
    or  a >= 10 or b >= 100
    not  if not b:   ( if b == False: 와 동일)
```
#### 비교연산
비교연산은 두 인자가 같은 값을 가지는지의 여부를 반환한다. 비교 연산의 결과는 bool 타입이다.
```
    >,  <,  <=, >=, ==, !=
```
객체 비교연산
```
   is 
   is not
```
#### 비트 연산 (Bitwise Operators)
```
    &: 비트 별 AND
    |: 비트 별 OR
    ^: 비트 별 XOR
    ~: 비트 별 NOT
    <<: left shift
    >>: right shift
```
### 제어문
if~elif~else~, while, for 
```
# 조건은 논리 조건으로 참일때만 해당 블록이 실행된다.
if (조건):
	내용
elif (조건2):
	내용
else:
	내용

# in-line으로 쓰려면?
if (조건): 내용

# 예
b = 5
if b == 5:
  print('참')
  b = 1
elif b >= 3:
  print('애매')
  b = 2
else:
  print('거짓')
  b = 0

##  loop는 특정 조건이 만족될 때 까지 수행되는 반복문이다.
a = 10
while a > 0:
    a -= 1
    print(a)
    if a > 3:
        break
## loop는 특정 반복 회수가 정해진 상태에서의 반복문이다.        
listitems = [0, 1, 2]
for item in listitems:
    if item == 0:
        continue
    print(item)          
```
#### Iterables & Iterators
Iterables : 
* Iterable한 객체는 반복 가능한 객체를 의미한다.이러한 객체는 iter() 함수를 통해 iterator로 변환될 수 있다.
* string, list, tuple, dict, set, frozonset 타입은 모두 iterable하다.
* 커스텀 클래스의 경우 클래스에 __iter__ 메서드를 정의하고 iterator 클래스를 반환해주면 해당 클래스가 iterable하게 만들 수 있다
Iterators : 
* Iterator는 Iterable한 객체로부터 연속적으로 값을 산출해내는 객체를 의미한다.
* Iterator 객체의 next 메서드를 통해 다음 값을 가져올 수 있다.
* Iterable 객체의 마지막 요소를 뱉은 후에는 StopIteration 예외가 발생한다.
```
a = ['com', 'jun', 'dev']
itr = iter(a)
itr.__next__()  //'com'
next(itr) //'jun'
next(itr) //'dev'
next(itr) 
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```
#### 반복문 분기
break : 반복문을 부수고 나간다.
        반복문이 깨지고 다음 코드가 실행된다
continue : 해당 반복 회차를 스킵하고 반복문의 처음으로 돌아가 다음 반복문을 실행한다.

### 함수
내장함수, 외부 라이브러리함수, 그리고 사용자 정의함수로 구분
#### 사용자 정의함수
가변파라메터 : 별표 (Asterisk, *) 사용, 디폴트 파라메터 = '값' 지정
```
    def function1(param1, param2='option'):
        print(param1)
        print(param2)

    function1('test')
    => test
    => option
    function1('test', 'ok')
    => test
    => ok
```
#### 내장함수
mport 없이 사용할 수 있는 함수
*  자주 사용하는 내장함수들
    - print()	출력
    - input()	입력
    - range()	정수의 범위 설정하고 배열로 만듬
    - list()	리스트 생성
    - abs()	부호를 + 로 변경
    - len()	길이
    - round()	소수점 이하 반올림
    - int()	int 정수형으로 변경
    - float()	float 실수형으로 변경
    - str()	문자열로 변경
    - type()	데이터 또는 클래스의 형을 반환
    - id()	변수, 함수, 클래스 등의 인스턴스의 메모리 주소를 나타내는 고유 id

### 클래스
```
class classname:
    def __init__(self):
        self.name = 'class1'
        
    def setname(self, name):
        self.name = name

    def getname(self):
        return self.name 

c1 = classname()
c1.setname('mvpcoding class')
print(c1.getname())
print(c1.name)
=> mvpcoding class       
```
### 모듈 패키지
파이썬의 패키지는 pip 로 설치 가능
```
    ## 설치
    pip install flask
    pip install numpy

    ## 프로그램에서 import 하여 사용
    import flask
    import numpy
```
#### 대표적인 라이브러리
- 데이터 분석	numpy, pandas, pytorch, scipy, scikit-learn, tensorflow, keras
- 시각화	matplotlib, seaborn
- 게임	turtle, pygame
- 이미지 프로세싱	opencv
- 데이터베이스	sqlite, pymysql, sqlalchemy
- 웹	flask, django
- GUI	Tkinter, PyQt5, kivy, flet

### 문자열 처리
* 문자열 기본 구조
```
# 따옴표 사이의 문자들
word = 'Hello world'    #작은 따옴표
word = "Hello world"    #큰 따옴표
# 숫자를 문자로 표현
word = "123" or '123'   #따옴표
word = str(123)         #str 함수

# 긴 문자열의 경우 ('''  '''사이의 문자들)
word = '''A
B
C
D
'''
```
* 문자열 인덱싱
```
word = "Hello Camp"
#index: 0123456789
print(word[0])      # H
print(word[-1])     # p
print(word[0:5])    # Hello
print(word[3:])     # lo Camp
```
* 문자열 포멧팅
%s	문자열(String)
%c	문자 1개(character)
%d	정수(Integer)
%f	부동소수(floating-point)
%o	8진수
%x	16진수
%%	Literal % (문자 % 자체)
```
date = 5
day = "금요일"
print("오늘은 %d일 %s입니다." % (date, day))
print("오늘은 {}일 {}입니다.".format(date, day))
print(f'오늘은 {date}일 {day}입니다.')
``` 
* 문자열 길이
```
str = 'abcdefg'
print(len(str))    
```
* 문자열 치환 : replace
```
str = 'this is sample string'
replace_str1 = str.replace('is', 'as')
replace_str2 = str.replace('is', 'as', 1)

print(replace_str1)
print(replace_str2)

# thas as sample string
# thas is sample string
```
* 문자열 자르기 : split
```
# 특정 문자 "/" 를 기준으로 단어를 자를 수 있음.
word = "2021/11/05/금요일"
word = word.split("/")
print(word)    
```
* 문자열 합치기 : join
```
str_list = ['this', 'is', 'sample', 'string']

str = ' '.join(str_list)
print(str)

# this is sample string    
```
* 문자 찾기 : find(),rfind()
```
str = 'this is sample string'
c1 = str.find('i')
c2 = str.find('i', 10)
c3 = str.find('i', 0, 10)

print(c1)
print(c2)
print(c3)

# 2
# 18
# 2
```

### 코딩 규칙
함수나 클래스 등의 Scope 즉 내부의 실행 범위를 정할 때 C 언어나 다른 언어처럼 범위를 나타내는 기호인 { } 등을 사용하지 않습니다. 
그럼 어떻게 함수의 내부인지를 판단하느냐 하면 indent 들여쓰기로 판단
들여쓰기는 보통 4칸으로 설정하면 좋긴 하나 2칸도 1칸도 된다.
단 같은 레벨은 같은 indent 상에 있어야 한다.
```
# indent 를 4 로 했을 때
a = 10
if a == 10:
    print('참')
    a = 1
else:
    print('거짓')
    a = 0

# indent 를 2 로 했을 때
b = 5
if b == 5:
  print('참')
  b = 1
else:
  print('거짓')
  b = 0

# indent 를 섞어서 사용 시 오류
c = 5
if c == 5:
    print('참')
  c = 1
else:
    print('거짓')
  c = 0

File "D:/basic.py", line 105
    c = 1
        ^
IndentationError: unindent does not match any outer indentation level 
```
### 리스트 객체 제공함수
append()	리스트의 끝에 추가
insert()	특정 index 에 추가
extend()	리스트의 끝에 다른 리스트를 추가
index()	특정 값을 가진 첫번째 요소 의 index 를 반환
pop()	특정 위치의 요소를 삭제
remove()	특정 값을 가진 요소를 삭제
clear()	모든 요소 삭제
count()	특정 값을 가진 요소의 수를 반환
sort()	정렬 , sort(reverse=True) 


len(list) 리스트 전체길이
max(list) 리스트 요소중 최대값 반환
min(list) 리스트 요소중 최소값 반환
list(튜플) 튜플을 리스트로 변환

### 딕션너릴 제공함수
* 기본 사용 방법
```
# 생성
my_dict = {"키1": "값1", "키2": "값2"}
another_dict = dict(키1="값1", 키2="값2")
# 접근
값 = my_dict["키1"]
값 = my_dict.get("키1", "기본값")  # 키가 없는 경우 기본값을 제공합니다.
# 추가
my_dict["새로운_키"] = "새로운_값"  # 새 항목 추가
my_dict["키1"] = "업데이트된_값"  # 기존 항목 업데이트
# 삭제
del my_dict["키1"]  # "키1" 키와 연결된 값을 제거합니다.
값 = my_dict.pop("키2")  # "키2" 키를 제거하고 해당 값을 반환합니다.
# 조회
for 키 in my_dict:
    print(키, my_dict[키])

for 값 in my_dict.values():
    print(값)

for 키, 값 in my_dict.items():
    print(키, 값)
# 키 존재 확인
if "키1" in my_dict:
    # 키가 딕셔너리에 존재합니다.
# 길이확인
길이 = len(my_dict)
```


## python 프로젝트관리

### 버전관리 (PyENV on Ubuntu)
하나의 컴퓨터에 여러가지 파이썬버전을 설치하고 이를 관리 (개발자 PC 반드시 필요)
#### 설치
* 설치
``` ubuntu
    ## udpate system package
    sudo apt update
    ## install required dependencies (optional)
    sudo sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
    ## install pyENV
    curl https://pyenv.run | bash
```
* 환경설정
- Bash Shell 사용자
~/.bashrc에 설정
```
    echo -e 'export PYENV_ROOT="$HOME/.pyenv"\nexport PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'eval "$(pyenv init --path)"\neval "$(pyenv init -)"' >> ~/.bashrc
```
- Zsh Shell 사용자
~/.zshrc에 설정
```
echo -e 'export PYENV_ROOT="$HOME/.pyenv"\nexport PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'eval "$(pyenv init --path)"\neval "$(pyenv init -)"' >> ~/.zshrc
```
* shell 재기동
```
    exec "$SHELL"
```
* PyEnv 확인
```
    pyenv --version
```
#### 사용법
* 설치할 python 버전 확인
```
    pyenv install --list
```
* python version 설치
```
    pyenv install 3.8.10
```
* python version 삭제
```
    pyenv uninstall 3.8.10
```
* pyenv 설치된 파이션 확인
```
    pyenv versions
    system
    * 3.10.8 (set by /Users/shawn/.pyenv/version)
    3.11.0    
```

* 설치된 버전 설정
```
    #global 설정
    pyenv global 3.8.10 

    #local 설정 프로젝트 디렉토리에서 설정한다.
    cd /home/dev/project1
    pyenv local 3.8.10 
```
* 파이션 버전확인
```
    # test.py
    print("Hello from Python", python_version())

    # run test.py
    python test.py
```
* 
pyenv 로 python 버전관리를 하고, 본인 기호에 맞는 가상환경 라이브러리로 가상환경을 세팅해주면 된다. ( venv, virtualenv, pipenv, poetry.. 등등 )

* 참조 URL
https://realpython.com/intro-to-pyenv/#using-the-pyenv-installer

https://shawn-dev.oopy.io/fe911cba-0b25-474c-9c3c-d18fd945c8b0

### 공식 URL
Venv vs Pipenv vs Poetry 관련
https://packaging.python.org/en/latest/tutorials/managing-dependencies/?ref=devbull.xyz#managing-dependencies

### pipenv
pipfile.lock 파일을 기반으로 패키지 관리,파이션 공식 권장
lock 파일로 패키지 관리를 하면 다음과 같은 장점
virtualenv로 가상환경을 생성하면서 pip으로 패키지를 자동으로 설치한다.
lock파일의 해쉬로 안전한 버전 관리가 가능하다.
pip으로 패키지를 설치/추가하면 자동으로 Pipfile에 변경사항이 반영된다.
* 설치
```
    pip install pipenv
```
* 가상환경 설치 & 제거
```
    pipenv --python 3.X
    pipenv --rm
```
* 가상환경 실행
```
    # Run shell
    pipenv shell

    # Rum custom commands
    pipenv run COMMANDS...
```
* 가상환경 종료
```
    exit
```
* 패키지 관리
lock 파일을 통해 패키지 관리가 이루어진다. 이 lock 파일을 만들기 위한 명세가 바로 pipfile이다. requirements.txt와 비슷
``` pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
bs4 = "*"
selenium = "*"
requests = "*"
cloudinary = "*"

[dev-packages]
python-dotenv = "*"

[requires]
python_version = "3.9"
```  
패키지명 뒤에 "*"과 같이 표시해 항상 최신 버전을 사용할 수 있다. dev-packages는 개발 환경에서만 필요한 패키지를 나타낸다
* 패키지 설치 & lock 파일 생성
```
    ## install package 
    pipenv install numpy pandas matplotlib
    ## pipfile 있는 경우 
    pipenv install

    ## make lock file
    pipenv lock
```



### venv(Virtual environment)
*  단점
- Pipenv, Poetry에 비해 부족한 기능
- pip 을 이용한 설치
- 디렉토리에 따라 activate, deactivate을 불편함
* 설치
``` ubuntu
    python3 -m pip install --user virtualenv
```
* 가상환경
```
    # 가상환경 생성
    python3 -m venv your_dir
    # 가상환경실행
    source your_dir/bin/activate
    # 가상환경 종료
    deactivate

```
* 패키지 관리
pip 와 requirements.txt 로 한다
```
    # 설치
    pip3 install -r requirements.txt
    # lock
    pip3 freeze > requirements.txt
```

### Poetry 나중에 하자.. 많이 했다.
