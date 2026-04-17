# Семинар 9 - Union, files

# Семинар 9 - Union, files

Сессия Q&A:

- Есть вопросы с прошлой лекции и семинара?
- Есть вопросы по задачам?

### Объединения (1 половина)

```jsx
// Способ 1: указателиdouble x = 17.3;int *ptr = (int*)&x;int low = ptr[0], high = ptr[1];// Способ 2: unionunion dbl2int {
  double d;  int i[2];};union dbl2int u;u.d = 17.3;int low = u.i[0], high = u.i[1];
```

**Вопрос**: Как понять, какой тип мы используем? - enum

enum…

### Файлы (2 половина)

Файл - синоним для impl-defined структуры:

```jsx
typedef struct _File_t { ??? } FILE;
sizeof(FILE) // undefined, всегда работаем с FILE*
```

errno…

perror()…