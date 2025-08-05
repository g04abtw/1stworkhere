# 1stworkhere

#include <iostream>
#include <cmath>    // Для функций sqrt и fabs

using namespace std;

// Функции для прямоугольника
double rectanglePerimeter(double a, double b) {
    // Периметр прямоугольника: P = 2 * (a + b)
    return 2 * (a + b);
}

double rectangleArea(double a, double b) {
    // Площадь прямоугольника: S = a * b
    return a * b;
}

double rectangleDiagonal(double a, double b) {
    // Длина диагонали прямоугольника: d = sqrt(a^2 + b^2)
    return sqrt(a * a + b * b);
}

// Функции для треугольника
double trianglePerimeter(double a, double b, double c) {
    // Периметр треугольника: P = a + b + c
    return a + b + c;
}

double triangleArea(double a, double b, double c) {
    // Площадь треугольника по формуле Герона
    double p = (a + b + c) / 2.0; // Полупериметр
    return sqrt(p * (p - a) * (p - b) * (p - c));
}

bool isIsosceles(double a, double b, double c) {
    // Проверка на равнобедренность (два равных ребра)
    const double EPS = 1e-6; // Допуск для сравнения вещественных чисел
    return fabs(a - b) < EPS || fabs(a - c) < EPS || fabs(b - c) < EPS;
}

int main() {
    // Пример для прямоугольника
    double rectA, rectB;
    cout << "Введите стороны прямоугольника (a и b): ";
    cin >> rectA >> rectB;

    cout << "Периметр прямоугольника: " << rectanglePerimeter(rectA, rectB) << endl;
    cout << "Площадь прямоугольника: " << rectangleArea(rectA, rectB) << endl;
    cout << "Длина диагонали прямоугольника: " << rectangleDiagonal(rectA, rectB) << endl;

    // Пример для треугольника
    double triA, triB, triC;
    cout << "\nВведите стороны треугольника (a, b, c): ";
    cin >> triA >> triB >> triC;

    // Проверка существования треугольника
    if (triA + triB > triC && triA + triC > triB && triB + triC > triA) {
        cout << "Периметр треугольника: " << trianglePerimeter(triA, triB, triC) << endl;
        cout << "Площадь треугольника: " << triangleArea(triA, triB, triC) << endl;
        if (isIsosceles(triA, triB, triC)) {
            cout << "Треугольник равнобедренный" << endl;
        }
        else {
            cout << "Треугольник не равнобедренный." << endl;
        }
    }
    else {
        cout << "Треугольник с такими сторонами не существует" << endl;
    }

    return 0;
}
