# 2, 3강 과제 정답

## 2강 문제

- 아스키 코드
    - 문자도 숫자로 다루어진다는 것을 이해하는 문제입니다
    ```c
    #include <stdio.h>
    int main()
    {
        char a;
        scanf("%c",&a);
        printf("%d",a);
    }
    ```

- 스타워즈 로고
    - 알고리즘 문제를 풀 때는 주어진 문제의 출력 형식을 정확하게 맞춰줘야 합니다.
    - 따라서 문제의 출력 형식을 복사-붙여넣기로 맞춰주는 것이 좋습니다.
    ```c
    #include <stdio.h>
    int main()
    {
        printf("    8888888888  888    88888\n");
        printf("   88     88   88 88   88  88\n");
        printf("    8888  88  88   88  88888\n");
        printf("       88 88 888888888 88   88\n");
        printf("88888888  88 88     88 88    888888\n");
        printf("\n");
        printf("88  88  88   888    88888    888888\n");
        printf("88  88  88  88 88   88  88  88\n");
        printf("88 8888 88 88   88  88888    8888\n");
        printf(" 888  888 888888888 88  88      88\n");
        printf("  88  88  88     88 88   88888888\n");
    }
    ```

- We love krill
    ```c
    #include <stdio.h>
    int main()
    {
        printf("강한친구 대한육군\n강한친구 대한육군");
        return 0;
    }
    ```

- 나부 함대 데이터
    ```c
    #include <stdio.h>
    int main()
    {
        printf("SHIP NAME      CLASS          DEPLOYMENT IN SERVICE\n");
        printf("N2 Bomber      Heavy Fighter  Limited    21        \n");
        printf("J-Type 327     Light Combat   Unlimited  1         \n");
        printf("NX Cruiser     Medium Fighter Limited    18        \n");
        printf("N1 Starfighter Medium Fighter Unlimited  25        \n");
        printf("Royal Cruiser  Light Combat   Limited    4         \n");
        return 0;
    }
    ```

- 개
    - printf 내부에서 "와 \는 특별한 의미를 가지기 때문에 이 문자들을 출력하기 위해서는 \를 붙여줘야 합니다.
    ```c
    #include <stdio.h>

    int main()
    {
        printf("|\\_/|\n");
        printf("|q p|   /}\n");
        printf("( 0 )\"\"\"\\\n");
        printf("|\"^\"`    |\n");
        printf("||_/=\\\\__|\n");
    }
    ```

- 고양이
    ```c
    #include <stdio.h>
    int main()
    {
        printf("\\    /\\\n");
        printf(" )  ( ')\n");
        printf("(  /  )\n");
        printf(" \\(__)|\n");
    }
    ```

- 콜센터
    ```c
    #include <stdio.h>
    int main(){
        printf("     /~\\\n");
        printf("    ( oo|\n");
        printf("    _\\=/_\n");
        printf("   /  _  \\\n");
        printf("  //|/.\\|\\\\ \n");
        printf(" ||  \\ /  ||\n");
        printf("============\n");
        printf("|          |\n");
        printf("|          |\n");
        printf("|          |\n");
        return 0;
    }
    ```

- A+B
    - 간단히 연산자를 사용해보는 문제입니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int a,b;
        scanf("%d%d",&a,&b);
        printf("%d", a+b);
    }
    ```

- A-B
    ```c
    #include <stdio.h>
    int main()
    {
        int a,b;
        scanf("%d%d",&a,&b);
        printf("%d", a-b);
    }
    ```

- AxB
    ```c
    #include <stdio.h>
    int main()
    {
        int a,b;
        scanf("%d%d",&a,&b);
        printf("%d", a*b);
    }
    ```

- A/B
    ```c
    #include <stdio.h>
    int main()
    {
        int a,b;
        scanf("%d%d",&a,&b);
        printf("%d", a/b);
    }
    ```

- 사칙연산
    ```c
    #include <stdio.h>
    int main()
    {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d\n", a + b);
    printf("%d\n", a - b);
    printf("%d\n", a*b);
    printf("%d\n", a / b);
    printf("%d\n", a%b);
    return 0;
    }
    ```

