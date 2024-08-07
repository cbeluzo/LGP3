Aula - Concurrency & Threads

**Intro**
Threads são unidades básicas de execução que permitem a execução de múltiplas tarefas simultaneamente dentro de um programa.

Em sistemas operacionais modernos, threads são usadas para aproveitar melhor os recursos do processador, especialmente em sistemas com múltiplos núcleos.

Cada thread dentro de um processo compartilha o mesmo espaço de memória, o que facilita a comunicação entre threads, mas também introduz desafios como a sincronização para evitar condições de corrida e outros problemas de concorrência.

A capacidade de executar várias threads em paralelo permite que programas realizem operações complexas de forma mais eficiente, melhorando o desempenho e a capacidade de resposta de aplicações interativas.

**Java**

Na linguagem de programação Java, a classe `Thread` e a interface `Runnable` são usadas para criar e gerenciar threads. 

A criação de uma thread pode ser feita estendendo a classe `Thread` ou implementando a interface `Runnable`.

A interface `Runnable` é geralmente preferida porque permite que a classe que implementa a thread possa herdar de outra classe, uma vez que Java não suporta herança múltipla. 

Após a criação de uma thread, seu ciclo de vida inclui estados como novo, executável, em execução, bloqueado e morto. 

O gerenciamento adequado do ciclo de vida das threads é crucial para evitar problemas como deadlocks e para garantir a eficiência da execução.

O `ExecutorService` no Java fornece uma maneira avançada de gerenciar threads, oferecendo um conjunto de métodos que facilitam a execução assíncrona de tarefas. 

Ele abstrai muitos dos detalhes de baixo nível do gerenciamento de threads, como a criação e a destruição de threads, e permite a reutilização eficiente de threads existentes por meio de pools de threads. 

Isso ajuda a evitar o overhead associado à criação constante de novas threads, melhorando o desempenho geral da aplicação. 

O `ExecutorService` também fornece mecanismos para lidar com a conclusão de tarefas, permitindo que os desenvolvedores aguardem a conclusão de todas as tarefas ou cancelem tarefas se necessário.

A programação multithread traz vários benefícios, como o melhor uso dos recursos do processador e a capacidade de realizar várias operações simultaneamente, o que é essencial em aplicações de alto desempenho e responsivas. 

No entanto, também introduz complexidade adicional no gerenciamento da concorrência e na sincronização dos acessos aos recursos compartilhados. 

Ferramentas e bibliotecas como o `ExecutorService`, junto com boas práticas de programação, como a utilização de blocos sincronizados e objetos de sincronização, são fundamentais para escrever código multithread seguro e eficiente.

---

**Conceitos**:
- **Threads**: A unidade básica de execução. Em Java, uma aplicação pode ter várias threads para realizar tarefas simultaneamente.
- **Sincronização**: Garantir que múltiplas threads possam acessar recursos compartilhados sem interferir umas nas outras.
- **Pacote `java.util.concurrent`**: Fornece classes utilitárias para trabalhar com concorrência de maneira eficiente, como `ExecutorService`, `CountDownLatch`, `Semaphore`, e `ConcurrentHashMap`.

#### Explicação Detalhada

1. **Threads**:
   - **Definição**: Uma thread é a menor unidade de processamento que pode ser executada de forma independente. Em Java, cada thread tem seu próprio caminho de execução.
   - **Criação de Threads**:
     - **Extender a classe `Thread`**: Uma maneira de criar uma thread é estendendo a classe `Thread` e sobrescrevendo o método `run()`.
     - **Implementar a interface `Runnable`**: Outra maneira é implementando a interface `Runnable` e passando uma instância de `Runnable` para um objeto `Thread`.
   - **Exemplo de Criação de Threads**:
     ```java
     // Estendendo a classe Thread
     class MyThread extends Thread {
         public void run() {
             System.out.println("Thread is running");
         }
     }

     // Implementando a interface Runnable
     class MyRunnable implements Runnable {
         public void run() {
             System.out.println("Runnable is running");
         }
     }

     public class ThreadExample {
         public static void main(String[] args) {
             MyThread t1 = new MyThread();
             t1.start();

             Thread t2 = new Thread(new MyRunnable());
             t2.start();
         }
     }
     ```

