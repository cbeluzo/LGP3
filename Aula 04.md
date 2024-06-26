## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---
# Aula 4: Conceitos Avançados de POO em Java

## Objetivo da Aula

Nesta aula, você aprenderá conceitos avançados de Programação Orientada a Objetos (POO) em Java, incluindo pacotes, modificadores de acesso, herança, classes abstratas, exceções, listas e interfaces. Vamos explorar cada conceito com exemplos práticos para reforçar o aprendizado.

## 1. Classes e Objetos

### Definição

- **Classe:** Um modelo ou plano a partir do qual os objetos são criados.
- **Objeto:** Uma instância de uma classe.

### Exemplo

```java
class Carro {
    String cor;
    String modelo;
}

public class Main {
    public static void main(String[] args) {
        Carro meuCarro = new Carro();
        meuCarro.cor = "Vermelho";
        meuCarro.modelo = "Ferrari";
        System.out.println("Cor: " + meuCarro.cor + ", Modelo: " + meuCarro.modelo);
    }
}
```

## 2. Pacotes em Java

### Definição

Pacotes são usados para agrupar classes relacionadas, ajudando a organizar o código e evitar conflitos de nomes. A convenção de nomenclatura de pacotes é usar nomes de domínio na Internet invertidos.

### Exemplo

```java
package br.com.exemplo;

public class MinhaClasse {
    // código da classe
}
```

## 3. Modificadores de Acesso

### Definição

- **public:** O membro é acessível de qualquer lugar.
- **protected:** O membro é acessível dentro do pacote e por subclasses fora do pacote.
- **private:** O membro é acessível apenas dentro da classe.
- **default (nenhum modificador):** O membro é acessível dentro do pacote.

### Exemplo

```java
public class MinhaClasse {
    public int variavelPublica;
    protected int variavelProtegida;
    private int variavelPrivada;
    int variavelDefault;
}
```

## 4. Herança

### Definição

A herança permite que uma classe herde campos e métodos de outra classe.

### Exemplo

```java
class Veiculo {
    int velocidade;
}

class Carro extends Veiculo {
    int numeroDeRodas;
}

public class Main {
    public static void main(String[] args) {
        Carro carro = new Carro();
        carro.velocidade = 100;
        carro.numeroDeRodas = 4;
        System.out.println("Velocidade: " + carro.velocidade + ", Número de Rodas: " + carro.numeroDeRodas);
    }
}
```

## 5. Classes Abstratas e Métodos Abstratos

### Definição

Uma classe abstrata é uma classe que não pode ser instanciada e é usada como classe base para outras classes. Métodos abstratos são declarados, mas sem implementação, e as subclasses devem fornecer a implementação.

### Exemplo

```java
abstract class Animal {
    abstract void fazerSom();
}

class Cachorro extends Animal {
    void fazerSom() {
        System.out.println("Au Au");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal meuCachorro = new Cachorro();
        meuCachorro.fazerSom();
    }
}
```

## 6. Exceções

### Definição

Exceções são eventos que ocorrem durante a execução de programas e perturbam o fluxo normal de instruções.

### Exemplo

```java
class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String mensagem) {
        super(mensagem);
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            throw new SaldoInsuficienteException("Saldo insuficiente para realizar a operação.");
        } catch (SaldoInsuficienteException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

## 7. Listas

### Definição

As listas são usadas para armazenar uma coleção ordenada de elementos.

### Exemplo

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> lista = new ArrayList<>();
        lista.add("item1");
        lista.add("item2");

        for (String item : lista) {
            System.out.println(item);
        }
    }
}
```

## 8. Interfaces

### Definição

Uma interface é uma referência de tipo em Java, similar a uma classe, e é uma coleção de métodos abstratos e constantes.

### Exemplo

```java
interface FormaGeometrica {
    void calcularArea();
    void calcularPerimetro();
}
```

## 9. Implementação de Interfaces

### Definição

A palavra-chave `implements` é usada para implementar uma interface. Todas as classes que implementam uma interface devem fornecer implementações para os métodos declarados na interface.

### Exemplo

```java
class Retangulo implements FormaGeometrica {
    @Override
    public void calcularArea() {
        System.out.println("Calculando área do retângulo...");
    }

    @Override
    public void calcularPerimetro() {
        System.out.println("Calculando perímetro do retângulo...");
    }
}

public class Main {
    public static void main(String[] args) {
        FormaGeometrica retangulo = new Retangulo();
        retangulo.calcularArea();
        retangulo.calcularPerimetro();
    }
}
```

## Atividade Prática

### Objetivo

- Aplicar conceitos avançados de POO em Java, incluindo pacotes, modificadores de acesso, herança, classes abstratas, exceções, listas e interfaces.

### Tarefas

1. **Criar um pacote `br.com.exemplo` e adicionar classes com diferentes modificadores de acesso.**
2. **Implementar uma hierarquia de classes utilizando herança.**
3. **Criar uma classe abstrata e herdar de outra classe, implementando métodos abstratos.**
4. **Lançar e tratar exceções personalizadas em Java.**
5. **Utilizar listas para armazenar e manipular dados.**
6. **Definir e implementar interfaces em classes concretas.**

### Discussão

1. **Quais foram os principais desafios ao implementar os conceitos avançados de POO em Java?**
2. **Como a utilização de pacotes e modificadores de acesso ajuda na organização do código?**
3. **Que vantagens você percebe ao utilizar herança e interfaces em seus projetos?**

---
