# Комментарии. Задание.

**3.1.**

```csharp
 public int HashFun(string value, int i)
        {
            // используем двойное хэширование, h1 первая хэш функция, h2 вторая
            if (value == null) throw new Exception("В хэш функцию, подано пустое значение");
            int res = 0;
            foreach (var item in value)
            {
                res += (int)item;
            }
            int h1 = res % size;
            int h2 = 1 + (res % (size - 1));
            return (h1 + i * h2) % size;
        }
```

```
 public bool IsCycled()
        {
            // используем два указателя, быстрый и медленный, если медленный догонит быстрый, то есть цикл
            if (head == null) return false;
            Node slow_pointer = head;
            Node fast_pointer = head.next;

            while (slow_pointer != null && fast_pointer != null && fast_pointer.next != null)
            {
                if (slow_pointer == fast_pointer) return true;
                slow_pointer = slow_pointer.next;
                fast_pointer = fast_pointer.next.next;
            }
            return false;
        }
```

```csharp
     public void Put(string key, T value)
        {
            // гарантированно записываем 
            // значение value по ключу key
            int idx;
            if (IsKey(key))
            {
                idx = FindKeyIndex(key);
                values[idx] = value;
                return;
            }
            if (size != counter)
            {   
                idx = SeekSlot(key);
                slots[idx] = key;
                values[idx] = value;
                counter++;
                return;
            }
            // если кэш полон, вставляем новый взамен элемента с наименьшим количеством обращений
            idx = FindMinEntranceIdx();
            Delete(idx);
            idx = SeekSlot(key);
            slots[idx] = key;
            values[idx] = value;
        }
```

```csharp
public int CalcSimple(int old_number)
        {
            // считаем новый размер, равный простому числу
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
  public class BankDynArray<T>
    {
    // используем банковский метод, каждая операция пополняет баланс на 3, расширение оплачивается накопленным балансом
        public T[] array;
        public int count;
        public int capacity;
        public int balance;
        public BankDynArray()
        {
            count = 0;
            MakeArray(16);
            balance = 0;
        }
    }
```

```csharp
  public void Sort()
        {
            // сортировка выбором, находим минимальный элемент и переносим его в новый отсортированный список
            if (head == null || head == tail) return;
            LinkedList2 tmp_linked_list = new LinkedList2();
            while (head != null)
            {
                Node min_node = head;
                Node node = head.next;
                while (node != null)
                {
                    if (min_node.value > node.value) min_node = node;
                    node = node.next;
                }
                tmp_linked_list.AddInTail(new Node(min_node.value));
                Remove(min_node.value);
            }
            this.head = tmp_linked_list.head;
            this.tail = tmp_linked_list.tail;
        }
```

```csharp
      public PowerSetSolution() : base() { }
            public static PowerSetSolution<string> DecartMultiply(PowerSetSolution<T> set1, PowerSetSolution<T> set2)
            {
                // создаем все возможные пары из первого и второго множества и записываем в результируещее
                // каждая пара записывается в результат через запятую
                PowerSetSolution<string> res = new PowerSetSolution<string>();
                for (int i = 0; i < set1.size; i++)
                {
                    if (!object.Equals(set1.slots[i], default(T)))
                    {
                        for (int j = 0; j < set2.size; j++)
                        {
                            if (!object.Equals(set2.slots[j], default(T)))
                            {
                                res.Put(set1.slots[i].ToString() + "," + set2.slots[j].ToString());
                            }
                        }
                    }
                }
                return res;
            }
```

**3.2.**

```csharp
      public void Add(string str1)
        {
            // добавляем строку str1 в фильтр
            bloom_filter[Hash1(str1)]++;
            bloom_filter[Hash2(str1)]++;
        }
```

В данном примере, можно убрать комментарий о сути метода, без изменений, из названия метода понятно, что он делает.

```csharp
     public bool IsValue(string str1)
        {
            // проверка, имеется ли строка str1 в фильтре
            if (bloom_filter[Hash1(str1)] > 0 && bloom_filter[Hash2(str1)] > 0) return true;
            return false;
        }
```

В данном примере, можно убрать комментарий о сути метода, без изменений, из названия метода понятно, что он делает.

```csharp
   public void Add(T value)
        {
            if (value == null) throw new ArgumentNullException("Пустое значение");
            if (list.Count == 0)
            {
                list.Add(value);
                return;
            }
            if (_ascending)
            {
                if (Compare(value, list.First()) == -1)
                {
                    list.Insert(0, value);
                    return;
                }
                if (Compare(value, list.Last()) == +1)
                {
                    list.Add(value);
                    return;
                }
                for (int i = 0; i < list.Count(); i++)
                {
                    if (Compare(value, list[i]) == -1 || Compare(value, list[i]) == 0)
                    {
                        list.Insert(i, value);
                        return;
                    }
                }
                return;
            }
            if (Compare(value, list.First()) == +1)
            {
                list.Insert(0, value);
                return;
            }
            if (Compare(value, list.Last()) == -1)
            {
                list.Add(value);
                return;
            }
            for (int i = 0; i < list.Count(); i++)
            {
                if (Compare(value, list[i]) == +1 || Compare(value, list[i]) == 0)
                {
                    list.Insert(i, value);
                    return;
                }
            }
        }
```

В данном примере, убрал комментарии про работу со списком по возростанию и убыванию, так как понятно из условия if(_ascending).

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

В данном примере, можно убрать комментарий о сути метода, без изменений, из названия метода понятно, что он делает.

```csharp
 public int SeekSlot(T value)
        {
            // находит индекс пустого слота для значения
            int idx = HashFun(value, 0);
            if (object.Equals(slots[idx], default(T)) && is_deleted[idx] == false) return idx; // если слот пустой и в нем не было до этого значений
            if (!object.Equals(slots[idx], default(T)) && value.Equals(slots[idx])) return -1; // если слот не пустой и значение дублируется
            // если есть коллизия, значит есть шанс, что данное значение уже во множестве
            int first_idx = -1;
            if (is_deleted[idx] == true) first_idx = idx; // если слот пуст, но значение из него было удалено, значит возможно дубликаты дальше
            for (int i = 1; i < size; i++)
            {
                idx = HashFun(value, i);
                if (is_deleted[idx] == true && first_idx == -1) first_idx = idx;
                if (!object.Equals(slots[idx], default(T)) && value.Equals(slots[idx])) return -1; // если слот не пустой и значение дублируется
                if (object.Equals(slots[idx], default(T)) && is_deleted[idx] == false) return first_idx != -1 ? first_idx : idx; // если слот пустой и значения там не было
            }
            return first_idx;
        }
        -----------------------------------------------------------------------------------------------------------------------------------------------------------------------
         public int SeekSlot(T value)
        {
            int idx = HashFun(value, 0);
            bool IsEmptySlot = object.Equals(slots[idx], default(T)) && !is_deleted[idx];
            if (IsEmptySlot) return idx;
            bool IsDuplicate = !object.Equals(slots[idx], default(T)) && value.Equals(slots[idx]);
            if (IsDuplicate) return -1;
            int first_idx = -1;
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

В данном примере, комментарии можно убрать, путем добавление булевых переменных для улучшения читаемости.
