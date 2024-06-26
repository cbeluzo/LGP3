## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---

# Aula 6: Exercícios de Fixação de Orientação a Objetos

## Objetivo da Aula

Nesta aula, você praticará os conceitos de Programação Orientada a Objetos (POO) em Java através de uma série de exercícios de diferentes níveis de dificuldade. Esses exercícios abordarão a criação de classes, herança, interfaces, e tratamento de exceções.

## Nível Básico

### 1. Classe Calculadora

Crie uma classe `Calculadora` com métodos para as quatro operações básicas: `somar()`, `subtrair()`, `multiplicar()` e `dividir()`. Cada método deve receber dois parâmetros e retornar o resultado da operação. Crie um objeto da classe `Calculadora` e teste os métodos.

#### Código

```java
public class Calculadora {
    public int somar(int a, int b) {
        return a + b;
    }

    public int subtrair(int a, int b) {
        return a - b;
    }

    public int multiplicar(int a, int b) {
        return a * b;
    }

    public double dividir(int a, int b) {
        if (b != 0) {
            return (double) a / b;
        } else {
            throw new ArithmeticException("Divisão por zero não é permitida");
        }
    }

    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        System.out.println("Soma: " + calc.somar(10, 5));
        System.out.println("Subtração: " + calc.subtrair(10, 5));
        System.out.println("Multiplicação: " + calc.multiplicar(10, 5));
        System.out.println("Divisão: " + calc.dividir(10, 5));
    }
}
```

### 2. Classe Estudante

Crie uma classe `Estudante` com os atributos `nome`, `idade` e `nota`. Adicione um método `aprovado()` que retorna `true` se a nota for maior ou igual a 7 e `false` caso contrário. Crie um objeto da classe `Estudante`, atribua valores aos atributos e chame o método `aprovado()` para verificar se o estudante foi aprovado ou não.

#### Código

```java
public class Estudante {
    private String nome;
    private int idade;
    private double nota;

    public Estudante(String nome, int idade, double nota) {
        this.nome = nome;
        this.idade = idade;
        this.nota = nota;
    }

    public boolean aprovado() {
        return this.nota >= 7;
    }

    public static void main(String[] args) {
        Estudante estudante = new Estudante("João", 20, 8.5);
        System.out.println("Estudante aprovado: " + estudante.aprovado());
    }
}
```

### 3. Classe Livro

Crie uma classe `Livro` com os atributos `titulo`, `autor` e `anoDePublicacao`. Adicione um método `imprimirDetalhes()` que imprime todos os detalhes do livro. Crie um objeto da classe `Livro`, atribua valores aos atributos e chame o método `imprimirDetalhes()`.

#### Código

```java
public class Livro {
    private String titulo;
    private String autor;
    private int anoDePublicacao;

    public Livro(String titulo, String autor, int anoDePublicacao) {
        this.titulo = titulo;
        this.autor = autor;
        this.anoDePublicacao = anoDePublicacao;
    }

    public void imprimirDetalhes() {
        System.out.println("Título: " + this.titulo);
        System.out.println("Autor: " + this.autor);
        System.out.println("Ano de Publicação: " + this.anoDePublicacao);
    }

    public static void main(String[] args) {
        Livro livro = new Livro("Dom Casmurro", "Machado de Assis", 1899);
        livro.imprimirDetalhes();
    }
}
```

### 4. Classe ContaBancaria

Crie uma classe `ContaBancaria` com os atributos `numeroDaConta` e `saldo`. A classe deve ter métodos para `depositar()`, `sacar()` e `verSaldo()`. O método `depositar()` deve adicionar o valor ao saldo, o método `sacar()` deve subtrair o valor do saldo e o método `verSaldo()` deve imprimir o saldo atual. Crie um objeto da classe `ContaBancaria` e teste os métodos.

#### Código

```java
public class ContaBancaria {
    private int numeroDaConta;
    private double saldo;

    public ContaBancaria(int numeroDaConta, double saldoInicial) {
        this.numeroDaConta = numeroDaConta;
        this.saldo = saldoInicial;
    }

    public void depositar(double valor) {
        this.saldo += valor;
    }

    public void sacar(double valor) {
        if (valor <= this.saldo) {
            this.saldo -= valor;
        } else {
            System.out.println("Saldo insuficiente");
        }
    }

    public void verSaldo() {
        System.out.println("Saldo atual: " + this.saldo);
    }

    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria(12345, 1000);
        conta.depositar(500);
        conta.sacar(200);
        conta.verSaldo();
    }
}
```

## Nível Médio

### 1. Classe Polígono

Crie uma classe abstrata `Poligono` com um método abstrato `area()`. Em seguida, crie classes `Retangulo`, `Circulo` e `Triangulo` que estendem a classe `Poligono` e implementam o método `area()`. Crie objetos dessas classes e teste o método `area()`.

#### Código

