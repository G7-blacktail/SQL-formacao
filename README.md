# Formação SQL Database Specialist

Este repositório trata-se dos assuntos estudados no bootcamp da DIO.me sobre Database chamado Formação SQL Database Specialist, aqui estou guardando tudo que achei importante anotar para prosseguir em meu estudo.

# Fundamentos de banco de dados Modulo 1 Anotações

## Arquitetura de banco de dados

### Arquitetura de BD: Modelos

abstração: coletar apenas as caracteristicas ideais e/ou essencial, retirando as informações que particularizam o contexto

Classificação está atrelada a estrutura que por sua vez define o modelo.

    Modelo de dados Conceitual

    Modelo de dados de implementação

    Modelo de dados físicos

Visão de alto nível (modelo de dados conceitual): { entidade , Atributos, Relacionamento }
    recursos: Generalização, especialização, modelo entidade-relacionamento (ER)

Representacional (Modelo de dados de implementação): { Modelo de dados relacional, modelo hierárquico }
    recursos: Constrains, linguagem (SQL) e operações

Especialista (Modelo de dados físicos): { índices, hashes }


### Arquitetura de BD: Esquema, Instâncias e estados de um BD's

Esquema: é uma descrição concisa do banco de dados, objetos e suas relações. Pode ser representado por diagramas. Em outras palavras é a estrutura onde os dados serão persistidos.
(Construct) a instância e ocorrências de dados não são utilizados no momento.

Também o esquema é equivalente ao estado inicial do banco de dados, ou seja, ele representa a estrutura porém sem nenhum dado ainda persistido, estando vazio.

Meta dados {Descrição Esquema, construtores, contrains}

### Three-Schema Archiecture

Para esta arquitetura existem 3 tipos de suporte: Isolamento data/program, catálogo e views.

Elas vão determinar o schema.

Este tipo de arquitetura possui o papel de definir o que cada esquema fará no banco.

### Linguagem de Banco de dados

DDL - Data Definition Language

linguagens e interfaces: são atreladas ao usuário.

Quando se cria o squema são utilizadas as DDL's 

Separação explicita:

SDL: Físicos
VDL: Views
DML: inserção, recuperação (linguagem de definição)


DML tem dois tipos: Baixo nível | procedural      (como recuperar)
                    Alto nível  | não procedural (o que recuperar e não como)


### Interfaces de SGBD's

Web client: baseado em lista, é acessado pelo front via API ou web browser, geralmente por meio de menus. (Requisições e estruturas)
App Mobile: Acesso à dados, está também limitado ao front porém com o escopo reduzido (Bancos, reservas, etc; são alguns exemplos)
Froms: Está relacionados a interface para novos dados, preenche totalmente ou parcialmente e não está ligado a uma interface de usuário (front)
GUI: Interface gráfica de usuário disposta em forma de diagrama, o usuário irá navegar usando Query para manipular o diagrama e acessar as informações
NLI: Natural Language Interface, intrepreta a linguagem natural do usuário. 
    (Interface de Linguagem Natural) é uma tecnologia que permite aos usuários interagirem com sistemas computacionais  utilizando linguagem natural, ou seja, de forma semelhante à comunicação entre seres humanos.
