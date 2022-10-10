#  Java 知识体系

## Java 基础

### <font color="#7A5FFF">Java 基础 — 面向对象</font>

####   <font color="#DF8400">三大特性</font>

- ##### <font color="#0091FF">封装</font>

  - 利用抽象数据类型将**数据**和**基于数据的操作**封装在一起，使其构成一个不可分割的独立实体。
  - 数据被保护在抽象数据类型的内部，尽可能地**隐藏内部的细节**，只保留一些**对外的接口**使之与外部发生联系。
  - 用户无需知道对象内部的细节，但可以通过对象对外提供的接口来访问该对象
  - 四种访问权限修饰符：
    - **==private==（当前访问权限）**：这个成员只能在当前类的内部被访问
    - **==*default*==（包访问权限）**：这个成员或外部类可以被相同包下的其他类访问
    - **==protected==（子类访问权限）**：这个成员既可以被同一个包的其他类访问，也可以被不同包中的子类访问
    - **==public==（公共访问权限）**：这个成员或外部类可以被所有类访问

- ##### <font color="#0091FF">继承</font>

  - 继承体现了 IS-A 关系，子类继承父类，从而获得父类**非 private 的属性和方法**
  - 继承应该遵循**里氏替换原则**，子类对象必须能够替换掉所有父类对象
  - 父类引用指向子类对象成为**向上转型**
  - Java 只支持单继承和多层继承，不允许多重继承

- ##### <font color="#0091FF">多态</font>

  - 多态分为**编译时多态**和**运行时多态**：
    - 编译时多态主要指方法的重载
    - 运行时多态指程序中定义的对象引用所指向的具体类型在运行期间才确定
  - 运行时多态有三个条件
    - 继承
    - 覆盖（重写）
    - 向上转型
  - 对象的多态性：把一个子类对象直接赋给一个父类引用变量（**父类引用指向子类对象**或**向上转型**）
  - 当把一个子类对象直接赋给父类引用变量时，编译时类型是父类类型，而运行时类型是子类类型，当运行时调用该引用变量的方法时，其**方法行为总是表现出子类方法的特征**，这就可能出现：<font color="#EF042A">**相同类型的变量，调用同一个方法时呈现出多种不同的行为特征**</font>，这就是**多态**
  - 引用变量在编译阶段只能调用其编译时类型所具有的方法，但运行时则执行它运行时类型所具有的方法。因此，在编写 Java 代码的时，<font color="#EF042A">**引用变量只能调用声明该变量时所用类型包含的方法**</font>

#### <font color="#DF8400">类和对象</font>

- 类是具有相同特征或行为的一种抽象
- 对象是类的具体的实例

##### <font color="#0091FF">属性（成员变量）</font>

- 变量的分类：

  - <font color="#4EB434">**成员变量：**</font>定义在类里的变量

    - 实例变量（不以 static 修饰）：作用域与<font color="#EF042A">**对应实例**</font>的生存范围相同
    - 类变量（以 static 修饰）：作用域与这个<font color="#EF042A">**类**</font>的生存范围相同

    >成员变量无须显示初始化，当一个对象被创建时，会对其中的**成员变量**进行初始化赋值

  - <font color="#4EB434">**局部变量**</font>

    - 形参（方法、构造器中定义的变量）：在整个**方法**内有效
    - 方法局部变量（在方法中定义）：从**定义该变量的地方生效，到该方法结束失效**
    - 代码块局部变量（在代码块中定义）：从**定义该变量的地方生效，到该方法结束失效**

    >局部变量除**形参**外，都必须显示初始化

- 一个类里不能定义两个同名的成员变量，一个方法里不能定义两个同名的方法局部变量，方法局部变量与形参也不能同名
- 如果方法里的局部变量和成员变量同名，**局部变量会覆盖成员变量**，如果需要在这个方法引用被覆盖的成员变量，则可使用 **this （对于实例变量）或类名（对于类变量）**作为调用者来限定访问成员变量

##### <font color="#0091FF">方法</font>

- 方法是类或对象行为特征的抽象，不能独立存在，必须定义在类里
  - **形参：**方法声明时的参数
  - **实参：**方法调用时实际传给形参的参数值
- <font color="#4EB434">**方法的值传递机制**：</font>
  - Java 中方法的参数传递方式只有一种：<font color="#EF042A">**值传递**</font>，即将实际参数值的副本传入方法内，参数本身不受影响
  - **值传递的实质：**当系统开始执行方法时，系统位形参执行初始化，将实参变量的值赋给方法的形参，方法里操作的并不是实参变量
- <font color="#4EB434">**方法重载：**</font>
  - 在同一个类中，允许存在一个以上的同名方法，只要它们的**形参列表**（参数个数或类型）不同就行
  - **与返回值类型无关**，要求**两同一不同**：同一类中方法名相同，参数列表不同
- <font color="#4EB434">**方法重写（Override）：**</font>
  - 子类继承父类后，对从父类继承的方法进行改造，成为方法重写（方法覆盖）
  - 方法重写遵循 **“两同两小一大”** 规则：
    - **两同：**<font color="#EF042A">**方法名**</font>相同，<font color="#EF042A">**形参列表**</font>相同
    - **两小：**子类方法的<font color="#EF042A">**返回值类型**</font>小于或等于父类的，子类方法声明<font color="#EF042A">**抛出的异常类**</font>小于或等于父类的
    - **一大：**子类方法的<font color="#EF042A">**访问权限**</font>大于或等于父类的
  - ==**注意**==：方法重写的方法必须同时声明为类方法（不是重写）或实例方法
  - 当子类覆盖了父类方法后，子类对象将无法访问父类中被覆盖的方法，但可以在子类中**调用父类中被覆盖的方法**。使用 **super （被覆盖的是实例方法）**或者**父类类名（被覆盖的是类方法）**作为调用者来调用父类中被覆盖的方法

##### <font color="#0091FF">构造器</font>

- 通过构造器来创建对象并给对象进行初始化
- 构造器的**特征**：
  - 构造器名必须**与类名相同**
  - 构造器**没有返回值类型**
  - 不能被static、final、synchronized、abstract、native修饰，不能有 return语句返回值
- Java 语言中，每个类至少有一个构造器
- 系统默认为每一个类提供一个**默认无参构造器**
- 一个类可以创建多个重载的构造器，一旦显示定义了构造器，系统不再提供默认构造器
- **父类的构造器不能被子类继承**

##### <font color="#0091FF">代码块</font>

- 通过代码块对对象进行初始化
- 相同类型的初始化块之间由顺序：前面定义的初始化块先执行，后面定义的初始化块后执行
- <font color="#4EB434">**静态代码块：**</font>用 static 修饰的代码块
  - **不能**调用非静态的属性和方法
  - 执行**优先于**非静态代码块
  - **静态代码块随着类的加载而加载，且只执行一次**
- <font color="#4EB434">**非静态代码块：**</font>没有 static 修饰的代码块
  - **每次创建对象的时候，都会执行一次**
  - 在**构造器之前**执行

##### <font color="#0091FF">this 关键字</font>

- 根据 this 出现的位置不同，this 作为对象的默认引用有两种情形：
  - **<font color="#4EB434">构造器中：</font>引用正在初始化的对象**
  - **<font color="#4EB434">方法中：</font>引用调用该方法的对象**
- 在构造器中使用 **this 调用另一个重载的构造器**时，必须作为**构造器执行体的第一条语句**
- 对于 static 修饰的方法而言，则可以使用类直接调用该方法。**static 修饰的方法不能使用 this 引用。**

##### <font color="#0091FF">super 关键字</font>

- super 关键字用于限定该对象调用它从**父类继承得到的实例变量或方法**，**不能出现在 static 修饰的方法中**
- 子类中的所有构造器**默认总会调用父类的无参构造器**
- 当父类中没有空参数的构造器时，子类的构造器必须通过**this(参 数列表)**或者**super(参数列表)**语句指定调用本类或者父类中相应的 构造器。同时，只能**“二选一”** ，且必须放在**构造器的首行**

