# 7강

## 목차
- 구조체
- 파일 입출력

## 구조체

개발을 서로 관련된 변수들이 많이 생겨서 관리하기가 어려울 때가 있습니다.  

**두 좌표 사이의 거리**
```c
#include <stdio.h>
#include <math.h>

int main()
{
	int a_x = 1, a_y = 2;
	int b_x = 4, b_y = 6;

	printf("%f", sqrt((b_x - a_x) * (b_x - a_x) + (b_y - a_y) * (b_y - a_y)));
}
```
서로 다른 좌표가 여러개 생긴다면 관리하기가 어렵습니다.  

```c
#include <stdio.h>
#include <math.h>

int main()
{
	int point_x[2] = {1, 4};
	int point_y[2] = {2, 6};
	printf("%f", sqrt((point_x[1] - point_x[0]) * (point_x[1] - point_x[0]) + 
    (point_y[1] - point_y[0]) * (point_y[1] - point_y[0])));
}
```
이런 식으로 간단하게 만들 수 있긴 하지만 여전히 복잡해 보입니다.  

다른 예제를 봅시다.  

**학생 관리 프로그램**
```c
#include <stdio.h>

int main()
{
	int a_id = 18101290;
	int a_age = 21;
	char a_major[30] = "Computer Engineering";
	char a_name[20] = "InSeoHwang";
	
	int b_id = 18101289;
	int b_age = 21;
	char b_major[30] = "Computer Engineering";
	char b_name[20] = "HaJiMwo";

	printf("a학생의 학번 : %d\n", a_id);
	printf("a학생의 나이 : %d\n", a_age);
	printf("a학생의 전공 : %s\n", a_major);
	printf("a학생의 이름 : %s\n", a_name);
	printf("\n");
	printf("b학생의 학번 : %d\n", b_id);
	printf("b학생의 나이 : %d\n", b_age);
	printf("b학생의 전공 : %s\n", b_major);
	printf("b학생의 이름 : %s\n", b_name);
}
```
저장할 학생들의 정보가 늘어나거나 수정될 때 마다 변수들을 일일이 변경해줘야 합니다.  

이런 관련된 정보들을 묶는것이 구조체입니다.  

### 구조체의 사용

구조체는 다음과 같이 선언합니다.  
```c
struct 구조체이름
{
    구조체 변수 선언
};

struct Point
{
	int x, y;
};
```
구조체는 이렇게 여러 변수를 묶어놓고 한번에 관리할 수 있도록 해주는 것입니다.  

구조체를 만들었으면 구조체 변수를 선언하고 사용해 봅시다.  
```c
#include <stdio.h>
#include <math.h>

struct Point
{
	int x, y;
};

int main()
{
	struct Point a;
    // struct 구조체이름 구조체변수의이름 으로 선언합니다.
	a.x = 1;
	a.y = 2;
    // 구조체 멤버는 . 을 통해 접근할 수 있습니다.
	printf("a.x = %d , a.y = %d", a.x, a.y);
}
```

위의 좌표로 거리 구하기 문제를 다음과 같이 풀 수 있겠습니다.  

```c
#include <stdio.h>
#include <math.h>

struct Point
{
	int x, y;
};

int main()
{
	struct Point a = { 1,2 }, b = { 4, 6 };
    // 이런식으로 초기화 해줄 수 있습니다.
	printf("%f", sqrt((b.x - a.x) * (b.x - a.x) + (b.y - a.y) * (b.y - a.y)));
}
```

