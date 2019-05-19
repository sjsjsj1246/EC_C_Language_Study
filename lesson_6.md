# 6강

## 목차
- 포인터
- 동적 할당

## 포인터

포인터를 알아보기 앞서 프로그램을 실행할 때 메모리의 구조가 어떠한지 알아야 합니다.

### 메모리

C언어 프로그램이 실행되면 프로그램은 컴퓨터의 메모리에 적재됩니다. 그리고 메모리 공간을 할당받습니다.  
메모리는 code, data, stack, heap 영역으로 구분됩니다.  
code 영역에는 프로그램의 코드가 들어가있습니다. 물론 컴퓨터가 알아들을 수 있는 기계어가 들어가 있습니다.  
data 영역에는 프로그램의 전역변수들이 들어가 있습니다.  
stack 영역에는 프로그램의 지역변수가 들어가고 프로그램이 실행되는 도중 생성, 소멸을 반복합니다.  
heap 영역에는 프로그램 실행도중 동적할당한 변수들이 들어갑니다.  
이러한 메모리 영역에 자료들이 저장되는 것입니다. 메모리는 한칸에 1바이트의 크기를 가집니다. 당연하게도 이러한 메모리 공간에는 주소가 있고 프로그램은 이 주소를 기반으로 변수를 사용하거나 수정할 수 있는 것입니다.  
참고로 주소는 한칸에 1씩 차이가 납니다.  

이 주소를 값으로 가지는 것이 포인터 입니다.  
포인터는 단어 그대로 가리키는 역할을 합니다. 메모리상의 어떤 주소를 가지고 있고 그 주소를 가지고 메모리 상의 값을 가져오거나 수정할 수 있습니다.  

### 포인터 선언

포인터는 다음과 같이 선언합니다.
```c
자료형* 변수명;
int* p = NULL;
자료형 *변수명1, *변수명2; // 여러개일 때
```
포인터는 NULL이라는 값으로 초기화해줄 수 있습니다. 값이 NULL인 포인터를 널 포인터라고 부릅니다.(사실 NULL=0 입니다.)  

### 포인터 연산자

변수 앖에 &를 붙이면 변수의 주소를 얻을 수 있습니다.  
주소 앞에 *를 붙이면 주소가 가리키는 값을 얻을 수 있습니다.  

```c
#include <stdio.h>

int main()
{
	int a = 1;
	int* p = &a;

	printf("a=%d *p=%d\n", a, *p);
	*p = 2;
	printf("a=%d *p=%d\n", a, *p);
}
```
이런식으로 주소를 가지고 값을 변경할 수 있습니다. 하지만 이런식으로 코딩을 하진 않습니다. 별 의미가 없지요.  
C언어는 함수 중심 프로그래밍 언어입니다. 저는 포인터의 사용 이유가 함수간의 정보의 전달을 용이하게 하기 위해서 라고 생각합니다.  

```c
#include <stdio.h>

void f(int a)
{
	a = 5;
}

int main()
{
	int a = 1;
	printf("a = %d\n", a); // 1
	f(a);
	printf("a = %d\n", a); // 1
}
```

```c
#include <stdio.h>

void f(int *a)
{
	*a = 5;
}

int main()
{
	int a = 1;
	printf("a = %d\n", a); // 1
	f(&a);
	printf("a = %d\n", a); // 5
}
```

```c
#include <stdio.h>

void swap(int* a, int* b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}

int main()
{
	int a = 1, b = 4;
	printf("a = %d, b = %d\n", a, b);
	swap(&a, &b);
	printf("a = %d, b = %d\n", a, b);
}
```
함수를 호출하면 다른 함수 내부에 있는 값을 가져올 수 있는 방법이 없습니다. 하지만 함수에 주소를 넘겨주면 함수는 주소를 가지고 다른 함수에 있는 정보를 가져올 수 있고 반대로 다른 함수에 자신이 가지고 있는 정보를 주소로 넘겨줄 수도 있습니다.  

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
}
```
이제 scanf에 왜 변수의 주소를 넘겨주는 지 알겠습니까? scanf는 사용자의 입력을 받아들인 후 매개변수로 받은 a의 주소를 통해 main함수 내부에 있는 a에 값을 저장할 수 있었던 것입니다.

### 배열과 포인터

배열의 이름은 사실 포인터입니다.  
배열을 선언하면 메모리 상에 연속적으로 저장됩니다.  
```c
#include <stdio.h>

