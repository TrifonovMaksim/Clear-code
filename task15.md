# Правильные комментарии. Задание.

**Внесите 12 правок в свои комментарии, дополнительно указывая, по какому из вышеприведённых пунктов была сделана та или иная правка.**

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

В данном примере добавил информативный комментарий.

```csharp
  public int? Find_Index(T val)
        {
            // используем бинарный поиск, ищем середину списка
            // затем исходя из того больше значение в середине или меньше, 
            // делим пополам и выбираем отрезок до середины или после
            if (list.Count() == 0) return null;
            if (Compare(list.First(), val) == 0) return 0;
            if (Compare(list.Last(), val) == 0) return list.Count() - 1;
            int MinIndex = 0;
            int MaxIndex = list.Count() - 1;
            if (_ascending)
            {
                while (MinIndex <= MaxIndex)
                {
                    int middle = (MaxIndex + MinIndex) / 2;
                    if (Compare(list[middle], val) == 0)
                    {
                        return middle;
                    }
                    if (Compare(list[middle], val) == -1)
                    {
                        MinIndex = middle + 1;
                        continue;
                    }
                    if (Compare(list[middle], val) == +1)
                    {
                        MaxIndex = middle - 1;
                        continue;
                    }
                }
            }
            if (!_ascending)
            {
                while (MinIndex <= MaxIndex)
                {
                    int middle = (MaxIndex + MinIndex) / 2;
                    if (Compare(list[middle], val) == 0)
                    {
                        return middle;
                    }
                    if (Compare(list[middle], val) == -1)
                    {
                        MaxIndex = middle - 1;
                        continue;
                    }
                    if (Compare(list[middle], val) == +1)
                    {
                        MinIndex = middle + 1;
                        continue;
                    }
                }
            }
            return null;
        }
```

В данном примере добавил информативный комментарий.

```csharp
  public class BloomFilter
    {
        public int Filterlen;
        public int BloomFilter;
        public BloomFilter(int f_len)
        {
            Filterlen = f_len;
            // BloomFilter это битовая маска для массива размером 32 бита
            BloomFilter = 0;
        }
```

В данном примере добавил информативный комментарий.

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

В данном примере, в комментарии объяснил намерение метода.

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

В данном примеие, в комментарии добавил прояснение.

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

В данном примере в комментарии добавил усиление.

```csharp
 public int SeekSlot(T value)
        {
            int idx = HashFun(value, 0);
            bool IsEmptySlot = object.Equals(slots[idx], default(T)) && !is_deleted[idx];
            if (IsEmptySlot) return idx;
            bool IsDuplicate = !object.Equals(slots[idx], default(T)) && value.Equals(slots[idx]);
            if (IsDuplicate) return -1;
            int first_idx = -1;
            // запоминаем первый удалённый слот чтобы использовать его для вставки
            bool IsDeletedSlot = is_deleted[idx];
            if (IsDeletedSlot) first_idx = idx;
            for (int i = 1; i < size; i++)
            {
                idx = HashFun(value, i);
                if (is_deleted[idx] == true && first_idx == -1) first_idx = idx;
                if (!object.Equals(slots[idx], default(T)) && value.Equals(slots[idx])) return -1; // если слот не пустой и значение дублируется
                if (object.Equals(slots[idx], default(T)) && is_deleted[idx] == false) return first_idx != -1 ? first_idx : idx; // если слот пустой и значения там не было
            }
            return first_idx;
        }
```

В данном примере, в комментарии объяснил намерение метода.

```csharp
 public static LinkedList LinkedListsSum(LinkedList q, LinkedList w)
        {
            LinkedList res_list = new LinkedList();
            // если списки не равны, возвращаем пустой список,
            // сложение поэлементно возможно, только если длины списков равны
            if (q.Count() != w.Count()) return res_list;
            Node qnode = q.head;
            Node wnode = w.head;
            while (qnode != null && wnode != null)
            {
                res_list.AddInTail(new Node(qnode.value + wnode.value));
                qnode = qnode.next;
                wnode = wnode.next;
            }
            return res_list;
        }
```

В данном примере добавил информативный комментарий.

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

В данном примеие, в комментарии добавил прояснение.

```csharp
 public PowerSet<T> Intersection(PowerSet<T> set2)
        {
            // пересечение текущего множества и set2
            PowerSet<T> res = new PowerSet<T>();
            PowerSet<T> SmallSet = set2;
            PowerSet<T> LargeSet = this;
            // идём по меньшему множеству и проверяем наличие в большем,
            // это помогает сделать меньше итераций при разных размерах множеств
            if (Size() < set2.Size())
            {
                SmallSet = this;
                LargeSet = set2;
            }
            for (int i = 0; i < SmallSet.size; i++)
            {
                if (!object.Equals(SmallSet.slots[i], default(T)) && LargeSet.Get(SmallSet.slots[i])) res.Put(SmallSet.slots[i]);
            }
                return res;
        }

```

В данном примере, в комментарии объяснил намерение метода.

```csharp
public bool Remove(T value)
        {
            // возвращает true если value удалено
            // иначе false
            int idx = FindKeyIndex(value);
            if (idx != -1)
            {
                slots[idx] = default(T);
                is_deleted[idx] = true;
                count--;
                // обновление массива удаленных элементов очень важен
                // если не обновить, старые записи будут мешать поиску свободного слота
                if (count == 0) is_deleted = new bool[size];
                return true;
            }
            return false;
        }
```

В данном примере, в комментарии сделал усиление.

```csharp
// TODO - На данный момент этот класс статического размера
// в будущем надо сделать динамическим. 
  public class PowerSet<T>
    {
        public int size;
        public T[] slots;
        public int count;
        public bool[] is_deleted;

        public PowerSet()
        {
            // ваша реализация хранилища
            size = 20011;
            slots = new T[size];
            is_deleted = new bool[size];
        }

```

В данном примере, в комментарии добавил TODO.