# Exemplo de Estrutura de Microsserviço
Este repositório tem o objetivo de demonstrar uma forma de arquitetar um projeto de microsserviço em C#, utilizando comandos CLI e camadas para sua construção.

## Para que serve?
Estruturar um projeto adequadamente ajuda a organizar o código, os recursos e as configurações de um aplicativo ou biblioteca, facilitando o desenvolvimento, a manutenção e a colaboração em projetos de software. A estrutura define como os arquivos e diretórios estão organizados no disco e estabelece convenções que ajudam a gerenciar o ciclo de vida do desenvolvimento.

## Camadas do Projeto
As camadas de um projeto em C# (ou em qualquer arquitetura de software) servem para organizar e separar responsabilidades, criando uma estrutura modular que facilita o desenvolvimento, a manutenção e a escalabilidade do sistema. Essa abordagem é conhecida como Arquitetura em Camadas (Layered Architecture).

## Como Criar?
Neste exemplo, foi criada uma estrutura básica, mas bastante utilizada para o desenvolvimento de microsserviços, visando segurança, comunicação e uma boa implementação do projeto como um todo.

### Camadas
As camadas utilizadas são:
- API
- Application
- Domain
- Infrastructure
- Integrations
- Util
- Tests

#### Qual a finalidade de cada camada?
- API: Tem como objetivo ser a porta de comunicação entre uma aplicação externa e a aplicação interna, por meio de endpoints construídos.
- Application: Atua como intermediária entre a camada API e a camada Domain. É responsável por coordenar ações, orquestrar operações e aplicar casos de uso específicos.
- Domain: Contém as regras de negócio e as abstrações do domínio. Ela modela o problema que a aplicação resolve, mantendo-se independente de outras camadas, como apresentação e infraestrutura.
- Infrastructure: Responsável por implementar detalhes técnicos e operacionais que suportam o funcionamento do sistema. Essa camada contém as implementações concretas necessárias para o sistema interagir com o mundo externo, como bancos de dados, envio de e-mails, logging e outros serviços.
- Integrations: Responsável por se comunicar com APIs de terceiros.
- Util: Contém classes e funções auxiliares ou genéricas que são utilizadas em diversas partes do sistema, mas que não se encaixam diretamente nas outras camadas. Ela fornece funcionalidades comuns e reutilizáveis que facilitam o desenvolvimento e evitam a duplicação de código.
- Tests: Essa camada serve para aplicar os testes unitários de todas as outras camadas. Em produção, ela não tem funcionalidade, mas é fundamental para garantir a funcionalidade e a integridade das demais camadas.

### Como criar o projeto
Neste exemplo, estou utilizando comandos CLI para criar a estrutura apresentada. Abaixo estão os comandos e suas finalidades, dispostos na ordem de execução:

1. Criar uma nova solução: **dotnet new sln**
2. Em caso de API: **dotnet new webapi -o nome-da-pasta.API**
3. Para as outras camadas: **dotnet new classlib -o nome-da-pasta.camada**
4. Para a camada de testes, será utilizada a biblioteca própria para testes unitários: **dotnet new xunit -o nome-da-pasta.camada.tests**
5. Adicionar a pasta na SolutionExplorer: **dotnet sln add nome-da-pasta-camada --solution-folder nome-da-pasta-solution**
6. Adicionar referências nos projetos: **dotnet add nome-da-pasta-que-receberá-a-referência reference nome-da-pasta-que-será-rreferênciado**

## Informações adicionais
### O que é SolutionExplorer?
O Solution Explorer é uma ferramenta do Visual Studio, um ambiente de desenvolvimento integrado (IDE), que permite aos desenvolvedores visualizar e gerenciar os projetos e arquivos dentro de uma solução. Uma "solução" no Visual Studio pode conter um ou mais projetos, e o Solution Explorer oferece uma visão hierárquica de todos os arquivos e componentes dentro desses projetos, como código-fonte, arquivos de configuração, dependências e recursos.

A principal função do Solution Explorer é ajudar os desenvolvedores a navegar entre os arquivos e pastas de forma eficiente, permitindo o acesso e a edição dos componentes dos projetos de maneira organizada. Além disso, ele facilita a construção, depuração e execução de projetos diretamente da interface do Visual Studio.

### Porque referenciar projetos?
As referências entre projetos permitem que você compartilhe funcionalidades e lógicas de negócio de maneira eficiente, sem duplicação de código.

Exemplo: Se você tiver um projeto de domínio (Domain), pode referenciar esse projeto em outros projetos (como Application ou Infrastructure) para reutilizar as regras de negócio e modelos de dados.

## Conclusão
Criar uma estrutura adequada e seguir convenções pode beneficiar a escalabilidade do seu projeto e facilitar o trabalho em equipe, especialmente para desenvolvedores que irão trabalhar no projeto no futuro. Isso garante que a integridade e a confiança na aplicação sejam mantidas.
