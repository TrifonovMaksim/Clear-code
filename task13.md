# Массивы. Задание.

**Приведите 5 примеров вашего кода, где вместо массивов можно использовать более безопасные структуры данных, или же работа с самими массивами может выполняться без их прямой индексации.**

```csharp
 public void Insert(T itm, int index)
        {
            if (index < 0 || index > count) throw new IndexOutOfRangeException("Некорректный индекс");
            int new_count = count + 1;
            if (new_count > capacity) MakeArray(capacity * 2);
            for (int i = count - 1; i >= index; i--)
            {
                array[i + 1] = array[i];
            }
            array[index] = itm;
            count = new_count;
        }

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

В данном примере, вместо копирования через индексы массива, для более безопасной работы, можно использовать встроенный метод Array.Copy.

```csharp
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

В данном примере, вместо прохода по массиву через инндексы, для исключения выхода за границы, можно было использовать foreach.

```csharp
       public List<string> GetAll()
        {
            // возвращает список со всеми значениями и их частотой
            List<string> lst = new List<string>();
            for (int i = 0; i < size; i++)
            {
                if (!object.Equals(slots[i], default(T)))
                {
                    lst.Add(slots[i].ToString() + "," + count_array[i].ToString());
                }
            }
            return lst;
        }
```

В данном  примере, вместо прохода по массиву через индексы, для исключения выхода за границы, можно было использовать foreach.

```csharp
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
```

В данном примере, можно было бы обратиться к последнему элементу не через индекс, а через метод Last.

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

В данном примере, можно было бы использовать не массив строк, а список и обходить его не через индексы, а через foreach.