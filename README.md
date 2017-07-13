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
end

# java 8 features
# Stream Min

description

```
List<String> list = Arrays.asList("Gza","Gzb","Gox","Elephant");
		String max = list.stream().max(Comparator.comparing(String::valueOf)).get();
		System.out.println("Max:"+ max);
		String min = list.stream().min(Comparator.comparing(String::valueOf)).get();
		System.out.println("Min:"+ min);
```
# Stream Max

Deepika,Brighty

![alt](http://javadeveloperzone.com/wp-content/uploads/2017/06/JAVA-8-STREAM-COLLECT-EXAMPLE-600x400.jpg)
# Java 8 feature #
## Stream to arrayList Example:Using Stream Interface Methods
## _Description_

### This is one of the way to convert a Stream to array in Java 8.We first convert Stream to ArrayList and then convert that ArrayList to an array.

## Syntax
```
<R> R collect(Supplier<R> supplier, BiConsumer<R,? super T> accumulator, BiConsumer<R,R> combiner)
<R,A> R collect(Collector<?  super T,A,R> collector)
```
## Program
```sh
package com.kgfsl.app;
import java .util.stream.*;
import java .util.*;
//import java.lang.*;
public class Streamtocollect
{
    public static void main(String args[])
    {
        Stream<String> numbers = Stream.of("1", "22", "33", "44", "55","12","14");
         ArrayList<String> list =   numbers
                            .filter(s->s.startsWith("1"))
                            .limit(2)
                            .collect(Collectors.toCollection(ArrayList::new));
         
        System.out.println(list);


    }
}
```
## Output:
```
[ 1 , 12 , 14 ]
```
### The _collect()_ method is used to accumulate all elements of Stream into a Collection e.g. a list. Though, there is a method called _Collectors.toList()_ which converts Stream to List, it doesn't provide any guarantee about the type of list returned by this method. Instead, by using _Collectors.toCollection()_ you can convert it into any specific Collection e.g. ArrayList. 

end

