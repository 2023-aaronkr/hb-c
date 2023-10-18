---
layout: page
title: Midterm Guide / 중간고사 가이드
permalink: /midterm/
---

{:toc}

---

<style>
table {
  border: 1px solid gainsboro;
  border-bottom: none;
  border-collapse: collapse;
  min-width: 80%;
}
th, td {
  border-bottom: 1px solid gainsboro;
  padding: 10px;
}
th {
  background-color: lightslategray;
  color: white;
}
td:first-child {
  background-color: whitesmoke;
}
</style>

1. [C 시작하기](#1-c-시작하기)
2. [개체와 함수, 형식](#2-개체와-함수-형식)
3. [산술 형식](#3-산술-형식)
4. [식과 연산자](#4-식과-연산자)
5. [흐름 제어](#5-흐름-제어)

---

### 1. C 시작하기

C는 1970년대에 시스템 프로그래밍 언어로 개발되었다.

- 1960: ALGOL 60 - International Algorithmic Language
- 1967: BCPL (Basic Combined Programming Language) - Martin Richards
- 1969: B - Ken Thompson
- 1972: C - Dennis Ritchie
- 1978: K&R C - Brian Kernighan, Dennis Ritchie
- 1989: ANSI C - American National Standards Institute
- 1990: ISO C - International Organization for Standardization
- 1999: `C99` - ISO C
- 2011: `C11` - ISO C
- 2018: `C17` - ISO C
- 2022: `C2x` - ISO C
- 2024: `C23` - ISO C

C 프로그래밍 언어의 인기는C의 정신spirit of C 이라고 하는 다음과 같은 언어의 여러 신조에서 기인했올 가능성이 크다.

1. **신뢰:** 프로그래머를 신뢰해야 한다.
2. **해제:** 프로그래머가 해야 할 일을 하지 못하도록 막으면 안 된다.
3. **간간한:** C 언어를 작고 간단하게 유지해야 한다.
4. **보존:** 연산 수행은 한 가지 방법만 제공해야 한다.
5. **빠른:** 이식성이 보장되지 않더라도 코드가 빠르게 동작하도록 만들어야 한다.

#### 첫 번째 C 프로그램 개발하기

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    puts("Hello, world!\n");
    // printf("%s\n", "Hello, world!\n");
    return EXIT_SUCCESS;
}
```

- puts 함수는 stdout에 문자열을 쓰는 간단한 함수입니다.
- printf 함수를 사용해 형식화된 출력formatted output을 인쇄해야 한다.

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    printf("%s %d %c %f\n", "Hello, world!", 42, 'a', 3.14);
    return EXIT_SUCCESS;
}
```

#### C 프로그램 개발하기 및 컴파일러 사용하기

1. C 프로그램을 작성하려면 소스 파일이라고 하는 C 언어 텍스트 파일을 만들고 편집해야 합니다. 프로그램이 C로 작성되면 기계가 읽을 수 있는 언어로 번역될 준비가 됩니다.
2. 컴파일러는 C 명령문을 기계 명령문으로 변환합니다. 우리가 사용하는 컴파일러는 **`GCC`(GNU Compiler Collection)** 라고 하며 C, C++, Objective-C 및 기타 언어에 대한 프런트엔드를 포함합니다.
3. 컴파일러는 소스 코드와 최종 실행 코드 사이의 중간 단계인 목적 코드를 생성합니다. 링커는 목적 코드를 실행 가능한 실행 파일로 결합합니다.

4. **소스 파일 (`*.c`) :** C언어 문법을 사용해서 작성한 파일
5. **목적 파일 (`*.obj`) :** 컴파일러(번역기)가 번역(컴파일) 한 파일
6. **실행 파일 (`*.exe`) :** 컴퓨터에서 실행할 수 있는 파일

[목차로 돌아가기](#midterm-guide--중간고사-가이드)

---

### 2. 개체와 함수, 형식

#### 메모리와 비트 그리고 바이트

메모리의 최소 저장 단위는 비트입니다.

1. 1비트는 `0` 또는 `1`을 저장할 수 있는 공간입니다.
2. 2비트는 각 비트에 `0`, `1` 중 한 개를 저장할 수 있으니 `00`, `01`, `10`, `11`입니다. 2진수라고 합니다.
3. 3비트는 `000`, `001`, `010`, `011`, `100`, `101`, `110`, `111`입니다. 10진수로 바꿔 보면 `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`까지 입니다.

- 1비트bit는 숫자 2개(`0~1`) 중 하나,
- 2비트는 숫자 4개(`0~3`) 중 하나,
- 3비트는 숫자 8개(`0~7`) 중 하나…

비트가 8개 모이면 새로운 단위를 사용하며 이것을 **바이트byte**라고 합니다.

- 부호를 고려하는 1바이트에서 각 비트의 값이 `01111111`이라면 127입니다 (양수).
- 또 1바이트의 각 비트 값이 `10000000` 이라면 -128입니다 (음수).

**자료형**

|        자료형        |  크기   |   비트의 수    |                          범위                          |
| :------------------: | :-----: | :------------: | :----------------------------------------------------: |
|        `char`        | 1바이트 | 2<sup>8</sup>  |                       -128 ~ 127                       |
|   `unsigned char`    | 1바이트 | 2<sup>8</sup>  |                        0 ~ 255                         |
|       `short`        | 2바이트 | 2<sup>16</sup> |                    -32,768 ~ 32,767                    |
|   `unsigned short`   | 2바이트 | 2<sup>16</sup> |                       0 ~ 65,535                       |
|        `int`         | 4바이트 | 2<sup>32</sup> |             -2,147,483,648 ~ 2,147,483,647             |
|    `unsigned int`    | 4바이트 | 2<sup>32</sup> |                   0 ~ 4,294,967,295                    |
|        `long`        | 4바이트 | 2<sup>32</sup> |             -2,147,483,648 ~ 2,147,483,647             |
|   `unsigned long`    | 4바이트 | 2<sup>32</sup> |                   0 ~ 4,294,967,295                    |
|     `long long`      | 8바이트 | 2<sup>64</sup> | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| `unsigned long long` | 8바이트 | 2<sup>64</sup> |             0 ~ 18,446,744,073,709,551,615             |

#### 개체와 함수, 형식, 그리고 포인터

C의 모든 형식은 개체형(object type)이거나
함수형(function type)이라는 것이다.

- **개체object** 는 값을 표현할 수 있는 스토리지storage다.
- **변수variable**에는 해당 값이 나타내는 개체의 종류를 알려주도록 형식type을 선언 해야 한다.
- **함수function**는 개체가 아니지만, 형식을 갖는다.

함수형function type은 반환형return type뿐만 아니라 함수의 매개변수 개수 및 유형을 갖는다.

#### 범위

- **지역 범위 (local scope)** : 함수 내에서 선언된 개체
- **블록 범위 (block scope)** : 중괄호로 묶인 블록 내에서 선언된 개체
- **함수 범위 (function scope)** : 함수 내에서 선언된 개체
- **파일 범위 (file scope)** : 함수 외부에서 선언된 개체
- **전역 범위 (global scope)** : 파일 범위에서 선언된 개체

#### 개체 형식

**부율 형식 (0과 1만) :** `_Bool`로 선언한 개체는 0과 1만 저장할 수 있다. `bool`을 사용하면 `<stdbool.h>`를 포함해야 한다.

```c
#include <stdbool.h>
bool b = true;
```

**문자 형식 :** `char`, `signed char`, `unsigned char`

```c
char c = 'a';
signed char sc = 'b';
unsigned char uc = 'c';
```

**숫자 형식 (정수 형식) :** `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long`, `long long`, `unsigned long long`

```c
short s = 1;
unsigned short us = 2;
int i = 3;
unsigned int ui = 4;
long l = 5;
unsigned long ul = 6;
long long ll = 7;
unsigned long long ull = 8;
```

**숫자 형식 (부동 소수점 형식) :** `float`, `double`, `long double` (실수 형식)

```c
float f = 3.14;
double d = 3.141592;
long double ld = 3.1415926535897932384626433832795028841971693993751058209749445923078164062862089986280348253421170679;
```

**숫자 형식 (열기형) :** `enum`으로 선언한 개체는 정수 형식의 값을 저장할 수 있다.

```c
enum { RED, GREEN, BLUE };
```

**void 형식**

조금 색다른 데이터 형식이다. 키워드 void는 (그 자체로) “어떤 값도 가질 수 없다”는 것을 의미한다.

**함수 형식**

**함수 형식function type**은 **파생된 형식derived type**이다.

이 경우 형식은 반환 형식return type과 함수 매개변수의 개수와 형식을 따른다.

함수의 반환 형식은 배열 형식이 될 수는 없다.

```c
int func(int, int);
```

#### 파생된 형식

**포인터 형식pointer type**

참조된 형식reference type이라고 하는 포인터가 가리키는 함수나 개체 형식에서 파생된 것이다. `&` 연산자를 사용해 개체나 함수의 주소를 가져올 수 있다.

```c
int i = 42;
int *pi = &i;
```

**배열 형식array type**

배열의 크기와 배열 요소의 형식에서 파생된 것이다. 배열array은 연속해서 모두 같은 요소 형식element type으로 할당된 개체의 시퀀스sequence다. 대괄호([ ])를 사용해 배열의 요소를 식별한다.

str이 배열 개체일 때 식 번호는 0부터 시작한다. `str[0]`은 배열의 첫 번째 요소를 가리킨다. 다차원 배열multi-dimensional array을 선언 할 수도 있다. `str[0][0]`은 2차원 배열의 첫 번째 요소를 가리킨다.

```c
char str[4] = { 'a', 'b', 'c', 'd' };
char str[6] = "abcde";
char str[2][3] = { "ab", "cd" };
```

**구조체 형식`struct` type**

구조체 멤버의 형식에서 파생된 것이다. 구조체structure type struct에는 순차적으로 할당된 멤버 개체member object가 있다.

구조체는 관련 개체의 집합을 선언하는 데 유용하며 날짜나 고객 또는 인사 기록과 같은 것을 나타내는 데 사용할 수 있다.

구조체를 정의하고 나면 구조체의 멤버를 참조해야 한다. 구조체 개체의 멤버는 구조체 멤버 연산자 (.)를 사용해 참조할 수 있다.

구조체에 대한 포인터를 사용하면 -> 연산자로 구조체 멤버를 참조할 수 있다.

```c
struct date {
    int month;
    int day;
    int year;
};

struct date today;
today.month = 9;
today.day = 25;
today.year = 2021;
```

**공용체 형식`union` type**

공용체 멤버의 형식에서 파생된 것이다.

공용체union type는 멤버 개체가 사용하는 메모리가 겹친다는 점을 제외하고는 구조체와 비슷하다.

공용체는 주로 메모리를 절약하기 위해 사용된다.

- 구조체와 마찬가지로 (.) 연산자를 사용해 공용체 멤버에 접근할 수 있다.
- 공용체에 대한 포인터를 사용하면 -> 연산자로 공용체 멤버를 참조할 수 있다.

```c
union {
    int i;
    float f;
} u;

u.i = 42;
printf("%d\n", u.i);

u.f = 3.14;
printf("%f\n", u.f);
```

#### 태그

태그tag는 구조체와 공용체, 열거형에 이름을 부여하는 특별한 메커니즘이다.

태그 자체는 형식의 이름이 아니며 변수를 선언하는 데 사용할 수 없다.

```c
struct date {
    int month;
    int day;
    int year;
} today;
```

#### 형식 한정자

- `const` : 개체를 수정할 수 없다는 것을 나타낸다.
- `volatile` : 개체가 예기치 않게 변경될 수 있음을 나타낸다.
- `restrict` : 개체에 대한 포인터가 개체를 참조하는 유일한 포인터임을 나타낸다.

[목차로 돌아가기](#midterm-guide--중간고사-가이드)

---

### 3. 산술 형식

#### 정수

정수 형식은 유한 범위의 정수를 표현한다.

- 부호 있는 정수 형식 (`signed`)
- 부호 없는 정수 (`unsigned`)

모든 정수 형식은 다음과 같은 세 가지 속성을 갖는다.

- **비트 수** : 정수 형식에 저장할 수 있는 비트 수
- **최소 범위** : 정수 형식에 저장할 수 있는 최소 값
- **최대 범위** : 정수 형식에 저장할 수 있는 최대 값.

그리고 정수의 값과 표현 방식에 따라 다음과 같은 두 가지 속성을 갖는다.

- **값** : 개체에 저장된 일반 수학적인 값
- **표현** : 체 값은 개체에 할당된 스토리지의 비트에 있는 값을 특정 인코딩
- **패딩** : 정수 형식의 비트 수가 정확히 정수의 비트 수와 일치하지 않는 경우
- **정밀도** : 정수 형식의 비트 수가 정수의 비트 수와 일치하는 경우
- **너비** : 정수 형식의 비트 수

```c
#include<stdio.h>

int main(void) {
  double Pi = 3.141592653589793238;
  printf("|%-lf|\n", Pi);
  printf("|%lf|\n", Pi); // default width
  printf("|%30lf|\n", Pi); // width 30 rt
  printf("|l%-30lf|\n", Pi); //width 30 lf
  printf("|%030.10f|\n", Pi); // width 30 precision 10 right justify. Filling blank space with '0'.
  printf("|%-6.3f|\n", Pi);
  printf("|%-0.15f|\n", Pi);
  printf("|%-030.15f|\n", Pi);
}

```

- **부호가 없는 정수** (`unsigned`)
  - 최소 범위 : 0
  - 최대 범위 : 최대값은 2<sup>비트 수</sup> - 1이다.
- **부호가 있는 정수** (`signed`)
  - 최소 범위 : 최소값은 -2<sup>비트 수 - 1</sup>이다.
  - 최대 범위 : 최대값은 2<sup>비트 수 - 1</sup> - 1이다.

`<limits.h>` 헤더 파일에서 정수 형식의 최소 및 최대 범위를 확인할 수 있다.

```c
#include <limits.h>
#include <stdio.h>

int main(void) {
    printf("CHAR_BIT: %d\n", CHAR_BIT);
    printf("CHAR_MAX: %d\n", CHAR_MAX);
    printf("CHAR_MIN: %d\n", CHAR_MIN);
    printf("INT_MAX: %d\n", INT_MAX);
    printf("INT_MIN: %d\n", INT_MIN);
    printf("LONG_MAX: %ld\n", (long) LONG_MAX);
    printf("LONG_MIN: %ld\n", (long) LONG_MIN);
    printf("SCHAR_MAX: %d\n", SCHAR_MAX);
    printf("SCHAR_MIN: %d\n", SCHAR_MIN);
    printf("SHRT_MAX: %d\n", SHRT_MAX);
    printf("SHRT_MIN: %d\n", SHRT_MIN);
    printf("UCHAR_MAX: %d\n", UCHAR_MAX);
    printf("UINT_MAX: %u\n", (unsigned int) UINT_MAX);
    printf("ULONG_MAX: %lu\n", (unsigned long) ULONG_MAX);
    printf("USHRT_MAX: %d\n", (unsigned short) USHRT_MAX);
    return 0;
}
```

#### 부호가 있는 정수

부호가 있는 정수 형식을 표현하는 것은 부호가 없는 정수를 표현하는 것보다 더 복잡하다.

- **부호와 크기** : 부호 있는 정수 형식은 부호와 크기를 나타내는 데 사용하는 비트를 포함한다.
- **1의 보수** : 부호 있는 정수 형식은 1의 보수를 사용해 음수를 나타낸다.
- **2의 보수** : 부호 있는 정수 형식은 2의 보수를 사용해 음수를 나타낸다.

1의 보수는 2진수의 비트를 반전시키는 것이다. 2의 보수는 비트를 반전시킨 다음 1을 더하는 것이다.

- 2진수: `11001010`
- 1의 보수: `00110101`
- 2의 보수: `00110110` = `00110101` + 1

---

#### 랩 어라운드 (wrap around) vs 오버플로우 (overflow)

**랩 어라운드wrap around**는 **부호 _없는_ 정수** 형식의 최대 범위를 초과하는 것이다.

- 부호 없는 정수 형식의 최대 범위를 초과하면 0부터 다시 시작한다.

유명한 랩 어라운드 예제는 ["강남스타일 INT_MAX 오버플로, YouTube를 64비트로 강제 전환"](https://arstechnica.com/information-technology/2014/12/gangnam-style-overflows-int_max-forces-youtube-to-go-64-bit/)이다.

**오버플로우overflow**는 **부호 _있는_ 정수** 형식의 최대 범위를 초과하는 것이다.

- 부호 없는 정수 형식의 최대 범위를 초과하면 0부터 다시 시작한다.
- 부호 있는 정수 형식의 최대 범위를 초과하면 최소값부터 다시 시작한다.

The difference between wrap around and overflow in C is that wrap around is a feature of unsigned integer types, while overflow is a feature of signed integer types.

랩 어라운드와 오버플로우의 차이점은 랩 어라운드는 부호 없는 정수 형식의 특징이고 오버플로우는 부호 있는 정수 형식의 특징이다.

```c
#include <stdio.h>

int main(void) {
    unsigned char c = 0;
    while (c >= 0) {
        printf("%d\n", c);
        c++;
    }
    return 0;
}

/* 출력:
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 ... 255 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 ... 255 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 ... 255 ...
*/
```

#### 3.2. 부동 소수점

- 부동 소수점 형식
- 부동 소수점 산술
- 부동 소수점 값
- 부동 소수점 상수

#### 3.3. 정수와 부동 소수점 형식

- 정수 변환 순위
- 정수 확장
- 일반 산술 변환
- 암시적 변환의 예
- 안전한 변환

[목차로 돌아가기](#midterm-guide--중간고사-가이드)

---

### 4. 식과 연산자

#### 4.1. 단순 할당

#### 4.2. 평가

#### 4.3. 함수 호출

#### 4.4. 증가 및 감소 연산자

#### 4.5. 연산자 우선순위 및 결합성

#### 4.6. 평가 순서

- 비순차적 평가와 규정되지 않은 순차적 평가
- 시퀀스 포인트

#### 4.7. sizeof 연산자

#### 4.8. 산술 연산자

- 단항 연산자 + 와 -
- 논리 부정 연산자 !
- 곱하기 연산자 \* / %
- 더하기 연산자 + -

#### 4.9. 비트 연산자

- 보수 연산자 ~
- 시프트 연산자 << >>
- 비트 AND 연산자 &
- 비트 XOR 연산자 ^ (배타적 OR)
- 비트 OR 연산자 | (포과적 OR)

#### 4.10. 논리 연산자

#### 4.11. 형 변환 연산자

#### 4.12. 조건부 연산자

#### 4.13. \_Alignof 연산자

#### 4.14. 관계형 연산자

#### 4.15. 복합 할당 연산자

#### 4.16. 쉼표 연산자

#### 4.17. 포인터 산술

[목차로 돌아가기](#midterm-guide--중간고사-가이드)

---

### 5. 흐름 제어

#### 5.1. 식문

#### 5.2. 복합문

#### 5.3. 선택문

- if 문
- switch 문

#### 5.4. 반복문

- while 문
- do...while 문
- for 문

#### 5.5. 점프문

- goto 문
- continue 문
- break 문
- return 문

[목차로 돌아가기](#midterm-guide--중간고사-가이드)