```java
abstract class Poligono {
    abstract double area();
}

class Retangulo extends Poligono {
    private double largura;
    private double altura;

    public Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    double area() {
        return largura * altura;
    }
}

class Circulo extends Poligono {
    private double raio;

    public Circulo(double raio) {
        this.raio = raio;
    }

    @Override
    double area() {
        return Math.PI * raio * raio;
    }
}

class Triangulo extends Poligono {
    private double base;
    private double altura;

    public Triangulo(double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    @Override
    double area() {
        return (base * altura) / 2;
    }
}

public class Main {
    public static void main(String[] args) {
        Poligono retangulo = new Retangulo(5, 10);
        Poligono circulo = new Circulo(7);
        Poligono triangulo = new Triangulo(4, 8);

        System.out.println("Área do Retângulo: " + retangulo.area());
        System.out.println("Área do Círculo: " + circulo.area());
        System.out.println("Área do Triângulo: " + triangulo.area());
    }
}
```

### 2. Classe Conta Bancária com Exceções

Modifique a classe `ContaBancaria` do exercício anterior para lançar uma exceção personalizada `SaldoInsuficienteException` quando uma tentativa de saque é feita, mas o saldo é insuficiente. Teste a classe com um programa que tente fazer um saque maior que o saldo disponível.

#### Código

```java
class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String mensagem) {
        super(mensagem);
    }
}

public class ContaBancaria {
    private int numeroDaConta;
    private double saldo;

    public ContaBancaria(int numeroDaConta, double saldoInicial) {
        this.numeroDaConta = numeroDaConta;
        this.saldo = saldoInicial;
    }

    public void depositar(double valor) {
        this.saldo += valor;
    }

    public void sacar(double valor) throws SaldoInsuficienteException {
        if (valor <= this.saldo) {
            this.saldo -= valor;
        } else {
            throw new SaldoInsuficienteException("Saldo insuficiente para realizar o saque.");
        }
    }

    public void verSaldo() {
        System.out.println("Saldo atual: " + this.saldo);
    }

    public static void main(String[] args) {
        ContaBancaria conta = new ContaBancaria(12345, 1000);
        conta.depositar(500);

        try {
            conta.sacar(2000);
        } catch (SaldoInsuficienteException e) {
            System.out.println(e.getMessage());
        }

        conta.verSaldo();
    }
}
```

### 3. Classe Agenda

Crie uma classe `Agenda` que mantém uma lista de `Compromissos`. Cada `Compromisso` tem uma `data`, `hora` e `descricao`. A classe `Agenda` deve ter métodos para adicionar um `Compromisso` e para retornar uma lista de `Compromissos` para uma data específica.



#### Código

```java
import java.util.ArrayList;
import java.util.List;

class Compromisso {
    private String data;
    private String hora;
    private String descricao;

    public Compromisso(String data, String hora, String descricao) {
        this.data = data;
        this.hora = hora;
        this.descricao = descricao;
    }

    public String getData() {
        return data;
    }

    @Override
    public String toString() {
        return "Data: " + data + ", Hora: " + hora + ", Descrição: " + descricao;
    }
}

class Agenda {
    private List<Compromisso> compromissos;

    public Agenda() {
        this.compromissos = new ArrayList<>();
    }

    public void adicionarCompromisso(Compromisso compromisso) {
        compromissos.add(compromisso);
    }

    public List<Compromisso> listarCompromissosPorData(String data) {
        List<Compromisso> compromissosNaData = new ArrayList<>();
        for (Compromisso c : compromissos) {
            if (c.getData().equals(data)) {
                compromissosNaData.add(c);
            }
        }
        return compromissosNaData;
    }

    public static void main(String[] args) {
        Agenda agenda = new Agenda();
        agenda.adicionarCompromisso(new Compromisso("2023-06-01", "10:00", "Reunião com o cliente"));
        agenda.adicionarCompromisso(new Compromisso("2023-06-01", "14:00", "Consulta médica"));
        agenda.adicionarCompromisso(new Compromisso("2023-06-02", "09:00", "Reunião de equipe"));

        List<Compromisso> compromissos = agenda.listarCompromissosPorData("2023-06-01");
        for (Compromisso c : compromissos) {
            System.out.println(c);
        }
    }
}
```

### 4. Interface FormaGeometrica

Crie uma interface `FormaGeometrica` com métodos para `calcularArea()` e `calcularPerimetro()`. Em seguida, crie classes `Quadrado`, `Circulo` e `Retangulo` que implementam a interface `FormaGeometrica`. Crie objetos dessas classes e teste os métodos.

#### Código

