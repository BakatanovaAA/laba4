#   Работа 5
## Вариант 1
## Код
```c
#define _CRT_SECURE_NO_DEPRECATE
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#define M_PI 3.14159265358979323846

double sin_deg(double gr);
double calc_a(double x);
double calc_b(double a, double x, double c);
double calc_y(double x, double b);
int check_usl1(int A, int B);
int check_usl2(int A, int B, int C);

int main()
{
    double gr, res;
    double x, y, a, b;
    double c = 0.4;
    int A, B, C;
    int usl1, usl2;

    setlocale(LC_ALL, "RUS");

    /* Задание 1 */
    puts("Введите угол в градусах");
    scanf("%lf", &gr);

    res = sin_deg(gr);

    printf("sin(%.0f град) = %.6f\n", gr, res);

    /* Задания 2 и 3 */
    puts("Введите x");
    scanf("%lf", &x);

    a = calc_a(x);
    b = calc_b(a, x, c);
    y = calc_y(x, b);

    printf("x = %.1f, y = %.2f\n", x, y);

    A = (int)a;
    B = (int)b;
    C = (int)y;

    usl1 = check_usl1(A, B);
    usl2 = check_usl2(A, B, C);

    printf("Только одно из чисел A и B четное, условие выполнено (1 - да, 0 - нет): %d\n", usl1);
    printf("Каждое из чисел A, B, C кратно трем, условие выполнено (1 - да, 0 - нет): %d\n", usl2);

    system("pause");
    return 0;
}

double sin_deg(double gr)
{
    double res;
    res = sin(gr * M_PI / 180);
    return res;
}

double calc_a(double x)
{
    double a;
    a = log10(x);
    return a;
}

double calc_b(double a, double x, double c)
{
    double b;
    b = a * a + sqrt(c * x);
    return b;
}

double calc_y(double x, double b)
{
    double y;
    y = exp(2 * x) + pow(9.7, b);
    return y;
}

int check_usl1(int A, int B)
{
    int usl1;
    usl1 = (A % 2 == 0) != (B % 2 == 0);
    return usl1;
}

int check_usl2(int A, int B, int C)
{
    int usl2;
    usl2 = (A % 3 == 0) && (B % 3 == 0) && (C % 3 == 0);
    return usl2;
}
```
## Результат
задание 1
```
Введите угол в градусах
30
sin(30 град) = 0,500000
Введите угол в градусах
60
sin(60 град) = 0,866025
Введите угол в градусах
90
sin(90 град) = 1,000000
```
задание 2 и 3 
```
Введите x
3,5
x = 3,5, y = 1125,45 
Только одно из чисел A и B четное, условие выполнено (1 - да, 0 - нет): 1
Каждое из чисел A, B, C кратно трем, условие выполнено (1 - да, 0 - нет): 0
```
значение `y` совпадает с контр. примером
## Выполнила
Бакатанова Алла бИД-261 пдг2