##### <font color="#0091FF">static 关键字</font>

- static 可以修饰**属性、方法、代码块、内部类**
- 被 static 修饰的成员的<font color="#4EB434">**特点：**</font>
  - 随着类的加载而加载
  - 优先于对象存在
  - 修饰的成员被所有对象所共享
  - 访问权限允许时，可以不创建对象，直接被类调用
- <font color="#4EB434">**类变量：**</font>
  - 类变量由该类的所有实例共享
  - 不用创建对象就可以访问静态成员 `类名.类属性`
- <font color="#4EB434">**类方法：**</font>
  - 不用创建对象就可以访问静态成员 `类名.方法名()`
  - static 方法内部**只能访问 static 修饰的属性或方法**，不能访问非 static 的结构
  - static 方法内**不能有 this 和 super**
  - static 修饰的方法**不能被重写**

##### <font color="#0091FF">final 关键字</font>

- final 关键字可用于修饰**类、变量和方法**。final修饰变量时，表示该变量一旦获得初始值就不可被改变
- <font color="#4EB434">**final 类**</font>：
  - final 修饰的类不可以有子类，即**不可被继承**
- <font color="#4EB434">**final 变量：**</font>
  - **final 成员变量：**必须由程序员**显示地指定初始值**
  - **final 局部变量：**可以在定义时指定默认值，也可以在后续代码中赋值，但不能重复赋值。final 修饰的形参由传入的参数完成初始化，不能被赋值
- <font color="#4EB434">**final 方法：**</font>
  - final 修饰的方法**不可被重写**，但可以被重载
  - 对于一个 private 修饰的方法，子类无法重写该方法，如果子类定义了一个完全相同的方法，不是方法重写，只是重新定义了一个新的方法，因此即使使用 final 修饰，也可以在子类中定义完全相同的方法

#### <font color="#DF8400">抽象类</font>

- 抽象类和抽象方法必须使用 **abstract 修饰符**来定义
- 有抽象方法的类只能被定义为抽象类，抽象类里可以没有抽象方法
- <font color="#4EB434">**抽象方法：**</font>
  - 抽象方法不能有方法体
  - 非默认抽象方法必须被子类重写
- <font color="#4EB434">**抽象类：**</font>
  - 抽象类不能被实例化
  - 抽象类可以包含**成员变量、方法（普通方法和抽象方法）、构造器、初始化块、内部类（接口、枚举）**
  - 抽象类的构造器不能用于创建实例，主要用于被子类调用
- <font color="#4EB434">注意：</font>
  - final 和 abstract 不能同时使用
  - private 和 abstract 不能同时修饰方法
  - static 和 abstract 不能同时修饰方法，但可以修饰内部类

#### <font color="#DF8400">接口</font>

- 接口时抽象方法和常量定义的集合，使用 **interface 关键字**定义
- 接口中**不能包含构造器和初始化块**
- 接口中可以包含**成员变量（静态常量）、方法（抽象实例方法、类方法、默认方法或私有方法）、内部类（内部接口、枚举）**
- <font color="#4EB434">**成员变量：**</font>
  - 只能是**静态常量**，默认是由 public static final 修饰
- <font color="#4EB434">**方法：**</font>
  - **抽象实例方法：**即普通方法，默认是由 public abstract 修饰
  - **类方法：**由 public static 修饰
  - **默认方法：**必须使用 default 修饰，不能使用 static 修饰
  - **私有方法：**由 private 修饰，可以有方法体，但不能使用 default 修饰，可以使用 static 修饰
  - 接口里的普通方法不能有方法实现（方法体），但类方法、默认方法、私有方法都必须有方法实现（方法体）
- 接口完全**支持多继承**
- 接口不能用于创建实例，但可以用于声明引用变量类型变量，这个变量必须**引用到其实现类的对象**
- 一个类可以实现一个或多个接口，实现接口与继承父类相似，可以获得所实现接口里定义的常量、方法
- 一个类实现了一个或多个接口之后，这个类**必须完全实现这些接口里定义的全部抽象方法（也就是重写这些抽象方法）**，否则该类也必须定义为抽象类



### <font color="#7A5FFF">Java 基础 — 泛型机制</font>



### <font color="#7A5FFF">Java 基础 — 注解机制</font>



### <font color="#7A5FFF">Java 基础 — 异常机制</font>



### <font color="#7A5FFF">Java 基础 — 反射机制</font>



## Java 集合框架

### <font color="#7A5FFF">类关系图</font>

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\Collection.png" alt="Collection"  />



### <font color="#7A5FFF">Collection — ArrayList 源码解析</font>

#### <font color="#DF8400">ArrayList 概述</font>

- ArrayList 是实现了 List 接口的顺序容器，允许放入包括 `null` 在内的所有元素，底层通过**数组**实现
- 每个 ArrayList 实例都有一个容量，表示用来存储元素的数组的大小。当向容器内添加元素时，如果容量不足，容器会自动增大底层数组的大小
- ArrayList 没有实现同步，如果需要多个线程并发访问，可以手动同步，也可以使用 Vector 代替

![ArrayList_base](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\ArrayList_base.png)

#### <font color="#DF8400">ArrayList 的实现</font>

##### <font color="#0091FF">底层数据结构</font>

```java
// 默认初始容量为 10
private static final int DEFAULT_CAPACITY = 10;
// 用于空实例的共享空数组实例
private static final Object[] EMPTY_ELEMENTDATA = {};
// 用于默认大小的空实例的共享空数组实例
private static final Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};
// 存放元素的数组
transient Object[] elementData; // non-private to simplify nested class access
// 数组种包含的元素个数
private int size;
// 数组的最大上限
private static final int MAX_ARRAY_SIZE = Integer.MAX_VALUE - 8;
```

##### <font color="#0091FF">构造器</font>

```java
public ArrayList(int initialCapacity) {
    if (initialCapacity > 0) {
        this.elementData = new Object[initialCapacity];
    } else if (initialCapacity == 0) {
        this.elementData = EMPTY_ELEMENTDATA;
    } else {
        throw new IllegalArgumentException("Illegal Capacity: "+ initialCapacity);
    }
}

public ArrayList() {
    this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
}

public ArrayList(Collection<? extends E> c) {
    Object[] a = c.toArray();
    if ((size = a.length) != 0) {
        if (c.getClass() == ArrayList.class) {
            elementData = a;
        } else {
            elementData = Arrays.copyOf(a, size, Object[].class);
        }
    } else {
        // replace with empty array.
        elementData = EMPTY_ELEMENTDATA;
    }
}
```

>- 默认初始化为一个大小为 0 的空数组
>- 指定初始化大小的时候，初始化为所指定大小的数组

##### <font color="#0091FF">自动扩容</font>

```java
public void ensureCapacity(int minCapacity) {
    if (minCapacity > elementData.length
        && !(elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA
             && minCapacity <= DEFAULT_CAPACITY)) {
        modCount++;
        grow(minCapacity);
    }
}

private Object[] grow(int minCapacity) {
    return elementData = Arrays.copyOf(elementData, newCapacity(minCapacity));
}

private Object[] grow() {
    return grow(size + 1);
}

private int newCapacity(int minCapacity) {
     // overflow-conscious code
     int oldCapacity = elementData.length;
     int newCapacity = oldCapacity + (oldCapacity >> 1);
     if (newCapacity - minCapacity <= 0) {
         if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA)
             return Math.max(DEFAULT_CAPACITY, minCapacity);
         if (minCapacity < 0) // overflow
             throw new OutOfMemoryError();
         return minCapacity;
     }
     return (newCapacity - MAX_ARRAY_SIZE <= 0)
         ? newCapacity
         : hugeCapacity(minCapacity);
 }

private static int hugeCapacity(int minCapacity) {
    if (minCapacity < 0) // overflow
        throw new OutOfMemoryError();
    return (minCapacity > MAX_ARRAY_SIZE)
        ? Integer.MAX_VALUE
        : MAX_ARRAY_SIZE;
}
```