```java
interface FormaGeometrica {
    double calcularArea();
    double calcularPerimetro();
}

class Quadrado implements FormaGeometrica {
    private double lado;

    public Quadrado(double lado) {
        this.lado = lado;
    }

    @Override
    public double calcularArea() {
        return lado * lado;
    }

    @Override
    public double calcularPerimetro() {
        return 4 * lado;
    }
}

class Circulo implements FormaGeometrica {
    private double raio;

    public Circulo(double raio) {
        this.raio = raio;
    }

    @Override
    public double calcularArea() {
        return Math.PI * raio * raio;
    }

    @Override
    public double calcularPerimetro() {
        return 2 * Math.PI * raio;
    }
}

class Retangulo implements FormaGeometrica {
    private double largura;
    private double altura;

    public Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    public double calcularArea() {
        return largura * altura;
    }

    @Override
    public double calcularPerimetro() {
        return 2 * (largura + altura);
    }
}

public class Main {
    public static void main(String[] args) {
        FormaGeometrica quadrado = new Quadrado(4);
        FormaGeometrica circulo = new Circulo(3);
        FormaGeometrica retangulo = new Retangulo(5, 10);

        System.out.println("Área do Quadrado: " + quadrado.calcularArea());
        System.out.println("Perímetro do Quadrado: " + quadrado.calcularPerimetro());

        System.out.println("Área do Círculo: " + circulo.calcularArea());
        System.out.println("Perímetro do Círculo: " + circulo.calcularPerimetro());

        System.out.println("Área do Retângulo: " + retangulo.calcularArea());
        System.out.println("Perímetro do Retângulo: " + retangulo.calcularPerimetro());
    }
}
```

## Nível Difícil

### 1. Sistema de Reservas de Hotel

Crie um sistema de reservas de hotel com classes para `Hotel`, `Quarto`, `Reserva` e `Cliente`. Os clientes devem ser capazes de fazer reservas, que ocupam um quarto por um certo período de tempo. Garanta que os quartos não sejam reservados por mais de um cliente ao mesmo tempo.

### 2. Simulação de Tráfego

Crie uma simulação de tráfego. Use classes para representar `Carros`, `Semaforos` e `Intersecoes`. Carros devem se mover de uma interseção para outra, mas devem parar se um semáforo estiver vermelho. Você precisará usar multithreading para que vários carros e semáforos possam operar simultaneamente.

### 3. Jogo de Xadrez

Implemente um jogo de xadrez. Crie classes para o `Tabuleiro`, as `Pecas` e os `Jogadores`. Cada tipo de peça (Rei, Rainha, Bispo, Cavalo, Torre e Peão) deve ser uma subclasse da classe `Peca`. As peças devem saber como elas podem se mover no tabuleiro. Os jogadores devem ser capazes de fazer movimentos, que são então validados e executados pelo tabuleiro.

### 4. Sistema de Arquivos

Crie uma representação simplificada de um sistema de arquivos. Use classes para representar `Arquivos`, `Diretorios` e um `SistemaDeArquivos`. Arquivos devem ter um tamanho. Diretorios podem conter Arquivos e outros Diretorios. O `SistemaDeArquivos` deve ser capaz de calcular o tamanho total de um Diretorio, incluindo todos os Arquivos e Diretorios que ele contém.

## Atividade Prática

### Objetivo

- Aplicar conceitos de POO em Java através de exercícios práticos de diferentes níveis de dificuldade.
- Desenvolver habilidades de resolução de problemas e lógica de programação.

### Tarefas

1. **Implementar classes e métodos conforme descrito nos exercícios de nível básico, médio e difícil.**
2. **Testar as implementações para garantir o funcionamento correto dos métodos e funcionalidades.**
3. **Discutir as soluções e desafios encontrados durante a implementação dos exercícios.**

### Discussão

1. **Quais foram os principais desafios ao implementar os exercícios de diferentes níveis de dificuldade?**
2. **Como a prática dos conceitos de POO em diferentes cenários ajudou a consolidar o aprendizado?**
3. **Que melhorias ou funcionalidades adicionais você sugeriria para os exercícios de nível difícil?**

---

# Soluções

### 1. Sistema de Reservas de Hotel

#### Código

