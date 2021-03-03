### type_checker 데코레이터 만들기 (인자 유효성 검사)


def type_checker(function):
    def tester(digit1, digit2):
        if (type(digit1) != int) or (type(digit2) != int):
            print('only integer support')
            return
        return function(digit1, digit2)
    return tester

@type_checker
def multi(digit1, digit2):
    print (digit1 * digit2)