>数组进行扩容时，会将老数组种的元素拷贝一份到新数组种，**每次数组容量扩大为原容量的<font color="#EF042A"> 1.5 倍</font>**
>
>`int newCapacity = oldCapacity + (oldCapacity >> 1);`

#### <font color="#DF8400">常用方法</font>

##### <font color="#0091FF">add()、addAll() 方法</font>

```java
private void add(E e, Object[] elementData, int s) {
    if (s == elementData.length)
        elementData = grow();
    elementData[s] = e;
    size = s + 1;
}

public boolean add(E e) {
    modCount++;
    add(e, elementData, size);
    return true;
}

public void add(int index, E element) {
    rangeCheckForAdd(index);
    modCount++;
    final int s;
    Object[] elementData;
    if ((s = size) == (elementData = this.elementData).length)
        elementData = grow();
    System.arraycopy(elementData, index, elementData, index + 1, s - index);
    elementData[index] = element;
    size = s + 1;
}

public boolean addAll(Collection<? extends E> c) {
    Object[] a = c.toArray();
    modCount++;
    int numNew = a.length;
    if (numNew == 0)
        return false;
    Object[] elementData;
    final int s;
    if (numNew > (elementData = this.elementData).length - (s = size))
        elementData = grow(s + numNew);
    System.arraycopy(a, 0, elementData, s, numNew);
    size = s + numNew;
    return true;
}

public boolean addAll(int index, Collection<? extends E> c) {
    rangeCheckForAdd(index);
    Object[] a = c.toArray();
    modCount++;
    int numNew = a.length;
    if (numNew == 0)
        return false;
    Object[] elementData;
    final int s;
    if (numNew > (elementData = this.elementData).length - (s = size))
        elementData = grow(s + numNew);
    int numMoved = s - index;
    if (numMoved > 0)
        System.arraycopy(elementData, index, elementData, index + numNew, numMoved);
    System.arraycopy(a, 0, elementData, index, numNew);
    size = s + numNew;
    return true;
}
```

> - 在插入元素之前，**先检查是否需要扩容**，然后将元素添加到数组最后一个元素的后面
> - 当使用无参构造器创建 ArrayList 时，数组的大小为 0，只要在使用的时候，才通过 grow() 方法创建一个大小为 10 的数组

##### <font color="#0091FF">set() 方法</font>

```java
public E set(int index, E element) {
    Objects.checkIndex(index, size);
    E oldValue = elementData(index);
    elementData[index] = element;
    return oldValue;
}
```

> 直接对数组指定索引位置赋值

##### <font color="#0091FF">get() 方法</font>

```java
 public E get(int index) {
     Objects.checkIndex(index, size);
     return elementData(index);
 }
```

> 返回对应索引位置的元素

##### <font color="#0091FF">remove() 方法</font>

```java
 public E remove(int index) {
     Objects.checkIndex(index, size);
     final Object[] es = elementData;
     @SuppressWarnings("unchecked") E oldValue = (E) es[index];
     fastRemove(es, index);
     return oldValue;
 }

 private void fastRemove(Object[] es, int i) {
     modCount++;
     final int newSize;
     if ((newSize = size - 1) > i)
         System.arraycopy(es, i + 1, es, i, newSize - i);
     es[size = newSize] = null;
 }
```

> 删除指定索引的元素，需要将删除点之后的元素向前移动一个位置

##### <font color="#0091FF">trimToSize() 方法</font>

```java
public void trimToSize() {
    modCount++;
    if (size < elementData.length) {
        elementData = (size == 0) ? EMPTY_ELEMENTDATA : Arrays.copyOf(elementData, size);
    }
}
```

> 将底层数组的容量调整为当前列表保存的实际元素的大小

##### <font color="#0091FF">indexOf()、lastIndexOf() 方法</font>

```java
public int indexOf(Object o) {
    return indexOfRange(o, 0, size);
}

int indexOfRange(Object o, int start, int end) {
    Object[] es = elementData;
    if (o == null) {
        for (int i = start; i < end; i++) {
            if (es[i] == null) {
                return i;
            }
        }
    } else {
        for (int i = start; i < end; i++) {
            if (o.equals(es[i])) {
                return i;
            }
        }
    }
    return -1;
}

public int lastIndexOf(Object o) {
    return lastIndexOfRange(o, 0, size);
}

int lastIndexOfRange(Object o, int start, int end) {
    Object[] es = elementData;
    if (o == null) {
        for (int i = end - 1; i >= start; i--) {
            if (es[i] == null) {
                return i;
            }
        }
    } else {
        for (int i = end - 1; i >= start; i--) {
            if (o.equals(es[i])) {
                return i;
            }
        }
    }
    return -1;
}
```

> indexOf 获取元素第一次出现的 index，通过遍历比较数组中的每个元素来查找的
>
> lastIndexOf 获取元素最后一次出现的 index，原理与 indexOf 一样

#### <font color="#DF8400">Fail-Fast 机制</font>

- ArrayList 也采用了快速失败的机制，通过记录 modCount 参数来实现。在面对并发修改时，迭代器很快就会完全失败，而不是冒着在将来某个不确定时间发生人员不确定行为的风险

### <font color="#7A5FFF">Collection — LinkedList 源码解析</font>

#### <font color="#DF8400">LinkedList 概述</font>

- LinkedList 同时实现了 List 接口和 Deque 接口，它既可以看作一个顺序容器，又可以看作一个队列，同时还可以看作一个栈
- LinkedList 通过一个**双向链表**来实现，允许插入所有元素，包括 `null`
- LinkedList 没有实现同步，如果需要多个线程并发访问，可以先采用 `Collections.synchornizedList()` 方法对其进行包装

![LinkedList_base](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\LinkedList_base.png)

#### <font color="#DF8400">LinkedList 的实现</font>

##### <font color="#0091FF">底层数据结构</font>

```java
// 链表节点个数
transient int size = 0;
// 指向头节点的指针
transient Node<E> first;
// 指向尾节点的指针
transient Node<E> last;

private static class Node<E> {
    E item;
    Node<E> next;
    Node<E> prev;

    Node(Node<E> prev, E element, Node<E> next) {
        this.item = element;
        this.next = next;
        this.prev = prev;
    }
}
```

> LinkedList 底层通过双向链表实现，双向链表的每个节点用内部类 Node 表示
>
> LinkedList 通过 `first` 和 `last` 引用分别指向链表的第一个和最后一个元素。当链表为空时，`first` 和 `last` 都指向 `null`

##### <font color="#0091FF">构造器</font>

```java
public LinkedList() {
}

public LinkedList(Collection<? extends E> c) {
    this();
    addAll(c);
}
```

#### <font color="#DF8400">常用方法</font>

##### <font color="#0091FF">add()</font>

```java
public boolean add(E e) {
    linkLast(e);
    return true;
}

void linkLast(E e) {
    final Node<E> l = last;
    // 当前节点的前驱节点指向尾节点，后继节点指向 null
    final Node<E> newNode = new Node<>(l, e, null);
    // 尾节点指向新的尾结点
    last = newNode;
    // 如果原来有尾节点，则更新原来节点的后继节点，否则更新头指针
    if (l == null)
        first = newNode;
    else
        l.next = newNode;
    size++;
    modCount++;
}
```

> `add(E e)` 方法在 LinkedList 的末尾插入元素。当前节点的后继节点为 `null`，前驱节点为 `last` 指针指向的节点，然后还要修改 `last` 指针指向新的尾节点，修改原来尾节点的后继指针指向新的尾节点