- 나머지
    - 나머지 연산의 속성을 묻는 문제입니다. 
    ```c
    #include<stdio.h>
    int main()
    {
        int A,B,C;
        scanf("%d %d %d",&A,&B,&C);
        printf("%d\n",(A+B)%C);
        printf("%d\n",(A%C + B%C)%C);
        printf("%d\n",(A*B)%C);
        printf("%d\n",((A%C)*(B%C))%C);
        return 0;
    }
    ```

- 제리와 톰
    - 간단히 변수와 연산자를 활용하여 실생활의 문제를 푸는 문제입니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n, m;
        scanf("%d%d", &n, &m);
        printf("%d %d", m - n, m);
    }
    ```

- N찍기
    - 반복문과 반복문 변수를 활용하는 문제입니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n)
        for (int i = 0; i < n; i++)
        {
            printf("%d\n", i + 1);
        }
    }

- Hello Judge
    - 위 문제와 같습니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n)
        for (int i = 0; i < n; i++)
        {
            printf("Hello World, Judge %d!\n", i + 1);
        }
    }
    ```

- 합
    - 합을 저장할 변수를 만들고 반복문을 통해 합을 구합니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int sum = 0, n;
        scanf("%d", &n);
        for (int i = 1; i <= n; i++)
        {
            sum += i;
        }
        printf("%d", sum);
    }
    ```
    - 사실 등차수열의 합 공식을 쓰면 간단히 풀 수 있습니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        printf("%d", (n + 1) * n / 2);
    }
    ```

- 구구단
    ```c
    #include<stdio.h>
    int main()
    {
        int n = 0;
        scanf("%d", &n);
        for (int i = 1; i < 10; i++)
        {
            printf("%d * %d = %d\n", n, i, n * i);
        }
    }
    ```

- 숫자의 합
    - 숫자의 개수가 최대 100개입니다. 따라서 최대 100자리의 숫자를 입력받아야 한다는 뜻입니다.
    - C언어에서 100자리의 숫자를 숫자로 저장할 수 있는 방법이 없습니다.
    - scanf의 서식문자중 %1d를 활용하여 '한자리'씩만 입력받아 합을 더해가는 방법이 있습니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int n, sum = 0;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            int temp;
            scanf("%1d", &temp);
            sum += temp;
        }
        printf("%d", sum);
    }
    ```
    - 또는 연속된 숫자들을 문자로 취급하여 저장한 뒤 합을 더해가는 방법이 있습니다.
    ```c
    #include<stdio.h>
    #include<string.h>

    int main()
    {
        int n;
        char s[101];
        scanf("%d%s", &n, s);

        int sum = 0;
        for (int i = 0; i < n; i++)
        {
            sum += s[i] - '0';
        }
        printf("%d", sum);
    }
    ```

- 0 = not cute / 1 = cute
    - 정말 다양한 풀이가 있을 수 있습니다.
    - 반복문과 변수를 적절히 사용하여 푸는 문제입니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n, tmp, cnt = 0;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            scanf("%d", &tmp);
            if (tmp == 1)
            {
                cnt++;
            }
            else
            {
                cnt--;
            }
        }
        if (cnt > 0)
            printf("Junhee is cute!");
        else
            printf("Junhee is not cute!");
    }
    ```
    - 조금더 줄일 수 있습니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n, tmp, cnt = 0;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            scanf("%d", &tmp);
            tmp ? cnt++ : cnt--;
        }
        printf("%s", cnt > 0 ? "Junhee is cute!" : "Junhee is not cute!");
    }
    ```

- X보다 작은 수
    - 알고리즘 문제의 채점은 출력값만 보기 때문에 반복문을 도는 도중에 출력해도 됩니다.
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

- 시험 성적
    - 조건문의 구조를 이용하는 문제입니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        if (n >= 90)
        {
            printf("A");
        }
        else if (n >= 80)
        {
            printf("B");
        }
        else if (n >= 70)
        {
            printf("C");
        }
        else if (n >= 60)
        {
            printf("D");
        }
        else
            printf("F");
    }
    ```

