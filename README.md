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
4 лб 20 задача 
#include <iostream>
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS

int main()
{
    setlocale(LC_ALL, "Russian");
    long long k; //большие цел числа
    do {
        printf("Введите положительное число К (К<=10^9):");
        if (scanf_s("%lld", &k) != 1)
            return 0;
        if (k < 1)
            printf("число не положительное!");
    } while (k < 1);
    // while 
    long long k1 = k;
    printf("Резульат через while :");
    while (k1 > 0) {
        int digit = k1 % 10; // последняя цифра числа 
        printf("%d", digit);
        k1 /= 10;
    }
    printf("\n");
    // do while 
    long long k2 = k;
    printf("Резульат через do while :");
    do {
        int digit = k2 % 10; // последняя цифра числа 
        printf("%d", digit);
        k2 /= 10;
    } while (k2 > 0);
    printf("\n");
    // for 
    long long k3 = k;
    printf("Резульат через for :");
    for (;k3 > 0;k3 /= 10) {
        printf("%lld", k3 % 10);
    }
    printf("\n");
    return 0;
}

5 лб 8 задача 
#include <iostream>
#include <iostream>
#include <cstdio>
#include <clocale>
#include <cstdlib>
#include <ctime>
#include <algorithm>

using namespace std;

const int NMAX = 10;

int main()
{
    setlocale(LC_ALL, "Russian");
    srand(time(0));
    int N;
    double a[NMAX], b[NMAX];
    int k = 0;
    do {
        printf("Введите количество элементов массива (от 1 до %d): ", NMAX);
        if (scanf_s("%d", &N) != 1) {
            printf("Ошибка ввода!\n");
            return 1;
        }
        if (N < 1 || N > NMAX) {
            printf("Введите число от 1 до %d!\n", NMAX);
        }

    } while (N < 1 || N > NMAX);
    printf("\nИсходный массив:\n");
    for (int i = 0; i < N; i++) {
        a[i] = 1.0 + (rand() / (RAND_MAX + 1.0)) * 9.0;
        printf("%.2f ", a[i]);
        double fractional = a[i] - (int)a[i];
        if (fractional < 0.5) {
            b[k] = a[i];
            k++;
        }
    }
    for (int i = 0; i < k - 1; i++) { // сортировка по возрастанию 
        for (int j = 0; j < k - i - 1; j++) {
            if (b[j] > b[j + 1]) {
                double temp = b[j];
                b[j] = b[j + 1];
                b[j + 1] = temp;
            }
        }
    }
    printf("\n\nЭлементы с дробной частью меньше 0.5 "
        "в порядке возрастания:\n");
    if (k == 0) {
        printf("Таких элементов нет.\n");
    }
    for (int i = 0; i < k; i++) {
        printf("%.2f ", b[i]);
    }
    printf("\n");
    return 0;
}
5 лб 20 
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <math.h>
#include <locale.h>
int main()
{
    setlocale(LC_ALL, "Russian");
    srand(time(NULL));
    const int MAX = 100;
    double a[MAX];
    int N;
    double sum = 0;
    printf("Введите количество чисел в массиве (от 1 до 100): ");
    scanf_s("%d", &N);
    while (N < 1 || N > MAX)
    {
        printf("Ошибка! Введите количество от 1 до 100: ");
        scanf_s("%d", &N);
    }
    printf("\nМассив:\n");
    for (int i = 0; i < N; i++)
    {
        a[i] = 3.0 + (rand() / (double)RAND_MAX)* 7.0 ;
        printf("%.2f ", a[i]);
        sum += a[i];
    }
	     double sr = sum / N; //среднее арифметическое
    int minIndex = 0; //ближайшее число
    for (int i = 1; i < N; i++)
    {
        if (fabs(a[i] - sr) < fabs(a[minIndex] - sr))
        {
            minIndex = i;
        }
    }
    printf("\n\nСреднее арифметическое: %.2f\n", sr);
    printf("Ближайшее число: %.2f\n", a[minIndex]);
    printf("Номер числа: %d\n", minIndex + 1);

    return 0;
}
6 лб 8 задача 
#include <iostream>
#include <stdio.h>
#include <locale.h>
const int ISLANDS = 4;
const int MONTHS = 12;
int FindMax(double temperature[4][12], int month) // нахождение максимальной температуры
{
    int maxIndex = 0;
    for (int i = 1; i < ISLANDS; i++)
    {
        if (temperature[i][month] > temperature[maxIndex][month])
        {
            maxIndex = i;
        }
    }
    return maxIndex;
}
int main()
{
    setlocale(LC_ALL, "Russian");
    srand((unsigned int)time(NULL));
    char islands[4][20] =
    {
        "Куба",
        "Тринидад",
        "Ямайка",
        "Гаити"
    };
    double temperature[4][12];
    for (int i = 0; i < ISLANDS; i++) // температуры
    {
        for (int j = 0; j < MONTHS; j++)
        {
            temperature[i][j] = 20 + ( rand() % 160 ) / 10.0;
        }
    }
    printf("Таблица среднемесячных температур:\n\n"); // таблица температур
    printf("%-12s", "Остров");
    for (int j = 0; j < MONTHS; j++)
    {
        printf("%5d", j + 1);
    }
    printf("\n");
    for (int i = 0; i < ISLANDS; i++)
    {
        printf("%-12s", islands[i]);
        for (int j = 0; j < MONTHS; j++)
        {
            printf("%5.1f", temperature[i][j]);
        }
        printf("\n");
    }
    printf("\nМаксимальная температура по месяцам:\n\n");//  максимальная температура каждого месяца
    for (int j = 0; j < MONTHS; j++)
    {
        int maxIndex = FindMax(temperature, j);
        printf("Месяц %2d: %-12s %.1f градусов\n",
            j + 1,
            islands[maxIndex],
            temperature[maxIndex][j]);
    }
    return 0;
}
6 лб 20 задача 
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <ctime>
const int N = 3;
const int M = 5;


