# Задания

**7.1. Приведите пять примеров правильного именования булевых переменных в вашем коде в формате "было - стало".**

flag - IsListFound
// Найден ли подсписок

shift - IsShifted
// Был ли сдвиг в цикле

is_alocated - IsAlocated
// Была ли выделена память

res - IsSimple
// Простое ли число

is_deleted - DeletedSlots
// Массив - индикатор, в котором в соответствующих индексах проставляется флаг удален был слот или нет


**7.2. Найдите несколько подходящих случаев, когда в вашем коде можно использовать типичные имена булевых переменных.**

flag - Found
// Найден ли подсписок

Is_Balanced - Ok
// Балансированл ли список


**7.3. Проверьте, правильно ли вы даёте имена индексам циклов. Попробуйте найти случай, когда вместо i j k нагляднее использовать более выразительное имя.**

```chasrp
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
i - IndexInSet
// Индекс в сете


**7.4. Попробуйте найти в своих решениях два-три случая, когда можно использовать пары имён - антонимы.**

```csharp
    public class Queue_on_stacks<T>
    {
        Stack<T> stack1;
        Stack<T> stack2;
        public Queue_on_stacks()
        {
            stack1 = new Stack<T>();
            stack2 = new Stack<T>();
        }

        public void Enqueue(T item)
        {
            stack1.Push(item);
        }

        public T Dequeue()
        {
            if (stack1.Size() == 0 && stack2.Size() == 0) return default(T);
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

        public int Size()
        {
            return stack1.Size() + stack2.Size(); // размер очереди
        }

    }
```
stack1 - StraightStack
stack2 - ReverseStack


**7.5. Всем ли временным переменным в вашем коде присвоены выразительные имена? Найдите несколько случаев, когда временные переменные надо переименовать, и поищите, возможно, от некоторых временных переменных вам получится вообще полностью избавиться.**

```csharp
 public void Delete(T val)
        {
            if (counter == 0)
            {
                Console.WriteLine("Список пустой");
                return;
            }
            if (Compare(head.value, val) == 0)
            {
                if (counter == 1)
                {
                    head = tail = null;
                    counter--;
                    return;
                }
                head = head.next;
                head.prev = null;
                counter--;
                return;
            }
            if (Compare(tail.value, val) == 0)
            {
                tail = tail.prev;
                tail.next = null;
                counter--;
                return;
            }
            Node<T> node = head;
            for (int i = 0; i < counter; i++)
            {
                if (Compare(val, node.value) == 0)
                {
                    Node<T> tmp = node.next;
                    tmp.prev = node.prev;
                    node.prev.next = tmp;
                    counter--;
                    return;
                }
                node = node.next;
            }
            Console.WriteLine("Несуществующее значение");
        }
```
tmp - NodeAfterDeleted
// Узел для сохраненияя значения после удаленного

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
tmp - NodeForSaveNextValue
// Узел для сохранения следуюзщего узла