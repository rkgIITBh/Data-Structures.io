## C Program for Binary Heap Operations

```
#ifndef HEAP_H
#define HEAP_H
typedef struct heap{
    int *arr;     // Storage for elements
    int nElement; // No elements present
    int capacity; // Capacity of heap
    int type;     // 0 for min heap, 1 for max heap
} HEAP;

int isEmpty(HEAP *h) {
    return h->nElement == 0;
}

int randInput(){ 
    time_t t;  // Defined in <time.h>
    srand((unsigned) time(&t)); // Seeding value 
    return rand() % 100;        // Get between 1 to 100
}

HEAP *CreateHeap(int capacity,int type){
    HEAP *h = (HEAP * ) malloc(sizeof(HEAP)); 
    
    // Terminate if memory allocation fails 
    if(h == NULL){
        printf("Memory Error!");
        return NULL;
    }
    h->type = type;
    h->nElement = 0;  // Empty heap
    h->capacity = capacity;
    h->arr = (int *) malloc(capacity*sizeof(int)); //size in bytes

    //Check if allocation succeed
    if ( h->arr == NULL){
        printf("Error: malloc failed.\n");
        return NULL;
    }
    return h;
}


void bottomupHeapify(HEAP *h,int index){
    int temp;
    int parent = (index-1)/2;

    if(h->arr[parent] > h->arr[index]){
        //Swap and heapify recursively 
        temp = h->arr[parent];
        h->arr[parent] = h->arr[index];
        h->arr[index] = temp;
        bottomupHeapify(h,parent);
    }
}

void topdownHeapify(HEAP *h, int parent){
    int left = 2*parent + 1;
    int right = 2*parent + 2;
    int min;
    int temp;

    if(left >= h->nElement || left < 0)
        left = -1;
    if(right >= h->nElement || right < 0)
        right = -1;

    if(left != -1 && h->arr[left] < h->arr[parent])
        min=left;
    else
        min =parent;
    if(right != -1 && h->arr[right] < h->arr[min])
        min = right;

    if(min != parent){
        temp = h->arr[min];
        h->arr[min] = h->arr[parent];
        h->arr[parent] = temp;

        // Recursive  call
        topdownHeapify(h, min);
    }
}

void insert(HEAP *h, int key){
    if( h->nElement < h->capacity){
        h->arr[h->nElement] = key;
        bottomupHeapify(h, h->nElement);
        h->nElement++;
    }
}

int deleteMin(HEAP *h){
    int pop;
    if(isEmpty(h)){
        printf("\nHEAP is Empty\n");
        return -1;
    }
    // Replace first node by last and delete last
    pop = h->arr[0];
    h->arr[0] = h->arr[h->nElement-1];
    h->nElement--;
    topdownHeapify(h, 0);
    return pop;
}

void printHeap(HEAP *h){
    int i;
    printf("Heap\n");
    for(i = 0; i < h->nElement; i++){
        printf("%d, ",h->arr[i]);
    }
    printf("\n");
}


void decreaseKey(HEAP *h, int index, int val) {
    if (isEmpty(h)) {
        printf("Error: heap is empty\n"); 
        return;
    }
    h->arr[index] -= val;
    if (h->type == 0) 
         bottomupHeapify(h, index);
    else 
         topdownHeapify(h, index);
}

void increaseKey(HEAP *h, int index, int val) {
    if (isEmpty(h)) {
        printf("Error: heap is empty\n"); 
        return;
    }
    h->arr[index] += val;
    if (h->type == 0) 
         topdownHeapify(h, index);
    else 
         bottomupHeapify(h, index);
}
#endif
```


[Back to Index](../../index.md)