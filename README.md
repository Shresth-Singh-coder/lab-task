#include <stdio.h>

// Function to display the array
void showArray(int array[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", array[i]);
    }
    printf("\n");
}

// Function to insert an element at the beginning
void addAtStart(int array[], int *size, int element, int max_size) {
    if (*size == max_size) {
        printf("Array is full. Cannot add element.\n");
        return;
    }
    for (int i = *size; i > 0; i--) {
        array[i] = array[i - 1];
    }
    array[0] = element;
    (*size)++;
}

// Function to insert an element at the end
void addAtEnd(int array[], int *size, int element, int max_size) {
    if (*size == max_size) {
        printf("Array is full. Cannot add element.\n");
        return;
    }
    array[*size] = element;
    (*size)++;
}

// Function to insert an element at a specific position
void addAtPosition(int array[], int *size, int pos, int element, int max_size) {
    if (*size == max_size) {
        printf("Array is full. Cannot add element.\n");
        return;
    }
    if (pos < 0 || pos > *size) {
        printf("Invalid position.\n");
        return;
    }
    for (int i = *size; i > pos; i--) {
        array[i] = array[i - 1];
    }
    array[pos] = element;
    (*size)++;
}

// Function to delete the first element
void removeFirst(int array[], int *size) {
    if (*size == 0) {
        printf("Array is empty. Cannot remove element.\n");
        return;
    }
    for (int i = 0; i < *size - 1; i++) {
        array[i] = array[i + 1];
    }
    (*size)--;
}

// Function to delete the last element
void removeLast(int array[], int *size) {
    if (*size == 0) {
        printf("Array is empty. Cannot remove element.\n");
        return;
    }
    (*size)--;
}

// Function to delete an element at a specific position
void removeAtPosition(int array[], int *size, int pos) {
    if (pos < 0 || pos >= *size) {
        printf("Invalid position.\n");
        return;
    }
    for (int i = pos; i < *size - 1; i++) {
        array[i] = array[i + 1];
    }
    (*size)--;
}

// Function to search for an element using linear search
void findElement(int array[], int size, int element) {
    for (int i = 0; i < size; i++) {
        if (array[i] == element) {
            printf("Element found at index: %d\n", i);
            return;
        }
    }
    printf("Element not found.\n");
}

// Function to sort the array
void arrangeArray(int array[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for (int j = i + 1; j < size; j++) {
            if (array[i] > array[j]) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

// Function to sort elements at even indices
void arrangeEvenIndices(int array[], int size) {
    for (int i = 0; i < size; i += 2) {
        for (int j = i + 2; j < size; j += 2) {
            if (array[i] > array[j]) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

// Function to sort elements at odd indices
void arrangeOddIndices(int array[], int size) {
    for (int i = 1; i < size; i += 2) {
        for (int j = i + 2; j < size; j += 2) {
            if (array[i] > array[j]) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

// Function to sort elements that are even in value
void arrangeEvenValues(int array[], int size) {
    for (int i = 0; i < size; i++) {
        for (int j = i + 1; j < size; j++) {
            if (array[i] % 2 == 0 && array[j] % 2 == 0 && array[i] > array[j]) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

// Function to sort elements that are odd in value
void arrangeOddValues(int array[], int size) {
    for (int i = 0; i < size; i++) {
        for (int j = i + 1; j < size; j++) {
            if (array[i] % 2 != 0 && array[j] % 2 != 0 && array[i] > array[j]) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

int main() {
    int size, max_size;
    printf("Enter the size of the array: ");
    scanf("%d", &max_size);

    int array[max_size];

    printf("Enter the number of elements initially: ");
    scanf("%d", &size);

    printf("Enter the elements of the array:\n");
    for (int i = 0; i < size; i++) {
        scanf("%d", &array[i]);
    }

    printf("Original array: ");
    showArray(array, size);

    // Insert operations
    addAtStart(array, &size, 10, max_size);
    printf("After adding 10 at the beginning: ");
    showArray(array, size);

    addAtEnd(array, &size, 20, max_size);
    printf("After adding 20 at the end: ");
    showArray(array, size);

    addAtPosition(array, &size, 2, 30, max_size);
    printf("After adding 30 at position 2: ");
    showArray(array, size);

    // Delete operations
    removeFirst(array, &size);
    printf("After removing the first element: ");
    showArray(array, size);

    removeLast(array, &size);
    printf("After removing the last element: ");
    showArray(array, size);

    removeAtPosition(array, &size, 1);
    printf("After removing the element at position 1: ");
    showArray(array, size);

    // Search operation
    findElement(array, size, 30);

    // Sorting operations
    arrangeArray(array, size);
    printf("After arranging the array: ");
    showArray(array, size);

    arrangeEvenIndices(array, size);
    printf("After arranging elements at even indices: ");
    showArray(array, size);

    arrangeOddIndices(array, size);
    printf("After arranging elements at odd indices: ");
    showArray(array, size);

    arrangeEvenValues(array, size);
    printf("After arranging even values: ");
    showArray(array, size);

    arrangeOddValues(array, size);
    printf("After arranging odd values: ");
    showArray(array, size);

    return 0;
}
