# Семинар 10 - quick-sort, merge-sort

# Семинар 10 - quick-sort, merge-sort

### Quick-sort

Рисуем на доске quick-sort

**Вопрос**: в каком случае линейный поиск лучше бинарного?

**Вопрос**: в каком случае сортировка вставками лучше чем быстрая сортировка?

**Задача**: пусть у нас есть partition(), реализовать quicksort()

**Вопрос**: как реализовать partition()?

**Задача**: реализовать partition()

**Вопрос**: какой худший случай для этой сортировки?

```jsx
int partition(int *arr, int l, int r, int *s) {
  int p = arr[l];  while (l <= r) {
    while (arr[l] < p) l++;    while (arr[r] > p) r--;      if (l <= r) {
        int t = arr[l];        arr[l] = arr[r];        arr[r] = t;        l++; r--;      }
    }
    *s = l;    return r;}
void quicksort(int *arr, int l, int r) {
  if (l >= r) return;  int kek;  int pe = partition(arr, l, r, &kek);  quicksort(arr, l, pe);  quicksort(arr, kek, r);}
```

### Merge-sort

**Вопрос**: можно ли придумать сортировку без этого худшего случая? Как нужно разбивать массив?

Рисуем на доске merge-sort

Задача: пусть у нас есть функция merge(), реализовать mergesort()

Extra Задача: реализовать merge()

```java
// merge arr[l...m] with arr[m + 1, r]
void merge(int *arr, int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;
    int *temp = (int *)malloc((n1 + n2) * sizeof(int));
    int i = l, j = m + 1, k = 0;

    while (i <= m && j <= r) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
        }
    }

    while (i <= m) {
        temp[k++] = arr[i++];
    }
    while (j <= r) {
        temp[k++] = arr[j++];
    }

    for (i = l, k = 0; i <= r; i++, k++) {
        arr[i] = temp[k];
    }
    free(temp);
}

void mergesort(int *arr, int l, int r) {
  if (l >= r) return;
  int m = (l + r) / 2;
  mergesort(arr, l, m);
  mergesort(arr, m + 1, r);
  merge(arr, l, m, r);
}
```