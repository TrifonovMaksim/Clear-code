# Задание


**6.1.**

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
            return res_list;
        }
```
В данном примере можно нагляднее назвать переменные:

node1 - FirstListNode  
// Узел первого списка

node2 - SecondListNode  
// Узел второго списка

res_list - MergedLists  
// Объединеный список

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
            this.head = tmp_linked_list.head;
            this.tail = tmp_linked_list.tail;
        }
```
В данном примере можно нагляднее назвать переменные:

tmp_linked_list - SortedList  
// Отсортированный список

min_node - MinValueNode  
// Узел с минимальным значением


**6.2.**

```csharp  
public class BloomFilter
    
        public int filter_len;
        public int bloom_filter;
``` 
В данном примере исполизовал имя - термин bloom_filter.

```csharp   
public int HashFun(string value, int i)
        {
            // всегда возвращает корректный индекс слота
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
В данном примере использовал имена - термины h1 и h2.

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
            return false;
        }
```
В данном примере использовал имена - термины slow_pointer и fast_pointer.

```csharp  
public int? Find_Index(T val)
        {
            if (list.Count() == 0) return null;
            if (Compare(list.First(), val) == 0) return 0;
            if (Compare(list.Last(), val) == 0) return list.Count() - 1;
            int min_index = 0;
            int max_index = list.Count() - 1;
            if (_ascending == true)
            {
                while (min_index <= max_index)
                {
                    int middle = (max_index + min_index) / 2;
                    if (Compare(list[middle], val) == 0)
                    {
                        return middle;
                    }
                    if (Compare(list[middle], val) == -1)
                    {
                        min_index = middle + 1;
                        continue;
                    }
                    if (Compare(list[middle], val) == +1)
                    {
                        max_index = middle - 1;
                        continue;
                    }
                }
            }
            if (_ascending == false)
            {
                while (min_index <= max_index)
                {
                    int middle = (max_index + min_index) / 2;
                    if (Compare(list[middle], val) == 0)
                    {
                        return middle;
                    }
                    if (Compare(list[middle], val) == -1)
                    {
                        max_index = middle - 1;
                        continue;
                    }
                    if (Compare(list[middle], val) == +1)
                    {
                        min_index = middle + 1;
                        continue;
                    }
                }
            }
            return null;
        }
```

В данном примере middle имя термин и можно было бы назвать min и max index, как left и right.

**6.3.**

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
            return false;
        }
```

В данном примере, slow и fast pointer, даны с учетом контекста метода, мы идем двумя указателями и названия показывают чем они отличаются.

```csharp  
public class BloomFilter
    
        public int filter_len;
        public int bloom_filter;
``` 

В данном примере bloom_filter показывает, что в контексте класса эта переменная является фильтром.

```csharp  
static public void Is_Balanced(string str)
        {
            Stack<char> stack = new Stack<char>();
            bool Is_Balanced = true;
            foreach (char s in str)
            {
                if (s == '(') stack.Push(s);

                else
                {
                    if (stack.Pop() != '(')
                    {
                        Is_Balanced = false;
                        break;
                    }
                }
            }
            if (stack.stack_size != 0) Is_Balanced = false;
            Console.WriteLine( Is_Balanced == true ? "Последовательность сбалансированна" : "Последовательность не сбалансированна");
        }
```

В данном примере Is_Balanced в контексте функции показывает, что она показывает баланс.


**6.4.**

stack - BracketsStack  
// Стек для хранения скобок

chars - InputString  
// Строка с входными значениями

count - ElementsQuantity  
// Количество элементов в массиве

flag - IsSublist  
// Есть ли подсписок

shift - IsShifted  
// Был ли сдвиг во вложенном цикле