int main()
{
	int arr[5] = { 1,2,3,4,5 };
	for (int i = 0; i < 5; i++)
	{
		printf("%p ", &arr[i]); // 00AFF754 00AFF758 00AFF75C 00AFF760 00AFF764
	}
    printf("\n&arr[0] = %p\narr = %p", &arr[0], arr);
    // &arr[0] = 00AFF754
    // arr = 00AFF754
}
```
(주소값은 16진수이기 때문에 %x를 사용하기도 합니다)  
각 배열 원소의 주소를 보니 4byte씩 차이가 나는것을 알 수 있습니다. int 하나가 4byte이기 때문입니다.  
잘보니 arr[0] 처음 원소의 주소 즉 배열의 시작 주소와 arr의 값이 같은것을 알 수 있습니다.  
arr 자체가 배열의 시작 주소값을 가지고 있는 것입니다.

```c
#include <stdio.h>

int main()
{
	int arr[5] = { 1,2,3,4,5 };

	int* p = arr;
	for (int i = 0; i < 5; i++)
	{
		printf("%d ", *(p + i)); // 1 2 3 4 5
	}
}
```
즉 arr[i] = *(p + i) 입니다.
여기서 포인터의 자료형이 존재하는 이유를 알 수 있습니다. p = 0이라 가정했을 때 p+1은 무엇일까요?  
포인터의 증감연산의 결과는 포인터의 자료형에 달렸습니다. 위의 경우 p의 자료형이 int*이기 때문에 p+1을 하면 주소는 4만큼 증가하여 p+1 = 4가 됩니다. 이는 배열의 참조를 원활히 하기 위함이라고 생각합니다.  
배열의 이름이 주소이기 때문에 함수의 매개변수로 넘겨줄때 조심해야 합니다.  

```c
#include <stdio.h>

void swap(int *a, int *b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}

//void reverse(int arr[], int len)
void reverse(int* arr, int len)
{
	for (int i = 0; i < len / 2; i++)
	{
		swap(&arr[i], &arr[len - i - 1]);
	}
}

int main()
{
	int arr[5] = { 1,2,3,4,5 };
	for (int i = 0; i < 5; i++)
	{
		printf("%d ", *(arr + i));
	}
	printf("\n");
	reverse(arr, 5); // arr을 집어넣음, 즉 주소를 넘겨줌
	for (int i = 0; i < 5; i++)
	{
		printf("%d ", *(arr + i));
	}
}
```
reverse를 호출하는 모습을 보면 arr을 넣어줍니다. 즉 주소를 넘겨주는 것입니다.  
reverse()에서 첫 번째 매개변수로 배열의 주소를 받습니다. 이 주소값을 통해 배열을 수정합니다.  
5라는 값을 넣어주는것과 달리 주소를 넣어줬기 때문에 원본 배열이 수정됩니다.  
따라서 함수에 배열을 넘겨줄 때는 조심해야 합니다.  

```c
#include <stdio.h>

int main()
{
	char s[100] = "";
	scanf("%s", s);
}
```
문자열을 %s로 입력받을 때 왜 &를 안써도 되는지 이해가 가십니까?  

### 포인터 배열

포인터를 원소로 가지는 배열을 만들 수 있습니다.
```c
#include <stdio.h>

int main()
{
	int a = 10, b = 20, c = 30;
	int* arr[3] = { &a, &b, &c }; // int형 포인터 배열 선언  

	for (int i = 0; i < 3; i++)
	{
		printf("%d\n", *arr[i]);
	}
}
```

### 이중 포인터와 이차원 배열

이중 포인터는 포인터의 주소를 저장합니다. 포인터도 실제로는 변수이기 때문에 주소가 있지만 포인터의 주소는 이중 포인터에 저장해야 합니다.  

```c
#include <stdio.h>

