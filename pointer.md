## 배열과 포인터 
* 배열을 배열이고 포인터는 포인터이지만, sizeof 와 주소값 연산자와 함께 사용할 때를 제외하면, 배열의 이름은 첫 번째 원소를 가리킨다.
* arr[i] 와 같은 문장은 사실 컴파일러에 의해 *(arr + i) 로 변환된다.

## 배열의 포인터 
```cpp
#include <stdio.h>

int main() {
  int arr[3] = {1, 2, 3};
  int (*parr)[3] = &arr;

  printf("arr[1] : %d \n", arr[1]);
  printf("parr[1] : %d \n", (*parr)[1]);
}
```
* 배열의 이름은 첫 번째 원소를 가리키는 암묵적 변환은 주소값 연산자가 왔을 때에는 이루어지지 않기 때문에, &arr 은 int 형 크기가 3인 주소값을 가르킨다. 
* arr 이 크기가 3 인 배열 이기 때문에, &arr 을 보관할 포인터는 크기가 3 인 배열을 가리키는 포인터가 되어야 한다. 
* int * parr[3] 은 int * 형 3개인 배열을 가르키기 때문에 괄호를 붙이지 않으면 안된다. 
* int (*parr)[3] = int [3] (*parr) 로 생각하면 int 형 크기가 3인 배열의 주소를 가르키는 포인터가 된다.   

## 2차원 배열의 주소값 
```cpp 
#include <stdio.h>

int main() {
  int arr[2][3];

  printf("arr[0] : %p \n", arr[0]);
  printf("&arr[0][0] : %p \n", &arr[0][0]);

  printf("arr[1] : %p \n", arr[1]);
  printf("&arr[1][0] : %p \n", &arr[1][0]);

  return 0;
}
```
* arr[0] 도 마찬가지로 배열의 이름 처럼 sizeof 연산자나 &연산자와 같이 쓰이지 않는다면 암묵적으로 arr[0][0] 의 주소값을 가르킨다. (arr[0] == &arr[0][0], arr[1] == &arr[1][0])

## 포인터 배열 
```cpp
#include <stdio.h>
int main() {
  int *arr[3];
  int a = 1, b = 2, c = 3;
  arr[0] = &a;
  arr[1] = &b;
  arr[2] = &c;

  printf("a : %d, *arr[0] : %d \n", a, *arr[0]);
  printf("b : %d, *arr[1] : %d \n", b, *arr[1]);
  printf("b : %d, *arr[2] : %d \n", c, *arr[2]);

  printf("&a : %p, arr[0] : %p \n", &a, arr[0]);
  return 0;
}
```