2. **Sincronização**:
   - **Definição**: Sincronização é o mecanismo que garante que múltiplas threads não interfiram umas nas outras ao acessar recursos compartilhados.
   - **Synchronized Blocks e Methods**: Usar a palavra-chave `synchronized` para proteger blocos de código ou métodos inteiros que devem ser acessados por uma thread por vez.
   - **Exemplo de Sincronização**:
     ```java
     class Counter {
         private int count = 0;

         public synchronized void increment() {
             count++;
         }

         public int getCount() {
             return count;
         }
     }

     public class SyncExample {
         public static void main(String[] args) throws InterruptedException {
             Counter counter = new Counter();

             Runnable task = () -> {
                 for (int i = 0; i < 1000; i++) {
                     counter.increment();
                 }
             };

             Thread t1 = new Thread(task);
             Thread t2 = new Thread(task);

             t1.start();
             t2.start();

             t1.join();
             t2.join();

             System.out.println("Count: " + counter.getCount());
         }
     }
     ```

3. **Pacote `java.util.concurrent`**:
   - **ExecutorService**: Uma interface que representa um pool de threads. Permite executar tarefas de forma assíncrona.
   - **CountDownLatch**: Um sincronizador que permite que uma ou mais threads esperem até que um conjunto de operações em outras threads seja concluído.
   - **Semaphore**: Um contador que controla o acesso a um recurso compartilhado.
   - **ConcurrentHashMap**: Uma implementação de `HashMap` segura para o uso concorrente.
   - **Exemplo de `ExecutorService`**:
     ```java
     import java.util.concurrent.ExecutorService;
     import java.util.concurrent.Executors;


	 public class ExecutorServiceExample {
    	public static void main(String[] args) throws InterruptedException {
    	/*
    	 * Estamos criando um pool com exatamente 3 threads. 
    		Isso significa que o pool pode executar até 3 tarefas simultaneamente.
    	 	Se mais de 3 tarefas forem submetidas ao executor 
    		enquanto todas as threads do pool estiverem ocupadas, 
    	 	as tarefas adicionais serão colocadas em uma fila e 
    	 	esperadas até que uma thread esteja disponível para executá-las.
    	 */
    	
        	ExecutorService executor = Executors.newFixedThreadPool(10);

	        for (int i = 0; i < 100; i++) {
    	        executor.execute(new WorkerThread("" + i));
        	}
        
	        executor.shutdown();
     	   
        	while (!executor.isTerminated()) {
        		//System.out.println("still running...");
            	//Thread.sleep(1000);
        	}

	        System.out.println("Finished all threads");
    	}
	 }
	
		class WorkerThread implements Runnable {
    		private String command;
			
	    	public WorkerThread(String s) {
        	this.command = s;
	    }
		
    	@Override
    	public void run() {
    		// Pega o nome da thread no sistemas pool-X-thread-A
        	System.out.println(Thread.currentThread().getName() + " Start. Command = " + command);
        	processCommand();
        	System.out.println(Thread.currentThread().getName() + " End. Command = " + command);
    		}
		
   	 	private void processCommand() {
        	try {
            	Thread.sleep(3000);
	        } catch (InterruptedException e) {
    	        e.printStackTrace();
        	}
	    }
			
	    @Override
    	public String toString() {
        	return this.command;
    		}
		}
     ```

---

### Exemplo Prático 2: Processamento de Dados em Paralelo

**ExecutorService** é uma interface do framework de concorrência do Java que facilita a criação e gerenciamento de um pool de threads para executar tarefas de forma assíncrona. Ele simplifica o gerenciamento de threads, permitindo que você se concentre mais na lógica da aplicação do que em lidar com detalhes de gerenciamento de threads.

Suponha que temos um conjunto de dados que queremos processar em paralelo para melhorar o desempenho. Vamos criar um pool de threads para processar esses dados.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class ExemploExecutorService {
    public static void main(String[] args) {
        // Cria um pool de threads com 5 threads
        ExecutorService executor = Executors.newFixedThreadPool(5);

        // Simula um conjunto de dados para processamento
        int[] dados = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

        // Cria e envia tarefas para o executor
        for (int dado : dados) {
            Runnable tarefa = new TarefaProcessamento(dado);
            executor.submit(tarefa);
        }

        // Inicia um shutdown ordenado do executor
        executor.shutdown();

        try {
            // Aguarda a conclusão de todas as tarefas
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                executor.shutdownNow(); // Força o shutdown se as tarefas não terminarem no tempo especificado
            }
        } catch (InterruptedException e) {
            executor.shutdownNow(); // Força o shutdown se a thread principal for interrompida
            Thread.currentThread().interrupt();
        }

        System.out.println("Processamento completo.");
    }
}

class TarefaProcessamento implements Runnable {
    private final int dado;

    public TarefaProcessamento(int dado) {
        this.dado = dado;
    }