- 세 수
    - 조건문을 통해 경우의 수를 나눠서 문제를 풉니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int a, b, c;
        scanf("%d%d%d", &a, &b, &c);
        if (a < b)
        {
            //a<b<c
            //c<a<b
            //a<c<b
            if (b < c) printf("%d", b);
            else if (c < a) printf("%d", a);
            else printf("%d", c);
        }
        else
        {
            //b<a
            //c<b<a
            //b<a<c
            //b<c<a
            if (c < b) printf("%d", b);
            else if (a < c) printf("%d", a);
            else printf("%d", c);
        }
    }
    ```

- 최댓값
    - 최댓값을 구하기 위해서는 최댓값을 저장할 변수를 만들고 주어진 자료들을 전부 검사해야 합니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int max = 0;
        int pos = 0;
        for (int i = 0; i < 9; i++)
        {
            int temp;
            scanf("%d", &temp);
            if (max < temp)
            {
                max = temp;
                pos = i + 1;
            }
        }
        printf("%d\n%d", max, pos);
    }
    ```

- 최소, 최대
    - 최댓값, 최솟값의 초기값은 주어진 자료의 최솟값, 최댓값으로 설정하거나 주어진 자료중 하나를 임의로 선택하여 초기값으로 지정해주는 방법이 있습니다.
    ```c
    int main()
    {
        int n, temp;
        scanf("%d", &n);
        int max = -1000000;
        int min = 1000000;
        for (int i = 0; i < n; i++)
        {
            scanf("%d", &temp);
            if (max < temp) max = temp;
            if (min > temp) min = temp;
        }
        printf("%d %d", min, max);
    }
    ```
    
    ```c
    #include <stdio.h>
    int main()
    {
        int n, temp;
        scanf("%d%d", &n, &temp);
        int max = temp;
        int min = temp;
        for (int i = 1; i < n; i++)
        {
            scanf("%d", &temp);
            if (max < temp) max = temp;
            if (min > temp) min = temp;
        }
        printf("%d %d", min, max);
    }
    ```

- 최대공약수와 최소공배수
    - 최대공약수를 구하는 방법은 두 수와 동시에 나누어 떨어지는 수를 반복문을 통해 찾는 방법이 있고 유클리드 호제법이라는 방법을 통해 찾을 수 있습니다.
    - 반복문 이용
    ```c
    #include <stdio.h>
    int main()
    {
        int a, b;
        scanf("%d%d", &a, &b);
        int c = a > b ? b : a;
        int gcd;
        for (int i = c; i >= 1; i--)
        {
            if (a % i == 0 && b % i == 0)
            {
                gcd = i;
                break;
            }
        }
        printf("%d\n%d", gcd, a * b / gcd);
    }
    ```

    - 유클리드 호제법 이용
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
        int c = gcd(a, b);
        printf("%d\n%d", c, a * b / c);
    }
    ```
- 팩토리얼
    - 합을 구하는 문제와 비슷하지만 0!=1 임을 조심해야 합니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int n, ans = 1;
        scanf("%d", &n);
        for (int i = 1; i <= n; i++)
        {
            ans *= i;
        }
        printf("%d", ans);
    }
    ```

- 2의 제곱인가?
    - 이 문제는 정말 다양한 풀이가 있습니다.
    - 2로 계속 나누다가 나머지가 있다면 2의 제곱이 아님
    ```c
    #include <stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        while (n > 1)
        {
            if (n % 2)
            {
                printf("0");
                return 0;
            }
            n /= 2;
        }
        printf("1");
    }
    ```
    - 2의 제곱수를 만들어가다가 입력값보다 커지면 제곱수 아님 일치하면 2의 제곱수
    ```c
    #include <stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int i = 1; i <= n; i *= 2)
        {
            if (i == n)
            {
                printf("1");
                return 0;
            }
        }
        printf("0");
    }
    ```
    - 컴퓨터공학에서 2는 특별한 수 입니다. 컴퓨터는 숫자들을 2진수로 저장합니다. 따라서 2진수의 성질을 이용해서 풀 수 있습니다.
    - 2의 제곱수는 이진수로 나타내면 모두 100 1000 10000 의 형태를 가집니다. 따라서 2의 제곱수&2의 제곱수-1 을 하면 100 & 011 = 0 이런 식으로 모두 0이 됩니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        printf("%d", n&(n - 1) ? 0 : 1);
    }
    ```

- 별찍기 - 1
    - 중첩 반복문을 사용하는 문제입니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int j = 0; j < n; j++)
        {
            for (int i = 0; i < j + 1; i++)
            {
                printf("*");
            }
            printf("\n");
        }
    }
    ```

