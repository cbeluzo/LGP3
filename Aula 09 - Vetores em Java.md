# Recursos Avançados para Manipulação de Arrays e Coleções em Java

**Objetivo**

Objetivo é aprofundar o conhecimento em Java, explorando classes e recursos adicionais para a manipulação de arrays e coleções. Serão abordadas as classes `Arrays`, `ArrayDeque`, `Vector`, `Stack`, `LinkedList`, bem como conceitos de Streams, `Iterable`, e a classe `Collections`. Cada tópico incluirá uma breve introdução teórica, exemplos práticos e exercícios para reforço.


**Introdução**

Coleções em Java são estruturas de dados que permitem o armazenamento e manipulação de grupos de objetos de forma organizada. A API de Collections faz parte do pacote `java.util` e fornece uma ampla gama de classes e interfaces para trabalhar com diferentes tipos de coleções, como listas, conjuntos e mapas. Essas coleções abstraem a complexidade do gerenciamento manual de arrays e fornecem funcionalidades adicionais, como a capacidade de redimensionamento dinâmico, operações de pesquisa e ordenação.

Neste exemplo, utilizamos a classe `ArrayList`, que implementa a interface `List`. Criamos uma lista de strings para armazenar os nomes de frutas. Usamos o método `add()` para adicionar elementos à lista e o método `toString()` implícito na impressão exibe os elementos da lista.



**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.List;

public class CollectionExample {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();  // Cria uma lista vazia de Strings
        fruits.add("Apple");  // Adiciona "Apple" à lista
        fruits.add("Banana");  // Adiciona "Banana" à lista
        fruits.add("Orange");  // Adiciona "Orange" à lista

        System.out.println(fruits);  // Exibe os elementos da lista: [Apple, Banana, Orange]
    }
}
```

**Exercício:**
Crie uma coleção que armazene os nomes de três cidades e exiba-os no console.

---



### 1. Classe `Arrays`

A classe `Arrays` oferece métodos estáticos para manipulação de arrays. É uma ferramenta poderosa para operações comuns como ordenação, busca, preenchimento e conversão de arrays para listas.

**Exemplo Explicado:**
```java
import java.util.Arrays;

public class ArraysExample {
    public static void main(String[] args) {
        int[] numbers = {5, 3, 8, 2};
        Arrays.sort(numbers);  // Ordena o array
        System.out.println(Arrays.toString(numbers));  // Exibe o array ordenado: [2, 3, 5, 8]

        int index = Arrays.binarySearch(numbers, 5);  // Busca binária para o número 5
        System.out.println("Index of 5: " + index);  // Exibe o índice de 5: 2
    }
}
```
**Exercício:**
Crie um array de strings, ordene-o e busque por um elemento específico usando `Arrays.binarySearch()`.

---

### 2. Classe `ArrayDeque`

`ArrayDeque` é uma implementação de `Deque` (fila dupla) que oferece uma alternativa eficiente a `Stack` e `LinkedList` para implementações de pilha e fila. É mais rápida para operações LIFO e FIFO, sem o overhead de sincronização de `Stack`.

**Exemplo Explicado:**
```java
import java.util.ArrayDeque;
import java.util.Deque;

public class ArrayDequeExample {
    public static void main(String[] args) {
        Deque<String> stack = new ArrayDeque<>();
        stack.push("First");
        stack.push("Second");
        stack.push("Third");

        System.out.println("Popped: " + stack.pop());  // Exibe "Third"
    }
}
```
**Exercício:**
Implemente uma fila usando `ArrayDeque` e adicione três elementos. Em seguida, remova e exiba o primeiro elemento inserido.

---

### 3. Classe `Vector`

`Vector` é uma lista dinâmica que é sincronizada, o que significa que é segura para operações em múltiplas threads. Embora `ArrayList` seja mais utilizada hoje em dia, `Vector` ainda é útil em ambientes que requerem sincronização.

**Exemplo Explicado:**
```java
import java.util.Vector;