```java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

class Cliente {
    private String nome;
    private String cpf;

    public Cliente(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }

    public String getNome() {
        return nome;
    }

    public String getCpf() {
        return cpf;
    }
}

class Quarto {
    private int numero;
    private boolean disponivel;

    public Quarto(int numero) {
        this.numero = numero;
        this.disponivel = true;
    }

    public int getNumero() {
        return numero;
    }

    public boolean isDisponivel() {
        return disponivel;
    }

    public void setDisponivel(boolean disponivel) {
        this.disponivel = disponivel;
    }
}

class Reserva {
    private Cliente cliente;
    private Quarto quarto;
    private Date dataInicio;
    private Date dataFim;

    public Reserva(Cliente cliente, Quarto quarto, Date dataInicio, Date dataFim) {
        this.cliente = cliente;
        this.quarto = quarto;
        this.dataInicio = dataInicio;
        this.dataFim = dataFim;
    }

    public Cliente getCliente() {
        return cliente;
    }

    public Quarto getQuarto() {
        return quarto;
    }

    public Date getDataInicio() {
        return dataInicio;
    }

    public Date getDataFim() {
        return dataFim;
    }
}

class Hotel {
    private List<Quarto> quartos;
    private List<Reserva> reservas;

    public Hotel() {
        quartos = new ArrayList<>();
        reservas = new ArrayList<>();
    }

    public void adicionarQuarto(Quarto quarto) {
        quartos.add(quarto);
    }

    public void fazerReserva(Cliente cliente, int numeroQuarto, Date dataInicio, Date dataFim) {
        for (Quarto quarto : quartos) {
            if (quarto.getNumero() == numeroQuarto && quarto.isDisponivel()) {
                Reserva reserva = new Reserva(cliente, quarto, dataInicio, dataFim);
                reservas.add(reserva);
                quarto.setDisponivel(false);
                System.out.println("Reserva realizada com sucesso para o cliente " + cliente.getNome());
                return;
            }
        }
        System.out.println("Quarto não disponível para reserva.");
    }

    public void listarReservas() {
        for (Reserva reserva : reservas) {
            System.out.println("Cliente: " + reserva.getCliente().getNome() + ", Quarto: " + reserva.getQuarto().getNumero() +
                    ", Data Início: " + reserva.getDataInicio() + ", Data Fim: " + reserva.getDataFim());
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Hotel hotel = new Hotel();
        hotel.adicionarQuarto(new Quarto(101));
        hotel.adicionarQuarto(new Quarto(102));
        hotel.adicionarQuarto(new Quarto(103));

        Cliente cliente1 = new Cliente("João Silva", "12345678901");
        Cliente cliente2 = new Cliente("Maria Oliveira", "98765432101");

        hotel.fazerReserva(cliente1, 101, new Date(), new Date(System.currentTimeMillis() + 86400000L)); // 1 dia de reserva
        hotel.fazerReserva(cliente2, 101, new Date(), new Date(System.currentTimeMillis() + 86400000L)); // Tentativa de reserva no mesmo quarto

        hotel.listarReservas();
    }
}
```

### 2. Simulação de Tráfego

#### Código

```java
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

class Semaforo {
    private String estado; // "verde", "amarelo", "vermelho"
    private Lock lock = new ReentrantLock();

    public Semaforo(String estadoInicial) {
        this.estado = estadoInicial;
    }

    public String getEstado() {
        return estado;
    }

    public void setEstado(String estado) {
        this.estado = estado;
    }

    public void mudarEstado() {
        lock.lock();
        try {
            switch (estado) {
                case "verde":
                    estado = "amarelo";
                    break;
                case "amarelo":
                    estado = "vermelho";
                    break;
                case "vermelho":
                    estado = "verde";
                    break;
            }
        } finally {
            lock.unlock();
        }
    }
}

class Carro extends Thread {
    private String id;
    private List<Semaforo> percurso;

    public Carro(String id, List<Semaforo> percurso) {
        this.id = id;
        this.percurso = percurso;
    }

    @Override
    public void run() {
        for (Semaforo semaforo : percurso) {
            while (semaforo.getEstado().equals("vermelho")) {
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println("Carro " + id + " passou pelo semáforo " + semaforo.getEstado());
            try {
                Thread.sleep(500); // Simulando tempo de deslocamento até o próximo semáforo
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("Carro " + id + " chegou ao destino.");
    }
}

public class Main {
    public static void main(String[] args) {
        Semaforo semaforo1 = new Semaforo("verde");
        Semaforo semaforo2 = new Semaforo("vermelho");
        Semaforo semaforo3 = new Semaforo("verde");

        List<Semaforo> percurso1 = new ArrayList<>();
        percurso1.add(semaforo1);
        percurso1.add(semaforo2);
        percurso1.add(semaforo3);

        Carro carro1 = new Carro("1", percurso1);
        Carro carro2 = new Carro("2", percurso1);

        carro1.start();
        carro2.start();

        // Mudança dos estados dos semáforos em intervalos regulares
        new Thread(() -> {
            while (true) {
                try {
                    Thread.sleep(1000); // Mudança a cada 1 segundo
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                semaforo1.mudarEstado();
                semaforo2.mudarEstado();
                semaforo3.mudarEstado();
                System.out.println("Estados dos semáforos atualizados.");
            }
        }).start();
    }
}
```

### 3. Jogo de Xadrez

#### Código

