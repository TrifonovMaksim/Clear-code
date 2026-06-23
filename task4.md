# Имена, которых следует избегать. Задания

**Найдите 12 примеров имён в вашем коде, которые следует избегать, исправьте, и выложите на гитхаб в формате "было - стало" (с учётом контекста).**

 ```csharp
  public void Reverse()
        {
            if (head == null || head == tail) return;
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

В данном примере имя tmp и node, неинформативны. 
tmp - NodeToSaveNextNode
// Временный узел для обмена данными
node - CurrentNode
// Текущий узел с которым работаем


```csharp
   // Задание 11 Добавьте метод, сортирующий список.
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

В данном примере имена tmp_linked_list, min_node, node неинформативны.

tmp_linked_list - SortedLinkedList
// Отсортированный список

min_node - NodeWithMinValue
// Узел с минимальным значением

node - CurrentNode
// Текущий узел с которым работаем


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

В данном примере есть много недочетов. Имена с цифрами list1, list2, node1, node2. Имя стандартного типа res_list.

list1 - FirstList
// Первый список

list2 - SecondList
// Второй список 

node1 - FirstListNode
// Узел первого списка

node2 - SecondListNode
// Узел второго списка

res_list - MergedList
// Суммарный лист двух связных списков


```csharp
   public int Compare(T v1, T v2)
        {
            int result = 0;
            if (typeof(T) == typeof(String))
            {
                // версия для лексикографического сравнения строк
                string a = ((string)((object)v1)).Trim();
                string b = ((string)((object)v2)).Trim();
                int res = a.CompareTo(b);
                if (res > 0) result = 1;
                if (res < 0) result = -1;
            }
            else
            {
                // универсальное сравнение
                IComparable a = (IComparable)((object)v1);
                IComparable b = (IComparable)((object)v2);
                int res = a.CompareTo(b);
                if (res > 0) result = 1;
                if (res < 0) result = -1;
            }

            return result;
            // -1 если v1 < v2
            // 0 если v1 == v2
            // +1 если v1 > v2
        }
```
В данном примере неинформативные имена a, b. Имена стандартного типа result, res. Также result, res это похожие имена.

a - FirstValueToCompare
// Первое значение для сравнения

b - SecondValueToCompare
// Второе значение для сравнения

result - CompareResult
// Итог сравнения переменных

res - IcomparableResult
// Результат встроенного метода Icomparable
