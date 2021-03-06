# 4강

이번 시간에는 여러분에게 코드의 효율성을 분석하는 방법과 기초적인 알고리즘을 몇개 소개할 것입니다.  
문제의 요구 조건을 파악하고 새로 배운 알고리즘을 적용하면서 문제를 풀고 재미를 느꼈으면 좋겠고, 여러분이 코드를 보는 안목이 늘었으면 좋겠습니다.  

## 목차

* 시공간 복잡도
* 에라토스테네스의 체
* 배열에서 선택하기
* 정렬 알고리즘
* 다차원 배열
* 구간 합

## 시공간 복잡도

컴퓨터 공학에서 프로그램이나 알고리즘의 효율성을 분석할 때는 주로 시간적 측면과 공간적 측면에서 효율성을 분석합니다.  
게임을 예로 들어봅시다. 만약 스킬을 사용해 몬스터를 떄린다고 했을 때 몬스터를 한마리 때렸을 때는 괜찮았는데, 10마리를 동시에 때렸더니 연산량이 많아져서 게임이 1초간 멈췄다고 생각해 봅시다. 순간 순간이 중요한 게임에서 이런 식으로 게임이 자꾸 끊긴다면 치명적인 문제가 됩니다. 따라서 상황에 따라 시간이 얼마나 걸릴지 예측하고 줄이는 것이 중요하고 프로그램의 동작 시간이 얼마나 걸릴지 파악하는 것이 시간복잡도 입니다.  
또한 게임을 실행할 때 램을 8GB를 잡아먹는다고 하면 일부 환경에서는 실행조차 할 수 없을 것입니다. 이렇게 프로그램이 차지할 메모리 공간을 파악하는 것이 공간 복잡도 입니다.  

시공간 복잡도를 잘 이해하면 문제를 보고 시간 제한, 메모리 제한, 입력데이터의 양을 보고 대충 얼마의 시공간 복잡도 내에 풀어야 할 지 파악하는 능력이 생깁니다.  
그리고 코드를 보고 얼마의 시간복잡도를 가질 지를 알고 동작 시간이 얼마나 걸릴 지 파악할 수 있는 능력이 생깁니다.  

### 시간 복잡도

프로그램의 동작 시간이 얼마나 걸릴지는 주로 연산량을 기준으로 판단합니다.  
시간 복잡도는 프로그램에 입력을 주었을 때 연산을 몇번을 하는지를 말합니다.    
즉 시간 복잡도 = 입력의 크기에 따른 연산량 이라고 볼 수 있습니다.  
이를 표기하는 법은 다양한데, 그중 빅-오 표기법을 살펴보도록 하겠습니다.  

#### 빅-오(Big-O) 표기법

빅-오 표기법은 O(n) 이렇게 사용합니다. 이 표기의 뜻은 입력의 크기가 n일 때 연산을 최대 n번 한다는 것입니다.  
빅-오 표기법은 알고리즘이 최악의 경우에 몇번 연산을 할 지를 표시합니다. 연산의 횟수는 주로 반복문이 결정합니다. 이 때 연산이라는 것은 더하기, 빼기 또는 입출력 같은 것을 연산이라고 합니다.  
빅-오 에서는 계수를 제외한 최고차항에만 관심이 있습니다. 직접 몇개의 시간복잡도를 구해봅시다. 


배열을 순회하면서 배열의 합을 구한다고 할 때는 배열의 크기만큼 연산이 일어나겠죠 숫자를 더하는 것이 하나의 연산 입니다.
```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    for(int i=0;i<n;i++) scanf("%d",&arr[i]);

    int sum=0;
    for(int i=0;i<n;i++) sum+=arr[i];
}
```
n을 입력받는 데 1번의 연산, 배열에 n개의 숫자를 입력받는데 n번의 연산 sum에 배열의 원소를 더하는 데 n번 연산 따라서 위 코드의 시간복잡도는, 2n+1의 연산에서 최고차항만 빼내서 O(n)이라고 나타냅니다.  

1억번 연산하는데 대략 1초가 걸립니다. O(n)의 시간복잡도에서 n의 크기가 1억이라면 1초 이상의 시간이 걸림을 예상할 수 있습니다. 하지만 빅-오 표기법은 정확한 시간은 모릅니다. 위의 코드에서도 실은 2n+1번 계산을 하기 때문에 n이 1억일 때 2억+1번 연산을 하므로 2초 이상이 걸릴 수 있죠. 빅-오 표기법은 대략적인 코드의 시간 복잡도를 파악하기 위해 사용합니다.  

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
최대공약수를 구하는 알고리즘이죠 최악의 경우 주어지는 입력의 크기 만큼 반복문이 돌 수 있으므로 시간복잡도는 O(n)이라고 할 수 있습니다.  