```java
abstract class Peca {
    protected int x, y;

    public Peca(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public abstract boolean mover(int novoX, int novoY);
}

class Rei extends Peca {
    public Rei(int x, int y) {
        super(x, y);
    }

    @Override
    public boolean mover(int novoX, int novoY) {
        if (Math.abs(novoX - x) <= 1 && Math.abs(novoY - y) <= 1) {
            x = novoX;
            y = novoY;
            return true;
        }
        return false;
    }
}

class Rainha extends Peca {
    public Rainha(int x, int y) {
        super(x, y);
    }

    @Override
    public boolean mover(int novoX, int novoY) {
        if (novoX == x || novoY == y || Math.abs(novoX - x) == Math.abs(novoY - y)) {
            x = novoX;
            y = novoY;
            return true;
        }
        return false;
    }
}

// Definir outras peças semelhantes (Bispo, Cavalo, Torre, Peão) aqui

class Tabuleiro {
    private Peca[][] tabuleiro;

    public Tabuleiro() {
        tabuleiro = new Peca[8][8];
    }

    public void adicionarPeca(Peca peca, int x, int y) {
        tabuleiro[x][y] = peca;
    }

    public boolean moverPeca(int x, int y, int novoX, int novoY) {
        Peca peca = tabuleiro[x][y];
        if (peca != null && peca.mover(novoX, novoY)) {
            tabuleiro[novoX][novoY] = peca;
            tabuleiro[x][y] = null;
            return true;
        }
        return false;
    }
}

public class Main {
    public static void main(String[] args) {
        Tabuleiro tabuleiro = new Tabuleiro();
        Peca rei = new Rei(0, 0);
        Peca rainha = new Rainha(1, 1);

        tabuleiro.adicionarPeca(rei, 0, 0);
        tabuleiro.adicionarPeca(rainha, 1, 1);

        tabuleiro.moverPeca(0, 0, 1, 1); // Movimento inválido para o Rei
        tabuleiro.moverPeca(1, 1, 3, 3); // Movimento válido para a Rainha
    }
}
```

### 4. Sistema de Arquivos

#### Código

```java
import java.util.ArrayList;
import java.util.List;

abstract class Item {
    protected String nome;

    public Item(String nome) {
        this.nome = nome;
    }

    public abstract int getTamanho();
}

class Arquivo extends Item {
    private int tamanho;

    public Arquivo(String nome, int tamanho) {
        super(nome);
        this.tamanho = tamanho;
    }

    @Override
    public int getTamanho() {
        return tamanho;
    }
}

class Diretorio extends Item {
    private List<Item> itens;

    public Diretorio(String nome) {
        super(nome);
        this.itens = new ArrayList<>();
    }

    public void adicionarItem(Item item) {
        itens.add(item);
    }

    @Override
    public int getTamanho() {
        int tamanhoTotal = 0;
        for (Item item : itens) {
            tamanhoTotal += item.getTamanho();
        }
        return tamanhoTotal;
    }
}

class SistemaDeArquivos {
    private Diretorio raiz;

    public SistemaDeArquivos() {
        raiz = new Diretorio("raiz");
    }

    public void adicionarItem(Item item) {
        raiz.adicionarItem(item);
    }

    public int getTamanhoTotal() {
        return raiz.getTamanho();
    }
}

public class Main {
    public static void main(String[] args) {
        SistemaDeArquivos sistema = new SistemaDeArquivos();

        Arquivo arquivo1 = new Arquivo("arquivo1.txt", 100);
        Arquivo arquivo2 = new Arquivo("arquivo2.txt", 200);

        Diretorio dir1 = new Diretorio("diretorio1");
        dir1.adicionarItem(arquivo1);
        dir1.adicionarItem(arquivo2);

        sistema.adicionarItem(dir1);
        sistema.adicionarItem(new Arquivo("arquivo3.txt", 300));

        System.out.println("Tamanho total do sistema de arquivos: " + sistema.getTamanhoTotal() + " bytes");
    }
}
```

---

# Discussão

Estas soluções cobrem os exercícios difíceis propostos e demonstram como implementar classes, herança, interfaces, tratamento de exceções e conceitos de multithreading em Java.

## 1) Sistema Reserva de Hotel
No sistema de reservas de hotel desenvolvido, diversos conceitos fundamentais de Programação Orientada a Objetos (POO) são utilizados. Abaixo estão os principais conceitos aplicados:

1. **Classes e Objetos**:
    - **Classes**: `Cliente`, `Quarto`, `Reserva`, `Hotel` representam diferentes entidades do sistema.
    - **Objetos**: Instâncias dessas classes, como `cliente1`, `cliente2`, `quarto1`, `quarto2`, etc., são criados para representar entidades específicas.

2. **Encapsulamento**:
    - **Atributos Privados**: Os atributos das classes (`nome`, `cpf`, `numero`, `disponivel`, etc.) são privados e só podem ser acessados ou modificados através de métodos públicos (getters e setters).
    - **Métodos Públicos**: Métodos como `getNome()`, `setDisponivel()`, `fazerReserva()`, `listarReservas()` permitem a interação controlada com os dados encapsulados nas classes.

3. **Composição**:
    - A classe `Hotel` contém listas de `Quarto` e `Reserva`, demonstrando a composição onde uma classe é composta de objetos de outras classes.

4. **Polimorfismo**:
    - Não utilizado explicitamente no exemplo dado, mas poderia ser aplicado, por exemplo, se `Quarto` fosse uma superclasse e houvesse subclasses como `QuartoSimples` e `QuartoLuxo`, e o método `fazerReserva()` lidasse polimorficamente com essas subclasses.

5. **Associações**:
    - **Associação**: Relacionamentos entre as classes `Reserva` e `Cliente`, `Reserva` e `Quarto`.
    - **Dependência**: A classe `Reserva` depende das classes `Cliente` e `Quarto` para a sua criação.