int main()
{
	int* numPtr1;     // 단일 포인터 선언
	int** numPtr2;    // 이중 포인터 선언
	int num1 = 10;

	numPtr1 = &num1;    // num1의 메모리 주소 저장 
	numPtr2 = &numPtr1; // numPtr1의 메모리 주소 저장

	printf("%d\n", **numPtr2);    // 포인터를 두 번 역참조하여 num1의 메모리 주소에 접근
}
```

1차원 배열을 단일 포인터를 통해 다룰수 있었으니 2차원 배열도 이중 포인터로 다룰 수 있을거라 생각할 수 있습니다. 하지만 이차원 배열의 주소를 포인터에 저장하려면 특별한 방법을 사용해야 합니다.  

```c
자료형 (*포인터이름)[가로크기];
int (*p)[4];
```
다음과 같이 이차원 포인터를 선언할 때 가로 크기를 명시해줘야 합니다.  
이차원 배열도 실제로 메모리상에선 일렬로 저장되어 있습니다. 따라서 프로그램 입장에서는 배열의 주소만 알아서는 배열의 가로 크기를 알 수 없습니다. 따라서 가로 크기를 명시해 주어야 하는 것입니다.  

```c
#include <stdio.h>

int main()
{
	int arr[2][3] =
	{
		{1,2,3},
		{4,5,6}
	};

	int (*p)[3] = arr;

	for (int i = 0; i < 2; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			printf("%d ", *(*(p + i) + j));
		}
		printf("\n");
	}
}
```
arr[i][j] = \*(\*(arr + i) + j) = \*(arr[i]+j) = (\*(arr + i))[j] 입니다.  
여기서 arr[0]은 {1,2,3}의 시작주소를 가리킵니다. arr[2][3]에서 arr[0]은 단일 포인터고 arr은 이중 포인터인 것입니다.  

이중 포인터와 포인터 배열은 잘 구분해야 합니다.
```c
int (*p)[3];
int *p[3];
```
위는 이중 포인터고 아래는 포인터 배열입니다.

### 함수와 포인터

함수의 이름도 주소입니다. 함수는 기계어로 변환돼서 메모리의 code영역에 저장됩니다. 함수의 이름은 code영역에 저장된 함수 코드의 시작 주소를 가리킵니다.  


선언은 다음과 같이 합니다.
```c
반환값자료형 (*함수포인터이름)();
void (*fp)(); // 반환값과 매개변수가 없는 함수 포인터 fp 선언
```

변수 포인터의 값을 가져올 때 *연산자를 사용했다면 함수 주소를 통해 함수를 실행시키기 위해선 ()를 붙이면 됩니다.

```c
#include <stdio.h>

void hello()
{
    printf("Hello, world!\n");
}

void bonjour()
{
    printf("bonjour le monde!\n");
}

int main()
{
    void (*fp)();   // 반환값과 매개변수가 없는 함수 포인터 fp 선언

    fp = hello;     // hello 함수의 메모리 주소를 함수 포인터 fp에 저장
    fp();           // Hello, world!: 함수 포인터로 hello 함수 호출

    fp = bonjour;   // bonjour 함수의 메모리 주소를 함수 포인터 fp에 저장
    fp();           // bonjour le monde!: 함수 포인터로 bonjour 함수 호출

    return 0;
}
```
Hello, world!
bonjour le monde!
가 출력됩니다.  

```
#include <stdio.h>

int add(int a, int b)
{
	return a + b;
}

int sub(int a, int b)
{
	return a - b;
}

int mul(int a, int b)
{
	return a * b;
}

int div(int a, int b)
{
	// TODO : handling divide by zero exception
	return a / b;
}