```c
#include <stdio.h>
#include <string.h>

struct Student
{
	int id, age;
	char major[32], name[20];
};

int main()
{
	struct Student a = { 18101290, 21, "Computer Engineering", "InSeoHwang" },
		b = { 18101289,21,"Computer Engineering", "a" };
	//문자열도 초기화가능

	strcpy(b.name, "HaJiMwo");
	// 문자열에 값을 넣기 위해선 strcpy(대상, 넣을 문자열) (string_copy약자) 함수 사용
	printf("a학생의 학번 : %d\n", a.id);
	printf("a학생의 나이 : %d\n", a.age);
	printf("a학생의 전공 : %s\n", a.major);
	printf("a학생의 이름 : %s\n", a.name);
	printf("\n");
	printf("b학생의 학번 : %d\n", b.id);
	printf("b학생의 나이 : %d\n", b.age);
	printf("b학생의 전공 : %s\n", b.major);
	printf("b학생의 이름 : %s\n", b.name);
}
```

구조체 변수를 구조체를 선언함과 동시에 만들 수 있습니다.  
```c
struct 구조체이름 {
    자료형 멤버이름;
} 변수;

struct Student
{
	int id, age;
	char major[32], name[20];
}a;
```

구조체 배열도 있습니다.  
```c
#include <stdio.h>
#include <math.h>

struct Point
{
	int x, y;
}p[2];

int main()
{
	p[0].x = 1, p[0].y = 2;
	p[1].x = 4, p[1].y = 6;
	printf("%f", sqrt((p[1].x - p[0].x) * (p[1].x - p[0].x) + (p[1].y - p[0].y) * (p[1].y - p[0].y)));
}
```

### typedef로 별칭 만들기

typedef는 기존 키워드의 별칭을 붙여주는 명령어 입니다.  
```c
typedef long long int ll;

int main()
{
    ll a;
    long long int b;
    // a와 b는 같은 타입
}
```

구조체도 자료형중 하나 입니다. 그리고 특별한 방법으로 별칭을 만들어줄 수 있습니다.  
```c
typedef struct pnt
{
	int x, y;
}Point;
// struct pnt의 별명을 point로 해줌

int main()
{
	Point a = { 1,2 }, b = { 4, 6 };
    // Point만 써도 구조체 변수 선언 가능 Point를 자료형처럼 사용함
	printf("%f", sqrt((b.x - a.x) * (b.x - a.x) + (b.y - a.y) * (b.y - a.y)));
}
```

아예 그냥 구조체의 이름을 생략할 수도 있습니다. 이를 익명 구조체라고 합니다. 대신 별칭만 있는 셈이죠  
```c
typedef struct
{
	int x, y;
}Point;

int main()
{
	Point a = { 1,2 }, b = { 4, 6 };
	printf("%f", sqrt((b.x - a.x) * (b.x - a.x) + (b.y - a.y) * (b.y - a.y)));
}
```

### 구조체 복사하기 memcpy()

구조체는 int a, b일때 a=b 하는 것처럼 a에다 b를 넣지 못합니다.  
```c
int main()
{
    int a=1, b=2;
    b = a;
}
```
memcpy (member copy의 약자) 함수를 이용해야 합니다.  
다음과 같이 사용합니다.  
```c
memcpy(대상의 주소, 넣을 것의 주소, 대상의 크기);
```

```c
#include <stdio.h>
#include <string.h>

struct Student
{
	int id, age;
	char major[32], name[20];
};

int main()
{
	struct Student a = { 18101290, 21, "Computer Engineering", "InSeoHwang" },b;

	memcpy(&b, &a, sizeof(a));

	printf("a학생의 학번 : %d\n", a.id);
	printf("a학생의 나이 : %d\n", a.age);
	printf("a학생의 전공 : %s\n", a.major);
	printf("a학생의 이름 : %s\n", a.name);
	printf("\n");
	printf("b학생의 학번 : %d\n", b.id);
	printf("b학생의 나이 : %d\n", b.age);
	printf("b학생의 전공 : %s\n", b.major);
	printf("b학생의 이름 : %s\n", b.name);
}
```

### 구조체의 동적할당

구조체는 처음부터 일일이 선언해서 만들어두기 보다는 필요할 때마다 동적할당해서 프로그램에 추가해주는 방식을 많이 활용합니다.