6. **Responsabilidade Única**:
    - Cada classe tem uma responsabilidade clara e única: 
        - `Cliente` gerencia informações do cliente.
        - `Quarto` gerencia informações do quarto.
        - `Reserva` gerencia informações da reserva.
        - `Hotel` gerencia a operação global do hotel, incluindo a gestão de quartos e reservas.

7. **Controle de Acesso**:
    - Métodos e atributos são definidos com modificadores de acesso (`private`, `public`) para controlar onde e como os dados e comportamentos podem ser acessados.

8. **Coesão**:
    - As classes são altamente coesas, cada uma tem um conjunto específico de responsabilidades que estão intimamente relacionadas.

### Exemplos no Código

- **Classes e Objetos**:
    ```java
    class Cliente { ... }
    class Quarto { ... }
    class Reserva { ... }
    class Hotel { ... }

    Cliente cliente1 = new Cliente("João Silva", "12345678901");
    Quarto quarto1 = new Quarto(101);
    ```

- **Encapsulamento**:
    ```java
    public class Cliente {
        private String nome;
        private String cpf;

        public Cliente(String nome, String cpf) {
            this.nome = nome;
            this.cpf = cpf;
        }

        public String getNome() {
            return nome;
        }

        public String getCpf() {
            return cpf;
        }
    }
    ```

- **Composição**:
    ```java
    class Hotel {
        private List<Quarto> quartos;
        private List<Reserva> reservas;

        public Hotel() {
            quartos = new ArrayList<>();
            reservas = new ArrayList<>();
        }

        public void adicionarQuarto(Quarto quarto) {
            quartos.add(quarto);
        }

        public void fazerReserva(Cliente cliente, int numeroQuarto, Date dataInicio, Date dataFim) {
            for (Quarto quarto : quartos) {
                if (quarto.getNumero() == numeroQuarto && quarto.isDisponivel()) {
                    Reserva reserva = new Reserva(cliente, quarto, dataInicio, dataFim);
                    reservas.add(reserva);
                    quarto.setDisponivel(false);
                    System.out.println("Reserva realizada com sucesso para o cliente " + cliente.getNome());
                    return;
                }
            }
            System.out.println("Quarto não disponível para reserva.");
        }
    }
    ```
---

## 2) Simulação de Tráfego
No sistema de simulação de tráfego desenvolvido, diversos conceitos fundamentais de Programação Orientada a Objetos (POO) são utilizados. Abaixo estão os principais conceitos aplicados:

1. **Classes e Objetos**:
    - **Classes**: `Semaforo`, `Carro` representam diferentes entidades do sistema.
    - **Objetos**: Instâncias dessas classes, como `semaforo1`, `semaforo2`, `carro1`, `carro2`, etc., são criados para representar entidades específicas.

2. **Encapsulamento**:
    - **Atributos Privados**: Os atributos das classes (`estado`, `id`, `percurso`) são privados e só podem ser acessados ou modificados através de métodos públicos (getters e setters).
    - **Métodos Públicos**: Métodos como `getEstado()`, `setEstado()`, `mudarEstado()`, `run()` permitem a interação controlada com os dados encapsulados nas classes.

3. **Composição**:
    - A classe `Carro` contém uma lista de `Semaforo`, demonstrando a composição onde uma classe é composta de objetos de outras classes.

4. **Multithreading**:
    - A classe `Carro` estende `Thread` e sobrescreve o método `run()`, permitindo a execução simultânea de múltiplas instâncias de `Carro`.
    - Uso de um thread separado para mudar os estados dos semáforos em intervalos regulares.

5. **Associações**:
    - **Associação**: Relacionamentos entre as classes `Carro` e `Semaforo`.
    - **Dependência**: A classe `Carro` depende da classe `Semaforo` para determinar o estado do semáforo ao longo do percurso.

6. **Controle de Acesso**:
    - Métodos e atributos são definidos com modificadores de acesso (`private`, `public`) para controlar onde e como os dados e comportamentos podem ser acessados.

7. **Responsabilidade Única**:
    - Cada classe tem uma responsabilidade clara e única:
        - `Semaforo` gerencia o estado de um semáforo.
        - `Carro` gerencia o comportamento de um carro ao percorrer uma lista de semáforos.

8. **Sincronização**:
    - Uso de `Lock` para garantir a mudança segura dos estados dos semáforos em um ambiente multithread.

### Exemplos no Código

- **Classes e Objetos**:
    ```java
    class Semaforo { ... }
    class Carro extends Thread { ... }

    Semaforo semaforo1 = new Semaforo("verde");
    Carro carro1 = new Carro("1", percurso1);
    ```

- **Encapsulamento**:
    ```java
    public class Semaforo {
        private String estado; // "verde", "amarelo", "vermelho"
        private Lock lock = new ReentrantLock();

        public Semaforo(String estadoInicial) {
            this.estado = estadoInicial;
        }

        public String getEstado() {
            return estado;
        }

        public void setEstado(String estado) {
            this.estado = estado;
        }

        public void mudarEstado() {
            lock.lock();
            try {
                switch (estado) {
                    case "verde":
                        estado = "amarelo";
                        break;
                    case "amarelo":
                        estado = "vermelho";
                        break;
                    case "vermelho":
                        estado = "verde";
                        break;
                }
            } finally {
                lock.unlock();
            }
        }
    }
    ```

