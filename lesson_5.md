# 5강

## 목차
- 함수
- 변수의 종류와 범위
- 제귀함수

## 함수

첫시간에 C언어는 함수 중심 프로그래밍(procedure-oriented-programming)(절차지향 프로그래밍 아님) 이라고 했습니다. 매번 사용한 main 함수도 함수이고 printf, scanf도 함수입니다. 이렇듯 C언어 프로그램의 동작은 함수 위주로 돌아가는 것을 알 수 있습니다. 이번에는 우리가 필요한 동작을 함수로 만들어 볼 겁니다

### 함수의 선언, 정의

함수는 반환형식, 함수이름, 매개변수(또는 인자) 3가지를 통해 선언합니다.  

함수의 반환이란 함수의 내용을 실행하고 함수를 실행한 곳으로 값을 주는 것을 말합니다.  

```
반환형식 함수이름(인자, 인자...);
```
선언할 때는 인자의 타입만 적어주면 됩니다.

함수를 정의하는 방법은 중괄호를 통해 함수의 내용을 만들어 주면 됩니다.  
```
반환형식 함수이름(인자, 인자...)
{
    코드
}
```
정의할 때는 인자의 이름도 적어줘야 합니다.

예를 들어 다음과 같이 선언, 정의 할 수 있습니다.
```c
int sum(int, int);
int sum(int a, int b);
int sum(int a, int b)
{
    return a+b;
}
```
return 명령어를 통해 반환을 할 수 있습니다.

```c
#include<stdio.h>

int sum(int a, int b)
{
    return a+b;
}

int main()
{
    printf("%d", sum(1,3));
}
```
이렇게 사용할 수 있습니다.  

함수를 바로 정의해서 쓰면 되지 왜 선언을 하냐 하면 컴파일러의 컴파일 순서 때문인 것도 있고 한눈에 함수를 보기 쉽기 때문입니다.

```c
#include<stdio.h>

int main()
{
    printf("%d", sum(1,3));
}

int sum(int a, int b)
{
    return a+b;
}
```
컴파일러는 코드를 위에서 아래로 컴파일을 합니다. 컴파일러가 main의 sum을 처음 만날 때는 sum이라는 것이 선언, 정의가 되지 않은 상태라서 sum이 무엇인지 알수가 없습니다. 따라서 컴파일 에러를 냅니다. 따라서 sum함수를 위에 정의하던지 선언을 위에 한번 해주는 방식으로 해결할 수 있습니다.  
```c
#include<stdio.h>

int sum(int, int);

int main()
{
    printf("%d", sum(1,3));
}

int sum(int a, int b)
{
    return a+b;
}
```
이렇게 선언을 먼저 해놓으면 sum을 어디에 정의하든 컴파일러가 잘 해석할 수 있습니다.  
왜 굳이 이렇게 선언과 정의를 따로 나누는 방식을 사용해야 하는가 궁금하실 수 있습니다.  
함수를 한두개만 만들었다면 이런식으로 코드를 짜지 않아도 됩니다. 하지만 함수가 아주 많아지고 함수끼리 서로 호출하는 상황이 오면 a를 b보다 먼저 정의하고 c는 b보다 먼저 정의하고 등등 구조가 헷갈리고 불안정해지게 됩니다. 따라서 프로그램의 규모가 커졌을 때 함수의 선언을 한번에 쭉 해놓고 정의를 따로 적어놓는 것이 C언어 프로그램의 기본 코딩 스타일입니다.  

```c
#include <stdio.h>

void a();
void b();
void c();

int main()
{
	a();
}

void a()
{
	b();
}

void b()
{
	c();
}

void c()
{
	a();
}
```

### 함수의 여러 형태

함수는 반환값과 인자가 없어도 됩니다. 함수의 반환값이 없을 때는 반환 형식을 void라 하고 인자가 없을 때는 void로 넣어도 되고 아무 것도 안써도 됩니다.  
```c
int sum(int a, int b);
int getValue();
void setValue(int a);
void printLogo();
```
함수의 형태는 사용자의 용도에 따라 선택하면 됩니다.

### 함수의 목적

