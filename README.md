# Array_operations_c
Fundamental  array operation implementation using c  language 
#include <stdio.h>

// 1. Insert element at position
void insertAt(int arr[], int *n, int pos, int val) {
    for (int i = *n; i > pos; i--) {
        arr[i] = arr[i - 1];
    }
    arr[pos] = val;
    (*n)++;
}

// 2. Delete element at position
void deleteAt(int arr[], int *n, int pos) {
    for (int i = pos; i < *n - 1; i++) {
        arr[i] = arr[i + 1];
    }
    (*n)--;
}

// 3. Linear Search & Binary Search
int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}

int binarySearch(int arr[], int n, int target) {
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

// 4. Reverse array in-place
void reverseArray(int arr[], int n) {
    int start = 0, end = n - 1;
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

// Helper function to reverse sub-array
void reverseRange(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

// 5. Rotate array by k positions
void rotateArray(int arr[], int n, int k) {
    k = k % n;
    reverseRange(arr, 0, n - 1);
    reverseRange(arr, 0, k - 1);
    reverseRange(arr, k, n - 1);
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int arr[20] = {10, 20, 30, 40, 50};
    int n = 5;

    insertAt(arr, &n, 2, 25);
    deleteAt(arr, &n, 3);
    reverseArray(arr, n);
    rotateArray(arr, n, 2);
    
    printArray(arr, n);
    return 0;
}
