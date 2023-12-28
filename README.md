# Documentação DYN365

Aplicativo(Solução): DYNTech Treinamentos

Nome: DYNTechTreinamentos

Tipo de Aplicativo: Aplicativo baseado em modelo

Versão: 1.2.2

Publicador: DYN365 Treinamento 

### Solução para gestão de instituição de ensino fantasia, com o nome de DYNTech Treinamentos. Desafio do Bootcamp CRM e Dynamics 365 da DIO em parceria com a Avanade.

O projeto terá 4 etapas, e você deverá segui-las da seguinte maneira:

O aplicativo foi criado no conceito Model Driven utilizando como Datasource o contexto do formulário em execução.

- Deverá conter Cabeçalho;
- Deverá conter um campo de entrada de texto do tipo caixa de combinação (ComboBox) permitindo a seleção do curso;
- Deverá conter Detalhe (componente do tipo Gallery);
- O Campo de entrada de texto deve ser do tipo caixa de combinação (ComboBox), permitindo a seleção do instrutor.
- Criar Fluxo do Power Automate. Criar um fluxo para que, quando um novo registro de instrutor for criado, envie um e-mail (endereço do e-mail será o informado no cadastro do instrutor).
- Exportar o aplicativo e postar no GitHub, juntamente com a planilha utilizada para carga dos dados dos estados.

## Criação da Solução

A solução foi criada no Microsoft Dynamics 365, com a criação das entidades, campos, formulários e recursos da web. 

## Base de Dados

A base de dados do curso foi obtida no site Kaggle, no formato .CSV

[Multi-Platform Online Courses Dataset](https://www.kaggle.com/datasets/everydaycodings/multi-platform-online-courses-dataset)

Para preencher informações faltantes, utilizei os seguintes recursos:

[Gerador de nomes de pessoas online - Site 112](https://site112.com/gerador-nomes-pessoas)

[Site 112 - Utilitários, ferramentas e recursos online!](https://site112.com/)

Os campos foram criados anteriormente,e em seguida foi gerado um **modelo de planilha** para o input das informações no Dataverse.

## Recursos da Web

### Validação CPF

Script para validar o número digitado e adicionar pontuação

### Logo Power Apps

Imagem de exibição do aplicativo

### Botão WorkBench

Adição do botão Curso na Ribbon na guia de criação de cursos

Foi criado um aplicativo Model Driven do tipo Canvas

## Demonstração do Aplicativo

### Tela principal com os instrutores habilitados

- Cabeçalho com Título principal
- Botão Adicionar Instrutor (cabeçalho)
- Cabeçalho com nome das colunas
- Gallery exibindo os instrutores habilitados
    - Campo com Nome do Instrutor
    - Campo com o Nível do Instrutor
- Botão para excluir instrutor (em cada linha da gallery)

### Tela para adicionar instrutor

- Cabeçalho com Título principal
- Caixa de combinação (combobox) para seleção do instrutor
- Rótulo para exibir Nível do instrutor selecionado
- Botão para cancelar a inclusão do instrutor
- Botão para salvar a inclusão do instrutor

### Tela para excluir instrutor

- Cabeçalho com Título principal
- Rótulo com texto para conferência do instrutor a ser excluído
- Rótulo com o nome do instrutor a ser excluído
- Rótulo para exibir Nível do instrutor selecionado
- Botão para cancelar a exclusão do instrutor
- Botão para confirmar a exclusão do instrutor

### Fluxo Power Automate para envio de e-mail para instrutor habilitado

- Criação do gatilho a partir do Dataverse, com a atualização da tabela Instrutores
- Ação de envio de e-mail, com a captura do e-mail do instrutor habilitado ao curso disponível