- **Composição**:
    ```java
    public class Carro extends Thread {
        private String id;
        private List<Semaforo> percurso;

        public Carro(String id, List<Semaforo> percurso) {
            this.id = id;
            this.percurso = percurso;
        }

        @Override
        public void run() {
            for (Semaforo semaforo : percurso) {
                while (semaforo.getEstado().equals("vermelho")) {
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                System.out.println("Carro " + id + " passou pelo semáforo " + semaforo.getEstado());
                try {
                    Thread.sleep(500); // Simulando tempo de deslocamento até o próximo semáforo
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println("Carro " + id + " chegou ao destino.");
        }
    }
    ```

- **Multithreading**:
    ```java
    public class Main {
        public static void main(String[] args) {
            Semaforo semaforo1 = new Semaforo("verde");
            Semaforo semaforo2 = new Semaforo("vermelho");
            Semaforo semaforo3 = new Semaforo("verde");

            List<Semaforo> percurso1 = new ArrayList<>();
            percurso1.add(semaforo1);
            percurso1.add(semaforo2);
            percurso1.add(semaforo3);

            Carro carro1 = new Carro("1", percurso1);
            Carro carro2 = new Carro("2", percurso1);

            carro1.start();
            carro2.start();

            // Mudança dos estados dos semáforos em intervalos regulares
            new Thread(() -> {
                while (true) {
                    try {
                        Thread.sleep(1000); // Mudança a cada 1 segundo
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    semaforo1.mudarEstado();
                    semaforo2.mudarEstado();
                    semaforo3.mudarEstado();
                    System.out.println("Estados dos semáforos atualizados.");
                }
            }).start();
        }
    }
    ```
---

## 3) Jogo de Xadrex

No jogo de xadrez desenvolvido, diversos conceitos fundamentais de Programação Orientada a Objetos (POO) são utilizados. Abaixo estão os principais conceitos aplicados:

1. **Classes e Objetos**:
    - **Classes**: `Peca`, `Rei`, `Rainha`, `Tabuleiro` representam diferentes entidades do sistema.
    - **Objetos**: Instâncias dessas classes, como `rei`, `rainha`, `tabuleiro`, etc., são criados para representar entidades específicas.

2. **Encapsulamento**:
    - **Atributos Privados**: Os atributos das classes (`x`, `y`) são privados e só podem ser acessados ou modificados através de métodos públicos.
    - **Métodos Públicos**: Métodos como `mover()` e `adicionarPeca()` permitem a interação controlada com os dados encapsulados nas classes.

3. **Herança**:
    - **Classe Base e Subclasses**: A classe `Peca` é a classe base, e as classes `Rei`, `Rainha`, etc., são subclasses que herdam da classe `Peca`.

4. **Polimorfismo**:
    - **Sobrescrita de Métodos**: As subclasses (`Rei`, `Rainha`) sobrescrevem o método `mover()` da classe base `Peca` para fornecer implementações específicas de movimentação para cada tipo de peça.

5. **Associações**:
    - **Associação**: Relacionamentos entre as classes `Peca` e `Tabuleiro`.

6. **Abstração**:
    - **Classe Abstrata**: A classe `Peca` é abstrata e define um método abstrato `mover()` que deve ser implementado pelas subclasses.

7. **Responsabilidade Única**:
    - Cada classe tem uma responsabilidade clara e única:
        - `Peca` define o comportamento geral de uma peça.
        - `Rei` e `Rainha` definem comportamentos específicos de movimentação.
        - `Tabuleiro` gerencia a posição das peças e suas movimentações.

8. **Controle de Acesso**:
    - Métodos e atributos são definidos com modificadores de acesso (`private`, `protected`, `public`) para controlar onde e como os dados e comportamentos podem ser acessados.

### Exemplos no Código

- **Classes e Objetos**:
    ```java
    abstract class Peca { ... }
    class Rei extends Peca { ... }
    class Rainha extends Peca { ... }
    class Tabuleiro { ... }

    Peca rei = new Rei(0, 0);
    Peca rainha = new Rainha(1, 1);
    ```

- **Encapsulamento**:
    ```java
    public abstract class Peca {
        protected int x, y;

        public Peca(int x, int y) {
            this.x = x;
            this.y = y;
        }

        public abstract boolean mover(int novoX, int novoY);
    }
    ```

- **Herança**:
    ```java
    class Rei extends Peca {
        public Rei(int x, int y) {
            super(x, y);
        }

        @Override
        public boolean mover(int novoX, int novoY) {
            if (Math.abs(novoX - x) <= 1 && Math.abs(novoY - y) <= 1) {
                x = novoX;
                y = novoY;
                return true;
            }
            return false;
        }
    }
    ```

