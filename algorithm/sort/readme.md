# Sort
배열과 같은 연속된 자료구조의 값을 기준에 따라 정렬
### 버블정렬(Bubble Sort)
리스트내의 인접한 두 수를 비교하며 정렬함


시간 복잡도 : O(n^2)
```
void bubbleSort(int[] arr){
        for (int i = 0; i < arr.length; i++) 
            for (int j = 0; j < arr.length-i-1; j++) 
                if(arr[j]>arr[j+1]) swap(arr,j,j+1);
}
void swap(int[] arr,int i,int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
}
```
### 선택 벙렬(Selection Sort)
선택된 수와 나머지 수들을 비교하여 알맞은 자리를 찾아 정렬함

시간 복잡도 : O(n^2)
```
void selectionSort(int[] arr){
        for (int i = 0; i < arr.length; i++) 
            for (int j = i+1; j < arr.length; j++) 
                if(arr[i]>arr[j]) swap(arr,i,j);
}

```
### 삽입 정렬(Insertion Sort)
선택된 수를 적당한 위치로 **삽입** 하여 정렬함


시간 복잡도 : 최선 O(n), 최악 O(n^2)
```
void insertionSort(int[] arr){
        for (int i = 1; i < arr.length; i++) {
            int key = arr[i];
            int j = i-1;
            for (;j >= 0 ; j-- )
                if(arr[j] > key)
                    arr[j+1] = arr[j];
                else
                    break;
            arr[j+1] = key;
        }
}
```
### 병합 정렬(Merge Sort)
리스트를 **분할**후 **병합**하며 정렬함

시간 복잡도 : O(nlogn)
> 제자리정렬X,O(N)의 메모리를 추가로 사용
```
static void mergeSort(int[] arr) {
        int[] temp = new int[arr.length];
        mergeSort(arr, temp, 0, arr.length - 1);
    }

    static void mergeSort(int[] arr, int[] temp, int left, int right) {
        for(int i = 1; i <= right; i += i) {
            for(int j = 0; j <= right - i; j += (2 * i)) {
                int low = j;
                int mid = j + i - 1;
                int high = Math.min(j + (2 * i) - 1, right);
                merge(arr,temp, low, mid, high);
            }
        }
    }
    static void merge(int[] arr, int[] temp, int left, int mid, int right) {
        int l = left;
        int r = mid + 1;
        int i = left;
        while (l <= mid && r <= right) {
            if (arr[l] <= arr[r]) {
                temp[i] = arr[l];
                i++;
                l++;
            } else {
                temp[i] = arr[r];
                i++;
                r++;
            }
        }
        if (l > mid) {
            while (r <= right) {
                temp[i] = arr[r];
                i++;
                r++;
            }
        } else {
            while (l <= mid) {
                temp[i] = arr[l];
                i++;
                l++;
            }
        }
        for(i = left ; i<= right ; i++){
            arr[i] = temp[i];
        }
    }
```