```java
public void add(int index, E element) {
    checkPositionIndex(index);
    if (index == size)
        linkLast(element);
    else
        linkBefore(element, node(index));
}

void linkBefore(E e, Node<E> succ) {
    // assert succ != null;
    // 指定节点的前驱节点
    final Node<E> pred = succ.prev;
    // 当前节点的前驱节点指向指定节点的前驱节点，后继节点指向指定的节点
    final Node<E> newNode = new Node<>(pred, e, succ);
    // 更新指定节点的前驱节点为当前节点
    succ.prev = newNode;
    // 如果指定节点是头节点，更新头节点为当前节点，否则，更新前驱节点的后继节点为当前节点
    if (pred == null)
        first = newNode;
    else
        pred.next = newNode;
    size++;
    modCount++;
}

// 查找指定索引处的节点
Node<E> node(int index) {
    // assert isElementIndex(index);
    if (index < (size >> 1)) { // 如果 index 靠近前端，从前往后遍历查找
        Node<E> x = first;
        for (int i = 0; i < index; i++)
            x = x.next;
        return x;
    } else { // 如果 index 靠近后端，从后往前遍历查找
        Node<E> x = last;
        for (int i = size - 1; i > index; i--)
            x = x.prev;
        return x;
    }
}
```

> `add(int index, E element)` 方法在指定下表处插入元素。
>
> 当 index == size 时，等同于 `add(E e)`。
>
> 否则，先通过 `node(int index)` 方法根据 index 找到要插入的位置，然后修改引用。当前节点的后继节点为指定节点，前驱节点为指定节点的前驱节点，然后还要修改前驱节点的后继节点为当前节点，以及后继节点的前驱节点为当前节点

##### <font color="#0091FF">removeFirst(), removeLast(), remove(Object o), remove(int index)</font>

```java
// 删除头节点，返回头节点元素的值
public E removeFirst() {
    final Node<E> f = first;
    if (f == null)
        throw new NoSuchElementException();
    return unlinkFirst(f);
}

private E unlinkFirst(Node<E> f) {
    // assert f == first && f != null;
    final E element = f.item;
    // 头节点的后继节点
    final Node<E> next = f.next;
    f.item = null;
    f.next = null; // help GC
    // 头节点指向后一个节点
    first = next; 
    // 如果原来只有一个头节点，将尾节点置为null，否则，新结点的前驱节点为 null
    if (next == null)
        last = null;
    else
        next.prev = null;
    size--;
    modCount++;
    return element;
}

//删除表尾节点，返回表尾元素的值
public E removeLast() {
    final Node<E> l = last;
    if (l == null)
        throw new NoSuchElementException();
    return unlinkLast(l);
}

private E unlinkLast(Node<E> l) {
    // assert l == last && l != null;
    final E element = l.item;
    // 尾节点的前驱节点
    final Node<E> prev = l.prev;
    l.item = null;
    l.prev = null; // help GC
    // 尾节点指向前一个节点
    last = prev;
    // 如果原来只有一个头节点，将头节点置为null，否则，新结点的后继节点为 null
    if (prev == null)
        first = null;
    else
        prev.next = null;
    size--;
    modCount++;
    return element;
}

// 删除指定元素的节点
public boolean remove(Object o) {
    if (o == null) {
        for (Node<E> x = first; x != null; x = x.next) {
            if (x.item == null) {
                unlink(x);
                return true;
            }
        }
    } else {
        for (Node<E> x = first; x != null; x = x.next) {
            if (o.equals(x.item)) {
                unlink(x);
                return true;
            }
        }
    }
    return false;
}

// 删除指定索引的节点
public E remove(int index) {
    checkElementIndex(index);
    return unlink(node(index));
}

E unlink(Node<E> x) {
    // assert x != null;
    final E element = x.item;
    // 当前节点的后继节点
    final Node<E> next = x.next;
    // 当前节点的前驱节点
    final Node<E> prev = x.prev;
    if (prev == null) { // 如果当前节点为头节点，更新头节点指向后一个节点
        first = next;
    } else {
        prev.next = next; // 否则，更新前驱节点的后继为当前节点的后继
        x.prev = null;
    }
    if (next == null) { // 如果当前节点为尾节点，更新尾节点指向前一个结点
        last = prev;
    } else {
        next.prev = prev; // 否则，更新后继节点的前驱为当前节点的前驱
        x.next = null;
    }
    x.item = null;
    size--;
    modCount++;
    return element;
}
```

> 移除元素，需要把当前节点的前驱节点的后继节点修改为当前节点的后继节点，以及当前节点的后继节点的前驱节点修改为当前节点的前驱节点

##### <font color="#0091FF">get(int index)、getFirst()、getLast()</font>

```java
// 获取指定索引位置的元素
public E get(int index) {
    checkElementIndex(index);
    return node(index).item;
}

// 获取第一个元素
public E getFirst() {
    final Node<E> f = first;
    if (f == null)
        throw new NoSuchElementException();
    return f.item;
}

// 获取最后一个元素
public E getLast() {
    final Node<E> l = last;
    if (l == null)
        throw new NoSuchElementException();
    return l.item;
}
```

##### <font color="#0091FF">clear()</font>

```java
public void clear() {
    // Clearing all of the links between nodes is "unnecessary", but:
    // - helps a generational GC if the discarded nodes inhabit
    //   more than one generation
    // - is sure to free memory even if there is a reachable Iterator
    for (Node<E> x = first; x != null; ) {
        Node<E> next = x.next;
        x.item = null;
        x.next = null;
        x.prev = null;
        x = next;
    }
    first = last = null;
    size = 0;
    modCount++;
}
```

> 循环遍历将 node 直接的引用关系赋空

##### <font color="#0091FF">set(int index, E element)</font>

```java
public E set(int index, E element) {
    checkElementIndex(index);
    Node<E> x = node(index);
    E oldVal = x.item;
    x.item = element;
    return oldVal;
}
```

> 修改指定索引位置的元素的值

##### <font color="#0091FF">Queue 方法</font>

```java
// 获取头节点的值，表头为空返回 null
public E peek() {
    final Node<E> f = first;
    return (f == null) ? null : f.item;
}
// 获取表头节点的值，表头为空抛出异常
public E element() {
    return getFirst();
}
// 获取表头节点的值，并删除表头节点，表头为空返回 null
public E poll() {
    final Node<E> f = first;
    return (f == null) ? null : unlinkFirst(f);
}
// 获取表头节点的值，并删除表头节点，表头为空抛出异常
public E remove() {
    return removeFirst();
}
// 添加元素到列表尾部
public boolean offer(E e) {
    return add(e);
}
```

##### <font color="#0091FF">Deque() 方法</font>

```java
// 添加元素到表头
public boolean offerFirst(E e) {
    addFirst(e);
    return true;
}
// 添加元素到表尾
public boolean offerLast(E e) {
    addLast(e);
    return true;
}
// 获取头节点的值，表头为空返回 null
public E peekFirst() {
    final Node<E> f = first;
    return (f == null) ? null : f.item;
}
// 获取尾节点的值，表尾为空返回 null
public E peekLast() {
    final Node<E> l = last;
    return (l == null) ? null : l.item;
}
// 获取表头节点的值，并删除表头节点，表头为空返回 null
public E pollFirst() {
    final Node<E> f = first;
    return (f == null) ? null : unlinkFirst(f);
}
// 获取表尾节点的值，并删除表尾节点，表尾为空返回 null
public E pollLast() {
    final Node<E> l = last;
    return (l == null) ? null : unlinkLast(l);
}
// 添加元素到表头
public void push(E e) {
    addFirst(e);
}
// 删除表头元素
public E pop() {
    return removeFirst();
}
// 删除第一个出现的元素
public boolean removeFirstOccurrence(Object o) {
    return remove(o);
}
// 删除最后一个出现的元素
public boolean removeLastOccurrence(Object o) {
    if (o == null) {
        for (Node<E> x = last; x != null; x = x.prev) {
            if (x.item == null) {
                unlink(x);
                return true;
            }
        }
    } else {
        for (Node<E> x = last; x != null; x = x.prev) {
            if (o.equals(x.item)) {
                unlink(x);
                return true;
            }
        }
    }
    return false;
}
```

### <font color="#7A5FFF">Map — HashSet & HashMap 源码解析</font>