함수는 첫번째로 코드의 재사용을 위해 만듭니다. 수를 뒤집어주는 알고리즘을 기억하나요. 이 알고리즘은 필요한 변수가 많아 여러번 사용하면 코드가 지저분해 집니다. 따라서 이 코드를 함수로 빼면 구조가 굉장히 단순해집니다. 수 뒤집기 문제를 푸는 코드를 통해 보여드리겠습니다.  
```c
#include<stdio.h>
int main()
{
    int t;
    scanf("%d", &t);
    while (t--)
    {
        int n;
        scanf("%d", &n);

        int rev_n = 0;
        int temp = n;
        while (temp > 0)
        {
            rev_n *= 10;
            rev_n += temp % 10;
            temp /= 10;
        }

        int sum = n + rev_n;

        int rev_sum = 0;
        temp = sum;
        while (temp > 0)
        {
            rev_sum *= 10;
            rev_sum += temp % 10;
            temp /= 10;
        }

        if (sum == rev_sum) printf("YES\n");
        else printf("NO\n");
    }
}
```

함수 활용
```c
#include <stdio.h>
int rev(int n)
{
    int res = 0;
    while (n > 0)
    {
        res = res * 10 + n % 10;
        n /= 10;
    }
    return res;
}

int main()
{
    int t;
    scanf("%d", &t);
    while (t--)
    {
        int n;
        scanf("%d", &n);
        int sum = n + rev(n);
        printf("%s\n", sum == rev(sum) ? "YES" : "NO");
    }
}
```
함수의 재사용성의 중요성이 돋보이는 코드입니다.  

함수를 사용하는 두번 째 이유는 제가 좀 느끼는 것인데, 프로그램의 동작을 주요 동작에 의해 함수로 나누어서 각각의 함수의 동작이 독립적이게 되면, 코딩을 할 때 신경써야 할 요소들이 각각의 함수에 분산되기 때문에 함수를 사용합니다.  
함수 공간에서 변수를 선언하고 인자를 받아 코드를 실행하고 값을 반환한 뒤 함수를 종료하면 함수의 변수들도 모두 소멸됩니다. 함수는 제 할 일을 하고 값을 반환한 뒤에 깔끔하게 모든 것이 소멸됩니다.  
이는 위 코드에서도 느낄 수 있습니다. main함수 입장에서는 수 뒤집기에 관한 코드를 신경쓸 필요가 없이 rev()함수를 잘 호출하고 값만 받으면 되고 rev()함수는 수를 뒤집는 알고리즘만 잘 작동하도록 신경쓰면 됩니다.  

rev 함수를 생성함으로써 코드를 재사용하여 변수의 개수도 줄어들고 코드가 단순해집니다. 또한 코딩을 할 때 한번에 신경써야 할 것들이 분산돼서 코딩이 수월해집니다.  

### 함수를 만들 때 주의할 점

함수는 기본적으로 하나의 목적에 맞는 동작만 해야 합니다. 더하기를 해주는 함수 sum()을 만들었는데 이 함수가 더한 값을 출력까지 해준다고 생각해봅시다.  
```c
int sum(int a, int b)
{
    printf("%d + %d = %d\n", a, b, a+b);
    return a+b;
}
```
당시에 필요에 의해서 이런 식으로 함수를 짰을 수도 있지만 이런식으로 함수의 본 목적에 맞지 않는 명령이 섞이면 함수의 재사용성이 급격히 떨어집니다.  
더한 값만 얻어야 할 때 이 함수를 쓸 수 없고 출력하는 형식이 언제든 바뀔 수 있기 때문에 더한 값을 반환한다는 목적에 맞는 동작만 해야 합니다.  

```c
int sum(int a ,int b)
{
    return a+b;
}

int main()
{
    printf("%d + %d = %d\n", a, b, sum(a, b));
}
```
이런식으로 함수는 목적에 맞는 동작만 하는 것이 재활용을 하거나 프로그램을 작성할때도 좋습니다.  

### 기타 예제

- 수 회전
```c
int rotate(int n)
{
	int size = 1;
	while (size*10 <= n)
	{
		size *= 10;
	}
	return n % size * 10 + n / size;
}

int main() 
{
	printf("%d", rotate(1234)); //2341
}
```

