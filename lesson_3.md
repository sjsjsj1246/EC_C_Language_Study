# 3강



## 목차

* 반복문 활용예제
* 중첩 반복문
* 1차원 배열
* 문자열 처리

## 반복문 활용 예제

### do~while 입력값 검사

```c
int main()
{
	int n;
	do
	{
		printf("1 과 10 사이의 정수를 입력해 주세요 : ");
		scanf("%d", &n);
	} while (n <= 0 || n>10);

	printf("%d", n);
}
```
하지만 이렇게쓰는게 더 좋습니다.  
```c
#include <stdio.h>

int main()
{
	int n;
	while (1)
	{
		printf("1 과 10 사이의 정수를 입력해 주세요 : ");
		scanf("%d", &n);
		if (n > 0 && n <= 10) break;
		else printf("범위 오류!\n");
	}

	printf("%d", n);
}
```

### while문 활용

#### 수 뒤집기

```c
#include <stdio.h>

int main()
{
	int n;
	scanf("%d", &n);
	
	int rev = 0;
	while (n > 0)
	{
		rev *= 10;
		rev += n % 10;
		n /= 10;
	}
	printf("%d", rev);
}
```

#### 십진수 이진수로 바꾸기
```c
#include <stdio.h>

int main()
{
	int n;
	scanf("%d", &n);
	
	int bi = 0;
	while (n > 0)
	{
		bi *= 10;
		bi += n % 2;
		n /= 2;
	}

	// 이진수가 거꾸로 저장되기 때문에 뒤집어줘야 한다.
	int rev = 0;
	while (bi > 0)
	{
		rev *= 10;
		rev += bi % 10;
		bi /= 10;
	}

	printf("%d", rev);
}
```

### for문 활용

```c
	for (char c = 'a'; c <= 'z'; c++);
    for (int i = 1; i < n; i *= 2)
```

#### 소수 판별 알고리즘
```c
#include <stdio.h>

int main()
{
	int n, check = 1;
	scanf("%d", &n);
	for (int i = 2; i < n; i++)
	{
		if (n%i == 0)
		{
			check = 0;
			break;
		}
	}
	if (n <= 1) check = 0;
	if (check) printf("소수입니다.");
	else printf("소수가 아닙니다.");
}
```

#### 최대공약수 알고리즘
```c
#include <stdio.h>

int main()
{
	int a, b;
	scanf("%d%d", &a, &b);
	int c = (a > b ? b : a);
	int gcd;
	for (int i = c; i > 0; i--)
	{
		if (a%i == 0 && b%i == 0)
		{
			gcd = i;
			break;
		}
	}
	printf("%d", gcd);
}
```

## 중첩 반복문

반복문 내부에 반복문을 사용하는 구조입니다.   

### 중첩 반복문의 구조  
```c
#include <stdio.h>

int main()
{
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			printf("i = %d  j = %d\n", i, j);
		}
	}
}
```

```c
#include <stdio.h>

int main()
{
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j <= i; j++)
		{
			printf("*");
		}
		printf("\n");
	}
}
```
사실 그렇게 새로울 것은 없고 예제를 보며 여러번 사용하면서 구조를 익히는 것이 가장 좋습니다.  

### 정렬 알고리즘(버블 소트)  
```c
#include <stdio.h>

int main()
{
	int arr[5] = { 3,2,1,4,5 };

	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 5 - i - 1; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}

	for (int i = 0; i < 5; i++) printf("%d ", arr[i]);
}
```

### for문과 배열
```c
#include <stdio.h>

int main()
{
	int arr[5];
	for (int i = 0; i < 5; i++)
		scanf("%d", &arr[i]);
	for (int i = 0; i < 5; i++)
		printf("%d ", arr[i]);
}
```

변수를 사용할 때와 마찬가지로 배열에는 원하는 값을 저장하면 되고 다른 점은 그 값을 인덱싱할 수 있다는 점이 좋습니다.  



## 1차원 배열

배열은 값을 연속적으로 저장하는 공간을 말합니다.  
자료형 배열의 이름[배열의 크기] 로 선언합니다.  
배열의 크기에는 항상 상수가 들어가야 합니다.  
배열을 선언할 때 메모리 상에 연속적으로 공간을 할당합니다.  
배열의 이름은 그 자체로 주소를 나타냅니다. 이는 메모리상의 배열의 시작 주소와 같습니다.  
배열의 값을 얻을 때 연속적으로 인덱싱을 할 수 있다는 것이 굉장히 중요한 속성입니다.  
이러한 연속적인 성질 때문에 배열은 99% for문과 함께 사용합니다. for문은 반복과 인덱싱을 하기에 편하기 때문입니다.

이러한 성질을 활용하는 것 역시 실습을 통해 익혀가는 것이 가장 빠릅니다.  


### 배열의 입력과 출력

```c
#include <stdio.h>

int main()
{
	int arr[5];
	for (int i = 0; i < 5; i++)
		scanf("%d", &arr[i]);
	for (int i = 0; i < 5; i++)
		printf("%d ", arr[i]);
}
```

### 두 배열이 같은지 체크

```c
#include <stdio.h>

int main()
{
	int check = 1;
	int a[] = { 1,2,3,4,5 };
	int b[] = { 2,3,4,1,2 };

	for (int i = 0; i < 5; i++)
	{
		if (a[i] != b[i])
		{
			check = 0;
			break;
		}
	}
	if (check) printf("같다");
	else printf("다르다");
}
```

### 배열이 오름차순인지 체크

```c
#include <stdio.h>

int main()
{
	int arr[5] = { 1,2,3,4,5 };

	int check = 1;
	for (int i = 0; i < 4; i++)
		if (arr[i] > arr[i + 1])
			check = 0;

	if (check) printf("오름차순");
	else printf("오름차순 아님");
}
```

## 문자열 처리

우리는 실생활에서 문자열을 굉장히 많이 사용합니다.  
배열의 자료형을 char로 선언함으로써 문자열을 만들 수 있습니다.  
배열과 똑같이 사용할 수 있지만 문자열을 다룰 때 배열보다 편합니다.  
조금 특이한 것은 문자열의 마지막에는 무조건 \0(널) 값이 들어가야 한다는 것입니다.  
따라서 arr[5] 는 4글자의 문자열만 입력받을 수 있습니다.  

### 문자열의 입력

문자열은 보통 %s 라는 서식문자로 입력받습니다.
```c
char s[100];
scanf("%s",s);
```

하지만 입력 중간에 공백이 있으면 한번에 받지 못합니다. 그럴때는 다음과 같이 입력받으면 됩니다.  

한 줄 입력받기 (공백 포함)
```c
#include <stdio.h>

int main()
{
	char s[100];
	scanf("%[^\n]", s);
	printf("%s", s);
}
```

### 문자열의 출력

출력 역시 %s 서식문자로 출력합니다. 특이한 것은 문자열의 시작 주소부터 \0을 만날 때 까지 출력합니다.  
```c
#include <stdio.h>

int main()
{
	char s[10] = "";
	scanf("%s", s);
	printf("%s", s + 1);
    //s[1] 부터 끝까지 출력
}
```