#### <font color="#DF8400">HashMap 概述</font>

- HashMap 实现了 Map 接口，允许放入 `key` 为 `null` 和 `value` 为 `null` 的元素
- HashMap 基于哈希表实现，不保证元素的顺序，据需要该容器可能会对元素重新哈希，元素的顺序也会被重新打散，因此不同时间迭代同一个*HashMap*的顺序可能会不同
- 根据对冲突的处理方式不同，哈希表有两种实现方式，一种开放地址方式(Open addressing)，另一种是冲突链表方式(Separate chaining with linked lists)。**Java7 HashMap 采用的是冲突链表方式**
- 有两个参数可以影响 *HashMap* 的性能：**初始容量（initial capacity）和负载系数（load factor）**
  - 初始容量指定了初始 `table` 的大小
  - 负载系数用来指定自动扩容的临界值
  - 当 `entry` 的数量超过 `capacity * load_factor`时，容器将自动扩容并重新哈希
- 将对象放入到 *HashMap* 或 *HashSet* 时，需要关注 `hashCode()` 和 `equals()` 方法。**`hashCode()` 方法决定了对象会被存放到哪个 `bucket` 里，当多个对象的哈希值冲突时，`equals()` 方法决定了这下对象是否是“同一个对象”。**所以，如果要将自定义的对象放入到 *HashMap* 或 *HashSet* 中，需要重写 `hashCode()` 和 `equals()` 方法
- Java7，HashMap的内部存储结构是**数组 + 链表**
- Java8，HashMap的内部存储结构是**数组 + 链表 + 红黑树**

#### <font color="#DF8400">Java 7 HashMap</font>

![HashMap_base](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\HashMap_base.png)

##### <font color="#0091FF">底层数据结构</font>

```java
// 默认初始容量为 16
static final int DEFAULT_INITIAL_CAPACITY = 16;
// 最大容量上限为 2^30
static final int MAXIMUM_CAPACITY = 1 << 30;
// 默认负载因子为 0.75
static final float DEFAULT_LOAD_FACTOR = 0.75f;
// 哈希表
transient Entry<K,V>[] table;
// 哈希表中键值对的个数
transient int size;
// 哈希表被修改的次数
transient int modCount;
// 扩容阈值，通过 capacity * loadFactor 计算
int threshold;
// 负载因子
final float loadFactor;
```

##### <font color="#0091FF">构造器</font>

```java
public HashMap(int initialCapacity, float loadFactor) {
    if (initialCapacity < 0)
        throw new IllegalArgumentException("Illegal initial capacity: " +
                                           initialCapacity);
    if (initialCapacity > MAXIMUM_CAPACITY)
        initialCapacity = MAXIMUM_CAPACITY;
    if (loadFactor <= 0 || Float.isNaN(loadFactor))
        throw new IllegalArgumentException("Illegal load factor: " +
                                           loadFactor);
    // Find a power of 2 >= initialCapacity
    int capacity = 1;
    while (capacity < initialCapacity)
        capacity <<= 1;
    this.loadFactor = loadFactor;
    threshold = (int)Math.min(capacity * loadFactor, MAXIMUM_CAPACITY + 1);
    table = new Entry[capacity];
    useAltHashing = sun.misc.VM.isBooted() &&
        (capacity >= Holder.ALTERNATIVE_HASHING_THRESHOLD);
    init();
}

 public HashMap(int initialCapacity) {
     this(initialCapacity, DEFAULT_LOAD_FACTOR);
 }

public HashMap() {
    this.loadFactor = DEFAULT_LOAD_FACTOR; // all other fields defaulted
}
```

> - 当实例化一个 HashMap 时，系统会创建一个长度为 capacity 的 Entry 数组，这个长度在哈希表中被称为容量（Capacity），在这个数组中可以存放元素的位置称为“桶”（bucket）
> - 每个 bucket 中存储一个元素，即一个 Entry 对象，每个 Entry 对象可以带一个指向下一个元素的引用变量，因此，在一个 bucket 中肯生成一个 Entry 链且**新添加的元素作为链表的 <font color="#EF042A">head</font>**

##### <font color="#0091FF">数组扩容</font>

```java
void resize(int newCapacity) {
    Entry[] oldTable = table;
    int oldCapacity = oldTable.length;
    if (oldCapacity == MAXIMUM_CAPACITY) {
        threshold = Integer.MAX_VALUE;
        return;
    }

    Entry[] newTable = new Entry[newCapacity];
    boolean oldAltHashing = useAltHashing;
    useAltHashing |= sun.misc.VM.isBooted() &&
        (newCapacity >= Holder.ALTERNATIVE_HASHING_THRESHOLD);
    boolean rehash = oldAltHashing ^ useAltHashing;
    transfer(newTable, rehash);
    table = newTable;
    threshold = (int)Math.min(newCapacity * loadFactor, MAXIMUM_CAPACITY + 1);
}
```

> 当 HashMap 中元素的个数超过 capacity * loadFactor 时，就会进行数组扩容，将数组容量扩大一倍，然后重新计算每个元素在数组中的位置

##### <font color="#0091FF">put(K key, V value) 方法</font>

```java
public V put(K key, V value) {
    // 当 key 为 null 时，调用 putForNullKey 方法
    if (key == null)
        return putForNullKey(value);
    // 计算 hash 值
    int hash = hash(key);
    // 根据 hash 值查找对应 table 中的索引
    int i = indexFor(hash, table.length);
    // 如果 i 索引处的 Entry 不为 null，循环遍历 e 元素的下一个元素
    for (Entry<K,V> e = table[i]; e != null; e = e.next) {
        Object k;
        // 如果 key 相同，则替换 value 的值
        if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
            V oldValue = e.value;
            e.value = value;
            e.recordAccess(this);
            return oldValue;
        }
    }
    modCount++;
    // 如果 i 索引处的 Entry 为 null 或没有对应 key，将 key、value 添加到 i 索引处
    addEntry(hash, key, value, i);
    return null;
}

void addEntry(int hash, K key, V value, int bucketIndex) {
    // 如果 map 中的 key-value 对数超过了阈值，把 table 的长度扩容到原来的 2 倍
    if ((size >= threshold) && (null != table[bucketIndex])) {
        resize(2 * table.length);
        hash = (null != key) ? hash(key) : 0;
        bucketIndex = indexFor(hash, table.length);
    }
    // 创建 Entry 对象
    createEntry(hash, key, value, bucketIndex);
}

void createEntry(int hash, K key, V value, int bucketIndex) {
    // 获取指定 bucketIndex 索引处的 Entry
    Entry<K,V> e = table[bucketIndex];
    // 将新创建的 Entry 放入 bucketIndex 索引处，并让新的 Entry 指向原来的 Entry
    table[bucketIndex] = new Entry<>(hash, key, value, e);
    size++;
}
```

> `put(K key, V value)` 方法将指定的 `key, value` 添加到 `map` 中，先根据 key 计算 hash 值，根据 hash 值得到这个元素在数组中的位置，如果该位置已经存放其他元素，则遍历该位置上的链表，如果两个元素的 hash 相同且通过 equals 比较返回 true，则替换原来的value值，否则将当前节点插入到原链表的头部，如果该位置没有元素，则直接放到该位置上

![Java7HashMap之put方法](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\Java7HashMap之put方法.png)

##### <font color="#0091FF">get(Object key) 方法</font>

```java
public V get(Object key) {
    // 当 key 为 null 时，调用 getForNullKey() 方法
    if (key == null)
        return getForNullKey();
    // 调用 getEntry(key) 方法查找对应的 Entry
    Entry<K,V> entry = getEntry(key);
    return null == entry ? null : entry.getValue();
}

final Entry<K,V> getEntry(Object key) {
    // 计算 key 对应的 hash 值
    int hash = (key == null) ? 0 : hash(key);
    // 获取 hash 索引处的 Entry，并遍历冲突链表
    for (Entry<K,V> e = table[indexFor(hash, table.length)];
         e != null;
         e = e.next) {
        Object k;
        // 如果两者 hash 值相同，并且通过 equals 比较 key 相同，则返回
        if (e.hash == hash &&
            ((k = e.key) == key || (key != null && key.equals(k))))
            return e;
    }
    return null;
}
```