구조체도 포인터를 선언할 수 있습니다.  
```c
typedef struct
{
	int* p;
}Data;

int main()
{
	int n = 1;
	Data a = { &n };
	Data* sp = &a;
	printf("%p\n", sp->p);	// = a.p = &n
    //구조체 포인터를 통해 접근할 때는 화살표를 사용합니다.
    //또는 (*sp).p
	printf("%d\n", *sp->p); // = *a.p = n
}
```

malloc 함수를 이용해 구조체 크기만큼의 메모리를 할당받고 그 주소를 구조체 포인터로 형변환 시켜준 후에 구조체 포인터에 넣어주면 해당 구조체 포인터를 통해 동적할당한 공간에 접근할 수 있습니다.  
```c
struct 구조체이름 *포인터이름 = malloc(sizeof(struct 구조체이름));
```

```c
#include <stdio.h>

typedef struct Student
{
	int id, age;
	char major[32], name[20];
}Student;

int main()
{
	Student* p = (Student*)malloc(sizeof(Student));

	printf("학생의 학번을 입력하세요");
	scanf("%d", &p->id);
	printf("학생의 나이를 입력하세요");
	scanf("%d", &p->age);
	printf("학생의 전공을 입력하세요");
	scanf("%s", p->major);
	printf("학생의 이름을 입력하세요");
	scanf("%s", p->name);

	printf("학생의 학번 : %d\n", p->id);
	printf("학생의 나이 : %d\n", p->age);
	printf("학생의 전공 : %s\n", p->major);
	printf("학생의 이름 : %s\n", p->name);
}
```

학생 n명의 정보를 입력받고 출력해보는 프로그램입니다. 프로그램의 구조를 잘 보세요  
```c
#include <stdio.h>
#define MAX_SIZE 100

typedef struct Student
{
	int id, age;
	char major[32], name[20];
}Student;

Student* arr[MAX_SIZE];
int student_num;

void input_data(Student* student)
{
	printf("학번을 입력하세요 : ");
	scanf("%d", &student->id);
	printf("나이를 입력하세요 : ");
	scanf("%d", &student->age);
	printf("전공을 입력하세요 : ");
	scanf("%s", student->major);
	printf("이름을 입력하세요 : ");
	scanf("%s", student->name);
}

void printf_data(Student student)
{
	printf("학번 : %d\n", student.id);
	printf("나이 : %d\n", student.age);
	printf("전공 : %s\n", student.major);
	printf("이름 : %s\n", student.name);
}

void allocate_student()
{
	printf("\n");
	for (int i = 0; i < student_num; i++)
	{
		arr[i] = (Student*)malloc(sizeof(Student));
		printf("%d번째 학생의 정보 입력\n", i + 1);
		input_data(arr[i]);
		printf("%d번째 입력 완료!\n\n", i + 1);
	}
}

int main()
{
	printf("입력할 학생의 수(최대 %d명) : ", MAX_SIZE);
	scanf("%d", &student_num);
	allocate_student();

	for (int i = 0; i < student_num; i++)
	{
		printf("--%d번째 학생의 정보--------------\n", i + 1);
		printf_data(*arr[i]);
		printf("---------------------------------\n\n");
	}
}
```

### 자기참조 구조체

자기참조 구조체란 자기 자신의 포인터를 멤버 변수로 가지는 구조체를 말합니다.  
```c
struct A
{
    int a;
    struct A *p;
}
```

자기참조 구조체를 이용하면 특이한 구조의 자료를 많이 만들 수 있습니다. a가 b의 주소를 가지고 b가 c의 주소를 가지고 이런 식으로 말이죠.  
대표적인 예를 보겠습니다.  

#### 연결리스트