## 변수의 종류와 범위

변수들은 선언되는 위치나 종류에 따라 변수의 유효 범위와 생존 시간이 다릅니다. 변수의 종류에는 지역변수, 정연변수, 정적변수, 외부변수, 레지스터 변수 등이 있습니다. 이중 주로 사용하는 전역 변수와 지역 변수를 살펴보도록 하겠습니다.  

### 지역 변수

지역 변수는 중괄호{} 내부에서 선언된 변수와 함수의 매개변수를 의미합니다. 중괄호는 하나의 블록을 만듭니다.  
```c
#include <stdio.h>
int sum(int a, int b)
{
    return a+b;
}

int main()
{
    for(int i=1;i<5;i++)
    {
        printf("%d + %d = %d", i, i+1, sum(i, i+1));
    }
}
```
이 코드에서 사용한 모든 변수는 지역변수입니다. for내부에서 선언한 i는 for문이 종료되면 소멸됩니다. 함수의 매개변수 a, b는 함수가 종료되면 소멸됩니다.
중괄호{} 내부에서 선언한 변수는 중괄호 밖에서는 사용할 수 없습니다.

```c
#include <stdio.h>

int main()
{
	{
		int a = 1;
	}
	printf("%d", a); //에러
}
```

```c
#include <stdio.h>

int main() 
{
	//int sum = 0;

	for (int i = 0; i < 5; i++)
	{
		int sum = 0;
		sum += i;
	}

	printf("%d", sum);
}
```
위 코드에서 오류를 찾아보세요.  
for문 내부에서 선언된 sum을 for문 밖에서 사용하려고 하니 printf에서 에러가 날것입니다. for문 내부 sum을 지우고 main내부의 sum의 주석을 지우면 10이 출력될 것입니다.  
만약 변수 이름이 겹치면 어떻게 될까요. main의 sum과 for문의 sum이 둘다 있으면 더 내부에 있는 변수가 우선시 됩니다. 따라서 for문 내부의 sum만 값이 변동되고 main의 sum은 그대로 0인 상태가 됩니다. 따라서 0이 출력될 것입니다.  

### 함수의 매개변수

함수를 호출하고 매개변수를 넘길때, 메모리 상에 함수를 위한 새로운 공간을 만듭니다. 그리고 매개 변수로 넘겨준 값을 복사해서 함수의 공간에 집어넣습니다. 그리고 해당 공간에서만 작업하게 되고 매개변수로 받은 값을 아무리 변경시켜도 원래의 값은 변하지 않습니다.  
```c
#include <stdio.h>

void f(int a, int b)
{
	a = 3, b = 4;
}

int main() 
{
	int a = 1, b = 2;
	f(a, b);
	printf("a=%d, b=%d", a, b); //a=1 b=2
}
```

### 전역 변수

전역 변수는 어떤 함수 내부에도 포함되지 않는 변수입니다. 따라서 모든 함수에서 사용될 수 있습니다. 선언은 다음과 같이 모든 함수 위에서 사용해야 합니다.  
주의할 점은 전역변수는 특별히 초기화하지 않아도 0으로 초기화되어 있습니다.  
```c
#include <stdio.h>

int ans;

void solve(int n)
{
	while (n > 0)
	{
		ans += n % 10;
		n /= 10;
	}
}

int main() 
{
	solve(12345);
	printf("답 = %d", ans); //15
}
```

## 재귀함수

재귀함수는 자기 자신을 호출하는 함수를 말합니다.  
재귀합수가 자기 자신을 계속해서 호출하면 무한 루프에 빠지기 때문에 재귀함수를 종료시킬 조건문이 필요합니다. 이러한 조건을 재귀함수의 기저사례라고 합니다.  
재귀함수는 구조가 복잡해지기 때문에 재귀함수의 구조를 분석할 때는 기저사례를 생각하는 것이 좋습니다.  
재귀함수를 사용하는 이유는 실생활의 문제에 재귀적인 구조를 가진것이 많기 때문입니다. 재귀적인 구조란 문제를 쪼개어도 비슷한 구조를 가지는 것을 말합니다.
몇가지 예제를 봅시다.  

