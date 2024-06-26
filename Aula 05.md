## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---
# Aula 5: Aplicações Práticas de POO em Java

## Objetivo da Aula

Nesta aula, você aprenderá a aplicar conceitos de Programação Orientada a Objetos (POO) em Java através de exemplos práticos envolvendo listas, herança, interfaces e tratamento de exceções. Vamos explorar cada conceito com exercícios práticos para reforçar o aprendizado.

## 1. Listas

### Exemplo 1: Lista de Inteiros

Crie uma lista de inteiros e adicione 5 números à lista. Em seguida, imprima todos os números na lista.

#### Código

```java
import java.util.ArrayList;
import java.util.List;

public class ListaInteiros {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        numeros.add(1);
        numeros.add(2);
        numeros.add(3);
        numeros.add(4);
        numeros.add(5);

        for (int numero : numeros) {
            System.out.println(numero);
        }
    }
}
```

### Exemplo 2: Lista de Compras

Crie uma lista de Strings que represente uma lista de compras. Adicione alguns itens à lista e, em seguida, use um loop para imprimir todos os itens. Finalmente, remova um item da lista e imprima a lista novamente para verificar se o item foi removido.

#### Código

```java
import java.util.ArrayList;
import java.util.List;

public class ListaCompras {
    public static void main(String[] args) {
        List<String> listaCompras = new ArrayList<>();
        listaCompras.add("Leite");
        listaCompras.add("Pão");
        listaCompras.add("Manteiga");
        listaCompras.add("Ovos");

        for (String item : listaCompras) {
            System.out.println(item);
        }

        listaCompras.remove("Manteiga");
        System.out.println("Após remover Manteiga:");

        for (String item : listaCompras) {
            System.out.println(item);
        }
    }
}
```

## 2. Herança

### Exemplo 1: Herança Simples

Crie uma classe `Planta` com um método `fotossintese()`. Em seguida, crie duas classes, `Flor` e `Arvore`, que herdam de `Planta` e sobrescrevem o método `fotossintese()`.

#### Código

```java
class Planta {
    void fotossintese() {
        System.out.println("Realizando fotossíntese");
    }
}

class Flor extends Planta {
    @Override
    void fotossintese() {
        System.out.println("Flor realizando fotossíntese");
    }
}

class Arvore extends Planta {
    @Override
    void fotossintese() {
        System.out.println("Árvore realizando fotossíntese");
    }
}

public class Main {
    public static void main(String[] args) {
        Planta minhaFlor = new Flor();
        Planta minhaArvore = new Arvore();

        minhaFlor.fotossintese();
        minhaArvore.fotossintese();
    }
}
```

### Exemplo 2: Classes Abstratas

Crie uma classe abstrata `InstrumentoMusical` com métodos abstratos `tocar()` e `afinar()`. Em seguida, crie duas classes, `Violao` e `Piano`, que herdam de `InstrumentoMusical` e implementam os métodos `tocar()` e `afinar()`.

#### Código

```java
abstract class InstrumentoMusical {
    abstract void tocar();
    abstract void afinar();
}

class Violao extends InstrumentoMusical {
    @Override
    void tocar() {
        System.out.println("Tocando violão");
    }

    @Override
    void afinar() {
        System.out.println("Afinando violão");
    }
}

class Piano extends InstrumentoMusical {
    @Override
    void tocar() {
        System.out.println("Tocando piano");
    }

    @Override
    void afinar() {
        System.out.println("Afinando piano");
    }
}

public class Main {
    public static void main(String[] args) {
        InstrumentoMusical meuViolao = new Violao();
        InstrumentoMusical meuPiano = new Piano();

        meuViolao.tocar();
        meuViolao.afinar();

        meuPiano.tocar();
        meuPiano.afinar();
    }
}
```

## 3. Interfaces

### Exemplo: Implementação de Interface

Crie uma interface `DispositivoEletronico` com métodos `ligar()` e `desligar()`. Em seguida, crie duas classes, `Televisao` e `Computador`, que implementam a interface `DispositivoEletronico` e implementam os métodos `ligar()` e `desligar()`.

#### Código

```java
interface DispositivoEletronico {
    void ligar();
    void desligar();
}

class Televisao implements DispositivoEletronico {
    @Override
    public void ligar() {
        System.out.println("Televisão ligada");
    }

    @Override
    public void desligar() {
        System.out.println("Televisão desligada");
    }
}

class Computador implements DispositivoEletronico {
    @Override
    public void ligar() {
        System.out.println("Computador ligado");
    }

    @Override
    public void desligar() {
        System.out.println("Computador desligado");
    }
}

public class Main {
    public static void main(String[] args) {
        DispositivoEletronico minhaTV = new Televisao();
        DispositivoEletronico meuPC = new Computador();

        minhaTV.ligar();
        minhaTV.desligar();

        meuPC.ligar();
        meuPC.desligar();
    }
}
```

## 4. Tratamento de Exceções

### Exemplo: Exceção Definida pelo Usuário

Crie uma classe `Livro` com um método `lerPagina(int pagina)`. Este método deve lançar uma exceção se a página for menor que 1 ou maior que o número total de páginas do livro.

#### Código

```java
class PaginaInvalidaException extends Exception {
    public PaginaInvalidaException(String mensagem) {
        super(mensagem);
    }
}

class Livro {
    private int totalPaginas;

    public Livro(int totalPaginas) {
        this.totalPaginas = totalPaginas;
    }

    public void lerPagina(int pagina) throws PaginaInvalidaException {
        if (pagina < 1 || pagina > totalPaginas) {
            throw new PaginaInvalidaException("Número de página inválido: " + pagina);
        }
        System.out.println("Lendo página " + pagina);
    }
}

public class Main {
    public static void main(String[] args) {
        Livro meuLivro = new Livro(100);
        try {
            meuLivro.lerPagina(150);
        } catch (PaginaInvalidaException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

## Atividade Prática

### Objetivo

- Aplicar conceitos avançados de POO em Java, incluindo listas, herança, interfaces e tratamento de exceções.

### Tarefas

1. **Criar e manipular listas de diferentes tipos de dados.**
2. **Implementar herança simples e classes abstratas.**
3. **Definir e implementar interfaces.**
4. **Lançar e tratar exceções personalizadas em Java.**

### Discussão

1. **Quais foram os principais desafios ao implementar os conceitos avançados de POO em Java?**
2. **Como a utilização de listas facilita a manipulação de coleções de dados?**
3. **Que vantagens você percebe ao utilizar herança e interfaces em seus projetos?**

---
