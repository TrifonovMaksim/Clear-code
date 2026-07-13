# Время связывания переменных. Задание.

**Сделайте 3 примера с разбором различного времени связывания в вашем коде и поясните, почему в каждом случае был сделан такой выбор.**

*1 Пример*
```csharp
    public class DynHashTable
    {
        public string[] slots;
        public int count;
        public int size;
        public int step;

        public DynHashTable(int stp, int StartSize = 17)
        {
            step = stp;
            count = 0;
            if (StartSize < 17) StartSize = 17;
            MakeArray(StartSize);
        }
```

В данном примере, StartSize это раннее связывание. Оно тут к месту, так как массив динамический и нам нужен небольшой стартовый размер, который вряд ли будет меняться. 
Так как, если понадобится больший размер, массив увеличится автоматически.

*2 Пример*
```csharp
  public class BitDictionary<T>
    {
        public int size;
        long slots;
        public T[] values;
        private const int BIT_DICTIONARY_SIZE = 64;

        public BitDictionary()
        {
            size = BIT_DICTIONARY_SIZE;
            values = new T[size];
        }
```

В данном примере, BIT_DICTIONARY_SIZE это связывание при компиляции. Тут удобен данный способ, так как размер может изменяться, но не так часто, чтобы использовать связывание во время выполнения программы каждый раз. 

*3 Пример*

```csharp
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
```

В данном примере, f_len это связывание при выполнении, в этом случае при выполнении программы и создании нового объекта фильтра блюма, нам нужно указывать длину, так как для разных таблиц нужен свой размер фильтра.