Pesquisa Keyword: A partir de uma palavra chave é realizada a pesquisa, pode ser atrelada a indicie atravez do match com a palavra
Speech input/output: é solicitado a partir da linguagem natural e o retorno também, porém ele tem o contexto limitado (um exemplo é a pesquisa do Google através do microfone, comando de voz)
Interfaces: 
    Naive: operações repetitivas (um dos exemplos são os APP's de banco pois temos várias operações repetitivas e/ou rotinas)
    DBA: (DBA staff) comando com alto nível de privilêgios, podemos definir diversas coisas usando comandos para modular o desempenho


### Ambientes e utilities de SGBD

gerenciamento, monitoramento, reorganização do storage, backup e loading são alguns dos utilities dentro do SGBD's existentes no mercado atualmente.

DB design pode ser uma ferramenta muito ultil na hora de definir como será a banco de dados.

### Arquitetura Modelo cliente-servidor

### Classificação de SGBD's

Modelos de dados, Nº de usuários Nº de sites, custo e tipo de caminho de acesso.

Devemos levar em conta todos esses parâmetros para definir qual SGBD será usado.

    modelo de dados: dependendo do tipo de arquivo que estamso querendo armazenar devemos decidir entre NoSQL ou SQL.

    Nº Usuario: se houver um número grande de usuário e acessos.

    Nº de sites: temos Big datas, replicação, DB federado e Heterogeneidade (fontes diferentes).

Podemos classificar por performace também. 
(OLTP)

O OLTP ou Processamento de Transações Online é um tipo de processamento de dados que consiste na execução de várias transações que ocorrem simultaneamente (transações bancárias online, compras, entrada de pedidos ou envio de mensagens de texto, por exemplo).

# Modelo de entidade relacional com banco de dados Modulo 2 anotações

## Fundamentos de modelagem e projeto de banco de dados

### Mundo Fechado e mini-mundo

O conceito de mundo fechado quando estamos buscando uma informação que não está sendo contemplada (não existe) sempre será retornado falso e/ou quando realmente a informação seja falsa

O conceito de mini-mundo trata-se de modelar apenas o que é necessário, representando o contexto, sendo representado pelo mínimo possível.

O banco de dados, modelo lógico, irá armazenar apenas o que é apresentado no míni-mundo.

Ex.: 
Universidades 
{
    departamentos
    {
        profissionais,
        professores
    },
    {
        cursos
    }
}

CWA: está atrelado ao míni-mundo, pois estamos delimitando o que queremos e tudo que estiver fora não pode ser respondido, sendo falso automáticamente.
 Sendo uma preposição de lógica de predicados.

### Álgebra relacional

O predicado é a parte da oração que contém o verbo e que traz informações sobre o sujeito

[critério] -> [having] [Where]

Usando a teoria dos conjuntos temos a linguagem formal para consulta/extração de dados sendo as operações divididas em:

[conjunto de operações] { Op. de conjuntos, Op. de BD relacional}

Algumas dessas operações são:

    1.  SELECTION
    2.  PROJECTION
    3.  RENAMING
    4.  UNION
    5.  INTERSECTION
    6.  DIFFERENCE
    7.  CARTESIAN PRODUCT
    8.  JOIN
    9.  LOGICAL AND
    10. LOGICAL OR
    11. LOGICAL NOT

todos são exclusivos para SGBD's relacionais.

tipos de operações que temos usando SQL:

    ANY, MAX, AVG, COUNT, SUM, MIN 

### Álgebra relacional e projeto de banco de dados

Será enviado a álgebra relacional para o banco e será retornado o resultado da ação, com isso podemos perder a dependência da aplicação/dados, pois agora se tratara de N conjuntos individuais que podemos utilizar para as consultas (tabelas diferentes que podem ser consultadas e retornando como um conjunto resultante assim como a teoria dos conjuntos da álgebra comum).

tradeoff : Há um pequeno delay entre inserir ou remover dados do banco, por este motivo temos que tratar esse delay dependendo da performace que queremos no banco.

CLOCK do sistema > disponibilidade e tempo de gravação

processos : Projeto conceitual, Projeto lógico, projeto físico, validação, produção, manutenção.

### Falando sobre modelagem

BD particular - Softwares - queries & updates ->

            Aplicação de BD

Neste ponto é explicado sobre as etapas de desenvolvimento

            planejar 
    agir               fazer
            checar

### Projeto: Como "nasce" um banco de dados?

Para implementar é necessário fazer uma série de perguntas:

    Como implementar um BD?
        entender o contexto e requisitos
        perfil
    O que eu quero representar?

Processo evolutivo ou gradual: implementação, modelo, arquitetura e funcionalidades.

Cenários: Colaboradores, E-commerce, Universidade, Produção, Banco (financeiro), Farmácia, Biblioteca;

Como resolver:

    Modelagem

    conceitual -> Lógico -> Físico

### Design de BDs - Projeto Conceitual

Podemos criar o modelo conceitual de forma gráfica ou até mesmo de forma textual

Esta linguagem de modelagem de dados será uma representação dos dados.

 1º passo : requisitos, perguntas a serem respondidas, visões [coleta de dados] [ Análise]

### Projeto conceitual: Entendendo o passo a passo

Modelo de alto nível 

    Requisitos { 
                    O que executar? quais processos [ funcionais ]
                    Segurança, desempenho [ não funcionais ]
                }

Neste momento não iremos pensar como será armazenado

Fluxo da aplicação:

    dados e requisitos { coleta, analise } 
    design conceitual { Esquema conceitual }

### Exemplificando o projeto conceitual e processo

O processo será feito da seguinte forma:

Projeto Coneceitual [O que vai ter?] ---> Projeto Lógico [Como estruturar?] ---> Projeto físico [Como implementar?]

Os requisitos então resultaram em

Esquema Conceitual ---> Esquema Lógico ---> Esquema Físico

### Implementação: Projeto lógico e físico

Neste ponto do projeto iremos para o projeto lógico a partir da descrição do modelo conceitual, onde identificaremos a estrutura e a organização dos dados, obviamente dependendo do modelo de banco de dados.

[tabelas] -> [estrutura] -> [organização dos dados]

então será feito o mapeamento do projeto conceitual para o projeto lógico resultando o esquema do BD.

O percurso correto seria a criação do esquema lógico a instalação do SGBD e a criação do esquema do BD. Apartir do SGBD escolhido ele irá influencia o projeto lógico.

Qual tipo de entidade, Relacionamento (binário ou não, cardinalidade) , atributos (multivalorados), restrições e integridade.

Por fim o projeto físico é o resultado do projeto lógico e será a como a estrutura, índice, organização e caminhos de arquivos, segurança, performance, etc;

### Fases de desenvolvimento de BDs e Aplicações

O OLAP é uma tecnologia de banco de dados que foi otimizada para consulta e relatório, em vez de processar transações. Os dados de origem do OLAP são bancos de dados OLTP (Processamento Transacional Online) que são comumente armazenados em data warehouses.

O HTAP (processamento transacional e analítico híbrido) é uma técnica de análise quase em tempo real sem a necessidade de uma solução ETL complexa. No Azure Synapse Analytics, o HTAP tem suporte por meio Link do Azure Synapse.

### Aplicação: Modelagem de dados


## Modelo de Entidade Relacionamento com banco de dados

### Modelo ER: Tipos de entidades, chaves e atributos

Processos: Tipos de entidades, atributos e chaves, relacionamentos, papéis e constraints, esquema relacional, diagrama ER (DER)

    Entidades é basicamente um objeto que contem atributos sendo instanciado e guardando os atributos no banco os dados que estão relacionados a seus atributos.

    Atributos: São as caracteristicas/ descrições das entidades e estão relacioandos a instâncias das mesmas.

        tipos de atributos: Atômicos: São simples, contendo apenas 1 informação
                            Compostos: São complexos e possuem variações, pode ser composto por uma concatenação de informações.

                            Atributos multivalorados: São compostos por váriação de valor (grupo)

                            Armazenados: É um atributo que não será mudado
                            Derivados: É um atributo que é derivado de outro (data de nascimento -> idade)

                            Atributos nulos: São atributos que podem conter ou não valor real, podendo conter valor NULL

                            Atributos complexos: Está atrelado a estrutura sendo o mais complexo

### Tipos de atributos dentro do modelo ER

Multivalorados serão compostos por atributos que podem variar os dados encapsulados em sí. Podemos dizer que em multivalorados temos o intervalos.

Também temos o atributo unkown que é um atributo que existe porém é desconhecido, diferente de NULL de certa forma.

Antes de começar a falar de entidade vou descrever alguns simbolos e seus significados

    quadrado : representa a entidade
    circulo/elipse : representa o atributo atômico
    circulo/elipse com um __underline abaixo do nome: representa um atributo composto
    circulo/elipse sobreposto ou duplo: representa um atributo multivalorado


### O que é a entidade fraca no modelo ER

Entidades temos atributos e chaves;

Uma entidade fraca precisa estar relacionada com outa para exitir, de forma que seja dependênte da outra.

Ela possue a seguintes caracteristicas:

    Chave não é obrigatória
    Depêndencia
    Exclusão em cascata

Ela é representada por um quadrado duplo no Diagrama ER [[]] e para o relacionamento com elas um losango duplo <<>>

### Exemplo de modelo conceitual - Company

O exemplo foi feito no arquivo  [database.drawio] acompanhando o que foi dito na aula

Elipse trastejada representa

### Relacionamentos, papéis e constrainsts estruturais

Relacionamentos estão inteiramente ligado a teoria de conjuntos se tratando de uma função podendo ser classificado:

    Grau
    Auto-relacional ou não
    Cardinalidade

Os graus podem ser binário (de 1 para 1 entidade), ternário (de 1 : 3 entidades) e any ( de N : N entidades)

Relacionamentos como atributos não é uma prática correta, geralmente em primeiro momento pode ser definido porém a necessidade irá fazer com que ele seja convertido em um relacionamento.

Papel: ao atribuir um papel para cada entidade vai ficando claro o relacionamento entre elas como : empregado - departamento.

O auto-relacionamento 