연결리스트란 각 자료가 서로 데이터와 포인터를 가지고 한줄로 연결되어 있는 자료 구조를 말합니다.  
배열의 경우 무조건 연속적으로 메모리상에 저장되어 있어야 하는데 연결리스트는 서로의 주소를 통해 연결되어 있기 때문에 그럴 필요가 없고 중간에서 삽입과 삭제가 편합니다. 앞뒤의 포인터의 값만 바꾸면 되기 때문입니다.  

```c
#include <stdio.h>

typedef struct Data
{
	int val;
	struct Data* next;
}Data;

int main()
{
	Data a, b, c;
	a.val = 1;
	a.next = &b;
	b.val = 2;
	b.next = &c;
	c.val = 3;
	c.next = NULL;

	for (Data *x = &a; x != NULL; x = x->next)
	{
		printf("%d ", x->val);
	}
}
```
간단한 연결리스트의 구현입니다. 


다음은 n개의 데이터를 연결리스로 저장한 예제입니다.  
```c
#include <stdio.h>

typedef struct Data
{
	int val;
	struct Data* next;
}Data;

int main()
{
	Data *p = NULL, *start = NULL;

	int n;
	printf("연결리스트의 길이 : ");
	scanf("%d", &n);

	for (int i = 0; i < n; i++)
	{
		Data* temp = (Data*)malloc(sizeof(Data));
		printf("숫자 입력 : ");
		scanf("%d", &temp->val);
		temp->next = NULL;
		if (p != NULL) p->next = temp;
		else start = temp;
		p = temp;
	}

	for (Data* x = start; x != NULL; x = x->next)
	{
		printf("%d ", x->val);
	}
}
```
이게 아주 재밌습니다. 코드 어디에도 데이터를 직접 저장하지 않습니다. 데이터는 heap영역에 저장되어 있고 main함수에서는 그곳의 주소만 가지고 있는 상태이며 그 주소를 가지고 연결리스트에 접근합니다.  


이 뿐만 아니라 트리, 그래프 등의 자료구조도 구조체로 구현이 가능하기 때문에 굉장히 중요합니다.  

### 구조체 변수의 크기 (구조체 정렬)

구조체는 효율적인 연산을 위해 멤버중에서 가장 큰 자료형의 크기로 나머지 멤머들의 크기까지 맞춰줍니다. 따라서 조심해야 합니다.
```c
struct Data
{
    char c;
    int n;
}
```
이렇게 구조체륾 만들면 int의 크기가 4byte로 가장 크므로 c의 크기도 4byte가 됩니다. 문자열을 만들 때 주의해야 합니다. 따라서 sizeof(Data) = 8 이 되겠습니다.  

이런식으로 감싸주면 정렬을 하지 않습니다.
```c
#pragma pack(push, 1)    // 1바이트 크기로 정렬
struct Data
{
	char c;
	int n;
};
#pragma pack(pop) 
```
대신에 typedef와 같이 사용 못합니다. 위에서 sizeof(Data) = 5가 나옵니다.

## 파일 입출력

간단하게 알려드리겠습니다.  

- 파일 열기 : FILE* fp = fopen("test.txt", "w");
- 파일에 쓰기 : fprintf(fp, "helloworld %d", 1);
- 파일에서 읽기 : fscanf(fp, "%d", &n);
- 파일 입출력 종료 : fclose(fp); //꼭 해줘야 합니다.

파일포인터만 잘 열고 닫는 것을 제외하면 우리가 기존에 하던 콘슬 입출력과 비슷합니다.  

에라토스테네스의 체를 이용해서 소수를 메모장에 출력합니다.  
```c
#include <stdio.h>

int prime[100] = { 1,1 };

int main()
{
	for (int i = 2; i * i < 100; i++)
	{
		if (prime[i]) continue;
		for (int j = 2; i * j < 100; j++)
		{
			prime[i * j] = 1;
		}
	}

	FILE* fp = fopen("test.txt", "w");
	for (int i = 0; i < 100; i++)
	{
		if (!prime[i])
		{
			fprintf(fp, "%d ", i);
		}
	}
	fclose(fp);
}
```