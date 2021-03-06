프로그램 실행의 흐름을 구성하는 함수들도 바이너리 형태로 메모리 공간에 저장되어서 호출시 실행이 되는데, 메모리상에 저장된 함수의 주소값을 저장하는 포인터 변수가 바로 함수 포인터 변수이다.

## 함수포인터의 이해
1. 모든 함수는 프로그램 실행시 메인 메모리에 저장되어서 실행이 된다.   
2. 함수의 이름은 함수가 저장된 메모리공간의 주소값을 의미한다.   
3. 함수의 이름도 배열과 같이 상수형태의이다.   
4. 함수 포인터형은 반환형과 매개변수의 선언 형태를 기준으로 구분한다.   
5. 함수 포인터형 변수 선언 방법 또한 반환형 정보와 매개변수의 선언 정보를 모두 표현해서 만든다.   
```
ex)
    int SoSimpleFunc(int year, int month) {}
    int (*fptr) (int, int) = SoSimpleFunc;
    fptr(12, 31);  // SoSimpleFunc(12, 31)과 같은 표현
    // fptr과 SoSimpleFunc의 차이는 상수냐 변수냐의 차이이다.
```
6. 함수의 매개변수로 함수의 포인터형을 선언하여 함수를 받아와 내부에서 실행이 가능하다. 함수의 매개변수로 함수포인터를 사용하면, 함수의 동작방식에 유연성을 제공할 수 있다.    

## void 포인터
1. void 포인터는 포인터형이 존재하지 않음으로 어떠한 변수의 주소값이든 담을 수 있다. 하다 못해 함수의 주소값도 담을 수 있다.   
2. 주소값이라면 무엇이든 담을 수 있는 만능 그릇이지만, 포인터형이 없기 때문에 포인터연산, 값의 변경, 값의 참조 등이 불가능하다.   
3. 일단 주소값에만 의미를 두고, 포인터형은 나중에 정할 때 사용한다. 후에 메모리 동적할당과 연관이 있다.   
```
ex)
    int SoSimpleAdder(int n1, int n2) {}
    int main(void) {
      int num = 20;
      void* ptr;
      ptr = &num;  // int형 포인터도 담고
      ptr = SoSimpleAdder; // 함수 포인터도 담는다
    }
```