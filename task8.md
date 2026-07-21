# Константы. Задание.

```csharp
namespace AlgorithmsDataStructures
{
    public class BloomFilter
    {
        public int filter_len;
        public int bloom_filter;
        public BloomFilter(int f_len)
        {
            filter_len = f_len;
            // создаём битовый массив длиной f_len ...
            bloom_filter = 0;
        }

        // хэш-функции
        public int Hash1(string str1)
        {
            int res = 0;
            int hash1_rand = 17;
            // 17
            for (int i = 0; i < str1.Length; i++)
            {
                res = (res * hash1_rand + str1[i]) % filter_len;
            }
            // реализация ...
            return res;
        }
        public int Hash2(string str1)
        {
            // 223
            // реализация ...
            int res = 0;
            int hash1_rand = 223;
            // 17
            for (int i = 0; i < str1.Length; i++)
            {
                res = (res * hash1_rand + str1[i]) % filter_len;
            }
            // реализация ...
            return res;
        }
```

В данном примере, есть две переменные, которые можно указать, как константы.

hash1_rand - HASH1_MULTIPLIER  
// Случайный множитель первой хэш функции

hash2_rand - HASH2_MULTIPLIER  
// Случайный множитель второй хэш функции

```csharp
    public DynArray()
        {
            count = 0;
            MakeArray(16);
        }
```
В данном примере, 16 это "магическое число", означающее начальный размер массива

16 - ARRAY_START_SIZE  
// Начальный размер массива


```csharp
  public void Append(T itm)
        {
            balance += 3;
            if (count >= capacity)
            {
                int new_capacity = capacity * 2;
                if (balance < Cost(new_capacity)) throw new Exception("Кончился баланс");
                MakeArray(new_capacity);
                balance -= Cost(new_capacity);
            }
            array[count] = itm;
            count++;
        }
```

В данном примере, 3 это стоимость операции.

3 - OPERATION_COST  
// Стоимость операции в массиве, банковским методом

```csharp
   public class DynHashTable
    {
        public string[] slots;
        public int count;
        public int size;
        public int step;

        public DynHashTable(int stp, int start_size = 17)
        {
            step = stp;
            count = 0;
            if (start_size < 17) start_size = 17;
            MakeArray(start_size);
        }
        public bool IsSimple(int digit)
        {
            bool res = true;
            for (int i = 2; i <= Math.Sqrt(digit); i++)
            {
                if (digit % i == 0)
                {
                    res = false;
                    return res;
                }
            }
            return res;
        }
```

В данном примере, start_size = 17, можно вынести в константу.

17 - MIN_SIZE  
// Стандартный минимальный размер, если не указан иной


```csharp
 public class BitDictionary<T>
    {
        public int size;
        long slots;
        public T[] values;

        public BitDictionary()
        {
            size = 64;
            values = new T[size];
        }
```

В данном примере, 64 можно указать, как константу.

64 - DICTIONARY_SIZE  
// Размер словаря



```csharp
    public PowerSet()
        {
            // ваша реализация хранилища
            size = 20011;
            slots = new T[size];
            is_deleted = new bool[size];
        }
```

В данном примере, размер множества 20011 "магическое число".

20011 - SET_SIZE  
// Размер множества

```csharp
 public Bag()
        {
            // ваша реализация хранилища
            size = 20000;
            slots = new T[size];
            count_array = new int[size];
            is_deleted = new bool[size];
        }
```

В данном примере, размер мульти - множества 20000 "магическое число".

20000 - BAG_SIZE  
// Размер мульти - множества


```csharp
  public class NativeCache<T>
    {
        public int size;
        public string[] slots;
        public T[] values;
        public int[] hits;
        public int counter;
```

Тут можно добавить константу MAX_CACHE_SIZE.


```csharp
 public void Append(T itm)
        {
            if (count >= capacity)
            {
                int new_capacity = capacity * 2;
                MakeArray(new_capacity);
            }
            array[count] = itm;
            count++;
        }
```

В данном примере, можно 2 переименовать в константу.

2 - SIZE_GROW_MULTIPLIER  
// Множитель увеличения размера

```csharp
  public void Remove(int index)
        {
            if (index < 0 || index > count - 1) throw new IndexOutOfRangeException("Некорректный индекс");
            for (int i = index; i < count - 1; i++)
            {
                array[i] = array[i + 1];
            }
            count -= 1;
            if ((int)(capacity / 2) > count && capacity > 16) MakeArray((int)(capacity / 1.5) > 16 ? (int)(capacity / 1.5) : 16);
        }
```

В данном примере, можно 1.5 переименовать в константу.

1.5 - SIZE_DOWN_MULTIPLIER  
// МНожитель уменьшения размера


```csharp
 public class BloomFilter
    {
        public int filter_len;
        public int bloom_filter;
        public BloomFilter(int f_len)
```
В данном примере, можно добавить константу, которая будет указывать на количество используемых хэш функций, HASH_FUN_COUNT.