- n번 출력
    - 매개변수로 받은 n을 출력합니다. 그리고 n-1을 자기 자신에게 넘겨서 다시 호출합니다.
    - n이 0이되면 종료됩니다.
```c
#include <stdio.h>

void f(int n)
{
	if (n == 0) return;
	printf("%d\n", n);
	f(n - 1);
}

int main() 
{
	int n;
	scanf("%d", &n);
	f(n);
}
```
- 별찍기 1
    - cnt는 count로 재귀함수가 몇번 호출되었는지 알려줍니다.
    - cnt만큼 별을 찍고 cnt가 n보다 크면 재귀함수를 종료합니다.
```c
#include <stdio.h>

void star(int n, int cnt)
{
	if (n < cnt) return;
	for (int i = 0; i < cnt; i++)
		printf("*");
	printf("\n");
	star(n, cnt + 1);
}

int main()
{
	int n;
	scanf("%d", &n);
	star(n, 1);
}
```
- 팩토리얼
    - 함수의 반환값은 함수를 호출한 곳으로 반환됩니다.
    - n! = n*(n-1)! / 0! = 1 을 이용해 재귀적으로 계산합니다.
    - 반환값을 재사용하는 이러한 구조는 기저사례를 생각하고 거꾸로 올라가는 것이 좋습니다. n=0일 때 1을 반환합니다. 반환한 곳에서 n=1이고 1x1을 반환합니다. 반환한 곳에서 n=2이고 2x1을 반환합니다. 반환한 곳에서 n=3일것이고 3x2를 반환합니다. 이렇게 계속 거슬러 올라가면 n!이 완성됩니다.
    - 이처럼 점화식으로 나타낼 수 있는 문제는 재귀적으로 풀 수 있습니다.
```c
#include <stdio.h>

int fac(int n)
{
	if (n == 0) return 1;
	return n * fac(n - 1);
}

int main() 
{
	int n;
	scanf("%d", &n);
	printf("%d", fac(n));
}
```
- 피보나치 수열
    - 피보나치 수열은 앞의 두 수를 더한 수열입니다.
    - 0, 1, 1, 2, 3, 5, 8, 13 ...
    - f(n) = f(n-1) + f(n-2) / f(0)=0, f(1)=1을 이용해 재귀적으로 계산합니다.
    - 한번에 두번 자기자신을 호출하는 구조입니다.
```c
#include <stdio.h>

int fibo(int n)
{
	if (n <= 1) return n;
	return fibo(n - 1) + fibo(n - 2);
}

int main() 
{
	int n;
	scanf("%d", &n);
	printf("%d", fibo(n));
}
```
- 이항계수
    - 수능대비로 열심히 외웠던 이항계수의 공식을 여기서 사용합니다. nCr = n-1Cr-1 + n-1Cr / nCn =1, nC0 =1 임을 이용하여 재귀적으로 계산합니다.
```c
#include <stdio.h>

long long int C(int n, int r)
{
	if (n == r || r == 0) return 1;
	return C(n - 1, r - 1) + C(n - 1, r);
}

int main() 
{
	int n, r;
	scanf("%d%d", &n, &r);
	printf("%lld", C(n, r));
}
```
- n개 고르기
    - 앞서 중첩 반복문으로 풀었던 n개 고르기는 몇개를 고를지에 따라 코드의 구조가 심하게 변했습니다.
    - 재귀적으로 코드를 짜면 일정한 구조로 코드를 짤 수 있고 문제에 맞춰 코드를 변형하기도 쉽습니다.
```c
#include <stdio.h>

void pick(int size, int arr[], int pos, int picked[], int pickedNum, int toPick)
{
	if (pickedNum == toPick)
	{
		for (int i = 0; i < toPick; i++)
			printf("%d ", picked[i]);
		printf("\n");
		return;
	}
	for (int i = pos; i < size; i++)
	{
		picked[pickedNum] = arr[i];
		pick(size, arr, i + 1, picked, pickedNum + 1, toPick);
	}
}

int main()
{
	int arr[8] = { 1,2,3,4,5,6,7,8};
	int picked[3];
	pick(sizeof(arr) / sizeof(int), arr, 0, picked, 0, 3);
}
```

