# Плохие комментарии. Задание 

**Найдите 15 своих плохих комментариев, и напишите по каждому, что вы сделали для их улучшения с указанием соответствующего пункта из занятия.**

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
```csharp
   public class BloomFilter
    {
        public int filter_len;
        public int bloom_filter;
        public BloomFilter(int f_len)
        {
            filter_len = f_len;
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
            return res;
        }
        public int Hash2(string str1)
        {
            int res = 0;
            int hash1_rand = 223;
            for (int i = 0; i < str1.Length; i++)
            {
                res = (res * hash1_rand + str1[i]) % filter_len;
            }
            return res;
        }
```

В данном примере, комментарии были излишни. Их можно отнести к шуму, неочевидным,  обязательным.

```csharp
    public int Put(string value)
        {
            // записываем значение по хэш-функции

            // возвращается индекс слота или -1
            // если из-за коллизий элемент не удаётся разместить 
            if (fullnes == size)
            {
                Console.WriteLine("Хэш таблица заполнена");
                return -1;
            }
            int idx = SeekSlot(value);
            if (idx == -1) return -1;
            slots[idx] = value;
            fullnes++;
            return idx;
        }
```
```csharp
    public int Put(string value)
        {
            if (fullnes == size)
            {
                Console.WriteLine("Хэш таблица заполнена");
                return -1;
            }
            int idx = SeekSlot(value);
            if (idx == -1) return -1;
            slots[idx] = value;
            fullnes++;
            return idx;
        }
```


В данном примере, комментарии были избыточнымии.

```csharp
    public bool IsSimple(int digit)
        {
            // проверка числа на простоту
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
```csharp
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

В данном примере, комментарии были шумом.

```csharp
        public static PowerSet<T> MultiIntersection<T>(List<PowerSet<T>> lst)
        {
            // пересечение множеств
            PowerSet<T> res = lst[0];
            for (int i = 1; i < lst.Count; i++)
            {
                res = res.Intersection(lst[i]);
            }

            return res;
        }
```
```csharp
        public static PowerSet<T> MultiIntersection<T>(List<PowerSet<T>> lst)
        {
            PowerSet<T> res = lst[0];
            for (int i = 1; i < lst.Count; i++)
            {
                res = res.Intersection(lst[i]);
            }

            return res;
        }
```

В данном примере, комментарии были шумом.

```csharp
    public class Stack<T>
    {
        public List<T> stack;
        public int stack_size;
        public int tail;
        public Stack()
        {
            stack_size = 0;
            tail = 0;
            stack = new List<T>();
        }

        public int Size()
        {
            return stack_size;
        }

        // Pop работает за O(1)
        public T Pop()
        {
            T res;
            if (stack_size > 0)
            {
                res = stack[tail - 1];
                stack.RemoveAt(tail - 1);
                stack_size--;
                tail--;
            }
            else res = default(T);
            return res;
        }

        // Push тоже работает за O(1)
        public void Push(T val)
        {
            stack.Add(val);
            tail++;
            stack_size++;
        }

        public T Peek()
        {
            return stack_size > 0 ? stack[tail - 1] : default(T);
        }
    }
```
```csharp
    public class Stack<T>
    {
        public List<T> stack;
        public int stack_size;
        public int tail;
        public Stack()
        {
            stack_size = 0;
            tail = 0;
            stack = new List<T>();
        }

        public int Size()
        {
            return stack_size;
        }

        public T Pop()
        {
            T res;
            if (stack_size > 0)
            {
                res = stack[tail - 1];
                stack.RemoveAt(tail - 1);
                stack_size--;
                tail--;
            }
            else res = default(T);
            return res;
        }

        public void Push(T val)
        {
            stack.Add(val);
            tail++;
            stack_size++;
        }

        public T Peek()
        {
            return stack_size > 0 ? stack[tail - 1] : default(T);
        }
    }
```

В данном примере, комментарии были избыточнымии.

```csharp
public int HashFun(T value, int i)
        {
            if (value == null) throw new Exception("Неверное занчение");
            int res = 0;
            string key = value.ToString();
            foreach (var item in key)
            {
                res += (int)item;
            }
            // используем двойное хэширование, h1 первичная формула индекса
            // если получаем коллизию, делаем шаг h2 умноженный на количество попыток поиска индекса
            int h1 = res % size;
            int h2 = 1 + (res % (size - 1));
            return (h1 + i * h2) % size;
        }
```
```csharp
public int HashFun(T value, int i)
        {
            if (value == null) throw new Exception("Неверное занчение");
            int res = 0;
            string key = value.ToString();
            foreach (var item in key)
            {
                res += (int)item;
            }
            // используем двойное хэширование, h1 даёт первичный индекс, h2 шаг при коллизиях
            // (h1 + i * h2) % size гарантирует полный обход таблицы
            int h1 = res % size;
            int h2 = 1 + (res % (size - 1));
            return (h1 + i * h2) % size;
        }
```

