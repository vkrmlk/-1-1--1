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

3 лб 8 задача 
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <cstdio>

int main()
{
    setlocale(LC_ALL, "Russian");
    int n, i; // количество точек и счетчик цикла
    int k1, k2, k3, k4;  // количество точек в 1-м, 2-м и обоих прямоугольниках
    double x, y;  // координаты точки
    double plx1, ply1, plx2, ply2; // Координаты первого прямоугольника
    double plx2_1, ply2_1, plx2_2, ply2_2;// Координаты второго прямоугольника
    bool pr1, pr2,pr3;  // логические переменные
    printf("Введите число точек: ");
    scanf_s("%d", &n);
    printf("1-й прямоугольник\n");
    printf("Координаты левого нижнего угла: ");
    scanf_s("%lf %lf", &plx1, &ply1);
    printf("Координаты правого верхнего угла: ");
    scanf_s("%lf %lf", &plx2, &ply2);
    printf("2-й прямоугольник\n");
    printf("Координаты левого нижнего угла: ");
    scanf_s("%lf %lf", &plx2_1, &ply2_1);
    printf("Координаты правого верхнего угла: ");
    scanf_s("%lf %lf", &plx2_2, &ply2_2);
    k1 = 0;
    k2 = 0;// Начальное количество точек
    k3 = 0;
    k4 = 0;
    for (i = 1; i <= n; i++) {  // Цикл на n точек
        printf("Координаты %d-й точки: ", i);
        scanf_s("%lf %lf", &x, &y);
        // Его стороны параллельны
        pr1 = (x > plx1) && (x < plx2) &&  // Проверяем принадлежность первому прямоугольнику
            (y > ply1) && (y < ply2);
        pr2 = (x > plx2_1) && (x < plx2_2) && // Проверяем принадлежность второму прямоугольнику
            (y > ply2_1) && (y < ply2_2);
        pr3 = !pr1 && !pr2;
        if (pr1 && pr2) // Если точка принадлежит обоим прямоугольникам
            k3++;

        else {
            if (pr1) // Если только первому
                k1++;
            if (pr2)// Если только второму
                k2++;
            else { 
                if (pr3) //неодному 
                    k4++;

            }
        }
    }
    printf("\n1-й прямоугольник: %d\n", k1);
    printf("2-й прямоугольник: %d\n", k2);
    printf("Оба прямоугольника: %d\n", k3);
    printf("Не принадлежит прямоугольникам: %d\n", k4);

    return 0;
}

2 лб 7 задача 
#include <stdio.h>
#include <math.h>
int main(void)
 {

    int N;
    scanf_s("%d", &N);

    int bestP = 1;
    int bestQ = 1;
    int minDiff = N - 2;


    int limit = (int)sqrt(N) + 1;
    do {
        printf("Введите начальную положительное число N в диапозоне (1,1000000): ");
    } while (N >= 1000000 && N>0);
    int P, Q;

    for (P = 1; P <= limit; P++)
    {
        for (Q = P; Q <= limit; Q++)
        {
            int sum = P * P + Q * Q;
            int diff = sum - N;

            if (diff < 0)
                diff = -diff;

            if (diff < minDiff)
            {
                minDiff = diff;
                bestP = P;
                bestQ = Q;
            }

            // Если сумма уже слишком большая,
            // при дальнейшем увеличении Q она будет только расти.
            if (sum > N && Q > P)
                break;
        }
    }

        printf("%d %d\n", bestP, bestQ);

        return 0;
    }

    2 лб 6 задача 
    #include <iostream>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    setlocale(LC_ALL, "Russian"); //  включает поддержку русской локали в консоли.
    int start; //  нач сумма в копейках 
    int hod = 0;
    int max = 0; //сумма
    int first_hod = 0; // номер хода, когда впервые появился макс
    int sum;
    do {
        printf("Введите начальную положительную сумму в копейках в диапазоне (0..9999): ");
        if (scanf_s("%d", &start) != 1) { // проверка что ввод= число 
            start = -1; // повторить ввод
        }
    } while (start < 0 || start >= 10000); // проверка что ввод= число в диапазоне 0..9999
    sum = start; // сумму = нач сумме 
    max = sum;
    if (sum >= 29) {
        do {
            hod++;
            sum -= 29;
            sum = (sum % 100) * 100 + (sum / 100); // перестановка копеек и рублей
            if (sum > max) {
                max = sum;
                first_hod = hod;
            }
        } while (sum >= 29 && sum != start); // продолжаем, пока хватает на ход и не вернулись к началу
    }
    printf("%d - %d - %d\n", start, max, first_hod);
    return 0;
}

2 лб 5 задача

int main()
{
	int h = 2;
	int m = 43 ;
	float a = fabs(30 * (h % 12) + 0.5 * m - 6 * m);
	a = a > 180 ? 360 - a : a;
	printf("%.1f", a);
4 лб 8 задача 


#include <iostream>
#define _CRT_SECURE_NO_WARNINGS
#include <cstdio>

int main()  
{
    double S, sum;
    int n;
    setlocale(LC_ALL, "Russian");
    
    do {
        printf("Введите S (> 1): ");
        scanf_s("%lf", &S);
    } while (S <= 1);
    // 1. Цикл for параментр 
    sum = 0;
    n = 0;
    for (int i = 0;sum <= S; i++) {
        sum += (double)(2 * i + 1) / (2 * i + 2);
        n++;
    }
    printf("for : %d элементов\n", n);
    // 2. Цикл do while
    sum = 0;
    n = 0;
    do {
        sum += (double)(2 * n + 1) / (2 * n + 2);
        n++;
    } while (sum <= S);
    printf("do while: %d элементов\n", n);
    // 3. Цикл while
    sum = 0;
    n = 0;
    while (sum <= S) {
        sum += (double)(2 * n + 1) / (2 * n + 2);
        n++;
    }
    printf("while: %d элементов\n", n);
    return 0;;
}
