akshaya P R

# Java 8 features
This is classic OOP style of hiding method implementations from the caller. The caller simply passes a variable to the method which then does something with the value of the variable and returns another value or produces a side effect as it is in our case.
```
class LambdaDemo {
    public void printSomething(String something) {
        System.out.println(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        lambdaDemo.printSomething(something);
    }
}
```
see an equivalent implementation that uses behavior passing other than variable passing. To achieve this, we have to create a functional interface that defines that abstracts the behavior instead of a method. A functional interface is an interface that has only one method:

```package com.kg.lambdaapp;
interface Printer {
    void print(String val);
}

class LambdaDemo {
    public void printSomething(String something, Printer printer) {
        //System.out.println(something);
        printer.print(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        Printer printer = new Printer() {
            @Override
            public void print(String val) {
                System.out.println(val);
            }
        };
        String something = "Learning Lambda";
        lambdaDemo.printSomething(something, printer);
    }
}

```

```
public void print(String toPrint) {
                System.out.println(toPrint);
            }
```

lambda expressions

```package com.kg.lambdaapp;
interface Printer {
    void print(String val);
}

class LambdaDemo {
    public void printSomething(String something, Printer printer) {
        //System.out.println(something);
        printer.print(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        Printer printer = (String toPrint) -> {
                System.out.println(toPrint);
        };

        String something = "Learning Lambda";
        lambdaDemo.printSomething(something, printer);
    }
}
```

```
(String toPrint) -> {
                System.out.println(toPrint);
        }
```



```
package com.kg.lambdaapp;
interface Printer {
    void print(String something);
}

public class LambdaDemo {
    public static void printSomething(String something) {
        System.out.println(something);
        //printer.print(something);
    }


    public static void main(String[] args) {
        //LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        Printer printer = LambdaDemo::printSomething;
        printer.print(something);
    }
}
```
```
package com.kg.lambdaapp;
interface Printer {
    void print();
}

public class LambdaDemo {
    public static void printSomething() {
        System.out.println("something");
        //printer.print(something);
    }

    public static void main(String[] args) {
        //LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        Printer printer = LambdaDemo::printSomething;
        printer.print();
    }
}
```
MohanaPriya and Switha
Skip()

Description

It returns a stream consisting of the remaining elements of this stream after discarding the first n elements of the stream. If this stream contains fewer than n elements then an empty stream will be returned.

Syntax

Stream<T> skip(long n)
Example

 package com.kgfsl.log4jtest.app;
 import java.util.ArrayList;
 import java.util.List;
 import java.util.stream.Stream;

  public class StreamLimitSkipExample {
  public static void main(String[] args) {
  
  List<Integer> numbers = new ArrayList<>();
  numbers.add(1);
  numbers.add(2);
  numbers.add(3);
  numbers.add(4);
  numbers.add(5);
  numbers.add(6);

  Stream<Integer> stream1 = numbers.stream();
  // Limit - return new stream of 3 elements
  System.out.println("--------Stream elements after limiting----------");
  stream1.limit(3).forEach((a) -> {System.out.println(a);
  });
 }
}
output

 --------Stream elements after limiting----------
 1
 2
 3
Limit()

Description

Returns a stream consisting of the elements of this stream, truncated to be no longer than maxSize in length.

Syntax

      Stream<T> limit(long maxSize)	
Example

       package com.kgfsl.log4jtest.app;

       import java.util.ArrayList;
       import java.util.List;
       import java.util.stream.Stream;

       public class StreamLimitSkipExample {
       public static void main(String[] args) {
  
       List<Integer> numbers = new ArrayList<>();
       numbers.add(1);
       numbers.add(2);
       numbers.add(3);
       numbers.add(4);
       numbers.add(5);
       numbers.add(6);
       Stream<Integer> stream2 = numbers.stream();
       // Skip - return new stream of remaining elements
       // after skipping first 2 elements
       System.out.println("--------Stream elements after skipping----------");
       stream2.skip(2).forEach((a) -> {
       System.out.println(a);
       });
       }
       }
Output

--------Stream elements after skipping----------
3
4
5
6
Sort()

Description

Sorting without comparator

Returns a stream consisting of the elements of this stream, sorted according to natural order. If the elements of this stream are not Comparable, a java.lang.ClassCastException may be thrown when the terminal operation is executed.

Sorting using comparator

Returns a stream consisting of the elements of this stream, sorted according to the provided Comparator.

Syntax

Sorting without comparator

 Stream<T> sorted()	
Sorting using comparator

 Stream<T> sorted(Comparator<? super T> comparator)	
Example

        package com.kgfsl.log4jtest.app;

        import java.util.*;
        import java.util.ArrayList;
        import java.util.List;
        import java.util.Comparator;
        import java.util.stream.Collectors;

        public class StreamMethodMain {
        public static void main(String args[]) {
        List<StreamMethods> list = new ArrayList<StreamMethods>();
        list.add(new StreamMethods("Mohana", 001, 10000));
        list.add(new StreamMethods("Mona", 002, 8000));
        list.add(new StreamMethods("Priya", 003, 90000));
        list.add(new StreamMethods("Sona", 004, 5000));
        System.out.println("sorting....");
        List<StreamMethods> list1 = list.stream().sorted(Comparator.comparing(StreamMethods::getSalary).reversed()).collect(Collectors.toList());
        list1.forEach(l -> System.out.println("Name:" + l.getName() + "Id:" + l.getId() + "Salary:" + l.getSalary()));

     }
     }
Output

Name:Priya  Id:3 Salary:90000
Name:Mohana Id:1 Salary:10000
Name:Mona   Id:2 Salary:8000
Name:Sona   Id:4 Salary:5000
