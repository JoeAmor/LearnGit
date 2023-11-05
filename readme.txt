void insert_sort(int *a, int n){
    int temp;
    for (int i = 1; i < n; ++ i){
        temp = a[i];
        int j = i;
        for (; j >= 1; -- j){
            if (a[j - 1] > temp)
                a[j] = a[j - 1];
            else 
                break;
        }
        a[j] = temp;
    }
}
void binary_insert_sort(int *a, int n){
    int temp;
    for (int i = 1; i < n; ++ i){
        temp = a[i];
        int left = 0, right = i - 1;
        while (left <= right){
            int mid = (left + right) / 2;
            if (a[mid] > temp)
                right = mid - 1;
            else 
                left = mid + 1;
        }
 
        for (int j = i; j > right; -- j)
            a[j] = a[j - 1];
        a[right + 1] = temp;
    }
}
void selection_sort(int *a, int n){
    int min_v, min_idx;
    for (int i = 0; i < n; ++ i){
        min_v = a[i];
        min_idx = i;
        for (int j = i + 1; j < n; ++ j){   
            if (a[j] < min_v){
                min_v = a[j];
                min_idx = j;
            }
        }
        swap(a[i], a[min_idx]);
    }
}
void adjust(int *a, int low, int high)	// 在原本有序的大根堆中，改变堆顶元素后，调用该函数可以使得大根堆再次有序
{
    int temp = a[low];
    int i = low, j = 2 * i + 1;
    while (j <= high)
    {
        if (j + 1 <= high && a[j + 1] > a[j])
            j ++;
        if (temp >= a[j])
            break;
        a[i] = a[j];
        i = j, j = 2 * i + 1;
    }
    a[i] = temp;
}
 
void heap_sort(int *a, int n)
{
    for (int i = (n - 2) / 2; i >= 0; -- i)
        adjust(a, i, n - 1);
    for (int i = n - 1; i >= 1; -- i)
    {
        swap(a[0], a[i]);
        adjust(a, 0, i - 1);
    }
}