В данном примере, описание было слишком общее.

```csharp
public int CalcSimple(int old_number)
        {
            // простое число важно, так как двойное хэширование,
            // полностью может обойти только массив размер которого равен простому числу
            if (IsSimple(old_number)) return old_number;
            int new_number = old_number + 1;
            while (!IsSimple(new_number))
            {
                new_number++;
            }
            return new_number;
        }
```
```csharp
public int CalcSimple(int old_number)
        {
            if (IsSimple(old_number)) return old_number;
            int new_number = old_number + 1;
            while (!IsSimple(new_number))
            {
                new_number++;
            }
            return new_number;
        }
```

В данном примере, была нелокальная информация, которая относилась ко всему классу.

```csharp
  public void MakeArray(int new_capacity)
            {
                T[] new_array = new T[new_capacity];
                if (array == null)
                {
                    array = new_array;
                    capacity = new_capacity;
                    return;
                }
                // при копировании сохраняем порядок элементов массива
                // сначала копируем от head до конца массива, затем от начала до head
                Array.Copy(array, head, new_array, 0, capacity - head);
                Array.Copy(array, 0, new_array, capacity - head, head);
                head = 0;
                tail = capacity;
                array = new_array;
                capacity = new_capacity;
            }
```
```csharp
  public void MakeArray(int new_capacity)
            {
                T[] new_array = new T[new_capacity];
                if (array == null)
                {
                    array = new_array;
                    capacity = new_capacity;
                    return;
                }

                // копируем замкнутый массив в новый массив поочередно, начиная с head
                Array.Copy(array, head, new_array, 0, capacity - head);
                Array.Copy(array, 0, new_array, capacity - head, head);
                head = 0;
                tail = capacity;
                array = new_array;
                capacity = new_capacity;
            }
```

В данном примере, в комментарии было слишком много информации.

```csharp
           public void AddFront(T item)
            {
                // добавление в голову
                if (count >= capacity)
                {
                    int new_capacity = capacity * 2;
                    MakeArray(new_capacity);
                }
                // прибавление capacity не дает индексу стать отрицательным
                head = (head - 1 + capacity) % capacity;
                array[head] = item;
                count++;
            }
```
```csharp
           public void AddFront(T item)
            {
                if (count >= capacity)
                {
                    int new_capacity = capacity * 2;
                    MakeArray(new_capacity);
                }
                head = (head - 1 + capacity) % capacity;
                array[head] = item;
                count++;
            }
```

В данном примере, комментарий по смыслу функции был избыточен, а про формулу, шумом.

```csharp
  private int FindKeyIndex(string key)
        {
            // находит индекс ключа
            int idx = HashFun(key);
            for (int i = 0; i < size; i++)
            {
                if (slots[idx] == key) return idx;
                // шаг единица при пробировании может привести к кластеризации в структуре
                idx = (idx + 1) % size;
            }
            return -1;
        }
```
```csharp
  private int FindKeyIndex(string key)
        {
            int idx = HashFun(key);
            for (int i = 0; i < size; i++)
            {
                if (slots[idx] == key) return idx;
                idx = (idx + 1) % size;
            }
            return -1;
        }
```

В данном примере, комментарий по смыслу функции был избыточен, а второй, давал слишком много информации.

```csharp
   public T Get(string key)
        {
            // возвращает value для key, 
            // или null если ключ не найден
            if (!IsKey(key)) return default(T);
            return values[FindKeyIndex(key)];

        }
```
```csharp
   public T Get(string key)
        {
            if (!IsKey(key)) return default(T);
            return values[FindKeyIndex(key)];
        }
```

В данном примере, комментарии были шумом.

```csharp
      public int Count()
        {
            return counter; // здесь будет ваш код подсчёта количества элементов в списке
        }
```
```csharp
      public int Count()
        {
            return counter; 
        }

```

В данном примере, комментарий неочевидный.

```csharp

        public List<Node<T>> GetAll() // выдать все элементы упорядоченного 
                               // списка в виде стандартного списка
        {
            List<Node<T>> r = new List<Node<T>>();
            Node<T> node = head;
            while (node != null)
            {
                r.Add(node);
                node = node.next;
            }
            return r;
        }
```
```csharp

        public List<Node<T>> GetAll()
        {
            List<Node<T>> r = new List<Node<T>>();
            Node<T> node = head;
            while (node != null)
            {
                r.Add(node);
                node = node.next;
            }
            return r;
        }
```

В данном примере, комментарии были шумом.