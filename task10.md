# Переменные и их значения. Задание.

**Внесите 15 правок в свой код с учётом рекомендаций из данного занятия, и напишите по каждой, как и что конкретно вы улучшили.**

```cshrap
 public static LinkedList LinkedListsSum(LinkedList q, LinkedList w)
        {
            LinkedList res_list = new LinkedList();
            
            if (q.Count() != w.Count()) return res_list;
            Node qnode = q.head;
            Node wnode = w.head;
            while (qnode != null && wnode != null)
            {
                res_list.AddInTail(new Node(qnode.value + wnode.value));
                qnode = qnode.next;
                wnode = wnode.next;
            }
            qnode = null;
            wnode = null;
            return res_list;
        }
```

В данном примере, добавил обнуление переменных после исполтзования в цикле.

```csharp
public class DynArray<T>
    {
        public T[] array;
        public int count;
        public int capacity;

        public DynArray()
        {
            count = 0;
            capacity = 0;
            MakeArray(16);
        }

        public void MakeArray(int new_capacity)
        {
            T[] new_array = new T[new_capacity];
            if (array == null)
            {
                array = new_array;
                capacity = new_capacity;
                return;
            }
            Array.Copy(array, 0, new_array, 0, count);
            array = new_array;
            if (new_capacity < count) throw new Exception("Ошибка в значении переменной, количество элементов больше размера массива")
            capacity = new_capacity;
        }
```

В данном примере, добавил инициализацию capacity в конструкторе и проверку переменной capacity(размер массива), она не может быть меньше количества элементов.

```csharp
    public class HashTable
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
            fullnes = 0

            for (int i = 0; i < size; i++) slots[i] = null;
        }
```

В данном примере, добавил инициализацию fullnes.

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
            if (fullnes > size) throw new Exception("Ошибка в значении переменной, количество элементов больше размера таблицы")
            return idx;
        }
```

В данном примере, добавил проверку переменной fullnes, она не может быть больше размера таблицы.

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
            slots = null;
            if (start_size < 17) start_size = 17;
            MakeArray(start_size);
        }
```

В данном примере, добавил инициализацию slots.

```csharp
    public class DynDoubleHashTable
    {
        public string[] slots;
        public int count;
        public int size;

        public DynDoubleHashTable(int start_size = 17)
        {
            count = 0;
            size = 0;
            if (start_size < 17) start_size = 17;
            MakeArray(start_size);
        }
```

В данном примере, добавил инициализацию size.

```csharp
 public void Reverse()
        {
            if (head == null || head == tail) return;
            Node node = tail;
            node.next = node.prev;
            node.prev = null;
            tail = head;
            head = node;
            node = node.next;
            Node tmp = null;
            while (node != null)
            {
                tmp = node.next;
                node.next = node.prev;
                node.prev = tmp;
                node = node.next;
            }
        }
```

В данном примере, перенес инициализацию переменной tmp сверху, ближе к циклу.

```csharp
        public bool IsCycled()
        {
            if (head == null) return false;
            Node slow_pointer = head;
            Node fast_pointer = head.next;

            while (slow_pointer != null && fast_pointer != null && fast_pointer.next != null)
            {
                if (slow_pointer == fast_pointer) return true;
                slow_pointer = slow_pointer.next;
                fast_pointer = fast_pointer.next.next;
            }
            slow_pointer = null;
            fast_pointer = null;
            return false;
        }
```

В данном примере, добавил обнуление переменных после использования.

```csharp
public void Sort()
        {
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
            min_node = null;
            node = null;
            this.head = tmp_linked_list.head;
            this.tail = tmp_linked_list.tail;
        }
```

В данном примере, добавил обнуление переменных после использования.

