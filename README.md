Suriyan
## Stream mapToDouble (ToDoubleFunction mapper)

### Description

Stream mapToDouble(ToDoubleFunction<? super T> mapper) returns a DoubleStream consisting of the results of applying the given function to the elements of this stream. 

It returns a DoubleStream consisting of the results of replacing each element of this stream with the contents of a mapped stream produced by applying the provided mapping function to each element. Each mapped stream is closed after its contents have placed been into this stream. (If a mapped stream is null an empty stream is used, instead.)

### Syntax
```sh
DoubleStream mapToDouble(ToDoubleFunction<? super T> mapper)
```
### Example
```sh
import java.util.Arrays;
import java.util.List;

public class Main {
  public static void main(String[] args) {
    List<String> stringList = Arrays.asList("1.2","2.2","3","4","5");

    stringList.stream()
           .mapToDouble(n-> Double.parseDouble(n) )
           .filter(n-> n%2 == 0)
           .forEach(System.out::println);
  }
}
```
The code above generates the following result.
```sh
4.0
```
##
___
##
## Stream mapToInt(ToIntFunction mapper) 

### Description

Stream mapToInt(ToIntFunction<? super T> mapper) returns an IntStream by applying the given function to this stream.

It returns an IntStream consisting of the results of replacing each element of this stream with the contents of a mapped stream produced by applying the provided mapping function to each element. Each mapped stream is closed after its contents have been placed into this stream. (If a mapped stream is null an empty stream is used, instead.)

### Syntax

```
IntStream mapToInt(ToIntFunction<? super T> mapper) 
```
### Example

```sh
import java.util.Arrays;
import java.util.List;

public class Main {
  public static void main(String[] args) {
    List<String> stringList = Arrays.asList("1","2","3","4","5");

    stringList.stream()
           .mapToInt(n-> Integer.parseInt(n) )
           .filter(n-> n%2 == 0)
           .forEach(System.out::println);
  }
}
```
The code above generates the following result.
```sh
2
4
```
##
___
##
##
## Stream mapToLong(ToLongFunction mapper) 

### Description

Stream mapToLong(ToLongFunction<? super T> mapper) returns a LongStream by applying the function to the stream.

It returns a LongStream consisting of the results of replacing each element of this stream with the contents of a mapped stream produced by applying the provided mapping function to each element. Each mapped stream is closed after its contents have been placed into this stream. (If a mapped stream is null an empty stream is used, instead.)

### Syntax
```sh
LongStream mapToLong(ToLongFunction<? super T> mapper)
```
### Example
```sh
import java.util.Arrays;
import java.util.List;

public class Main {
  public static void main(String[] args) {
    List<String> stringList = Arrays.asList("1","2","3","4","5");

    stringList.stream()
           .mapToLong(n-> Long.parseLong(n) )
           .filter(n-> n%2 == 0)
           .forEach(System.out::println);
  }
}
```
The code above generates the following result.

```sh
2
4
```
#
#
___

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