int main()

{
    setlocale(LC_ALL, "Russian");
    int a[N][M];
    srand((unsigned int)time(0));
    for (int i = 0; i < N; i++) { // Заполнение массива 
        for (int j = 0; j < M; j++) {
            a[i][j] = rand() % 100 + 1;
        }
    }
    printf("                            пробег \n\n");
    printf("%-15s", "номер машины");
    for (int j = 0; j < M; j++) {
        printf("%7d", j + 1);
    }
    printf("\n");
    for (int i = 0; i < N; i++) { // Вывод массива
        printf("%-15d", i + 1);
        for (int j = 0; j < M; j++) {
            printf("%7d", a[i][j]);
        }
        printf("\n");
    }
    int maxSum = 0;
    int maxCar = 0;
    for (int i = 0; i < N; i++) { // поиск макс пробега 
        int sum = 0;
        for (int j = 0; j < M; j++) {
            sum += a[i][j];
        }

        if (sum > maxSum) {
            maxSum = sum;
            maxCar = i;
        }
    }
    printf("\nАвтомобиль с максимальным пробегом: %d\n", maxCar + 1);
    printf("Максимальный пробег: %d\n", maxSum);
    return 0;
}
7 ЛБ 
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <windows.h>

const int MAX_STUDENTS = 100;
const int MIN_YEAR = 1970;
const int MAX_YEAR = 2010;

const int MIN_MARK = 2;
const int MAX_MARK = 5;
const int BAD_MARK = 2;
char subjects[5][20] = { "физика","химия","информ","матем","история" };
struct Date {
    unsigned char day;
    unsigned char month;
    int year;
};
struct Student {
    char surname[50];
    char name[50];
    char patronymic[50];
    Date birth;

    int count;
    int data[5][2];
};

bool isLeap(int year) { //логический проверка на весокосный год
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}

int daysInMonth(int month, int year) { //  сколько дней в месяце проверка
    if (month == 2) {
        if (isLeap(year)) return 29;
        return 28;
    }
    if (month == 4 || month == 6 || month == 9 || month == 11) return 30;
    return 31;
}
int getMark(Student s, int code) { // найти оценку по коду предмета 
    for (int k = 0; k < s.count; k++) {
        if (s.data[k][0] == code)
            return s.data[k][1];
    }
    return 0;
}

int isUsed(Student s, int k, int code) { // проверка был ли введен код предмента 
    for (int j = 0; j < k; j++) {
        if (s.data[j][0] == code) return 1;
    }
    return 0;
}

void printHeader() { // шабка таблицы 
    printf("%-15s%-15s%-15s%-12s%s\n", "Фамилия", "Имя", "Отчество", "День рожд.", "Оценки");
}

void printRow(Student s) { // вывод студента одной строки 
    printf("%-15s%-15s%-15s%02d/%02d/%-4d  ", s.surname, s.name, s.patronymic,
        s.birth.day, s.birth.month, s.birth.year);
    for (int k = 0; k < s.count; k++) {
        printf("%s:%d ",subjects[ s.data[k][0]-1],s.data[k][1]);
    }
    printf("\n");
}

