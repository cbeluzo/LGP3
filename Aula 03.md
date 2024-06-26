## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---
# Aula 3: Sistema de Aluguel de Carros em Java

## Objetivo da Aula

Nesta aula, você aprenderá a aplicar conceitos de Programação Orientada a Objetos (POO) em Java, desenvolvendo um sistema básico para uma locadora de veículos. Vamos criar classes, objetos, e implementar métodos que refletem operações comuns em um sistema de aluguel de carros.

## Atividade Prática

### Objetivo:

- Implementar um sistema básico de gerenciamento de aluguel de carros utilizando conceitos de POO em Java.
- Aplicar práticas de codificação, incluindo criação de classes, instanciamento de objetos, e manipulação de coleções.

### Tarefas:

1. **Criar as classes `Carro`, `Cliente` e `Locadora` conforme os requisitos.**
2. **Implementar os métodos de adição, remoção, aluguel e listagem de carros e clientes.**
3. **Desenvolver a classe `Main` para permitir a interação do usuário com o sistema através do console.**
4. **Testar todas as funcionalidades implementadas para garantir que o sistema opere conforme o esperado.**


## Enunciado da Atividade

Você foi contratado para desenvolver um sistema para uma locadora de veículos. O sistema deve ser capaz de realizar as seguintes operações:

1. Adicionar um novo carro à lista de carros disponíveis.
2. Adicionar um novo cliente à lista de clientes.
3. Alugar um carro para um cliente.
4. Exibir a lista de carros disponíveis.
5. Exibir a lista de clientes.

### Classes e Atributos

1. **Classe `Carro`**
   - **Atributos:**
     - `marca` (String): a marca do carro (por exemplo, "Toyota", "Honda").
     - `modelo` (String): o modelo do carro (por exemplo, "Corolla", "Civic").
     - `anoFabricacao` (int): o ano de fabricação do carro.
     - `placa` (String): a placa do carro.
     - `disponivel` (boolean): indica se o carro está disponível para aluguel.
   - **Métodos:**
     - Construtor para inicializar os atributos.
     - Getters e setters para acessar e modificar os atributos.
     - Método `toString` para exibir informações detalhadas do carro.

2. **Classe `Cliente`**
   - **Atributos:**
     - `nome` (String): o nome do cliente.
     - `cpf` (String): o CPF do cliente.
     - `endereco` (String): o endereço do cliente.
     - `telefone` (String): o telefone do cliente.
   - **Métodos:**
     - Construtor para inicializar os atributos.
     - Getters e setters para acessar e modificar os atributos.
     - Método `toString` para exibir informações detalhadas do cliente.

3. **Classe `Locadora`**
   - **Atributos:**
     - `carros` (ArrayList de objetos `Carro`): lista de carros disponíveis.
     - `clientes` (ArrayList de objetos `Cliente`): lista de clientes.
   - **Métodos:**
     - Método para adicionar um novo carro à lista de carros.
     - Método para adicionar um novo cliente à lista de clientes.
     - Método para alugar um carro para um cliente (atualizando a disponibilidade do carro).
     - Métodos para exibir a lista de carros disponíveis e a lista de clientes.

### Código das Classes

#### Classe `Carro`

```java
public class Carro {
    private String marca;
    private String modelo;
    private int anoFabricacao;
    private String placa;
    private boolean disponivel;

    public Carro(String marca, String modelo, int anoFabricacao, String placa) {
        this.marca = marca;
        this.modelo = modelo;
        this.anoFabricacao = anoFabricacao;
        this.placa = placa;
        this.disponivel = true;
    }

    // Getters e setters
    public String getMarca() {
        return marca;
    }

    public void setMarca(String marca) {
        this.marca = marca;
    }

    public String getModelo() {
        return modelo;
    }

    public void setModelo(String modelo) {
        this.modelo = modelo;
    }

    public int getAnoFabricacao() {
        return anoFabricacao;
    }

    public void setAnoFabricacao(int anoFabricacao) {
        this.anoFabricacao = anoFabricacao;
    }

    public String getPlaca() {
        return placa;
    }

    public void setPlaca(String placa) {
        this.placa = placa;
    }

    public boolean isDisponivel() {
        return disponivel;
    }

    public void setDisponivel(boolean disponivel) {
        this.disponivel = disponivel;
    }

    @Override
    public String toString() {
        return "Carro{" +
                "marca='" + marca + '\'' +
                ", modelo='" + modelo + '\'' +
                ", anoFabricacao=" + anoFabricacao +
                ", placa='" + placa + '\'' +
                ", disponivel=" + disponivel +
                '}';
    }
}
```

