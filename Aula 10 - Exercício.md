### Exercício: Criação de uma Rede Social Utilizando Conceitos de Programação Orientada a Objetos

#### Objetivo:
Desenvolver uma aplicação de rede social simples, aplicando os principais conceitos de Programação Orientada a Objetos (POO), como abstração, herança, encapsulamento, polimorfismo, composição, associação e interfaces. Este exercício permitirá que você pratique a criação de classes, relacionamentos entre elas, e o uso de interfaces para definir comportamentos comuns.

#### Instruções:

Você deverá criar uma aplicação básica de rede social que permitirá a gestão de usuários, a criação e publicação de postagens, e a interação entre usuários através de funcionalidades como "curtir" e "comentar" postagens. A seguir, estão os passos que você deve seguir para criar essa aplicação, junto com explicações sobre como aplicar os conceitos de POO.

### 1. Definição das Classes Principais

Comece definindo as principais classes da sua aplicação. Pense nas entidades essenciais de uma rede social:

- **Usuário**: Esta será a classe base que representará os usuários da rede social. Um usuário pode ter atributos como nome de usuário, senha, e-mail, e outros detalhes pessoais. Este é um exemplo de abstração, onde você define uma entidade genérica que servirá de base para outras classes.

- **Postagem**: Essa classe representará as postagens que os usuários poderão criar. As postagens podem ter atributos como conteúdo, data de criação e contadores de curtidas e comentários. A classe `Postagem` é uma forma de abstração das funcionalidades básicas que qualquer tipo de conteúdo compartilhado na rede social poderia ter.

### 2. Aplicando Encapsulamento

Ao definir os atributos das suas classes, você deve proteger esses dados, garantindo que eles só possam ser acessados e modificados de forma controlada. Isso é feito utilizando o conceito de encapsulamento:

- Torne os atributos das classes `Usuario` e `Postagem` privados.
- Forneça métodos públicos (getters e setters) para acessar e modificar esses atributos conforme necessário. Por exemplo, o nome de usuário deve ser acessível através de um método `getNomeUsuario()`, mas a senha só deve poder ser modificada através de um método `setSenha()` que valide a segurança da nova senha.

### 3. Herança e Especialização

Em seguida, você deve criar classes derivadas que representem diferentes tipos de usuários na rede social. Isso é feito através do conceito de herança:

- **UsuárioPremium**: Uma classe que herda de `Usuario` e adiciona funcionalidades adicionais que só usuários premium têm acesso, como a capacidade de criar postagens em destaque.
  
- **UsuárioAdmin**: Outra classe que herda de `Usuario`, mas que tem permissões especiais, como a capacidade de deletar postagens ou banir usuários.

Aqui, você está especializando o comportamento dos usuários ao criar subclasses que herdam a estrutura básica de `Usuario` e adicionam ou modificam funcionalidades específicas.

### 4. Definição de Interfaces

As interfaces permitem que você defina contratos de comportamento que podem ser implementados por diferentes classes. Na sua rede social, você pode definir uma interface para comportamentos comuns a várias classes:

- **Curtivel**: Crie uma interface chamada `Curtivel` que define métodos como `curtir()` e `getCurtidas()`. Qualquer classe que implemente essa interface (como `Postagem` ou até mesmo um `Comentario`) deve fornecer sua própria implementação desses métodos.

Ao utilizar interfaces, você está criando uma forma de polimorfismo, onde diferentes classes podem ser tratadas de forma uniforme se implementarem a mesma interface.

### 5. Implementação de Composição e Associação

A composição e a associação descrevem como diferentes classes interagem entre si:

- **Composição**: A classe `Usuario` pode ser composta por um objeto `Perfil`, que contém informações detalhadas sobre o usuário, como biografia, foto de perfil, etc. Aqui, o `Perfil` é parte integrante do `Usuario` e só existe dentro do contexto de um `Usuario`.

- **Associação**: Defina uma relação entre `Usuario` e `Postagem`, onde um usuário pode ter várias postagens. A associação permite que os objetos `Usuario` e `Postagem` existam independentemente, mas ainda estejam logicamente conectados.

### 6. Criação de Funcionalidades

Depois de definir as classes e as relações entre elas, adicione funcionalidades que simulem as operações típicas de uma rede social:

- **Criar Postagem**: Permitir que os usuários criem novas postagens, onde o conteúdo e a data de criação são registrados.
  
- **Curtir Postagem**: Implementar a funcionalidade de curtir uma postagem, incrementando o contador de curtidas. As postagens devem implementar a interface `Curtivel`.

- **Comentar Postagem**: Adicionar a possibilidade de os usuários comentarem nas postagens, armazenando esses comentários em uma lista associada à postagem.

### 7. Teste e Expansão

Após implementar as funcionalidades básicas, teste a interação entre os diferentes tipos de usuários e postagens. Pense em como essas funcionalidades poderiam ser expandidas para incluir novos recursos, como compartilhamento de postagens, notificações, ou até mesmo a implementação de uma estrutura de dados para armazenar e ordenar as postagens (por exemplo, usando listas ou árvores).