```c
#include <stdio.h>

int size = 8, arr[8] = { 1,2,3,4,5,6,7,8 }, picked[3], toPick = 3;

void pick(int pos, int pickedNum)
{
	if (pickedNum == toPick)
	{
		for (int i = 0; i < toPick; i++)
			printf("%d ", picked[i]);
		printf("\n");
		return;
	}
	for (int i = pos; i < size; i++)
	{
		picked[pickedNum] = arr[i];
		pick(i + 1, pickedNum + 1);
	}
}

int main()
{
	pick(0, 0);
}
```
이렇게 매개변수 일부를 전역변수로 빼서 사용 할 수도 있습니다.  

### 재귀함수의 시간복잡도

재귀함수의 시간복잡도는 자기 자신을 몇번 호출하느냐에 따라 달렸습니다. 물론 여러 조건문이 섞이게 되면 약간 달라집니다.  
하지만 반복문을 쓰는 것과 함수를 호출하는 것에는 약간의 시간의 차이가 있습니다. 함수를 호출하는 쪽이 약간 시간이 더 느립니다. 따라서 재귀함수가 함수를 n번 호출하여 연산을 하는 것과 반복문으로 n번 연산하는 것에는 약간의 차이가 있습니다.  

위 코드중 팩토리얼 같은 코드는 n번 자기자신을 호출할 테니 O(n)의 시간복잡도를 가집니다. 

피보나치 같은 경우 한번에 2번씩 자기자신을 호출할테니 호출하는 횟수가 n에 따라 대략 2^n번 늘어납니다. (실제 연산량은 2^(n-2)-1) 따라서 피보나치 수열을 재귀함수로 구하면 O(2^n)의 시간복잡도를 가집니다.  
O(2^n)은 끔찍한 시간복잡도 입니다. n=50만 되어도 1125899906842624번 연산을 해야 합니다. 차라리 반복문을 통해 다음과 같이 푸는 것이 좋습니다.
```c
#include <stdio.h>

int main()
{
	int arr[100] = { 0,1 };
	int n;
	scanf("%d", &n);

	for (int i = 2; i <= n; i++) arr[i] = arr[i - 1] + arr[i - 2];
	printf("%d", arr[n]);
}
```
이 코드의 시간복잡도는 O(n)이고 n=50일때 50번만 연산하면 됩니다.

### 재귀함수의 문제점

함수를 호출하면 그 함수를 위한 공간이 새로 만들어진다고 했습니다. 따라서 재귀함수를 통해 함수를 너무 많이 호출하게 되면 메모리 공간이 꽉차 스택 오버플로우라는 에러가 날 수 있습니다. (스택은 메모리상의 공간의 이름이고 이곳에 함수의 공간이 만들어 집니다.)  
그리고 재귀함수는 불필요하게 연산의 횟수가 많아질 수 있습니다. (이를 해결하기 위해 동적 계획법과 가지치기라는 알고리즘이 있습니다.)

### 유클리드 호제법

유클리드 호제법은 두 수의 최대공약수를 구하는 알고리즘입니다. 우리가 기존에 사용하던 알고리즘은 O(n)의 시간복잡도가 걸렸지만 이 알고리즘은 O(logn)만에 최대공약수를 구할 수 있습니다.  
그 말은 n이 2^50=1125899906842624이어도 50번만의 연산에 최대공약수를 구할 수 있다는 뜻입니다.  
저는 이 알고리즘을 주로 재귀함수를 이용해 구현합니다. 3줄만 외우면 빠르고 간단하게 최대공약수를 구할 수 있습니다.  
```c
#include <stdio.h>

int gcd(int a, int b)
{
	if (b == 0) return a;
	return gcd(b, a % b);
}

int main()
{
	int a, b;
	scanf("%d%d", &a, &b);
	printf("%d", gcd(a, b));
}
```
유클리드 호제법에 대한 자세한 원리가 궁금하다면 검색하시면 됩니다. (저도 잘 모릅니다..)