#### Classe `Cliente`

```java
public class Cliente {
    private String nome;
    private String cpf;
    private String endereco;
    private String telefone;

    public Cliente(String nome, String cpf, String endereco, String telefone) {
        this.nome = nome;
        this.cpf = cpf;
        this.endereco = endereco;
        this.telefone = telefone;
    }

    // Getters e setters
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getCpf() {
        return cpf;
    }

    public void setCpf(String cpf) {
        this.cpf = cpf;
    }

    public String getEndereco() {
        return endereco;
    }

    public void setEndereco(String endereco) {
        this.endereco = endereco;
    }

    public String getTelefone() {
        return telefone;
    }

    public void setTelefone(String telefone) {
        this.telefone = telefone;
    }

    @Override
    public String toString() {
        return "Cliente{" +
                "nome='" + nome + '\'' +
                ", cpf='" + cpf + '\'' +
                ", endereco='" + endereco + '\'' +
                ", telefone='" + telefone + '\'' +
                '}';
    }
}
```

#### Classe `Locadora`

```java
import java.util.ArrayList;

public class Locadora {
    private ArrayList<Carro> carros;
    private ArrayList<Cliente> clientes;

    public Locadora() {
        this.carros = new ArrayList<>();
        this.clientes = new ArrayList<>();
    }

    public void adicionarCarro(Carro carro) {
        carros.add(carro);
        System.out.println("Carro adicionado: " + carro);
    }

    public void adicionarCliente(Cliente cliente) {
        clientes.add(cliente);
        System.out.println("Cliente adicionado: " + cliente);
    }

    public void alugarCarro(String placa, String cpf) {
        Carro carroParaAlugar = null;
        for (Carro carro : carros) {
            if (carro.getPlaca().equals(placa) && carro.isDisponivel()) {
                carroParaAlugar = carro;
                break;
            }
        }
        if (carroParaAlugar != null) {
            carroParaAlugar.setDisponivel(false);
            System.out.println("Carro alugado: " + carroParaAlugar);
        } else {
            System.out.println("Carro não disponível ou não encontrado.");
        }
    }

    public void listarCarrosDisponiveis() {
        System.out.println("Carros disponíveis:");
        for (Carro carro : carros) {
            if (carro.isDisponivel()) {
                System.out.println(carro);
            }
        }
    }

    public void listarClientes() {
        System.out.println("Clientes:");
        for (Cliente cliente : clientes) {
            System.out.println(cliente);
        }
    }
}
```

#### Classe `Main`

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Locadora locadora = new Locadora();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Escolha uma opção:");
            System.out.println("1. Adicionar carro");
            System.out.println("2. Adicionar cliente");
            System.out.println("3. Alugar carro");
            System.out.println("4. Listar carros disponíveis");
            System.out.println("5. Listar clientes");
            System.out.println("6. Sair");

            int opcao = scanner.nextInt();
            scanner.nextLine();  // Consome a linha restante

            switch (opcao) {
                case 1:
                    System.out.println("Digite a marca, modelo, ano de fabricação e placa do carro:");
                    String marca = scanner.nextLine();
                    String modelo = scanner.nextLine();
                    int anoFabricacao = scanner.nextInt();
                    scanner.nextLine();  // Consome a linha restante
                    String placa = scanner.nextLine();
                    locadora.adicionarCarro(new Carro(marca, modelo, anoFabricacao, placa));
                    break;
                case 2:
                    System.out.println("Digite o nome, CPF, endereço e telefone do cliente:");
                    String nome = scanner.nextLine();
                    String cpf = scanner.nextLine();
                    String endereco = scanner.nextLine();
                    String telefone = scanner.nextLine();
                    locadora.adicionarCliente(new Cliente(nome, cpf, endereco, telefone));
                    break;
                case 3:
                    System.out.println("Digite a placa do carro a ser alugado:");
                    placa = scanner.nextLine();
                    System.out.println("Digite o CPF do cliente:");
                    cpf = scanner.nextLine();
                    locadora.alugarCarro(placa, cpf);
                    break;
                case 4:
                    locadora.listarCarrosDisponiveis();
                    break;
                case 5:
                    locadora.listarClientes();
                    break;
                case 6:
                    System.out.println("Saindo...");
                    scanner.close();
                    return

;
                default:
                    System.out.println("Opção inválida.");
            }
        }
    }
}
```

---

### Discussão:

1. **Quais foram os principais desafios ao implementar o sistema de aluguel de carros?**
2. **Como a orientação a objetos ajudou na organização do código e na resolução do problema?**
3. **Que melhorias ou funcionalidades adicionais você sugeriria para o sistema?**

---
