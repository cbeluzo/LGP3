### 7. Classes from Java API: Uso de Classes Essenciais da API Java

#### Objetivo
Entender e utilizar as classes essenciais da Java Standard Edition (SE) API, que são frequentemente utilizadas em desenvolvimento de software. Essas classes facilitam tarefas comuns, como manipulação de strings, formatação de datas, coleções de dados, e entrada/saída (I/O).

#### Classes Essenciais

1. **String**
2. **StringBuilder**
3. **Math**
4. **Wrapper Classes (Integer, Double, etc.)**
5. **Date e Calendar**
6. **ArrayList**
7. **HashMap**
8. **Input/Output (I/O)**

### Detalhamento dos Tópicos

#### String

- **Conceitos Principais**:
    - A classe `String` é imutável e usada para representar sequências de caracteres.
    - Métodos comuns: `length()`, `charAt()`, `substring()`, `toUpperCase()`, `toLowerCase()`, `replace()`, `split()`, `equals()`, `compareTo()`.

- **Exemplo**:
    ```java
    public class StringExample {
        public static void main(String[] args) {
            String s = "Hello, World!";
            System.out.println("Length: " + s.length());
            System.out.println("Character at index 1: " + s.charAt(1));
            System.out.println("Substring (0-5): " + s.substring(0, 5));
            System.out.println("Uppercase: " + s.toUpperCase());
            System.out.println("Lowercase: " + s.toLowerCase());
            System.out.println("Replace 'World' with 'Java': " + s.replace("World", "Java"));
            System.out.println("Split by ', ': " + Arrays.toString(s.split(", ")));
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que verifica se uma string é um palíndromo.
    2. Escrever um programa que conte o número de vogais em uma string.
    3. Desenvolver um programa que encontre a primeira ocorrência de um caractere em uma string.

#### StringBuilder

- **Conceitos Principais**:
    - A classe `StringBuilder` é mutável e usada para construir strings de maneira eficiente.
    - Métodos comuns: `append()`, `insert()`, `delete()`, `reverse()`, `toString()`.

- **Exemplo**:
    ```java
    public class StringBuilderExample {
        public static void main(String[] args) {
            StringBuilder sb = new StringBuilder("Hello");
            sb.append(", World!");
            System.out.println(sb.toString());
            sb.insert(5, " Java");
            System.out.println(sb.toString());
            sb.delete(5, 10);
            System.out.println(sb.toString());
            sb.reverse();
            System.out.println(sb.toString());
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que usa `StringBuilder` para construir uma string a partir de um array de palavras.
    2. Desenvolver um programa que remove todas as vogais de uma string usando `StringBuilder`.
    3. Escrever um programa que insere uma string em outra string em uma posição específica usando `StringBuilder`.

#### Math

- **Conceitos Principais**:
    - A classe `Math` fornece métodos para operações matemáticas básicas e avançadas.
    - Métodos comuns: `abs()`, `max()`, `min()`, `sqrt()`, `pow()`, `random()`.

- **Exemplo**:
    ```java
    public class MathExample {
        public static void main(String[] args) {
            System.out.println("Absolute value: " + Math.abs(-10));
            System.out.println("Max value: " + Math.max(10, 20));
            System.out.println("Min value: " + Math.min(10, 20));
            System.out.println("Square root: " + Math.sqrt(16));
            System.out.println("Power: " + Math.pow(2, 3));
            System.out.println("Random number: " + Math.random());
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que calcula a hipotenusa de um triângulo retângulo dados os comprimentos dos catetos.
    2. Escrever um programa que gera um número aleatório entre 1 e 100.
    3. Desenvolver um programa que encontra o maior valor em um array de inteiros.

#### Wrapper Classes

- **Conceitos Principais**:
    - Classes wrapper (`Integer`, `Double`, etc.) são usadas para converter tipos primitivos em objetos.
    - Métodos comuns: `valueOf()`, `parseInt()`, `parseDouble()`, `toString()`, `intValue()`, `doubleValue()`.

- **Exemplo**:
    ```java
    public class WrapperExample {
        public static void main(String[] args) {
            Integer intObj = Integer.valueOf(10);
            int intValue = intObj.intValue();
            System.out.println("Integer object: " + intObj);
            System.out.println("Primitive int: " + intValue);

            String str = "123.45";
            Double doubleObj = Double.parseDouble(str);
            System.out.println("Parsed double: " + doubleObj);
        }
    }
    ```

- **Exercícios**:
    1. Converter uma lista de strings em uma lista de inteiros.
    2. Desenvolver um programa que calcula a soma e a média de uma lista de números inteiros.
    3. Criar um programa que lê uma string de números e retorna a soma total.

#### Date e Calendar

- **Conceitos Principais**:
    - Classes `Date` e `Calendar` são usadas para manipulação de datas.
    - Métodos comuns: `getTime()`, `setTime()`, `add()`, `get()`, `set()`.

- **Exemplo**:
    ```java
    import java.util.Date;
    import java.util.Calendar;

    public class DateExample {
        public static void main(String[] args) {
            Date now = new Date();
            System.out.println("Current date: " + now);

            Calendar cal = Calendar.getInstance();
            cal.set(2023, Calendar.JUNE, 15);
            Date specificDate = cal.getTime();
            System.out.println("Specific date: " + specificDate);

            cal.add(Calendar.DAY_OF_MONTH, 10);
            Date futureDate = cal.getTime();
            System.out.println("Future date: " + futureDate);
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que calcula a diferença em dias entre duas datas.
    2. Desenvolver um programa que adiciona um número específico de dias a uma data e exibe a nova data.
    3. Escrever um programa que verifica se uma data é antes ou depois de outra data.

#### ArrayList

- **Conceitos Principais**:
    - A classe `ArrayList` é uma implementação redimensionável da interface `List`.
    - Métodos comuns: `add()`, `get()`, `set()`, `remove()`, `size()`.

- **Exemplo**:
    ```java
    import java.util.ArrayList;

    public class ArrayListExample {
        public static void main(String[] args) {
            ArrayList<String> list = new ArrayList<>();
            list.add("Apple");
            list.add("Banana");
            list.add("Cherry");
            System.out.println("List: " + list);
            System.out.println("First element: " + list.get(0));
            list.set(1, "Blueberry");
            System.out.println("Updated list: " + list);
            list.remove(2);
            System.out.println("List after removal: " + list);
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que gerencia uma lista de tarefas, permitindo adicionar, remover e listar tarefas.
    2. Desenvolver um programa que ordena uma lista de números inteiros.
    3. Escrever um programa que encontra o maior e o menor valor em uma lista de números.

#### HashMap

- **Conceitos Principais**:
    - A classe `HashMap` implementa a interface `Map` e é usada para armazenar pares chave-valor.
    - Métodos comuns: `put()`, `get()`, `remove()`, `containsKey()`, `keySet()`.

- **Exemplo**:
    ```java
    import java.util.HashMap;

    public class HashMapExample {
        public static void main(String[] args) {
            HashMap<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            map.put("Two", 2);
            map.put("Three", 3);
            System.out.println("Map: " + map);
            System.out.println("Value for 'Two': " + map.get("Two"));
            map.remove("One");
            System.out.println("Map after removal: " + map);
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que gerencia um inventário de produtos, permitindo adicionar, remover e buscar produtos pelo nome.
    2. Desenvolver um programa que conta a frequência de palavras em um texto.
    3. Escrever um programa que armazena informações de contato (nome, telefone) e permite a busca por nome.

#### Input/Output (I/O)

- **Conceitos Principais**:
    - As classes de entrada/saída (I/O) são usadas para ler e escrever dados de e para arquivos, bem como para realizar outras operações de I/O.
    - Classes comuns: `File`, `FileInputStream`, `FileOutputStream`, `BufferedReader`, `BufferedWriter`.
    - Métodos comuns: `read()`, `write()`, `close()`.

- **Exemplo**:
    ```java
    import java.io.*;

    public class FileExample {
        public static void main(String[] args) {
            try {
                // Escrever em um arquivo
                BufferedWriter writer = new BufferedWriter(new FileWriter("example.txt"));
                writer.write("Hello, World!");
                writer.newLine();
                writer.write("Java I/O Example.");
                writer.close();

                // Ler de um arquivo
                BufferedReader reader = new BufferedReader(new FileReader("example.txt"));
                String line;
                while ((line = reader.readLine()) != null) {
                    System.out.println(line);
                }
                reader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
    ```

- **Exercícios**:
    1. Criar um programa que lê um arquivo de texto linha por linha e imprime o conteúdo no console.
    2. Desenvolver um programa que copia o conteúdo de um arquivo para outro.
    3. Escrever um programa que grava um array de strings em um arquivo, com cada string em uma nova linha.

---

Este roteiro de aula fornece uma visão detalhada do uso de classes essenciais da API Java, incluindo exemplos e exercícios práticos para reforçar o aprendizado. Cada tópico foi abordado com explicações claras e exemplos de código para demonstrar como utilizar essas classes no desenvolvimento de software.