```csharp
 public LinkedList2 CompareTwoLists(LinkedList2 list1, LinkedList2 list2)
        {
            LinkedList2 res_list = new LinkedList2();
            list1.Sort();
            list2.Sort();
            Node node1 = list1.head;
            Node node2 = list2.head;
            while (node1 != null && node2 != null)
            {
                if (node1.value < node2.value)
                {
                    res_list.AddInTail(new Node(node1.value));
                    node1 = node1.next;
                }
                else
                {
                    res_list.AddInTail(new Node(node2.value));
                    node2 = node2.next;
                }
            }
            while (node1 != null)
            {
                res_list.AddInTail(new Node(node1.value));
                node1 = node1.next;
            }
            while (node2 != null)
            {
                res_list.AddInTail(new Node(node2.value));
                node2 = node2.next;
            }
            node1 = null;
            node2 = null;
            return res_list;
        }
```

В данном примере, добавил обнуление переменных после использования.

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
            slots = 0;
        }
```

В данном примере, инициализировал slots.

```csharp
 public int Compare(string v1, string v2)
        {
                // версия для лексикографического сравнения строк
                string a = ((string)((object)v1)).Trim();
                string b = ((string)((object)v2)).Trim();
                int res = a.CompareTo(b);
                if (res > 0) result = 1;
                if (res < 0) result = -1;

                return result;
           
        }
```

В данном примере, убрал лишнюю ининциализацию res в начале.

```csharp
   public void Check(OrderedList<T> list)
        {
            if (list == null || list.counter == 0)
            {
                Console.WriteLine("Дан пустой список");
                return;
            }
            if (counter == 0)
            {
                Console.WriteLine("Список пуст");
                return;
            }
            if (list.counter > counter)
            {
                Console.WriteLine("Искомый список больше имеющегося");
                return;
            }
            bool flag = false;
            bool shift = false;
            Node<T> node1 = head;
            Node<T> node2 = list.head;
            for (int i = 0; i < counter - list.counter + 1; i++)
            {
                // Если работаем по возростанию и следующий элемент больше искомого, заведомо понятно, что искомого элемента в списке нет.
                if (_ascending == true)
                {
                    if (Compare(node2.value, node1.value) == -1)
                    {
                        Console.WriteLine("Подсписка нет");
                        return;
                    }
                }
                // Если работаем по убыванию и следующий элемент меньше искомого, заведомо понятно, что искомого элемента в списке нет.
                if (_ascending == false)
                {
                    if (Compare(node2.value, node1.value) == +1)
                    {
                        Console.WriteLine("Подсписка нет");
                        return;
                    }
                }
                shift = false;
                if (Compare(node1.value, node2.value) == 0)
                {
                    flag = true;
                    for (int j = 0; j < list.counter; j++)
                    {
                        if (Compare(node1.value, node2.value) != 0)
                        {
                            node2 = list.head;
                            flag = false;
                            break;
                        }
                        node1 = node1.next;
                        node2 = node2.next;
                        shift = true;
                    }
                    if (flag == true)
                    {
                        Console.WriteLine("Подсписок есть");
                        return;
                    }
                }
                if (shift == false) node1 = node1.next;
            }
            node1 = null;
            node2 = null;
            Console.WriteLine("Подсписка нет");
        }
```

В данном примере, добавил обнуление переменных после использования.

```csharp
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
            count = 0;
        }
```

В данном примере добавил инициализацию count.

```csharp
  public PowerSet<T> Intersection(PowerSet<T> set2)
        {
            // пересечение текущего множества и set2
            PowerSet<T> res = new PowerSet<T>();
            PowerSet<T> small = set2;
            PowerSet<T> large = this;
            if (Size() < set2.Size()) // выгоднее идти по меньшему множеству
            {
                small = this;
                large = set2;
            }
            for (int i = 0; i < small.size; i++)
            {
                if (!object.Equals(small.slots[i], default(T)) && large.Get(small.slots[i])) res.Put(small.slots[i]);
            }
            small = null;
            large = null;
                return res;
        }
```

В данном примере, добавил обнуление переменных после использования.