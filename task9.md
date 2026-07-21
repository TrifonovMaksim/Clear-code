# Типы данных. Задание.

В данном примере добавил проверку на  переполнение инта.

```csharp
       public void AddFront(T item)
            {
                // добавление в голову
                if (count >= capacity)
                {
                    if (capacity > int.MaxValue / 2) throw new Exception("Переполнение переменной, размера массива");
                    int new_capacity = capacity * 2;
                    MakeArray(new_capacity);
                }
                head = (head - 1 + capacity) % capacity;
                array[head] = item;
                count++;
            }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
  public void Remove(int index)
        {
            bool IsIndexUncorrect = index < 0 || index > count - 1; 
            balance += 3;
            if (IsIndexUncorrect) throw new IndexOutOfRangeException("Некорректный индекс");
            for (int i = index; i < count - 1; i++)
            {
                array[i] = array[i + 1];
                balance += 3;
            }
            count -= 1;
            bool IsDecreaseSize = capacity / 2 > count && capacity > 16;
            if (IsDecreaseSize)
            {
                int new_capacity = ((int)(capacity / 1.5) > 16 ? (int)(capacity / 1.5) : 16);
                if (balance < Cost(new_capacity)) throw new Exception("Кончился баланс");
                MakeArray(new_capacity);
                balance -= Cost(new_capacity);
            }
        }
```

В данном примере, проверил на деление на 0.

```csharp
 public int HashFun(string value)
        {
            // всегда возвращает корректный индекс слота
            if (value == null) throw new Exception("В хэш функцию, подано пустое значение");
            int res = 0;
            for (int i = 0; i < value.Length; i++)
            {
                res += (int)value[i] * (i + 1);
            }
            if (size == 0) throw new Exception("Размер равен 0");
            return Math.Abs(res) % size;
        }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
 public void Reverse()
        {
            bool IsListEmpty = head == null || head == tail;
            if (IsListEmpty) return;
            Node node = tail;
            Node tmp = null;
            node.next = node.prev;
            node.prev = null;
            tail = head;
            head = node;
            node = node.next;
            while (node != null)
            {
                tmp = node.next;
                node.next = node.prev;
                node.prev = tmp;
                node = node.next;
            }
        }
```

В данном примере, проверил на деление на 0.

```csharp
static public void calculation(string str)
        {
            string[] chars = str.Split(' ');
            Stack<string> stack1 = new Stack<string>();
            Stack<int> stack2 = new Stack<int>();
            for (int i = chars.Length - 1; i >= 0; i--) stack1.Push(chars[i]);
            while(stack1.stack_size > 0) 
            {
                string s = stack1.Pop();
                if (int.TryParse(s, out int res))
                {
                    stack2.Push(res);
                }
                else
                {
                    if(s == "=") continue;
                    int a = stack2.Pop();
                    int b = stack2.Pop();
                    switch (s)
                    {
                        case "+":
                            stack2.Push(a + b);
                            break;
                        case "-":
                            stack2.Push(a - b);
                            break;
                        case "/":
                            if (b == 0) throw new Exception("Деление на ноль");
                            stack2.Push(a / b);
                            break;
                        case "*":
                            stack2.Push(a * b);
                            break;
                    }
                }
            }
            Console.WriteLine("Результат " + stack2.Pop());

        }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
  public bool IsCycled()
        {
            if (head == null) return false;
            Node slow_pointer = head;
            Node fast_pointer = head.next;

            bool CanGo = slow_pointer != null && fast_pointer != null && fast_pointer.next != null;
            while (CanContinue)
            {
                if (slow_pointer == fast_pointer) return true;
                slow_pointer = slow_pointer.next;
                fast_pointer = fast_pointer.next.next;
            }
            return false;
        }
```

В данном примере добавил проверку на  переполнение инта.

```csharp
 public void Append(T itm)
        {
            balance += 3;
            if (count >= capacity)
            {
                if (capacity > int.MaxValue / 2) throw new Exception("Переполнение переменной, размера массива");
                int new_capacity = capacity * 2;
                if (balance < Cost(new_capacity)) throw new Exception("Кончился баланс");
                MakeArray(new_capacity);
                balance -= Cost(new_capacity);
            }
            array[count] = itm;
            count++;
        }
``` 

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
public int SeekSlot(string value)
        {
            // находит индекс пустого слота для значения, или -1
            bool IsTableFull = fullnes == size;
            if (IsTableFull)
            {
                Console.WriteLine("Хэш таблица заполнена");
                return -1;
            }
            int idx = HashFun(value);
            if (slots[idx] == null) return idx;
            for (int i = 0; i < size; i ++)
            {
                idx = (idx + step) % size;
                if (slots[idx] == null) return idx; 
            }
            return -1;
        }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
public T Dequeue()
        {
            bool IsStacksEmpty = stack1.Size() == 0 && stack2.Size() == 0;
            if (IsStacksEmpty) return default(T);
            if (stack2.Size() == 0)
            {
                int len = stack1.Size();
                for (int i = 0; i < len; i++)
                {
                    stack2.Push(stack1.Pop());
                }
            }
            return stack2.Pop();
        }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных. Также добавил проверку на переполнение.

```csharp
 public void Insert(T itm, int index)
        {
            balance += 3;
            bool is_alocated = false;
            bool IndexOutOfRange = index < 0 || index > count;
            if (IndexOutOfRange) throw new IndexOutOfRangeException("Некорректный индекс");
            int new_count = count + 1;
            if (new_count > capacity)
            {
                if (capacity > int.MaxValue / 2) throw new Exception("Переполнение переменной, размера массива");
                int new_capacity = capacity * 2;
                if (balance < Cost(new_capacity)) throw new Exception("Кончился баланс");
                MakeArray(new_capacity);
                balance -= Cost(new_capacity);
            }
            for (int i = count - 1; i >= index; i--)
            {
                array[i + 1] = array[i];
                if (is_alocated == false) balance += 3;
                
            }
            array[index] = itm;
            count = new_count;
        }
```

В данном примере, можно улучшить читаемость путем добавления булевых переменных.

```csharp
public bool IsSubset(PowerSet<T> set2)
        {
            // возвращает true, если set2 есть
            // подмножество текущего множества,
            // иначе false
            bool IsSubsetBiger = set2.Size() > Size();
            if (IsSubsetBiger) return false;
            for (int i = 0; i < set2.size; i++)
            {
                if (!object.Equals(set2.slots[i], default(T)) && !this.Get(set2.slots[i])) return false;
            }
            return true;
        }
```
