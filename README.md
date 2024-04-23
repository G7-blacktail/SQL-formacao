# Formação SQL Database Specialist

Este repositório trata-se dos assuntos estudados no bootcamp da DIO.me sobre Database chamado Formação SQL Database Specialist, aqui estou guardando tudo que achei importante anotar para prosseguir em meu estudo.

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



