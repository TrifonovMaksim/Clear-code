# Время жизни переменных. Задание.
   ```csharp
   public class Node
    {
        internal int value;
        internal Node next;
    }

    public class LinkedList
    {
        private Node head;
        private Node tail;
```

В данном примере поля класса Node сделал видимыми только в рамках проекта, а поля класса LinkedList приватными.

```csharp
 public class BloomFilter
    {
        private int filter_len;
        private int bloom_filter;
```

В данном примере поля класса BloomFilter сделал приватными, так как они используются только внутри класса.

```csharp
  class Deque<T>
    {
        private LinkedList<T> deque;
        private int size;
```

В данном примере поля класса Deque сделал приватными, так как они используются только внутри класса.

```csharp
 public class DynArray<T>
    {
        private T[] array;
        private int count;
        private int capacity;
```

В данном примере поля класса DynArray сделал приватными, так как они используются только внутри класса.

```csharp
 public class BankDynArray<T>
    {
        private T[] array;
        private int count;
        private int capacity;
        private int balance;
```

В данном примере поля класса BankDynArray сделал приватными, так как они используются только внутри класса.

```csharp
  public class HashTable
    {
        private int size;
        private int step;
        private string[] slots;
        private int fullnes;
```

В данном примере поля класса HashTable сделал приватными, так как они используются только внутри класса.

```csharp
 public class DynHashTable
    {
        private string[] slots;
        private int count;
        private int size;
        private int step;
```

В данном примере поля класса DynHashTable сделал приватными, так как они используются только внутри класса.

```csharp
  public class DynDoubleHashTable
    {
        private string[] slots;
        private int count;
        private int size;
```

В данном примере поля класса DynDoubleHashTable сделал приватными, так как они используются только внутри класса.

```csharp
public class HashTableWithSalt
    {
        private int size;
        private int step;
        private string[] slots;
        private int fullnes;
```

В данном примере поля класса HashTableWithSalt сделал приватными, так как они используются только внутри класса.

```csharp
  public class Node
    {
        internal int value;
        internal Node next, prev;

        internal Node(int _value)
        {
            value = _value;
            next = null;
            prev = null;
        }
    }

    public class LinkedList2
    {
        private Node head;
        private Node tail;
```

В данном примере поля класса Node сделал видимыми только в рамках проекта, а поля класса LinkedList2 приватными.

```csharp
  public class NativeCache<T>
    {
        private int size;
        private string[] slots;
        private T[] values;
        private int[] hits;
        private int counter;
```

В данном примере поля класса NativeCache сделал приватными, так как они используются только внутри класса.

```csharp
  public class NativeDictionary<T>
    {
        private int size;
        private string[] slots;
        private T[] values;
```

В данном примере поля класса NativeDictionary сделал приватными, так как они используются только внутри класса.

```csharp
    public class Node<T>
    {
        internal T value;
        internal Node<T> next, prev;

        internal Node(T _value)
        {
            value = _value;
            next = null;
            prev = null;
        }
    }

    public class OrderedList<T>
    {
        private Node<T> head, tail;
        private bool _ascending;
        private int counter;
```

В данном примере поля класса Node сделал видимыми только в рамках проекта, а поля класса OrderedList приватными.

```csharp
   public class PowerSet<T>
    {
        private int size;
        private T[] slots;
        private int count;
        private bool[] is_deleted;
```

В данном примере поля класса PowerSet сделал приватными, так как они используются только внутри класса.

```csharp
  public class Stack<T>
    {
        private List<T> stack;
        private int stack_size;
        private int tail;
```

В данном примере поля класса Stack сделал приватными, так как они используются только внутри класса.