- **Polimorfismo**:
    ```java
    public class Main {
        public static void main(String[] args) {
            Tabuleiro tabuleiro = new Tabuleiro();
            Peca rei = new Rei(0, 0);
            Peca rainha = new Rainha(1, 1);

            tabuleiro.adicionarPeca(rei, 0, 0);
            tabuleiro.adicionarPeca(rainha, 1, 1);

            tabuleiro.moverPeca(0, 0, 1, 1); // Movimento inválido para o Rei
            tabuleiro.moverPeca(1, 1, 3, 3); // Movimento válido para a Rainha
        }
    }
    ```

- **Abstração**:
    ```java
    abstract class Peca {
        protected int x, y;

        public Peca(int x, int y) {
            this.x = x;
            this.y = y;
        }

        public abstract boolean mover(int novoX, int novoY);
    }
    ```

---
## 4) Sistema de Arquivos

No sistema de arquivos desenvolvido, diversos conceitos fundamentais de Programação Orientada a Objetos (POO) são utilizados. Abaixo estão os principais conceitos aplicados:

1. **Classes e Objetos**:
    - **Classes**: `Item`, `Arquivo`, `Diretorio`, `SistemaDeArquivos` representam diferentes entidades do sistema.
    - **Objetos**: Instâncias dessas classes, como `arquivo1`, `arquivo2`, `diretorio1`, etc., são criados para representar entidades específicas.

2. **Encapsulamento**:
    - **Atributos Privados**: Os atributos das classes (`nome`, `tamanho`, `itens`) são privados e só podem ser acessados ou modificados através de métodos públicos (getters e setters).
    - **Métodos Públicos**: Métodos como `getTamanho()`, `adicionarItem()` permitem a interação controlada com os dados encapsulados nas classes.

3. **Herança**:
    - **Classe Base e Subclasses**: A classe `Item` é a classe base, e as classes `Arquivo`, `Diretorio` são subclasses que herdam da classe `Item`.

4. **Polimorfismo**:
    - **Sobrescrita de Métodos**: As subclasses (`Arquivo`, `Diretorio`) sobrescrevem o método `getTamanho()` da classe base `Item` para fornecer implementações específicas.

5. **Composição**:
    - A classe `Diretorio` contém uma lista de `Item`, demonstrando a composição onde uma classe é composta de objetos de outras classes.

6. **Associações**:
    - **Associação**: Relacionamentos entre as classes `Item`, `Arquivo`, `Diretorio`, e `SistemaDeArquivos`.

7. **Abstração**:
    - **Classe Abstrata**: A classe `Item` é abstrata e define um método abstrato `getTamanho()` que deve ser implementado pelas subclasses.

8. **Responsabilidade Única**:
    - Cada classe tem uma responsabilidade clara e única:
        - `Item` define o comportamento geral de um item do sistema de arquivos.
        - `Arquivo` e `Diretorio` definem comportamentos específicos.
        - `SistemaDeArquivos` gerencia a estrutura de arquivos e diretórios.

9. **Controle de Acesso**:
    - Métodos e atributos são definidos com modificadores de acesso (`private`, `protected`, `public`) para controlar onde e como os dados e comportamentos podem ser acessados.

### Exemplos no Código

- **Classes e Objetos**:
    ```java
    abstract class Item { ... }
    class Arquivo extends Item { ... }
    class Diretorio extends Item { ... }
    class SistemaDeArquivos { ... }

    Item arquivo1 = new Arquivo("arquivo1.txt", 100);
    Item diretorio1 = new Diretorio("diretorio1");
    ```

- **Encapsulamento**:
    ```java
    public abstract class Item {
        protected String nome;

        public Item(String nome) {
            this.nome = nome;
        }

        public abstract int getTamanho();
    }
    ```

- **Herança**:
    ```java
    class Arquivo extends Item {
        private int tamanho;

        public Arquivo(String nome, int tamanho) {
            super(nome);
            this.tamanho = tamanho;
        }

        @Override
        public int getTamanho() {
            return tamanho;
        }
    }
    ```

- **Polimorfismo**:
    ```java
    public class Main {
        public static void main(String[] args) {
            SistemaDeArquivos sistema = new SistemaDeArquivos();

            Arquivo arquivo1 = new Arquivo("arquivo1.txt", 100);
            Arquivo arquivo2 = new Arquivo("arquivo2.txt", 200);

            Diretorio dir1 = new Diretorio("diretorio1");
            dir1.adicionarItem(arquivo1);
            dir1.adicionarItem(arquivo2);

            sistema.adicionarItem(dir1);
            sistema.adicionarItem(new Arquivo("arquivo3.txt", 300));

            System.out.println("Tamanho total do sistema de arquivos: " + sistema.getTamanhoTotal() + " bytes");
        }
    }
    ```

- **Abstração**:
    ```java
    abstract class Item {
        protected String nome;

        public Item(String nome) {
            this.nome = nome;
        }

        public abstract int getTamanho();
    }
    ```

