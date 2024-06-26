## Linguagem de Programação 3
**Prof. Carlos Beluzo | beluzo@ifsp.edu.br**

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

---

# Aula 1: Introdução à Orientação a Objetos

## 1. Introdução ao curso

- Apresentação do professor
- Apresentação da turma
- Apresentação do curso: ementa, bibliografia, metodologia de ensino, avaliação

## 2. Apresentação do programa e dos objetivos

- **Objetivos gerais e específicos do curso**
  - Discutir como os objetivos serão alcançados
  - Ênfase na importância da participação ativa dos alunos
- **Discussão sobre as expectativas dos alunos**
  - Abertura para sugestões e feedback
  - Adaptação do programa às necessidades da turma

## 3. Definição de Orientação a Objetos

### O que é Orientação a Objetos?

A Orientação a Objetos (OO) é um paradigma de programação que se baseia no conceito de "objetos", que são instâncias de classes contendo dados (atributos) e procedimentos (métodos). Essa abordagem permite modelar sistemas complexos de forma mais intuitiva e modular, refletindo melhor a organização do mundo real.

### Definição formal e exemplos práticos

Formalmente, a OO organiza o software como uma coleção de objetos individuais que se comunicam entre si. Por exemplo, em um sistema de gerenciamento de biblioteca, cada livro pode ser representado como um objeto com atributos como título, autor e número de páginas, e métodos como empréstimo e devolução.

### Diferenças entre POO e programação procedural

A principal diferença entre a POO e a programação procedural está na abordagem para resolver problemas. Na programação procedural, o foco está nos procedimentos (funções). Na POO, o foco está na definição de objetos que encapsulam dados e comportamentos relacionados.

### Vantagens da Orientação a Objetos

- **Reutilização de código:** Objetos podem ser reutilizados em diferentes partes do sistema, economizando tempo e esforço.
- **Modularidade:** Sistemas OO podem ser divididos em módulos independentes, facilitando a manutenção e o desenvolvimento incremental.
- **Flexibilidade:** A OO permite que os sistemas sejam facilmente adaptáveis a novos requisitos e mudanças, através da modificação ou extensão de classes existentes.

### Exemplos de como a POO pode ser vantajosa em projetos reais

- **Sistemas de Informação:** Um sistema de gestão de vendas pode ter classes como Cliente, Produto e Venda.
- **Jogos:** Personagens, inimigos e itens podem ser modelados como objetos.
- **Aplicações Web:** Diferentes partes do sistema, como front-end, back-end e banco de dados, podem ser representadas como objetos.

### Comparação entre paradigmas de programação

- **POO:** Baseada em objetos que encapsulam dados e comportamentos.
- **Programação Funcional:** Baseada em funções puras e imutáveis.
- **Programação Lógica:** Baseada em regras lógicas e inferências.

#### Vantagens e desvantagens de cada paradigma

- **POO:** Vantagens incluem reutilização de código e modularidade; desvantagens incluem complexidade e overhead.
- **Programação Funcional:** Vantagens incluem imutabilidade e expressividade; desvantagens incluem curva de aprendizado e performance.
- **Programação Lógica:** Vantagens incluem facilidade de representação de problemas complexos; desvantagens incluem eficiência e dificuldade de depuração.

### Perguntas para discussão

1. Quais são os principais benefícios da Orientação a Objetos em comparação com outros paradigmas de programação?
2. Cite exemplos de problemas que podem ser facilmente solucionados utilizando a Orientação a Objetos.
3. Em sua opinião, quais são os principais desafios de aprender a programar utilizando o paradigma da Orientação a Objetos?

## 4. Conceitos básicos

### Classe: definição, características, exemplos

- **Definição formal de classe e seus elementos**
- **Características de uma classe:** nome, atributos, métodos
- **Exemplos de classes:** Pessoa, Carro, Animal

### Objeto: definição, características, exemplos

- **Definição formal de objeto e suas propriedades**
- **Características de um objeto:** estado, comportamento, identidade
- **Exemplos de objetos:** João (um objeto da classe Pessoa), Fiat Argo (um objeto da classe Carro), Gato (um objeto da classe Animal)

### Atributo: definição, tipos, exemplos

- **Definição formal de atributo e suas características**
- **Tipos de atributos:** primitivos (int, String) e compostos (objetos)
- **Exemplos de atributos:** nome (String), idade (int), raça (String)

### Método: definição, tipos, exemplos

- **Definição formal de método e suas características**
- **Tipos de métodos:** getters, setters, outros métodos específicos
- **Exemplos de métodos:** andar(), comer(), dormir()

### Perguntas para discussão

1. Qual a diferença entre classe e objeto?
2. Quais são os diferentes tipos de dados que podem ser utilizados como atributos em uma classe?
3. Como os métodos definem o comportamento de um objeto?

### Exemplos para Discussão

1. **Pergunta:** O que significa programação orientada a objetos e por que é importante?
   - **Resposta:** A programação orientada a objetos organiza o código em estruturas chamadas objetos, que representam entidades do mundo real. Isso promove a reutilização de código, modularidade e facilita a manutenção do software.

2. **Pergunta:** Quais são as principais vantagens da programação orientada a objetos em comparação com a programação procedural?
   - **Resposta:** Vantagens incluem encapsulamento, herança, polimorfismo e reutilização de código.

3. **Pergunta:** Você pode dar exemplos de aplicativos do mundo real que se beneficiariam da programação orientada a objetos?
   - **Resposta:** Exemplos podem incluir sistemas de gerenciamento de bancos de dados, sistemas de comércio eletrônico e jogos de computador.

4. **Pergunta:** Qual é a diferença entre uma classe e um objeto?
   - **Resposta:** Uma classe é uma estrutura que define os atributos e métodos comuns a um conjunto de objetos, enquanto um objeto é uma instância específica dessa classe.

5. **Pergunta:** Por que o conceito de encapsulamento é importante na programação orientada a objetos?
   - **Resposta:** O encapsulamento protege os dados dentro de um objeto, permitindo que apenas os métodos definidos na classe acessem e modifiquem esses dados, aumentando a segurança e a integridade do código.

6. **Pergunta:** Qual é a diferença entre um atributo e um método em uma classe?
   - **Resposta:** Um atributo é uma variável que armazena dados sobre o objeto, enquanto um método é uma função que define o comportamento do objeto.

## Atividade Prática: Reforçando Conceitos Básicos de Orientação a Objetos (20 minutos)

### Objetivo:

- Reforçar os conceitos básicos de Orientação a Objetos: classe, objeto, atributo e método.
- Estimular a criatividade e o pensamento computacional.
- Praticar a implementação de classes e objetos em linguagem de programação.

### Descrição da Atividade:

Os alunos serão divididos em grupos de 2 a 3 pessoas. Cada grupo deverá:

1. **Criar uma classe para representar um animal.**
   - Nome da classe: `Animal`
   - **Atributos:**
     - `nome` (String)
     - `idade` (int)
     - `raça` (String)
     - `som` (String)
   - **Métodos:**
     - `falar()`: Imprime o som do animal.
     - `comer()`: Imprime uma mensagem que o animal está comendo.
     - `dormir()`: Imprime uma mensagem que o animal está dormindo.

2. **Criar um objeto da classe `Animal`.**
   - Nome do objeto: `meuAnimal`
   - **Atributos:**
     - `nome`: "Rex"
     - `idade`: 5
     - `raça`: "Pastor Alemão"
     - `som`: "Au au!"

3. **Testar o objeto criado.**
   - Chamar os métodos `falar()`, `comer()` e `dormir()` do objeto `meuAnimal`.
