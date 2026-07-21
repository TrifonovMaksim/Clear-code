# ООП и интерфейсы.  Задания.

**3.1.**

```csharp  public class OrderedList<T>
    {
        public Node<T> head, tail;
        private bool _ascending;
        public int counter;

        public OrderedList(bool asc)
        {
            head = null;
            tail = null;
            _ascending = asc;
            counter = 0;    
        }
```

В данном примере, можем улучшить читаемость при создании упорядоченного списка по возростанию или убыванию. Путем создания статических методов-фабрик с указанием спиисок создается по убыванию или по возростанию:  

```csharp 
public static OrderedList<T> Ascending()
{
    return new OrderedList<T>(true);
}
public static OrderedList<T> Descending()
{
    return new OrderedList<T>(false);
}
```





```csharp public class BloomFilter
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

В данном примере, можем добавить, что надо указать длину в конструкторе:

```csharp 
public static BloomFilter WithLength(int length)
{
    return new BloomFilter(length);
}
```




```csharp  public class HashTable
    {
        public int size;
        public int step;
        public string[] slots;
        public int fullnes;

        public HashTable(int sz, int stp)
        {
            size = sz;
            step = stp;
            slots = new string[size];

            for (int i = 0; i < size; i++) slots[i] = null;
        }
```

В данном примере, можем указать, что надо прописать в конструкторе:

```csharp
public statuc HashTable WithSizeStep(int size, int step)
{
    return new HashTable(size, step);
}
```

**3.2.**

К сожалению, еще не использовал. Но, абстрактный класс должен называться абстрактно, описывать своим названием общую сферу классов наследуемых от него.