> `get(Object key)`方法根据指定的`key`值返回对应的`value`，先根据 key 计算 hash 值，根据 hash 值得到数组中对应位置的元素，然后遍历对应位置上的链表，通过 key 的 equals 方法找到对应的元素

##### <font color="#0091FF">remove(Object key) 方法</font>

```java
public V remove(Object key) {
    // 根据 key 获取并删除对应的节点
    Entry<K,V> e = removeEntryForKey(key);
    return (e == null ? null : e.value);
}

final Entry<K,V> removeEntryForKey(Object key) {
    // 计算 key 对应的 hash 值
    int hash = (key == null) ? 0 : hash(key);
    // 根据 hash 值查找 table 中的索引
    int i = indexFor(hash, table.length);
    // 指定链表表头节点
    Entry<K,V> prev = table[i];
    Entry<K,V> e = prev;
	// 循环遍历冲突链表
    while (e != null) {
        Entry<K,V> next = e.next;
        Object k;
        // 如果 key 相同，则删除当前对应的 Entry 节点
        if (e.hash == hash &&
            ((k = e.key) == key || (key != null && key.equals(k)))) {
            modCount++;
            size--;
            if (prev == e)
                table[i] = next;
            else
                prev.next = next;
            e.recordRemoval(this);
            return e;
        }
        prev = e;
        e = next;
    }
    return e;
}
```

> `remove(Object key)`方法根据指定的`key`删除对应的`entry`，先根据 key 计算 hash 值，根据 hash 值得到数组中对应位置的元素，然后遍历对应位置上的链表，通过 key 的 equals 方法找到对应的元素并删除

#### <font color="#DF8400">Java 8 HashMap</font>

![img](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\java-collection-hashmap8.png)

##### <font color="#0091FF">底层数据结构</font>

```java
// 默认初始容量为 16
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16
// 最大容量上限为 2^30
static final int MAXIMUM_CAPACITY = 1 << 30;
// 默认负载因子为 0.75
static final float DEFAULT_LOAD_FACTOR = 0.75f;
// 变成树形结构的临界值为 8
static final int TREEIFY_THRESHOLD = 8;
// 恢复链式结构的临界值为 6
static final int UNTREEIFY_THRESHOLD = 6;
// 变成树形结构的最小表容量为 64
static final int MIN_TREEIFY_CAPACITY = 64;
// 哈希表
transient Node<K,V>[] table;
// 存储具体元素的集
transient Set<Map.Entry<K,V>> entrySet;
// 哈希表中键值对的个数
transient int size;
// 哈希表被修改的次数
transient int modCount;
// 扩容阈值，通过 capacity * loadFactor 计算
int threshold;
// 负载因子
final float loadFactor;
```

##### <font color="#0091FF">构造器</font>

```java
public HashMap(int initialCapacity, float loadFactor) {
    if (initialCapacity < 0)
        throw new IllegalArgumentException("Illegal initial capacity: " +
                                           initialCapacity);
    if (initialCapacity > MAXIMUM_CAPACITY)
        initialCapacity = MAXIMUM_CAPACITY;
    if (loadFactor <= 0 || Float.isNaN(loadFactor))
        throw new IllegalArgumentException("Illegal load factor: " +
                                           loadFactor);
    this.loadFactor = loadFactor;
    this.threshold = tableSizeFor(initialCapacity);
}
```

> - 当实例化一个 HashMap 时，会初始化`initialCapacity`和`loadFactor`，在添加第一对映射关系时，系统会通过扩容创建一个长度为 initialCapacity 的 Node 数组
> - 每个 bucket 中存储一个元素，即一个 Node 对象，每个 Node 对象可以带一个指向下一个元素的引用变量，因此，在一个 bucket 中，有可能生成一个 **Node 链**，也可能生成一个 **TreeNode 对象**，新添加的元素作为链表的**<font color="#EF042A">last 或树的叶子节点</font>**

##### <font color="#0091FF">数组扩容</font>

```java
final Node<K,V>[] resize() {
    // 原数组
    Node<K,V>[] oldTab = table;
    // 原容量
    int oldCap = (oldTab == null) ? 0 : oldTab.length;
    // 原阈值
    int oldThr = threshold;
    int newCap, newThr = 0;
    // 计算扩容后的大小
    if (oldCap > 0) {
        // 如果当前容量超过最大容量，则无法进行扩容
        if (oldCap >= MAXIMUM_CAPACITY) {
            threshold = Integer.MAX_VALUE;
            return oldTab;
        }
        // 否则，将数组大小扩大为原来的 2 倍
        else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                 oldCap >= DEFAULT_INITIAL_CAPACITY)
            // 将阈值扩大为原来的 2 倍
            newThr = oldThr << 1; // double threshold
    }
    // 对应使用 new HashMap(int initialCapacity) 初始化后，第一次 put 的时候
    else if (oldThr > 0) // initial capacity was placed in threshold
        newCap = oldThr;
    // 对应使用 new HashMap() 初始化后，第一次 put 的时候
    else {               // zero initial threshold signifies using defaults
        newCap = DEFAULT_INITIAL_CAPACITY;
        newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
    }
    if (newThr == 0) {
        float ft = (float)newCap * loadFactor;
        newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                  (int)ft : Integer.MAX_VALUE);
    }
    // 新阈值
    threshold = newThr;
    // 创建新的数组
    @SuppressWarnings({"rawtypes","unchecked"})
    Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];
    table = newTab; // 如果时初始化数组，到此结束，返回 newTab
    // 遍历数组进行数据迁移
    if (oldTab != null) {
        for (int j = 0; j < oldCap; ++j) {
            Node<K,V> e;
            if ((e = oldTab[j]) != null) {
                oldTab[j] = null;
                // 如果该数组位置上只有一个元素，直接进行迁移
                if (e.next == null)
                    newTab[e.hash & (newCap - 1)] = e;
                // 如果时红黑树，调用相关方法将树分离开
                else if (e instanceof TreeNode)
                    ((TreeNode<K,V>)e).split(this, newTab, j, oldCap);
                // 如果时链表，将此链表拆成两个链表，并保留原来的先后顺序
                else { // preserve order
                    Node<K,V> loHead = null, loTail = null;
                    Node<K,V> hiHead = null, hiTail = null;
                    Node<K,V> next;
                    do {
                        next = e.next;
                        if ((e.hash & oldCap) == 0) {
                            if (loTail == null)
                                loHead = e;
                            else
                                loTail.next = e;
                            loTail = e;
                        }
                        else {
                            if (hiTail == null)
                                hiHead = e;
                            else
                                hiTail.next = e;
                            hiTail = e;
                        }
                    } while ((e = next) != null);
                    if (loTail != null) {
                        loTail.next = null;
                        // 第一条链表
                        newTab[j] = loHead;
                    }
                    if (hiTail != null) {
                        hiTail.next = null;
                        // 第二条链表
                        newTab[j + oldCap] = hiHead;
                    }
                }
            }
        }
    }
    return newTab;
}
```

> - 当 HashMap 中元素的个数超过 capacity * loadFactor 时，就会进行数组扩容，将数组容量扩大一倍，然后重新计算每个元素在数组中的位置。
> - 当 HashMap 中的一个链的对象个数超过了 8 个，如果 capacity 没有达到 64，则会先扩容解决，如果达到了 64，则会转换为红黑树。如果当映射关系被移除后，下次 resize 方法时判断树节点的个数低于 6 个，会将树转换为链表

##### <font color="#0091FF">put(K key, V value) 方法</font>