- 히스토그램
    - 수를 입력받고 그만큼 출력합니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            int m;
            scanf("%d", &m);
            for (int j = 0; j < m; j++)
            {
                printf("=");
            }
            printf("\n");
        }
    }
    ```

## 3강 문제

- 수 뒤집기
    - 수를 뒤집는 테크닉과 변수를 활용하는 조금 복잡한 문제입니다. 함수를 활용하면 더 편하게 풀 수 있습니다.
    - 변수의 이름을 헷갈리게 지으면 안되고 초기화를 꼭 잘 해줘야 합니다.
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
    - 함수 활용
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

- 이진수
    - 10진수를 2진수로 변환하는 과정을 이해하면 풀기 쉽습니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int t;
        scanf("%d", &t);
        while (t--)
        {
            int n, cnt = 0;
            scanf("%d", &n);
            while (n > 0)
            {
                if (n % 2) printf("%d ", cnt);
                n /= 2;
                cnt++;
            }
            printf("\n");
        }
    }
    ```

- A+B-3
    - 단순 반복문 문제입니다.
    ```c
    #include <stdio.h>

    int main()
    {
        int n, a, b;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            scanf("%d %d", &a, &b);
            printf("%d\n", a+b);
        }
    }
    ```

- 짝수를 찾아라
    - 중첩 반복문 + 변수 활용
    ```c
    #include <stdio.h>
    int main()
    {
        int t;
        scanf("%d", &t);
        while (t--)
        {
            int min = 100, sum = 0;
            for (int i = 0; i < 7; i++)
            {
                int temp;
                scanf("%d", &temp);
                if (temp % 2 == 0)
                {
                    sum += temp;
                    if (temp < min) min = temp;
                }
            }
            printf("%d %d\n", sum, min);
        }
    }
    ```

- 별 찍기 - 2
    - 별도 찍고 공백도 찍어야 합니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            //공백 출력부분
            for (int j = 0; j < n - i - 1; j++)
            {
                printf(" ");
            }
            //별 출력 부분
            for (int j = 0; j < 1 + i; j++)
            {
                printf("*");
            }
            printf("\n");
        }
    }
    ```

- 별찍기 - 5
    - 별을 찍기 위해 반복을 몇 번 해야하는지 잘 생각해야 합니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int i = 0; i < n; i++)
        {
            //공백 출력부분
            for (int j = 0; j < n - i - 1; j++)
            {
                printf(" ");
            }
            //별 출력 부분
            for (int j = 0; j < 2 * i + 1; j++)
            {
                printf("*");
            }
            printf("\n");
        }
    }
    ```

- 숫자의 개수
    - %연산자를 이용해 숫자를 한자리씩 다룰 수 있습니다.
    - 배열을 활용해 연속된 정보를 저장합니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int a, b, c;
        scanf("%d%d%d", &a, &b, &c);
        int n = a * b * c;

        int check[10] = { 0, };
        while (n > 0)
        {
            check[n % 10]++;
            n /= 10;
        }

        for (int i = 0; i < 10; i++) printf("%d\n", check[i]);
    }
    ```

- 음계
    - 배열의 오름차순, 내림차순을 검사하는 테크닉이 필요합니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int arr[8];
        for (int i = 0; i < 8; i++)
            scanf("%d", &arr[i]);

        //오름차순 판단 맞으면 출력 후 return 0
        int check = 1;
        for (int i = 0; i < 7; i++)
        {
            if (arr[i] > arr[i + 1])
            {
                check = 0;
                break;
            }
        }
        if (check)
        {
            printf("ascending");
            return 0;
        }
        
        //내림차순 판단 맞으면 출력 후 return 0
        check = 1;
        for (int i = 0; i < 7; i++)
        {
            if (arr[i] < arr[i + 1])
            {
                check = 0;
                break;
            }
        }
        if (check)
        {
            printf("descending");
            return 0;
        }
        else printf("mixed");
    }
    ```

