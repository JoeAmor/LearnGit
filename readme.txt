void insert_sort(int *a, int n)
{
    int temp;
    for (int i = 1; i < n; ++ i)
    {
        temp = a[i];
        int j = i;
        for (; j >= 1; -- j)
        {
            if (a[j - 1] > temp)
                a[j] = a[j - 1];
            else 
                break;
        }
        a[j] = temp;
    }
}
void binary_insert_sort(int *a, int n)
{
    int temp;
    for (int i = 1; i < n; ++ i)
    {
        temp = a[i];
        int left = 0, right = i - 1;
        while (left <= right)
        {
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
void bubble_sort(int *a, int n)
{
    for (int i = 0; i < n; ++ i)
    {
        for (int j = 1; j < n - i; ++ j)
            if (a[j - 1] > a[j])
                swap(a[j - 1], a[j]);
    }
}
void selection_sort(int *a, int n)
{
    int min_v, min_idx;
    for (int i = 0; i < n; ++ i)
    {
        min_v = a[i];
        min_idx = i;
        for (int j = i + 1; j < n; ++ j)
        {   
            if (a[j] < min_v)
            {
                min_v = a[j];
                min_idx = j;
            }
        }
        swap(a[i], a[min_idx]);
    }
}