```java
public V put(K key, V value) {
    return putVal(hash(key), key, value, false, true);
}

final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
               boolean evict) {
    Node<K,V>[] tab; Node<K,V> p; int n, i;
    // 如果数组为空，即第一次 put 的时候，先调用 resize 初始化数组长度
    if ((tab = table) == null || (n = tab.length) == 0)
        n = (tab = resize()).length;
    // 如果当前位置没有元素，直接初始 Node 并放入此位置
    if ((p = tab[i = (n - 1) & hash]) == null)
        tab[i] = newNode(hash, key, value, null);
    // 如果当前位置有元素
    else {
        Node<K,V> e; K k;
        // 判断该位置的第一个元素的 key 与要插入的 key 是否相等，如果是，取出当前节点
        if (p.hash == hash &&
            ((k = p.key) == key || (key != null && key.equals(k))))
            e = p;
        // 如果是红黑树，调用红黑树的插值方法
        else if (p instanceof TreeNode)
            e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
        // 如果是链表
        else {
            // 循环遍历链表
            for (int binCount = 0; ; ++binCount) {
                // 如果没有包含重复的 key，插入到链表的最后
                if ((e = p.next) == null) {
                    p.next = newNode(hash, key, value, null);
                    // 如果插入的节点是链表中的第 8 个，转换为红黑树
                    if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                        treeifyBin(tab, hash);
                    break;
                }
                // 如果链表中找到了相等的 key，结束循环
                if (e.hash == hash &&
                    ((k = e.key) == key || (key != null && key.equals(k))))
                    break;
                p = e;
            }
        }
        // 如果存在旧值的 key 与要插入的 key 相等，将旧值覆盖，并返回
        if (e != null) { // existing mapping for key
            V oldValue = e.value;
            if (!onlyIfAbsent || oldValue == null)
                e.value = value;
            afterNodeAccess(e);
            return oldValue;
        }
    }
    ++modCount;
    // 如果size 超过了阈值，进行扩容
    if (++size > threshold)
        resize();
    afterNodeInsertion(evict);
    return null;
}

 final void treeifyBin(Node<K,V>[] tab, int hash) {
     int n, index; Node<K,V> e;
     // 如果数组为空或数组大小没有达到最小树形化容量，则进行扩容
     if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY)
         resize();
     // 否则，将所有节点替换为树节点
     else if ((e = tab[index = (n - 1) & hash]) != null) {
         TreeNode<K,V> hd = null, tl = null;
         do {
             TreeNode<K,V> p = replacementTreeNode(e, null);
             if (tl == null)
                 hd = p;
             else {
                 p.prev = tl;
                 tl.next = p;
             }
             tl = p;
         } while ((e = e.next) != null);
         // 进行树形化
         if ((tab[index] = hd) != null)
             hd.treeify(tab);
     }
 }
```

![Java8HashMap之put方法](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\Java8HashMap之put方法.png)

##### <font color="#0091FF">get(Object key) 方法</font>

```java
public V get(Object key) {
    Node<K,V> e;
    return (e = getNode(hash(key), key)) == null ? null : e.value;
}

final Node<K,V> getNode(int hash, Object key) {
    Node<K,V>[] tab; Node<K,V> first, e; int n; K k;
    if ((tab = table) != null && (n = tab.length) > 0 &&
        (first = tab[(n - 1) & hash]) != null) {
        // 判断第一个节点是否满足，如果满足直接返回
        if (first.hash == hash && // always check first node
            ((k = first.key) == key || (key != null && key.equals(k))))
            return first;
        // 判断是否有后续节点
        if ((e = first.next) != null) {
            // 如果是红黑树，调用红黑树的 getTreeNode 方法获取
            if (first instanceof TreeNode)
                return ((TreeNode<K,V>)first).getTreeNode(hash, key);
            // 否则，循环遍历链表查找是否存在对应的 key
            do {
                if (e.hash == hash &&
                    ((k = e.key) == key || (key != null && key.equals(k))))
                    return e;
            } while ((e = e.next) != null);
        }
    }
    return null;
}
```

> `get(Object key)`方法根据指定的`key`值返回对应的`value`，先根据 key 计算 hash 值，根据 hash 值得到数组中对应位置，判断该处是否为要找的key，如果不是，则查看后续节点，如果后续节点是红黑树，通过红黑树方法查找，否则，遍历对应位置上的链表，通过 key 的 equals 方法找到对应的元素

##### <font color="#0091FF">remove(Object key) 方法</font>

```java
public V remove(Object key) {
    Node<K,V> e;
    return (e = removeNode(hash(key), key, null, false, true)) == null ?
        null : e.value;
}

final Node<K,V> removeNode(int hash, Object key, Object value,
                           boolean matchValue, boolean movable) {
    Node<K,V>[] tab; Node<K,V> p; int n, index;
    if ((tab = table) != null && (n = tab.length) > 0 &&
        (p = tab[index = (n - 1) & hash]) != null) {
        Node<K,V> node = null, e; K k; V v;
        // 判断第一个节点是否满足，如果满足直接赋值给 node
        if (p.hash == hash &&
            ((k = p.key) == key || (key != null && key.equals(k))))
            node = p;
        // 判断是否有后续节点
        else if ((e = p.next) != null) {
            // 如果是红黑树，通过红黑树的方法进行查找
            if (p instanceof TreeNode)
                node = ((TreeNode<K,V>)p).getTreeNode(hash, key);
            // 如果是链表，循环遍历链表查找结点
            else {
                do {
                    if (e.hash == hash &&
                        ((k = e.key) == key ||
                         (key != null && key.equals(k)))) {
                        node = e;
                        break;
                    }
                    p = e;
                } while ((e = e.next) != null);
            }
        }
        // 如果找到要删除的结点，并比对 value
        if (node != null && (!matchValue || (v = node.value) == value ||
                             (value != null && value.equals(v)))) {
            // 如果是红黑树，通过红黑树的方法删除节点
            if (node instanceof TreeNode)
                ((TreeNode<K,V>)node).removeTreeNode(this, tab, movable);
            // 使用链表的操作删除节点
            else if (node == p)
                tab[index] = node.next;
            else
                p.next = node.next;
            ++modCount;
            --size;
            afterNodeRemoval(node);
            return node;
        }
    }
    return null;
}
```

#### <font color="#DF8400">HashSet</font>

- *HashSet*是对*HashMap*的简单包装，对*HashSet*的函数调用都会转换成合适的*HashMap*方法
- *HashSet* 中存储的元素作为 *HashMap* 的键存储在 *HashMap* 中，*HashMap* 的值为一个虚拟的 Object 对象

### <font color="#7A5FFF">Map — LinkedHashSet & LinkedHashMap 源码解析</font>

#### <font color="#DF8400">LinkedHashMap 概述</font>

- LinkedHashMap 是 Map 接口的哈希表和链接表实现，具有可知的迭代顺序
- *LinkedHashMap*是*HashMap*的直接子类，**二者唯一的区别是*LinkedHashMap*在*HashMap*的基础上，采用双向链表(doubly-linked list)的形式将所有`entry`连接起来，这样是为保证元素的迭代顺序跟插入顺序相同**

![LinkedHashMap_base.png](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java 知识体系.assets\LinkedHashMap_base.png)

#### <font color="#DF8400">Java 7 LinkedHashMap</font>

##### <font color="#0091FF">底层数据结构</font>

```java
// 双向链表的表头元素
private transient Entry<K,V> header;
// 继承 HashMap 的 Entry 元素，保存了其上一个元素 before 和下一个元素 after 的引用
private static class Entry<K,V> extends HashMap.Entry<K,V> {
    Entry<K,V> before, after;
    Entry(int hash, K key, V value, HashMap.Entry<K,V> next) {
        super(hash, key, value, next);
    }
	// 从双向链表中移除元素
    private void remove() {
        before.after = after;
        after.before = before;
    }
	// 向双向链表中添加元素
    private void addBefore(Entry<K,V> existingEntry) {
        after  = existingEntry;
        before = existingEntry.before;
        before.after = this;
        after.before = this;
    }
    void recordAccess(HashMap<K,V> m) {
        LinkedHashMap<K,V> lm = (LinkedHashMap<K,V>)m;
        if (lm.accessOrder) {
            lm.modCount++;
            remove();
            addBefore(lm.header);
        }
    }
    void recordRemoval(HashMap<K,V> m) {
        remove();
    }
}
```

