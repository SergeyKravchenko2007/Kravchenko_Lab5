# Kravchenko_Lab5
#include <iostream>
#include <algorithm>
using namespace std;
const int SIZE = 4;
void printMatrix(int matrix[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
}
int main() {
    int matrix[SIZE][SIZE] = {
        {5, 2, 1, 7},
        {8, 3, 4, 6},
        {2, 9, 5, 1},
        {6, 7, 8, 3}
    };
    cout << "Початкова матриця:" << endl;
    printMatrix(matrix);
    int columnSums[SIZE] = {0};
    for (int j = 0; j < SIZE; j++) {
        for (int i = 0; i < SIZE; i++) {
            columnSums[j] += matrix[i][j];
        }
    }
    for (int j = 0; j < SIZE - 1; j++) {
        for (int k = 0; k < SIZE - j - 1; k++) {
            if (columnSums[k] > columnSums[k + 1]) {
                swap(columnSums[k], columnSums[k + 1]);
                for (int i = 0; i < SIZE; i++) {
                    swap(matrix[i][k], matrix[i][k + 1]);
                }
            }
        }
    }
    cout << "Матриця після сортування стовпців за їх сумами:" << endl;
    printMatrix(matrix);
    return 0;
}
