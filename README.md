20 задача из 3 лабы
#include <iostream>
#define _CRT_SECURE_NO_WARNINGS

#include <cstdio>
int main()
{
    setlocale(LC_ALL, "Russian");
    int N, k = 0;
    double x1, y1, x2, y2;
    printf("Введите положительное количество отрезков: ");
    scanf_s("%d", &N);
    do {
        printf("Введите положительное количество отрезков: ");
        scanf_s("%d", &N);
    } while (N <= 0);
    for (int i = 1; i <= N; i++) {
        printf("Введите координаты концов %d-го отрезка: ", i);
        scanf_s("%lf %lf %lf %lf", &x1, &y1, &x2, &y2);
        if (x1 * x2 > 0 && y1 * y2 > 0) { // Отрезок не имеет общих точек с осями
            k++;
        }
    }
    printf("Ответ: %d отрезков\n", k);
    return 0; 
}
