# Nested Classes

嵌入类分为非静态（内部类）和静态，属于外部类的成员。

## 1. Why Use Nested Classes

- 归置一个只在一个地方使用的类
- 更好的封装
- 代码可读性和可维护性更高

## 2. Non-static Nested Classes (Inner Classes)

非静态嵌入类也叫内部类，可在延申出本地内部类（local class）和匿名内部类（anonymous class）两个特殊的内部类。另外也和 Lambda 表达式方法有关联。

内部类的特点：

- 可以访问外部类的成员，甚至是私有的
- 内部类属于外部类，所以必须要实例外部类
- 因为内部类是和实例关联，所以它不能定义静态的成员

### 2.1 Local Class

典型地，定义在方法内部的本地类

- 可以访问外部方法的参数和本地变量。特殊的，本地类只能访问方法的不变本地变量（可为定义 final 或 实际上是 final）
- 可以定义静态原始类型和String类型常量，因为该常量是在编译时替换成实际值，是可知的

```java
    public void sayGoodbyeInEnglish() {
        class EnglishGoodbye {
            public static final String farewell = "Bye bye";
            public void sayGoodbye() {
                System.out.println(farewell);
            }
        }
        EnglishGoodbye myEnglishGoodbye = new EnglishGoodbye();
        myEnglishGoodbye.sayGoodbye();
    }
```

### 2.2 Anonymous Class

匿名内部类是一个表达式，让代码更简洁，在同一时间声明和实例一个类。

- 只使用一次
- 可以访问外部方法的参数和本地变量。特殊的，本地类只能访问方法的不变本地变量（可为定义 final 或 实际上是 final）
- 可以定义静态原始类型和String类型常量，因为该常量是在编译时替换成实际值，是可知的
- 可以声明其他的方法，但是不能声明构造方法

```java
        HelloWorld frenchGreeting = new HelloWorld() {
            String name = "tout le monde";
            public void greet() {
                greetSomeone("tout le monde");
            }
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Salut " + name);
            }
        };
```

### 2.3 Lambda Expressions

为了简化只有单个方法接口的代码编写

- 代码类似于声明一个匿名方法
- 可以访问外部方法的参数和本地变量。特殊的，本地类只能访问方法的不变本地变量（可为定义 final 或 实际上是 final）
- 可以定义静态原始类型和String类型常量，因为该常量是在编译时替换成实际值，是可知的
- 不像内部类，Lambda 表达式不会新开一个新层级的区间，所以不会有同名变量覆盖的问题。

```JAVA
p -> p.getGender() == Person.Sex.MALE 
    && p.getAge() >= 18
    && p.getAge() <= 25
```

### 2.4 Serialization

不推荐对内部类进行序列化，因为内部类的特殊编译机制，在不同的 JRE 环境下可能存在兼容性问题

## 3. Static Nested Classes

和原先类一致，只是可以认为增加了父 package

## 4. When to Use Above Class

- **Local class**: Use it if you need to create more than one instance of a class, access its constructor, or introduce a new, named type (because, for example, you need to invoke additional methods later)
- **Anonymous class**: Use it if you need to declare fields or additional methods
- **Lambda expression**: 
  - Use it if you are encapsulating a single unit of behavior that you want to pass to other code
  - Use it if you need a simple instance of a functional interface and none of the preceding criteria apply (for example, you do not need a constructor, a named type, fields, or additional methods)
- **Nested class**: 
  - Use it if your requirements are similar to those of a local class, you want to make the type more widely available, and you don't require access to local variables or method parameters
  - Use a non-static nested class (or inner class) if you require access to an enclosing instance's non-public fields and methods. Use a static nested class if you don't require this access

