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




subitha vanitha

# **STREAM METHODS**

## **Maximum**
### **Description**
 * Return maximum element of the stream
 ### **Syntax**
    Maximum:System.out.println(listname.stream().max(Integer::max).get());
 ## **Minimum**
### **Description**
 * Return minimum element of the stream
 ### **Syntax**
    Mininum:System.out.println(listname.stream().min(Integer::min).get());
## **Limit**
### **Description**
 * limit() method selects the elements from start. We need to pass a max value and it returns the stream up to the max number of elements.
 ### **Syntax**
    stream-instance.limit(n)
 ## **Count**
### **Description**
 * Returns the count of elements in this stream.
 ### **Syntax**
    long count = listname.stream().count();
 ## **Skip**
### **Description**
 * Returns a stream consisting of the remaining elements of this stream after discarding the first n elements of the stream.
 ### **Syntax**
    stream-instance.skip(n) 
 ## **Filter**
### **Description**
 *  filtering data by using stream. You can see that code is optimized and maintained. Stream provides fast execution.
 ### **Syntax**
    stream-instance.filter() 
## **Distinct**
### **Description**
 * returns a stream consisting of the distinct elements
 ### **Syntax**
    stream-instance.distinct()
 ## **FindAny**
### **Description**
 * findAny() method can find any element from stream. It returns Optional instance. If there is no data in stream, it returns empty Optional instance. 
 ### **Syntax**
    list.stream().findAny().ifPresent(s->System.out.println(s));
 ## **FindFirst**
### **Description**
 * findFirst() returns first element of the stream and if stream has defined no encounter order, then it may return any element. If stream is empty, it returns empty Optional instance. 
 ### **Syntax**
    list.stream().findFirst().ifPresent(s->System.out.println(s));
## **Anymatch**
### **Description**
 * For anyMatch() method we pass Predicate as an argument. The element of stream is iterated for this Predicate. If any element matches then it returns true otherwise false. 
 ### **Syntax**
    boolean anyMatch(Predicate<? super T> predicate);
## **Allmatch**
### **Description**
 * We pass Predicate as an argument to allMatch() method. That Predicate is applied to each element of stream and if each and every element satisfies the given Predicate then it returns true otherwise false. 
 ### **Syntax**
    boolean allMatch(Predicate<? super T> predicate);
## **Nonematch**
### **Description**
 * Returns whether no elements of this stream match the provided predicate.
 ### **Syntax**
    boolean noneMatch(Predicate<? super T> predicate);

## `Pojo class-person`
```
package com.kgfsl.stream;
class Person
{
    private String name;
    private int age;
   Person(String name,int age)
   {
       this.name=name;
       this.age=age;
   }
    public String getName()
    {
        return name;
    }
    
    public int getAge()
    {
        return age;
    }
    public String toString()
    {
        return "  name: "+name+"  age: "+age;
    }
}
```
## `Main class`
```
package com.kgfsl.stream;
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;
import java.util.*;
import java.util.stream.Collectors;
import java.util.Optional;
class Sample
{
    public static void main(String[] args) {
        List<Person> persons=Arrays.asList(new Person("ani",21),new Person("vani",18),new Person("vani",99),new Person("azar",11));
        //Find Maximum value
        persons.stream().max(Comparator.comparing(Person::getName)).ifPresent(p->System.out.println("sort by alphabet order person max"+p));
        //Find Minimum value
        persons.stream().min(Comparator.comparing(Person::getName)).ifPresent(s->System.out.println("sort by alphabet order person min "+s));
       //using filter
       List<Person> l1=persons.stream().filter(s->s.getName().endsWith("i")).collect(Collectors.toList());
        l1.stream().forEach(System.out::println);
        //count
        long n=persons.stream().filter(e->e.getName().endsWith("i")).count();
        System.out.println(n);
        //foreach and distinct
        System.out.println("distinct");
        List<String> d=persons.stream().map(Person::getName).distinct().collect(Collectors.toList());
        d.forEach(System.out::println);
        //skip
        System.out.println("skip");
        persons.stream().skip(2).forEach(System.out::println);
        //limit
        System.out.println("limit");
        persons.stream().limit(3).forEach(System.out::println);
        //allmatch
        boolean b1 = persons.stream().allMatch(p1->p1.getAge()>20 && p1.getName().startsWith("v"));
        System.out.println(b1);
        //nonematch
        boolean b2 = persons.stream().noneMatch(p1->p1.getAge()>20 && p1.getName().startsWith("m"));
        System.out.println(b2);
        //anymatch
        boolean b3 = persons.stream().anyMatch(p1->p1.getAge()>20 && p1.getName().startsWith("v"));
        System.out.println(b3);
        //string reduce
        String[] myArray = { "this", "is", "a", "sentence" };
        String result = Arrays.stream(myArray).reduce("", (a,b) -> a + b);
        System.out.println(result);
        //number reduce
        int[] myArray1 = { 1,2,3,4 };
        int result1 = Arrays.stream(myArray1).reduce(0,(a,b) -> a + b);
        System.out.println(result1);
       //boolean b5=persons.stream().filter(s->s.getName().endsWith("i")).findAny();
       //l1.stream().forEach(System.out::println);
       //find any
       Optional<Person> anyEmpAbove40 = persons.stream().filter(emp -> emp.getAge() > 40).findAny();
      if(anyEmpAbove40.isPresent()){
      System.out.println("Any Employee above age 40: " + anyEmpAbove40.get());
     }
     //find first
     Optional<Person> o1 = persons.stream()
                                       .filter(emp ->       emp.getAge() > 20)
                                       .findFirst();
     if(o1.isPresent()){
      System.out.println("Any Employee above age 20: " + o1.get());
     }
     //sort
     List<Person> slist = persons.stream().sorted(Comparator.comparing(Person::getAge)).collect(Collectors.toList());
		slist.forEach(System.out::println);
        //Person[] type=persons.stream().filter(s->s.getName().endsWith("i")).toArray(Person[]::new);
     //peek
      List<Integer> list = Arrays.asList(10,11,12);
        list.stream().peek(i->System.out.println(i*i)).collect(Collectors.toList());
        //map
        List<String> alpha = Arrays.asList("a", "b", "c", "d");
         List<String> c1 = alpha.stream().map(String::toUpperCase).collect(Collectors.toList());
        System.out.println(c1); 
  
    }

}

```
end