- 피보나치 수 5
    - 배열을 이용해서 피보나치의 값을 저장하고 이전에 저장한 값을 활용하여 나머지 값을 계산합니다.
    ```c
    #include <stdio.h>
    int main()
    {
        int fibo[21] = { 0,1 };
        for (int i = 2; i <= 20; i++)
        {
            fibo[i] = fibo[i - 1] + fibo[i - 2];
        }

        int n;
        scanf("%d", &n);
        printf("%d", fibo[n]);
    }
    ```

- 수 정렬하기
    - 배열을 정렬하는 여러 방법이 있습니다.
    - 버블소트를 이용해 문제를 풀 수 있습니다. 버블소트는 모든 수를 서로 비교해서 정렬하는 방법입니다.
    ```c
    #include<stdio.h>
    int main()
    {
        int n;
        scanf("%d", &n);

        int arr[1000];
        for (int i = 0; i < n; i++)
        {
            scanf("%d", &arr[i]);
        }

        for (int i = 0; i < n; i++)
        {
            for (int j = i + 1; j < n; j++)
            {
                if (arr[i] > arr[j])
                {
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }

        for (int i = 0; i < n; i++)
        {
            printf("%d\n", arr[i]);
        }
    }
    ```

- 열 개씩 끊어 출력하기
    - 문자열을 받고 문자열을 순회하면서 한문자씩 출력하고 10개를 출력했을 때 줄바꿈을 출력합니다.
    - strlen() 함수는 문자열의 길이만큼 시간이 걸리기 때문에 반복문 내부에 넣으면 안됩니다.
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        char A[100];
        gets(A);
        int len = strlen(A);
        for (int i = 0; i < len; i++)
        {
            printf("%c", A[i]);
            if ((i+1) % 10 == 0) printf("\n");
        }
    }
    ```

- 문자열 반복
    - 문자열을 받고 문자열을 순회하면서 한 문자를 반복문을 통해 여러번 출력합니다.
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        int n1, n2;
        char A[21];
        scanf("%d",&n1);
        
        for(int i=0;i<n1;i++)
        {	
            scanf("%d %s",&n2,A);
            for(int j=0;j<strlen(A);j++)
            {
                for(int k=0;k<n2;k++)
                {
                    printf("%c",A[j]);
                }
            }
            printf("\n");
        }
    }
    ```

- 그대로 출력하기
    - 서식문자 "%[^\n]"를 이용해서 한 줄을 전부 입력받습니다.
    - "%[^\n]"는 줄바꿈을 입력받지 않기 때문에 버퍼에 줄바꿈을 남김니다. 따라서 getchar()를 통해 줄바꿈을 버퍼에서 입력받아서 없애줘야 합니다.
    ```c
    #include<stdio.h>
    int main()
    {
        char s[100];
        while (scanf("%[^\n]", s) != EOF)
        {
            printf("%s\n", s);
            getchar();
        }

    }
    ```

- 알파벳 찾기
    - 문자열을 입력받고 순회하면서 처음 나온 알파벳의 위치를 배열에 저장합니다.
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        int A[26];
        char Word[100];
        for (int i = 0; i<26; i++)
        {
            A[i] = -1;
        }

        scanf("%s", Word);
        int len = strlen(Word)
        for (int i = 0; i < len; i++)
        {
            if(A[Word[i] - 'a']==-1)A[Word[i] - 'a'] = i;
        }

        for (int i = 0; i<26; i++)
        {
            printf("%d ", A[i]);
        }
    }
    ```

- IBM 빼기 1
    - 문자열을 입력받고 순회하면서 문자에 1을 더한 뒤 출력합니다. 만약 문자가 Z라면 A로 출력합니다
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        int n;
        scanf("%d", &n);
        for (int t = 1; t <= n; t++)
        {
            printf("String #%d\n", t);
            char s[51];
            scanf("%s", s);
            int len = strlen(s);
            for (int i = 0; i < len; i++)
            {
                if (s[i] == 'Z') printf("A");
                else printf("%c", s[i] + 1);
            }
            printf("\n\n");
        }
    }
    ```

