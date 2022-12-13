#include<iostream>
#include<ctime>
using namespace std;
void foo_array_random(float arr[], int SIZE)
{
    for (int index = 0; index < SIZE; index++)
    {
        arr[index] = (rand() % 20000 - 10000) * 0.01;
    }
}
void foo_array_cin(float arr[], int SIZE)
{
    for (int index = 0; index < SIZE; index++)
    {
        cout << endl << "Введите " << index << " элемент масива : ";
        cin >> arr[index];
    }
}
void foo_array_cout(float arr[], int SIZE)
{
    for (int index = 0; index < SIZE; index++)
    {
        cout << "  " << arr[index];
    }
}
void foo_array_sum(float arr[], int SIZE)
{
    float sum = 0;
    for (int index = 1; index < SIZE; index += 2)
    {
        sum = sum + arr[index];
    }
    cout << " " << sum;
}
void foo_array_sum_in_range(float arr[], int SIZE)
{
    int begin, end;
    float sum = 0;
    for (int index = 0; index < SIZE; index++)
    {
        if (arr[index] < 0)
        {
            begin = index;
            break;
        }
    }
    for (int index = SIZE - 1; index >= 0; index--)
    {
        if (arr[index] < 0)
        {
            end = index;
            break;
        }
    }
    for (int index = begin + 1; index < end; index++)
    {
        sum = sum + arr[index];
    }
    cout << " " << sum;
}
void foo_array_cut(float arr[], int SIZE)
{
    int N = 0, i = 0;
    for (int index = 0; index < SIZE; index++)
    {
        if ((arr[index] < 1) && (arr[index] > -1))
        {
            N++;
        }
    }
    float* arr_result = new float[SIZE - N];
    for (int index = 0; index < SIZE; index++)
    {
        if ((arr[index] >= 1) || (arr[index] <= -1))
        {
            arr_result[i] = arr[index];
            i++;
        }
    }
    cout << endl << "Сжатый масив : ";
    foo_array_cout(arr_result, SIZE - N);
    delete[] arr_result;
}
int main()
{
    setlocale(LC_ALL, "rus");
    srand(time(NULL));
    int SIZE, method, variant;
    float arr[100];
    cout << "Введите размер масива : ";
    cin >> SIZE;
    cout << endl << "Выберите способ заполнения масива :  " << endl << "1 - рандом " << endl << "2 - ручной ввод   ";
    cin >> method;
    switch (method)
    {
    case 1: foo_array_random(arr, SIZE);
        break;
    case 2: foo_array_cin(arr, SIZE);
        break;
    }
    cout << "Ваш масив :  ";
    foo_array_cout(arr, SIZE);
    cout << endl << "Выберите функцию : " << endl << " 1 - сума всех элементов масива с непарными индексами " << endl << " 2 - сума элементов между первым и последним отрицательным элементом " << endl << " 3 - сжатие масива    ";
    cin >> variant;
    switch (variant)
    {
    case 1:foo_array_sum(arr, SIZE);
        break;
    case 2:foo_array_sum_in_range(arr, SIZE);
        break;
    case 3: foo_array_cut(arr, SIZE);
        break;
    }
    return 0;
}