public class VectorExample {
    public static void main(String[] args) {
        Vector<Integer> vector = new Vector<>();
        vector.add(10);
        vector.add(20);
        vector.add(30);

        System.out.println("Vector: " + vector);  // Exibe o vetor: [10, 20, 30]
    }
}
```
**Exercício:**
Crie um `Vector` de inteiros e adicione quatro elementos. Exiba o conteúdo do vetor.

---

### 4. Classe `Stack`

`Stack` é uma implementação de uma pilha (LIFO) baseada em `Vector`. Embora seja considerada legada, ainda é útil em situações específicas onde o comportamento de pilha é necessário.

**Exemplo Explicado:**
```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<String> stack = new Stack<>();
        stack.push("Element 1");
        stack.push("Element 2");
        stack.push("Element 3");

        System.out.println("Top of the stack: " + stack.peek());  // Exibe o topo da pilha: "Element 3"
        System.out.println("Popped from stack: " + stack.pop());  // Remove e exibe "Element 3"
    }
}
```
**Exercício:**
Crie uma pilha de strings usando `Stack` e adicione três elementos. Remova o topo da pilha e exiba o elemento removido.

---

### 5. Classe `LinkedList`

`LinkedList` implementa tanto `List` quanto `Deque`, oferecendo uma estrutura de lista encadeada que é eficiente para inserções e remoções no início, meio e fim da lista. Ao contrário de `ArrayList`, onde essas operações podem ser lentas, `LinkedList` é ideal para manipulações frequentes de elementos.

**Exemplo Explicado:**
```java
import java.util.LinkedList;
import java.util.List;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList <String> list = new LinkedList<>();
        list.add("Element A");
        list.add("Element B");
        list.addFirst("Element 0");  // Adiciona ao início da lista

        System.out.println(list);  // Exibe a lista: [Element 0, Element A, Element B]
    }
}
```
**Exercício:**
Crie uma `LinkedList` de strings e adicione três elementos. Adicione um elemento no início da lista e exiba a lista completa.

---

### 6. Interface `Iterable`

`Iterable` é a interface raiz para todas as coleções em Java que podem ser iteradas com um loop `for-each`. Implementar `Iterable` permite que uma classe forneça um iterador, permitindo iterações concisas e seguras.

**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.List;

public class IterableExample {
    public static void main(String[] args) {
        List<String> items = new ArrayList<>();
        items.add("Item 1");
        items.add("Item 2");

        for (String item : items) {
            System.out.println(item);
        }
    }
}
```
**Exercício:**
Implemente uma coleção personalizada que seja iterável, e itere sobre seus elementos usando um loop `for-each`.

---

### 7. Classe `Collections`

A classe `Collections` fornece métodos estáticos para manipular coleções, como ordenação, inversão, sincronização e buscas. É uma ferramenta essencial para manipulação avançada de coleções.

**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionsExample {
    public static void main(String[] args) {
        List<String> items = new ArrayList<>();
        items.add("Banana");
        items.add("Apple");
        items.add("Orange");

        Collections.sort(items);  // Ordena a lista
        System.out.println(items);  // Exibe a lista ordenada: [Apple, Banana, Orange]
    }
}
```
**Exercício:**
Crie uma lista de strings, ordene-a em ordem decrescente usando `Collections.reverseOrder()` e exiba a lista.

---


### 8. Interface Collection

A interface `Collection` é a raiz da hierarquia de coleções em Java e define os métodos básicos que todas as coleções devem implementar, como `add()` para adicionar elementos, `remove()` para remover elementos e `size()` para retornar o número de elementos na coleção. Essa interface é genérica, o que significa que pode ser usada para criar coleções que armazenam qualquer tipo de objeto.

**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.Collection;

public class CollectionInterfaceExample {
    public static void main(String[] args) {
        Collection<String> items = new ArrayList<>();  // Cria uma coleção de Strings usando ArrayList
        items.add("Item 1");  // Adiciona "Item 1" à coleção
        items.add("Item 2");  // Adiciona "Item 2" à coleção

        System.out.println("Total items: " + items.size());  // Exibe o número de itens na coleção: 2
    }
}
```
Aqui, usamos a interface `Collection` diretamente para criar uma coleção de `String`. Como `ArrayList` implementa `Collection`, podemos usá-la para armazenar e manipular os elementos da lista. O método `size()` retorna o número de elementos presentes na coleção.

**Exercício:**
Implemente uma coleção usando a interface `Collection` e adicione cinco números inteiros. Em seguida, exiba o número total de elementos.

---

### 9. Interface List e Classe ArrayList

A interface `List` estende `Collection` e representa uma coleção ordenada de elementos onde a ordem de inserção é mantida. Cada elemento tem um índice associado, permitindo acessos e manipulações baseados na posição. Listas permitem elementos duplicados e fornecem métodos adicionais, como `get(int index)` para recuperar elementos por sua posição.

`ArrayList` é uma das implementações mais comuns da interface `List`. Ela utiliza um array dinâmico para armazenar os elementos, oferecendo acesso rápido aos elementos através de seus índices. No entanto, operações como inserção e remoção podem ser mais lentas, especialmente em listas grandes, já que podem envolver o redimensionamento do array subjacente.

