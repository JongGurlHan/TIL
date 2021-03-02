### 2.2. First-class function 

### First-class 함수 
- First-class 함수는 다음의 특징을 가지고 있다.
  - 함수 자체를 변수에 저장 가능
  - 함수의 인자에 다른 함수를 인수로 전달 가능
  - 함수의 반환 값(return 값)으로 함수를 전달 가능

#### 1. 다른 변수에 함수 할당 가능
def calc_square(digit):
    return digit * digit

calc_square(2)

# 1. func1 이라는 변수에 함수를 할당 가능
func1 = calc_square
func1(4)

#### 2. 함수가 할당된 변수는 동일한 함수처럼 활용 가능 

def calc_multi(num):
    return num * num

def calc_plus(num):
    return num + num

def calc_tri(num):
    return num * num * num

def list_square(function, num_list):
    result = list()
    for num in num_list:
        result.append(function(num))
    print(result)

def list_calculator(function, num_list):
    result = list()
    for num in num_list:
        result.append(function(num))
    print(result)

num_list = [1,2,3,4,5]

list_calculator(calc_multi, num_list)
list_calculator(calc_plus, num_list)
list_calculator(calc_tri, num_list)

#### 3. 함수의 결과값으로 함수를 리턴할 수도 있음

def logger(msg):
    message = msg
    def msg_creator():
        print('[HIGH LEVEL]: ', message)
    return msg_creator

log1 = logger("Mr Han logged-in")
print(log1)
log1()

def html_creator(tag):
    def text_wrapper(msg):
        print('<{0}>{1}</{0}>'.format(tag, msg))
    return text_wrapper

h1_html_creator = html_creator('h1')
h1_html_creator('H1 태그는 타이틀을 표시하는 태그입니다')