int main()
{
	int (*cal)(int, int) = NULL;

	int c;
	while (1)
	{
		printf("*사칙연산*\n숫자를 입력하세요\n");
		printf("1:더하기 2:빼기 3:곱하기 4:나누기\n");
		printf("입력 : ");
		scanf("%d", &c);
		if (c >= 1 && c <= 4) break;
		else printf("다시 입력하세요\n\n");
	}
	switch (c)
	{
	case 1:
		cal = add;
		break;
	case 2:
		cal = sub;
		break;
	case 3:
		cal = mul;
		break;
	case 4:
		cal = div;
		break;
	}

	int a, b;
	printf("정수 두개를 입력하세요 : ");
	scanf("%d%d", &a, &b);

	int res = cal(a, b);
	printf("결과는 %d", res);
}
```
간단한 사칙연산 프로그램입니다.  

### 함수 포인터 배열

함수 포인터를 원소로 가지는 배열을 만들 수 있습니다.  
위의 코드에 적용시켜 보겠습니다.  
```c
int main()
{
	int (*cal[4])(int, int) = {add, sub, mul, div};  // 함수 포인터 배열

	int c;
	while (1)
	{
		printf("*사칙연산*\n숫자를 입력하세요\n");
		printf("1:더하기 2:빼기 3:곱하기 4:나누기\n");
		printf("입력 : ");
		scanf("%d", &c);
		if (c >= 1 && c <= 4) break;
		else printf("다시 입력하세요\n\n");
	}

	int a, b;
	printf("정수 두개를 입력하세요 : ");
	scanf("%d%d", &a, &b);

	int res = cal[c](a, b); // 사용
	printf("결과는 %d", res);
}
```

## 동적 할당

data영역과 stack영역에 할당되는 메모리 크기는 컴파일 시에 미리 결정됩니다. 하지만 힙 영역의 크기는 프로그램이 실행되는 도중에 변경될 수 있습니다.  
이렇게 런타임 시에 메모리를 할당받는 것을 메모리의 동적 할당이라고 합니다.  

### malloc()함수

malloc()은 stdlib.h에 있습니다.  
malloc()함수는 프로그램이 실행중일 때 사용자가 직접 힙 영역에 메모리를 할당할 수 있게 해줍니다.  
malloc(크기) 를 하면 heap영역에서 전달받은 크기만큼 메모리를 할당하고 그 메모리의 주소를 반환합니다.  
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
	int n;
	scanf("%d", &n);
	
	int* p;
	p = (int*)malloc(n * sizeof(int));
	
	for (int i = 0; i < n; i++)
	{
		scanf("%d", p + i);
	}
	for (int i = 0; i < n; i++)
	{
		printf("%d ", *(p + i));
	}
}
```
malloc을 쓴 부분을 유심히 봐야 합니다. n을 입력받아서 크기가 n인 배열을 만들고 싶습니다.  
따라서 크기가 n인 배열의 크기는 n*int사이즈 이고 그만큼의 메모리를 할당받아야 합니다.  
malloc이 반환한 값은 할당받은 메모리의 주소입니다. 이때 malloc의 반환타입은 void\*입니다. 즉 타입이 void인 포인터 입니다. 이 포인터는 증감 연산을 할 수 없고 일단 주소를 저장만 할 수 있는 타입입니다. 따라서 이 주소를 형변환 해줘야 합니다. (int*)는 할당받은 주소를 int\*형으로 바꾼 것입니다. p의 자료형이 int*이기 때문에 맞춰준 것입니다.  


### free()함수

heap 영역에 동적할당하여 생성한 변수는 지역변수와 달리 한번 생성하면 직접 삭제시켜주기 전까지는 없어지지 않습니다. 따라서 heap에 잔뜩 생성해놓고 제 때 지워주지 않으면 메모리가 부족해지는 현상이 발생할 수 있습니다. 이를 메모리 누수라고 합니다.  
free(주소)를 하면 해당 공간을 해제할 수 있습니다.  
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
	int n;
	scanf("%d", &n);

	int* p;
	p = (int*)malloc(n * sizeof(int));

	free(p);
}
```
