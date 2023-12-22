# Documentação DYN365

Aplicativo(Solução): DYNTech Treinamentos

Nome: DYNTechTreinamentos

Tipo de Aplicativo: Aplicativo baseado em modelo

Versão: 1.2.0

Publicador: DYN365 Treinamento

Descrição: Solução para gestão de instituição de ensino. Desafio do Bootcamp CRM e Dynamics 365 da DIO em parceria com a Avanade.

Propriedade: Organização

admin@RenataGarcia874.onmicrosoft.com

Truly1992!

[](https://org656f8b75.crm2.dynamics.com/)

## Base de Dados

A base de dados do curso foi obtida no site Kaggle, no formato .CSV

[Multi-Platform Online Courses Dataset](https://www.kaggle.com/datasets/everydaycodings/multi-platform-online-courses-dataset)

[Gerador de nomes de pessoas online - Site 112](https://site112.com/gerador-nomes-pessoas)

Optei por escolher os cursos da Microsoft e retirei as informações que entendi que seriam relevantes para construir o projeto e realizei a modelagem dos dados de acordo com os requisitos solicitados pelo cliente.

Para preencher informações faltantes, utilizei os seguintes recursos:

[Site 112 - Utilitários, ferramentas e recursos online!](https://site112.com/)

Os campos foram criados no Dynamics 365, em seguida foi gerado um **modelo de planilha** para o carregamento das informações no Dataverse.

### Relações

As informações estão dispostas em três tabelas, de acordo com o diagrama UML abaixo:

### Tabela/Entidade:

Aluno

### Colunas/Atributos/Campos:

Canvas Aluno

CPF do aluno	

Nome do aluno: Chave Primária : dyn365_name

Telefone do aluno	

E-mail do aluno

### Tabela/Entidade:

Curso

### Colunas/Atributos/Campos:

Canvas Instrutores: Campo de vínculo com a criação de aplicativo no Power Apps

ID do curso: dyn365_cursoid

Nome do curso:  dyn365_name

Tipo do curso: Pago, Gratuito

Valor do curso: R$ 

Nível do curso: Básico, Intermediário, Avançado

Tipo de certificado: Certificado profissional, Curso, Especialização.

### Tabela/Entidade:

Instrutor

### Colunas/Atributos/Campos:

CPF instrutor

Nome do Instrutor dyn365_name

Nível do instrutor: Principiante, Intermediário, Avançado

E-mail do instrutor:

## Tabelas de Consulta

### Tabela/Entidade: Cursos Disponíveis X Instrutores Habilitados

Relação: N:N

Um único registro de um instrutor para cada curso e vice versa

Criação de chave: Curso X Instrutor

### Tabela/Entidade: Cursos Disponíveis  X Alunos Inscritos

Relação: N:N

Um único registro de um aluno para cada curso e vice versa

Criação de chave: Curso X Aluno

### Regras de negócio

Um cliente deseja criar um aplicativo de gerenciamento de uma plataforma de cursos online. Existe uma lista de cursos com que eles já trabalharam, mas apenas alguns estão disponíveis. 

Os cursos podem ser Pagos ou Gratuitos, sendo obrigatório o preenchimento do campo Valor do curso caso ele seja Pago.

Os cursos estão identificados por um ID, enquanto os Instrutores e Alunos são identificados pelo CPF.

Nome da regra de negócios: Obrigatoriedade do Campo Valor do Curso

Descrição: Preenchimento obrigatório do campo Valor do Curso caso o campo Tipo do Curso for definido como Pago

Condição

Nome de exibição: Campo Tipo de curso Pago

Entidade: Curso

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled.png)

Nome de Exibição: Campo Valor do curso obrigatório

Entidade: Cursos

Requisitos Comerciais: Obrigatório

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%201.png)

Nome de Exibição: Campo Valor do curso não obrigatório

Entidade: Cursos

Requisitos Comerciais: Não é obrigatório

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%202.png)

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%203.png)

## Recursos da Web

### Validação CPF

Script para validar o número digitado e adicionar pontuação

### Logo Power Apps

Imagem de exibição do aplicativo

### Botão WorkBench

Adição do botão Curso na Ribbon na guia de criação de cursos

## Fluxos

## Exportação

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%204.png)

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%205.png)

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%206.png)

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%207.png)

```
Patch('Cursos X Instrutores'; Defaults('Cursos X Instrutores');
{
    Instrutores: CmbInstrutor.Selected;
    'Cursos Disponíveis': [@ModelDrivenFormIntegration].Item;
    Nome:[@ModelDrivenFormIntegration].Nome & " - " & CmbInstrutor.Selected.'Nome do Instrutor'
}
);;
Reset(CmbInstrutor);;
Back()
```

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%208.png)

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%209.png)

```
Patch('Cursos X Instrutores'; Defaults('Cursos X Instrutores');
{
    'Instrutores Habilitados': CmbInstrutor.Selected;
    'Cursos Disponíveis': CmbCursosDisponiveis.Selected;
    Nome: CmbCursosDisponiveis.Selected.'Nome do curso' & " - " & CmbInstrutor.Selected.'Nome do Instrutor'
  
}
);;
Reset(CmbInstrutor);;
Reset(CmbCursosDisponiveis);;
Back()
```

![Untitled](Documentac%CC%A7a%CC%83o%20DYN365%20034e7db883dc417d89dd56481ef5fe8e/Untitled%2010.png)

**Remove( IceCream,LookUp( IceCream, Flavor="Chocolate" ))**

Filter(Instrutores; 'Instrutores (Modos de exibição)'.'Exibição Associada de Instrutor')

'Cursos X Instrutores’