- OX퀴즈
    - 변수를 잘 활용해야 하는 문제입니다.
    - OX를 문자열로 받고 순회하면서 O가 등장할 때마다 카운트를 해줍니다.
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        int t;
        char s[81];
        scanf("%d", &t);
        while(t--)
        {
            int cnt = 0, ans = 0;
            scanf("%s", s);
            int len = strlen(s);
            for (int j = 0; j < len; j++)
            {
                if (s[j] == 'O')
                {
                    cnt += 1;
                    ans += cnt;
                }
                else cnt = 0;
            }
            printf("%d\n", ans);
        }
    }
    ```

- 단어 공부
    - 대소문자 구분 없이 알파벳의 개수를 세고 최댓값과 그 위치를 찾아야 하는 문제입니다. 조금 복잡할 수 있습니다.
    ```c
    #include<stdio.h>
    #include<string.h>

    int main()
    {
        char s[1000001];
        scanf("%s", s);

        int len = strlen(s);
        for (int i = 0; i < len; i++)
        {
            if (s[i] >= 'A' && s[i] <= 'Z')
                s[i] = s[i] - 'A' + 'a';
        }

        int alpha[26] = { 0 };
        for (int i = 0; i < len; i++)
        {
            alpha[s[i] - 'a']++;
        }

        int max = 0, pos = 0;
        for (int i = 0; i < 26; i++)
        {
            if (max < alpha[i])
            {
                max = alpha[i];
                pos = i;
            }
        }

        int cnt = 0;
        for (int i = 0; i < 26; i++)
        {
            if (alpha[i] == max) cnt++;
        }

        if (cnt > 1) printf("?");
        else
        {
            printf("%c", pos + 'A');
        }
    }
    ```

- !밀비 급일
    - 서식문자 "%[^\n]"를 이용해서 한 줄을 전부 입력받습니다. 그다음 문자열을 거꾸로 순회하면서 출력해주면 됩니다. 또는 배열 뒤집기를 쓸 수도 있습니다.
    - getchar를 해주는 것을 잊지 말아야 합니다.
    ```c
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char S[502];
        while (1)
        {
            scanf(" %[^\n]", S);
            if (S[0] == 'E'&&S[1] == 'N'&&S[2] == 'D') return 0;
            int len = strlen(S);

            for (int i = 0; i < len / 2; i++)
            {
                char temp = S[i];
                S[i] = S[len - i - 1];
                S[len - i - 1] = temp;
            }
            printf("%s\n", S);
        }
    }
    ```
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        char s[502];
        while (1)
        {
            scanf(" %[^\n]", s);
            if (s[0] == 'E' && s[1] == 'N' && s[2] == 'D') return 0;
            int len = strlen(s);

            for (int i = len - 1; i >= 0; i--)
            {
                printf("%c", s[i]);
            }
            printf("\n");
        }
    }
    ```

- 팰린드롬
    - 서식문자 "%[^\n]"를 이용해서 한 줄을 전부 입력받습니다. 반복문을 통해 문자열의 앞과 뒤가 계속해서 일치하는지 검사하면 됩니다. 대소문자를 구분하지 않기 때문에 대문자는 소문자로 바꿔주거나 소문자를 대문자로 바꿔줍시다.
    - 주의할 점은 scanf("%d")를 쓸 때도 버퍼에 줄바꿈이 남기 때문에 getchar를 써줘야 합니다.
    ```c
    #include <stdio.h>
    #include <string.h>
    int main()
    {
        int t;
        char s[101];
        scanf("%d", &t);
        getchar();
        while (t--)
        {
            scanf("%[^\n]", s);
            getchar();
            int len = strlen(s);

            for (int i = 0; i < len; i++)
            {
                if (s[i] >= 'A' && s[i] <= 'Z') s[i] = s[i] - 'A' + 'a';
            }

            bool flag = 1;
            for (int i = 0; i < len / 2; i++)
            {
                if (s[i] != s[len - i - 1])
                {
                    printf("No\n");
                    flag = 0;
                    break;
                }
            }
            if (flag) printf("Yes\n");
        }
    }
    ```