##### <font color="#0091FF">构造器</font>

```java
public LinkedHashMap(int initialCapacity, float loadFactor) {
    super(initialCapacity, loadFactor);
    accessOrder = false;
}

@Override
void init() {
    header = new Entry<>(-1, null, null, null);
    header.before = header.after = header;
}
```

> - 实例化 LinkedHashMap 时，实际调用了父类 HashMap 的相关构造器进行初始化
>
> - LinkedHashMap 重写了 init()方法，在调用父类的构造方法完成构造后，进一步实现了 对其元素 Entry 的初始化操作

##### <font color="#0091FF">put(K key, V value) 方法</font>

```java
void addEntry(int hash, K key, V value, int bucketIndex) {
    // 调用父类方法添加 Entry
    super.addEntry(hash, key, value, bucketIndex);
    // Remove eldest entry if instructed
    Entry<K,V> eldest = header.after;
    if (removeEldestEntry(eldest)) {
        removeEntryForKey(eldest.key);
    }
}

void createEntry(int hash, K key, V value, int bucketIndex) {
    HashMap.Entry<K,V> old = table[bucketIndex];
    Entry<K,V> e = new Entry<>(hash, key, value, old);
    table[bucketIndex] = e;
    // 调用元素的 addBrefore 方法，将元素加入到哈希、双向链接列表
    e.addBefore(header);
    size++;
}
```

> LinkedHashMap 未重写父类 HashMap 的 put 方法，而是重写了父类 HashMap 的 put 方法调用的子方法 void addEntry(int hash, K key, V value, int bucketIndex) 和 void  createEntry(int hash, K key, V value, int bucketIndex)，提供了自己特有的双向链接列表的实现

##### <font color="#0091FF">get(Object key) 方法</font>

```java
public V get(Object key) {
    // 调用父类 HashMap 的 getEntry()方法，取得要查找的元素
    Entry<K,V> e = (Entry<K,V>)getEntry(key);
    if (e == null)
        return null;
    e.recordAccess(this);
    return e.value;
}
```

##### <font color="#0091FF">remove(Object key) 方法</font>

> LinkedHashMap 未重写父类 HashMap 的 remove 方法，父类的 remove 方法中调用了 `Entry` 的 `e.recordRemoval(this)`方法，LinkedHashMap 中的`Entry`重写了父类的`recordRemoval`方法用来移除双向链表中对应的引用关系

#### <font color="#DF8400">Java 8 LinkedHashMap</font>

##### <font color="#0091FF">底层数据结构</font>

```java
// 头指针
transient LinkedHashMap.Entry<K,V> head;
// 尾指针
transient LinkedHashMap.Entry<K,V> tail;
// 点继承了 HashMap 的 Node，而且每个节点都包含了前指针和后指针
static class Entry<K,V> extends HashMap.Node<K,V> {
    Entry<K,V> before, after;
    Entry(int hash, K key, V value, Node<K,V> next) {
        super(hash, key, value, next);
    }
}
```

##### <font color="#0091FF">构造器</font>

```java
public LinkedHashMap(int initialCapacity, float loadFactor) {
    super(initialCapacity, loadFactor);
    accessOrder = false;
}
```

> 实例化 LinkedHashMap 时，实际调用了父类 HashMap 的相关构造器进行初始化

##### <font color="#0091FF">方法</font>

```java
 // Callbacks to allow LinkedHashMap post-actions
void afterNodeAccess(Node<K,V> p) { }
void afterNodeInsertion(boolean evict) { }
void afterNodeRemoval(Node<K,V> p) { }
```

> HashMap 中有 3 个空方法，表示分别在**访问、插入、删除**某个节点之后进行一些处理，它们在 LinkedHashMap 中有各自的实现，通过这三个方法保证链表的插入、删除的有序性

```java
void afterNodeAccess(Node<K,V> e) { // move node to last
    LinkedHashMap.Entry<K,V> last;
    if (accessOrder && (last = tail) != e) {
        LinkedHashMap.Entry<K,V> p =
            (LinkedHashMap.Entry<K,V>)e, b = p.before, a = p.after;
        p.after = null;
        if (b == null)
            head = a;
        else
            b.after = a;
        if (a != null)
            a.before = b;
        else
            last = b;
        if (last == null)
            head = p;
        else {
            p.before = last;
            last.after = p;
        }
        tail = p;
        ++modCount;
    }
}

void afterNodeInsertion(boolean evict) { // possibly remove eldest
    LinkedHashMap.Entry<K,V> first;
    if (evict && (first = head) != null && removeEldestEntry(first)) {
        K key = first.key;
        removeNode(hash(key), key, null, false, true);
    }
}

void afterNodeRemoval(Node<K,V> e) { // unlink
    LinkedHashMap.Entry<K,V> p =
        (LinkedHashMap.Entry<K,V>)e, b = p.before, a = p.after;
    p.before = p.after = null;
    if (b == null)
        head = a;
    else
        b.after = a;
    if (a == null)
        tail = b;
    else
        a.before = b;
}
```

## Java 多线程与并发

### <font color="#7A5FFF">JUC 概述</font>

#### <font color="#DF8400">理论概述</font>

#### <font color="#DF8400">线程与进程</font>

- <font color="#0091FF">**进程：**</font>指系统中正在运行的一个应用程序，程序一旦运行就是进程，**进程 —— 资源分配的最小单位**
- <font color="#0091FF">**线程：**</font>系统分配处理器时间资源的基本单元，或者说进程之内独立执行的一个单元执行流。**线程 —— 程序执行的最小单位**

##### <font color="#0091FF">线程的状态</font>

- <font color="#4EB434">**新建（New）**</font>
- <font color="#4EB434">**可运行（Runnable）**</font>
- <font color="#4EB434">**阻塞（Blocked）**</font>
- <font color="#4EB434">**无限期等待（Waiting）**</font>
- <font color="#4EB434">**限期等待（Timed Waiting）**</font>
- <font color="#4EB434">**死亡（Terminated）**</font>

##### <font color="#0091FF">wait 和 sleep 的区别</font>

- sleep 是 Thread 的静态方法，wait 是 Object 的方法，任何对象实例都能调用
- sleep 不会释放锁，也不需要占用锁。wait 会释放锁，但调用它的前提是当前线程占有锁（代码要在 synchronized 中）
- 它们都可以被 interrupted 方法中断

##### <font color="#0091FF">并发和并行</font>

- <font color="#4EB434">**串行：**</font>所有任务按先后顺序执行，一次只能取得一个任务并执行
- <font color="#4EB434">**并行：**</font>可同时取得多个任务，并同时去执行所取得的任务
- <font color="#4EB434">**并发：**</font>多个程序可以同时运行的现象，同一时刻多个线程访问同一个资源

##### <font color="#0091FF">管程</font>

- 管程（monitor）是一种**同步机制**，保证同一时刻只有一个进程在管程内活动，即管程内定义的操作在同 一时刻只被一个进程调用
- JVM 中同步是基于进入和退出管程对象实现的，每个对象都会有一个管程对象，**管程会随着 Java 对象一同创建和销毁**
- 执行线程首先要持有管程对象，然后才能执行方法，当方法完成之后释放管程，方法执行时会持有管程，其他线程无法获得同一管程

##### <font color="#0091FF">用户进程和守护进程</font>

- <font color="#4EB434">**用户线程：**</font>平时用到的普通线程，自定义线程。
- <font color="#4EB434">**守护线程：**</font>运行在后台，是一种特殊的线程
- 当主线程结束后，用户线程还在运行，JVM 存活；如果没有用户线程，都是守护线程，JVM 结束



## Java IO/NIO/AIO

  