**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        List<String> animals = new ArrayList<>();  // Cria uma lista de Strings
        animals.add("Dog");  // Adiciona "Dog" à lista
        animals.add("Cat");  // Adiciona "Cat" à lista
        animals.add("Horse");  // Adiciona "Horse" à lista

        System.out.println("Animal at index 1: " + animals.get(1));  // Exibe o segundo elemento: Cat
    }
}
```
Neste exemplo, a lista `animals` armazena nomes de animais. Usamos o método `get(int index)` para acessar o elemento no índice 1 (segundo elemento), que neste caso é "Cat". Isso demonstra como as listas mantêm a ordem e permitem acesso indexado.

**Exercício:**
Crie uma lista de três cores. Exiba a cor armazenada no segundo índice.

---

### 10. Interface Set, HashSet e LinkedHashSet

A interface `Set` estende `Collection`, mas difere da `List` porque não permite elementos duplicados. Um `Set` não mantém a ordem dos elementos, exceto em implementações específicas como `LinkedHashSet`, que preserva a ordem de inserção. 

**HashSet:** É uma das implementações mais comuns de `Set` e é baseada em uma tabela hash. `HashSet` permite operações de adição, remoção e busca de elementos de forma muito eficiente. No entanto, ele não mantém a ordem de inserção dos elementos, o que significa que a ordem em que os elementos são iterados pode ser diferente da ordem em que foram adicionados.

**LinkedHashSet:** Esta classe estende `HashSet` e mantém uma lista duplamente ligada dos elementos. Como resultado, `LinkedHashSet` preserva a ordem de inserção, o que significa que os elementos são iterados na mesma ordem em que foram adicionados. Isso é útil quando você precisa de uma coleção que combine a eficiência do `HashSet` com a ordem previsível do `List`.

**Exemplo Explicado com HashSet:**
```java
import java.util.HashSet;
import java.util.Set;

public class HashSetExample {
    public static void main(String[] args) {
        Set<String> countries = new HashSet<>();  // Cria um conjunto de Strings
        countries.add("Brazil");  // Adiciona "Brazil" ao conjunto
        countries.add("India");  // Adiciona "India" ao conjunto
        countries.add("USA");  // Adiciona "USA" ao conjunto
        countries.add("Brazil");  // Tenta adicionar "Brazil" novamente (duplicado)

        System.out.println(countries);  // Exibe os elementos do conjunto: [Brazil, USA, India]
    }
}
```
Neste exemplo, utilizamos um `HashSet` para armazenar nomes de países. Ao tentar adicionar "Brazil" novamente, o conjunto ignora a entrada duplicada, mantendo apenas uma instância de "Brazil". A ordem de impressão pode variar, pois `HashSet` não mantém a ordem de inserção.

**Exemplo Explicado com LinkedHashSet:**
```java
import java.util.LinkedHashSet;
import java.util.Set;