상수 시간 복잡도라는 것도 있습니다. O(1)로 표기하고 이는 주어진 입력의 크기와 상관 없이 항상 일정한 연산을 하는 것을 의미합니다.
```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    n++;
    printf("입력값+1 = %d", n);
}
```
위 코드에서 n의 크기와 상관없이 일정한 횟수의 연산을 하므로 O(1)이라고 할 수 있습니다.


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
수를 뒤집는 알고리즘입니다. 이건 좀 특이합니다. 수의 자릿수 만큼 반복문이 돕니다. 따라서 시간 복잡도는 O(log_10(n)) 입니다.

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
십진수를 이진수로 바꾸는 알고리즘입니다. 첫번 째 while문을 유의해서 봐야 합니다. 2로 나눠가면서 연산을 하기 때문에 입력의 크기가 64면 8번 연산을 하겠죠. 따라서 저 부분의 시간복잡도는 O(log_2(n))이고 프로그램 전체의 시간복잡도는 O(log_2(n)+log_10(n)) = O(log_입니다.  
알고리즘에서 O(log_2(n))복잡도는 굉장히 중요합니다. 자료를 절반으로 나눠가면서 처리하는 테크닉이 자주 등장하기 때문입니다. 따라서 O(log_2(n))은 그냥 O(logn)으로 많이 씁니다. 

```c
#include <stdio.h>

int main()
{
	int arr[5] = { 3,2,1,4,5 };

	for (int i = 0; i < 5; i++)
	{
		for (int j = i + 1; j < 5; j++)
		{
			if (arr[i] > arr[j])
			{
				int temp = arr[i];
				arr[i] = arr[j];
				arr[j] = temp;
			}
		}
	}

	for (int i = 0; i < 5; i++) printf("%d ", arr[i]);
}
```
버블 소트 알고리즘입니다. 중첩 반복문을 사용했고 자료의 크기가 n이라 할 때 연산이 n(n-1)/2번 일어납니다 따라서 버블소트의 시간복잡도는 O(n^2)입니다.  

이 이외에도 O(n!), O(2^n), O(nlogn)등의 다양한 시간복잡도를 가지는 코드들이 있습니다.  

### 공간 복잡도

프로그램이 실햄되면서 메모리를 얼마나 차지할 지 찾는 것을 말하며 주로 배열의 크기가 결정합니다.  
```c
#include <stdio.h>

int main()
{
    int n, m;
    scanf("%d%d",&n,&m);
    for(int i=0;i<n;i++)
    {
        int temp;
        scanf("%d",&temp);
        if(temp < m) printf("%d ",temp);
    }
}
```
X보다 작은 수 라는 문제의 풀이입니다. 숫자를 n개 입력받는데 그 숫자가 m보다 작으면 출력합니다. 이 문제를 배열을 사용해 풀 수 있긴 합니다.  
```c
#include <stdio.h>

int main()
{
	int n, m;
	scanf("%d%d", &n, &m);
	int arr[10001];
	for (int i = 0; i < n; i++)
	{
		scanf("%d", &arr[i]);
		if (arr[i] < m) printf("%d ", arr[i]);
	}
}
```
n의 크기가 최대 10000이라고 알려줬기 때문에 이렇게 풀 수 있습니다. 하지만 만약 n의 크기가 1000000이고 문제의 메모리 제한이 1MB라고 가정해 보면. int의 크기는 4바이트이기 때문에 배열이 4MB를 차지하므로 문제를 풀 수 없습니다. 따라서 배열을 써서 모두 저장하는 방식으로는 풀 수 없게 됩니다.  
아직 공간복잡도를 깊게 고민해야 하는 문제는 못 만나봤을 겁니다. 하지만 어떤 코드가 메모리를 얼마나 먹는 지 생각할 수 있어야 합니다. 원하는 만큼 배열의 크기를 1억씩 해버릴 수는 없다는 겁니다.  

## 에라토스테네스의 체

에라토스테네스의 체는 소수를 판단하는 문제입니다.  
이전에 소수를 판단하는 방법을 배웠습니다.
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
n이 소수라면 반복문을 n번 도므로 시간복잡도는 O(n)이겠죠.  
이런 알고리즘이 있는데 왜 에라토스테네스의 체가 필요하냐 하면 에라토스테네스의 체가 훨씬 빠르기 때문입니다.  
에라토스테네스의 체를 사용하면 처음에 nlog(logn)번 연산을 한번 하면 그다음엔 O(1)만에 소수인지 아닌지 알 수 있습니다.  
n개의 수가 주어지고 그 수들이 소수인지 아닌지 판단하는 문제가 있다고 치면 기존의 방법으로는 O(nm)이 걸리겠지만(m=수의 최댓값) 에라토스테네스의 체를 사용하면 O(mlog(logm)+n)만에 풀 수 있습니다.  

에라토스테네스의 체 알고리즘
- 원하는 크기의 배열을 만든다.
- 0과 1은 소수가 아니다.
- 2부터 시작하여 처음 만나는 수는 모두 소수다
- 처음 만나는 수의 배수들은 모두 소수가 아니고 한반 만난것으로 간주한다.
즉 소수의 배수들을 모두 소수가 아닌 것으로 만들어 가는 것. 말로하니 조금 복잡합니다.  
```c
#include <stdio.h>

int main()
{
	int prime[10000] = { 1,1, }; //0이면 소수
	for (int i = 2; i < 10000; i++)
	{
		if (prime[i]) continue;
		for (int j = 2; i*j < 10000; j++)
		{
			prime[i*j] = 1;
		}
	}

	for (int i = 0; i < 10000; i++)
	{
		if (!prime[i]) printf("%d ", i);
	}
}
```
이렇듯 처음에 에라토스테네스의 체를 통하여 배열을 만들어 두면 그다음 어떤 수가 소수인지 아닌지 판단하는 데에는 O(1)만에 알 수 있습니다.

## 배열에서 선택하기

이건 따로 이름이 있는 알고리즘은 아니지만 배열에서 n개의 서로 다른 원소들을 골라야 할 때가 많습니다. 
가장 간단한 방법으로는 n중첩 반복문을 쓰는 것이고 다른 방법은 재귀함수를 사용하는 것입니다. 추후에 설명하도록 하겠습니다.  

```c
#include <stdio.h>

int main()
{
	int arr[5] = { 1,2,3,4,5 };
	//1개씩 고르기
	for (int i = 0; i < 5; i++) printf("%d\n", arr[i]);
	printf("\n");
	//2개씩 고르기
	for (int i = 0; i < 5; i++)
	{
		for (int j = i + 1; j < 5; j++)
		{
			printf("%d %d\n", arr[i], arr[j]);
		}
	}
	printf("\n");
	//3개씩 고르기
	for (int i = 0; i < 5; i++)
	{
		for (int j = i + 1; j < 5; j++)
		{
			for (int k = j + 1; k < 5; k++)
			{
				printf("%d %d %d\n", arr[i], arr[j], arr[k]);
			}
		}
	}
}
```

## 정렬 알고리즘

배열을 정렬하는 알고리즘은 정말 다양합니다. 이번에는 버블 소트를 자세히 살펴보겠습니다.  
버블 소트는 모든 원소를 서로 비교하면서 정렬하는 알고리즘입니다. 따라서 n(n-1)/2 번의 연산이 필요하고 O(n^2)의 시간복잡도를 가집니다.  
모든 원소를 서로 비교할 때 방금 배운 원소 선택법을 사용합니다.

```c
#include <stdio.h>

int main()
{
	int arr[5] = { 3,2,1,4,5 };

	for (int i = 0; i < 5; i++)
	{
		for (int j = i + 1; j < 5; j++)
		{
			if (arr[i] > arr[j])
			{
				int temp = arr[i];
				arr[i] = arr[j];
				arr[j] = temp;
			}
		}
	}

	for (int i = 0; i < 5; i++) printf("%d ", arr[i]);
}
```
i가 0일 때 j는 1~4 이므로 0과 1,2,3,4 즉 모든 원소를 서로 비교한 뒤에 0의 자리에 최솟값을 넣어주었습니다. 그리고 i가 1일 때 다시 이 과정을 반복해서 오름차순으로 정렬할 수 있는 것입니다.  

## 다차원 배열

다차원 배열을 배열의 인덱스가 여러개인 배열입니다. 1차원 배열은 직선적으로 2차원 배열은 표를 다루듯이 다룹니다. 2차원 배열은 좌표평면처럼 다룰 때도 있습니다. 3차원 배열은 큐브 모양 이겠죠? 하지만 꼭 기하학적인 관점으로 볼 필요는 없습니다. 4차원 배열은 상상할 수도 없죠. 1차원 배열은 for문으로 다루듯이 n차원 배열은 n중 for문으로 다룹니다. 배열의 초기화나 성질들은 1차원 배열과 동일합니다. 

초기화와 출력
```c
#include <stdio.h>

int main()
{
	int arr1[5] = { 1,2,3,4,5 };
	int arr2[5][5] = 
	{
		{1,2,3,4,5},
		{5,4,3,2,1},
		{3,4,5,6,7},
		{1,1,1,1,1},
		{2,2,2,2,2},
	};

	for (int i = 0; i < 5; i++)
	{
		printf("%d", arr1[i]);
	}

	printf("\n");
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 5; j++)
		{
			printf("%d", arr2[i][j]);
		}
		printf("\n");
	}
}
```

입력과 출력
```c
#include <stdio.h>

int main()
{
	int arr[5][5];
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 5; j++)
		{
			scanf("%d", &arr[i][j]);
		}
	}
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 5; j++)
		{
			printf("%d", arr[i][j]);
		}
	}
}
```

다차원 배열도 메모리에 저장될 때는 직선으로 저장됩니다. 참고만 해두세요  

다차원 배열을 잘 다루려면 결국 다중 중첩 반복문을 잘 쓸줄 알아야 합니다. 2차원 배열을 회전해서 출력해보는 등 자유자재로 다룰 수 있어야 합니다.
```c
#include <stdio.h>

int main()
{
	int arr2[2][3] = 
	{
		{1,2,3},
		{4,5,6},
	};

	for (int j = 0; j < 3; j++)
	{
		for (int i = 1; i >= 0; i--)
		{
			printf("%d", arr2[i][j]);
		}
		printf("\n");
	}
}
```
3차원 이상의 배열은 잘 다뤄지진 않습니다. 2차원 배열의 경우 굉장히 많이 사용합니다.  
처음에는 2차원 배열을 사용하는 데 조금 헷갈릴 수 있습니다. 2차원 배열에서 값을 가져오는 부분은 직접 많이 해봐야 합니다. i와 j가 몇일 때 데이터가 어디 저장되는 지 중첩 반복문을 어떻게 짜야 되는지 등등은 문제로 감을 익히는게 최고입니다.  

## 구간 합

구간 합이란 배열에서 a위치에서 b위치까지의 합을 구하는 것을 말합니다. 물론 직접 배열을 순회해서 구할 수도 있겠지만 구간 합을 여러번 구해야 할 때는 특별한 방법을 사용해야 합니다.  
배열의 값을 처음부터 순서대로 저장한 배열이 있다고 생각합니다.  
배열이 arr[4] = {a, b, c, d} 일 때 누적합 배열을 pre[5] = {0, a, a+b, a+b+c, a+b+c+d} 라고 하면 우리는 arr의 2~4번째 원소의 합을 pre[4]-pre[1] 으로 O(1)로 바로 구할 수 있습니다.  
```c
#include <stdio.h>

int main()
{
	int arr[] = { 1,2,3,4,5 };
	
	int pre[6] = {0,};
	for (int i = 0; i < 5; i++) pre[i + 1] = arr[i] + pre[i];
	int a, b;
	scanf("%d%d", &a, &b);
	printf("구간 [%d, %d]의 합 = %d", a, b, pre[b] - pre[a - 1]);
}
```


### 2차원에서 구간 합

이를 2차원 배열에 확장할 수 있습니다. 
자기보다 인덱스가 작은 배열의 값을 전부 저장합니다. 저장할 때 중복으로 값을 더할 수 있기 때문에 조심해야 합니다.  
```c
#include <stdio.h>

int main()
{
	int arr[5][5] =
	{
		{1,2,3,4,5},
		{5,4,3,2,1},
		{3,4,5,6,7},
		{1,1,1,1,1},
		{2,2,2,2,2},
	};
	
	int pre[6][6] = { 0, };
	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 5; j++)
		{
			pre[i + 1][j + 1] = arr[i][j] + pre[i][j + 1] + pre[i + 1][j] - pre[i][j];
		}
	}

	int a, b, c, d;
	scanf("%d%d%d%d", &a, &b, &c, &d);
	printf("(%d, %d) 부터 (%d, %d) 까지의 합 = %d", 
		a, b, c, d, pre[c][d] - pre[a - 1][d] - pre[c][b - 1] + pre[a - 1][b - 1]);
}
```
기하학적으로 보면 쉽게 이해할 수 있습니다.