void printAll(Student st[], int n) { //вывод всех студентов 
    printf("\n");
    printHeader();
    for (int i = 0; i < n; i++) {
        printRow(st[i]);
    }
}

void printSurnameV(Student st[], int n) { // cтуденты с фамилией на букву В
    printf("\nResult (фамилии на В):\n");
    printHeader();
    int count = 0;
    for (int i = 0; i < n; i++) {
        if (st[i].surname[0] == 'В') {
            printRow(st[i]);
            count++;
        }
    }
    if (count == 0) printf("Таких нет.\n");
}

void printFailed(Student st[], int n) { // студенты с двойками 
    printf("\nResult (двойки по физике и химии):\n");
    printHeader();
    int count = 0;
    for (int i = 0; i < n; i++) {
        if (getMark(st[i], 1) == BAD_MARK && getMark(st[i], 2) == BAD_MARK) {
            printRow(st[i]);
            count++;
        }
    }
    if (count == 0) printf("Таких нет.\n");
}
int main()
{
    SetConsoleCP(1251);
    SetConsoleOutputCP(1251);

    Student st[MAX_STUDENTS];
    int n;

    printf("Введите кол-во студентов: ");
    scanf_s("%d", &n);
    while (n < 1 || n > MAX_STUDENTS) {
        printf("Ошибка! Попробуйте еще раз: ");
        scanf_s("%d", &n);
    }

    for (int i = 0; i < n; i++) {
        printf("Личные данные %d - студент\n", i + 1);

        printf("Фамилия: ");
        scanf_s("%49s",  st[i].surname, (unsigned)sizeof(st[i].surname)); // приведение типа 
        printf("Имя: ");
        scanf_s("%49s",  st[i].name, (unsigned)sizeof(st[i].name));
        printf("Отчество: ");
        scanf_s("%49s",  st[i].patronymic, (unsigned)sizeof (st[i].patronymic));

        printf("Год рождения (%d-%d): ", MIN_YEAR, MAX_YEAR);
        scanf_s("%d", &st[i].birth.year);
        while (st[i].birth.year < MIN_YEAR || st[i].birth.year > MAX_YEAR) {
            printf("Ошибка! Попробуйте еще раз: ");
            scanf_s("%d", &st[i].birth.year);
        }

        printf("Месяц рождения (1-12): ");
        scanf_s("%hhu", &st[i].birth.month);
        while (st[i].birth.month < 1 || st[i].birth.month > 12) {
            printf("Ошибка! Попробуйте еще раз: ");
            scanf_s("%hhu", &st[i].birth.month);
        }
        // сколько дней в месяце этого года с учетом весокосного года 
        int maxDay = daysInMonth(st[i].birth.month, st[i].birth.year);
        printf("День рождения (1-%d): ", maxDay);
        scanf_s("%hhu", &st[i].birth.day);
        while (st[i].birth.day < 1 || st[i].birth.day > maxDay) {
            printf("Ошибка! В этом месяце дней: %d. Попробуйте еще раз: ", maxDay);
            scanf_s("%hhu", &st[i].birth.day);
        }

        printf("Сколько предметов (2-5): ");
        scanf_s("%d", &st[i].count);
        while (st[i].count < 2 || st[i].count > 5) {
            printf("Ошибка! Попробуйте еще раз: ");
            scanf_s("%d", &st[i].count);
        }

        for (int k = 0; k < st[i].count; k++) {
            int code;
            if (k < 2) {
                code = k + 1;
                printf("Предмет %d: %s\n", k + 1, subjects[k]);
            }
            else {
                printf("Предмет %d (", k + 1);
                for (int j = 2; j < 5; j++) {
                    printf("%d-%s ", j + 1, subjects[j]);
                }
                printf("): ");
                scanf_s("%d", &code);
                while (code < 3 || code > 5 || isUsed(st[i], k, code)) {
                    printf("Ошибка! Нужен код от 3 до 5, не повторяя уже введённые. Попробуйте еще раз: ");
                    scanf_s("%d", &code);
                }
            }
            st[i].data[k][0] = code; // код предмета 

            printf("Оценка по предмету %s (%d-%d): ", subjects[code - 1], MIN_MARK, MAX_MARK);
            scanf_s("%d", &st[i].data[k][1]);
            while (st[i].data[k][1] < MIN_MARK || st[i].data[k][1] > MAX_MARK) {
                printf("Ошибка! Попробуйте еще раз: ");
                scanf_s("%d", &st[i].data[k][1]);
            }
        }
    }

    printAll(st, n);
    printSurnameV(st, n);
    printFailed(st, n);

    return 0;
}