public class LinkedHashSetExample {
    public static void main(String[] args) {
        Set<String> countries = new LinkedHashSet<>();  // Cria um conjunto de Strings com ordem de inserção preservada
        countries.add("Brazil");  // Adiciona "Brazil" ao conjunto
        countries.add("India");  // Adiciona "India" ao conjunto
        countries.add("USA");  // Adiciona "USA" ao conjunto
        countries.add("Brazil");  // Tenta adicionar "Brazil" novamente (duplicado)

        System.out.println(countries);  // Exibe os elementos do conjunto na ordem de inserção: [Brazil, India, USA]
    }
}
```
Neste exemplo, o `LinkedHashSet` preserva a ordem de inserção dos elementos. Mesmo após tentar adicionar "Brazil" novamente, a ordem de inserção original é mantida.

**Exercício:**
Crie um conjunto usando `LinkedHashSet` que armazene os nomes de três frutas. Adicione uma fruta duplicada e observe como a ordem de inserção é preservada.

---

### 11. Interface Map

A interface `Map` representa um mapeamento de chaves para valores, onde cada chave é única. `Map` não estende `Collection`, mas é frequentemente usado em conjunto com coleções. As implementações mais comuns incluem `HashMap`, que utiliza uma tabela hash para armazenar os dados, e `TreeMap`, que mantém as chaves ordenadas. Métodos como `put(K key, V value)` adicionam pares chave-valor ao mapa, e `get(Object key)` recupera o valor associado a uma chave específica.

**Exemplo Explicado:**
```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        Map<String, Integer> ageMap = new HashMap<>();  // Cria um mapa de Strings (nomes) para Integers (idades)
        ageMap.put("John", 25

);  // Adiciona o par "John" -> 25 ao mapa
        ageMap.put("Sara", 30);  // Adiciona o par "Sara" -> 30 ao mapa

        System.out.println("John's age: " + ageMap.get("John"));  // Exibe a idade associada a "John": 25
    }
}
```
Neste exemplo, usamos um `HashMap` para associar nomes de pessoas às suas idades. Ao chamar o método `get()` com a chave "John", recuperamos o valor associado (25). `HashMap` é eficiente para operações de inserção e recuperação, mas não mantém a ordem dos pares chave-valor.

**Exercício:**
Crie um mapa que armazene três pares de chave-valor representando nomes de pessoas e suas idades. Exiba a idade de uma pessoa específica.

---

### 12. Interface Iterator

A interface `Iterator` fornece uma maneira de percorrer elementos de uma coleção de forma sequencial, sem expor a estrutura subjacente. `Iterator` é útil para realizar operações como remoção de elementos durante a iteração. Ele define métodos como `hasNext()` para verificar se há mais elementos e `next()` para acessar o próximo elemento.

**Exemplo Explicado:**
```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class IteratorExample {
    public static void main(String[] args) {
        List<String> names = new ArrayList<>();  // Cria uma lista de Strings
        names.add("Alice");  // Adiciona "Alice" à lista
        names.add("Bob");  // Adiciona "Bob" à lista
        names.add("Charlie");  // Adiciona "Charlie" à lista

        Iterator<String> iterator = names.iterator();  // Obtém um iterador para a lista
        while (iterator.hasNext()) {  // Verifica se há mais elementos na lista
            System.out.println(iterator.next());  // Exibe o próximo elemento e avança o iterador
        }
    }
}
```
Aqui, utilizamos um `Iterator` para percorrer os elementos da lista `names`. O método `hasNext()` verifica se há mais elementos para iterar, enquanto `next()` retorna o próximo elemento. Este é um padrão comum para iterar coleções em Java.

**Exercício:**
Implemente uma coleção de números inteiros. Use um `Iterator` para percorrer a coleção e exibir cada número no console.

---

### 13. Interface Comparable e Comparator

A interface `Comparable` é usada para definir a ordem natural dos objetos de uma classe específica. Ela requer a implementação do método `compareTo()`, que compara o objeto atual com outro objeto do mesmo tipo. `Comparator`, por outro lado, é uma interface separada que permite definir ordens alternativas. É especialmente útil quando a ordem natural não é suficiente ou quando múltiplos critérios de ordenação são necessários.

**Exemplo Explicado com Comparable:**
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class Person implements Comparable<Person> {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age);  // Compara as idades para ordenar os objetos
    }

    @Override
    public String toString() {
        return name + " - " + age;
    }
}

public class ComparableExample {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();  // Cria uma lista de pessoas
        people.add(new Person("John", 30));  // Adiciona uma nova pessoa à lista
        people.add(new Person("Sara", 25));  // Adiciona uma nova pessoa à lista

        Collections.sort(people);  // Ordena a lista de pessoas usando a ordem natural definida em compareTo()
        System.out.println(people);  // Exibe a lista ordenada: [Sara - 25, John - 30]
    }
}
```
Neste exemplo, criamos a classe `Person` que implementa `Comparable` para permitir a ordenação por idade. O método `compareTo()` define a lógica de comparação. Ao chamar `Collections.sort(people)`, a lista é ordenada com base nas idades. A ordem definida por `Comparable` é usada automaticamente quando a lista é classificada.

**Exemplo Explicado com Comparator:**
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return name + " - " + age;
    }
}

class NameComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return p1.name.compareTo(p2.name);  // Compara os nomes para ordenar os objetos
    }
}

public class ComparatorExample {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();  // Cria uma lista de pessoas
        people.add(new Person("John", 30));  // Adiciona uma nova pessoa à lista
        people.add(new Person("Sara", 25));  // Adiciona uma nova pessoa à lista
        people.add(new Person("Alice", 28));  // Adiciona uma nova pessoa à lista

        Collections.sort(people, new NameComparator());  // Ordena a lista de pessoas usando o Comparator
        System.out.println(people);  // Exibe a lista ordenada: [Alice - 28, John - 30, Sara - 25]
    }
}
```
Neste exemplo, usamos a interface `Comparator` para definir um critério de ordenação alternativo para a classe `Person`. O `NameComparator` ordena as instâncias de `Person` com base nos nomes. Ao chamar `Collections.sort(people, new NameComparator())`, a lista é ordenada de acordo com os nomes das pessoas.

**Exercício:**
Crie uma classe `Produto` que implementa `Comparable` para ordenar produtos por preço. Em seguida, crie um `Comparator` para ordenar produtos por nome. Ordene uma lista de produtos por preço e depois por nome, exibindo a lista em cada caso.

---