    @Override
    public void run() {
        System.out.println("Processando dado: " + dado + " - Thread: " + Thread.currentThread().getName());
        try {
            // Simula algum processamento
            Thread.sleep((long) (Math.random() * 1000));
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        System.out.println("Dado processado: " + dado + " - Thread: " + Thread.currentThread().getName());
    }
}
```

### Explicação

1. **Criação do ExecutorService**:
    ```java
    ExecutorService executor = Executors.newFixedThreadPool(5);
    ```
    Criamos um pool de threads com 5 threads usando o método `Executors.newFixedThreadPool(5)`. Isso significa que até 5 threads podem ser executadas simultaneamente.

2. **Envio de Tarefas para o Executor**:
    ```java
    for (int dado : dados) {
        Runnable tarefa = new TarefaProcessamento(dado);
        executor.submit(tarefa);
    }
    ```
    Para cada dado no array `dados`, criamos uma nova instância da tarefa `TarefaProcessamento` e a submetemos ao executor para execução.

3. **Shutdown do ExecutorService**:
    ```java
    executor.shutdown();
    ```
    Chamamos `shutdown()` para iniciar um desligamento ordenado. Isso significa que o executor não aceitará novas tarefas, mas concluirá as tarefas já submetidas.

4. **Aguardando Conclusão das Tarefas**:
    ```java
    if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
        executor.shutdownNow();
    }
    ```
    Usamos `awaitTermination` para aguardar a conclusão de todas as tarefas por até 60 segundos. Se as tarefas não forem concluídas nesse tempo, chamamos `shutdownNow()` para forçar o encerramento.

5. **Classe TarefaProcessamento**:
    ```java
    class TarefaProcessamento implements Runnable {
        private final int dado;

        public TarefaProcessamento(int dado) {
            this.dado = dado;
        }

        @Override
        public void run() {
            System.out.println("Processando dado: " + dado + " - Thread: " + Thread.currentThread().getName());
            try {
                Thread.sleep((long) (Math.random() * 1000));
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            System.out.println("Dado processado: " + dado + " - Thread: " + Thread.currentThread().getName());
        }
    }
    ```
    A classe `TarefaProcessamento` implementa a interface `Runnable`. Cada instância dessa classe processa um único dado e simula algum processamento com um `Thread.sleep`.

---


**Exercícios**:
### Exercício Prático: Sistema de Reservas de Voos com Threads

#### Descrição do Exercício

Você foi contratado para desenvolver um sistema de reservas de voos para uma companhia aérea fictícia. O sistema deve ser capaz de processar múltiplas reservas de maneira concorrente, garantindo que as reservas sejam feitas de forma eficiente e segura. Este exercício prático tem como objetivo exercitar o uso de threads em Java para gerenciar múltiplas tarefas de reserva simultaneamente.

#### Objetivos

1. **Implementar o uso de threads para gerenciar reservas de voos.**
2. **Utilizar ExecutorService para criar e gerenciar um pool de threads.**
3. **Garantir a integridade das reservas usando mecanismos de sincronização.**
4. **Simular um ambiente real onde múltiplos usuários tentam fazer reservas ao mesmo tempo.**

#### Requisitos

1. **Classe `Voo`**:
   - A classe `Voo` deve conter informações como número do voo, capacidade total e número de assentos reservados.
   - Deve ter métodos para verificar a disponibilidade de assentos e fazer uma reserva.

2. **Classe `Reserva`**:
   - A classe `Reserva` deve representar uma tarefa de reserva que implementa `Runnable`.
   - Deve tentar reservar um assento em um voo específico.

3. **Gerenciamento de Threads**:
   - Utilizar `ExecutorService` para criar um pool de threads que processará múltiplas reservas simultaneamente.
   - Garantir que as reservas sejam feitas de maneira segura, utilizando mecanismos de sincronização para evitar condições de corrida.

4. **Simulação de Reservas**:
   - Simular a tentativa de reserva de assentos por múltiplos usuários ao mesmo tempo, criando várias instâncias de `Reserva` e submetendo-as ao `ExecutorService`.

#### Explicação

1. **Classe `Voo`**:
   - A classe `Voo` gerencia as informações de um voo, incluindo a capacidade total e o número de assentos reservados.
   - O método `reservarAssento` é sincronizado para garantir que as reservas sejam feitas de forma segura, evitando condições de corrida.

2. **Classe `Reserva`**:
   - A classe `Reserva` representa uma tarefa de reserva. Implementa `Runnable` para ser executada em uma thread separada.
   - No método `run`, tenta reservar um assento no voo e imprime o resultado.

3. **Classe Principal (`SistemaReservas`)**:
   - Cria uma instância de `Voo` com um número de voo e capacidade total.
   - Utiliza `ExecutorService` para criar um pool de threads com 5 threads.
   - Submete 15 tarefas de reserva ao executor para simular múltiplas tentativas de reserva simultâneas.
   - Chama `shutdown()` para iniciar um encerramento ordenado do executor e `awaitTermination()` para aguardar a conclusão de todas as tarefas.
