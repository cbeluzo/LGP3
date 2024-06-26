## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---
# Aula 2: Programação Orientada a Objetos em Java

## Objetivo da Aula

Nesta aula, você aprenderá a aplicar conceitos de Programação Orientada a Objetos (POO) em Java, desenvolvendo um sistema básico para uma biblioteca. Vamos criar classes, objetos, e implementar métodos que refletem operações comuns em um sistema de biblioteca.


## Atividade Prática

### Objetivo:

- Implementar um sistema básico de gerenciamento de biblioteca utilizando conceitos de POO em Java.
- Aplicar práticas de codificação, incluindo criação de classes, instanciamento de objetos, e manipulação de coleções.

### Tarefas:

1. **Criar as classes `Livro` e `Biblioteca` conforme os requisitos.**
2. **Implementar os métodos de adição, remoção, empréstimo, devolução e listagem de livros.**
3. **Desenvolver a classe `Main` para permitir a interação do usuário com o sistema através do console.**
4. **Testar todas as funcionalidades implementadas para garantir que o sistema opere conforme o esperado.**

## Enunciado da Atividade

Você foi contratado para desenvolver um sistema para uma biblioteca. O sistema deve ser capaz de realizar as seguintes operações:

1. Adicionar um livro à biblioteca.
2. Remover um livro da biblioteca.
3. Emprestar um livro da biblioteca.
4. Devolver um livro à biblioteca.
5. Listar todos os livros disponíveis na biblioteca.

Cada livro deve ter as seguintes informações:
- Título
- Autor
- Ano de publicação
- Gênero
- Disponibilidade (se o livro está disponível para empréstimo)

## Estrutura das Classes

### Classe `Livro`

A classe `Livro` deve ter os seguintes atributos:
- `titulo` (String)
- `autor` (String)
- `ano` (int)
- `genero` (String)
- `disponivel` (boolean) - inicialmente, um livro é sempre disponível.

A classe `Livro` deve ter os seguintes métodos:
- `getTitulo()`, `getAutor()`, `getAno()`, `getGenero()` - métodos getters para acessar os atributos.
- `isDisponivel()` - método para verificar a disponibilidade do livro.
- `setDisponivel(boolean disponivel)` - método para definir a disponibilidade do livro.

### Código da Classe `Livro`

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Livro {
    private String titulo;
    private String autor;
    private int ano;
    private String genero;
    private boolean disponivel;

    public Livro(String titulo, String autor, int ano, String genero) {
        this.titulo = titulo;
        this.autor = autor;
        this.ano = ano;
        this.genero = genero;
        this.disponivel = true;
    }

    // getters e setters
    public String getTitulo() {
        return titulo;
    }

    public String getAutor() {
        return autor;
    }

    public int getAno() {
        return ano;
    }

    public String getGenero() {
        return genero;
    }

    public boolean isDisponivel() {
        return disponivel;
    }

    public void setDisponivel(boolean disponivel) {
        this.disponivel = disponivel;
    }
}
```

### Classe `Biblioteca`

A classe `Biblioteca` deve gerenciar uma lista de livros e permitir as operações especificadas. Ela deve ter os seguintes métodos:
- `adicionarLivro(Livro livro)` - adiciona um livro à biblioteca.
- `removerLivro(String titulo)` - remove um livro da biblioteca com base no título.
- `emprestarLivro(String titulo)` - empresta um livro, se disponível.
- `devolverLivro(String titulo)` - devolve um livro.
- `listarLivros()` - lista todos os livros disponíveis.

### Código da Classe `Biblioteca`

```java
public class Biblioteca {
    private List<Livro> livros;

    public Biblioteca() {
        this.livros = new ArrayList<>();
    }

    public void adicionarLivro(Livro livro) {
        livros.add(livro);
    }

    public void removerLivro(String titulo) {
        livros.removeIf(livro -> livro.getTitulo().equals(titulo));
    }

    public void emprestarLivro(String titulo) {
        for (Livro livro : livros) {
            if (livro.getTitulo().equals(titulo)) {
                if (livro.isDisponivel()) {
                    livro.setDisponivel(false);
                    System.out.println("Livro emprestado com sucesso.");
                } else {
                    System.out.println("O livro já está emprestado.");
                }
                return;
            }
        }
        System.out.println("Livro não encontrado.");
    }

    public void devolverLivro(String titulo) {
        for (Livro livro : livros) {
            if (livro.getTitulo().equals(titulo)) {
                livro.setDisponivel(true);
                System.out.println("Livro devolvido com sucesso.");
                return;
            }
        }
        System.out.println("Livro não encontrado.");
    }

    public void listarLivros() {
        for (Livro livro : livros) {
            if (livro.isDisponivel()) {
                System.out.println(livro.getTitulo());
            }
        }
    }
}
```

### Classe `Main`

A classe `Main` deve conter o método `main` para interagir com o usuário e realizar as operações no sistema da biblioteca.

### Código da Classe `Main`

```java
public class Main {
    public static void main(String[] args) {
        Biblioteca biblioteca = new Biblioteca();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Escolha uma opção:");
            System.out.println("1. Adicionar livro");
            System.out.println("2. Remover livro");
            System.out.println("3. Emprestar livro");
            System.out.println("4. Devolver livro");
            System.out.println("5. Listar livros");
            System.out.println("6. Sair");

            int opcao = scanner.nextInt();
            scanner.nextLine();  // consome a linha restante

            switch (opcao) {
                case 1:
                    System.out.println("Digite o título, autor, ano e gênero do livro:");
                    String titulo = scanner.nextLine();
                    String autor = scanner.nextLine();
                    int ano = scanner.nextInt();
                    scanner.nextLine();  // consome a linha restante
                    String genero = scanner.nextLine();
                    biblioteca.adicionarLivro(new Livro(titulo, autor, ano, genero));
                    break;
                case 2:
                    System.out.println("Digite o título do livro a ser removido:");
                    titulo = scanner.nextLine();
                    biblioteca.removerLivro(titulo);
                    break;
                case 3:
                    System.out.println("Digite o título do livro a ser emprestado:");
                    titulo = scanner.nextLine();
                    biblioteca.emprestarLivro(titulo);
                    break;
                case 4:
                    System.out.println("Digite o título do livro a ser devolvido:");
                    titulo = scanner.nextLine();
                    biblioteca.devolverLivro(titulo);
                    break;
                case 5:
                    biblioteca.listarLivros();
                    break;
                case 6:
                    System.out.println("Saindo...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Opção inválida.");
            }
        }
    }
}
```

---
### Discussão:

1. **Quais foram os principais desafios ao implementar o sistema de biblioteca?**
2. **Como a orientação a objetos ajudou na organização do código e na resolução do problema?**
3. **Que melhorias ou funcionalidades adicionais você sugeriria para o sistema?**

