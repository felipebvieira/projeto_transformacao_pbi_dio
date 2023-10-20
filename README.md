# Processando e Transformando Dados com Power BI
Desenvolvi um sistema de gerenciamento de dados de alta eficiência ao criar um banco de dados MySQL na nuvem, utilizando a plataforma Azure da Microsoft. Com expertise, modelei e populei o banco com tabelas estratégicas, garantindo a integridade dos dados. A seguir, integrei perfeitamente o ambiente ao Power BI, realizando a extração direta dos dados hospedados na Azure. Utilizando o Power Query, aprimorei a qualidade dos dados, corrigindo eventuais imperfeições e mesclando tabelas para uma visão abrangente. Concluí o processo com a elaboração de um relatório sólido no Power BI, consolidando todas as informações de forma intuitiva e acessível.

## Minhas alterações
Minhas alterações

- removi as constraints, os metas dados, porque são reacionadas somente ao banco de dados
- alterei o nome de algumas colunas para facil identificação
- alterei salario para decimal fixo
- separei o endereço em estado, cidade, rua e numero
- corrigi o erro quando utilizei o dividir com delemitador
- coloquei o numero da rua como texto pois pode haver letra
- o employee com null no ssn é um gerente da sede e não tem horas contabilizadas
- em mesclar utilizei o Dnumber para poder combinar as duas tabelas e agregar informações, exclui uma das tabelas Dnumber pois não era necessário, uma resposta bem simples foi que basicamente mesclar complementa informações com colunas adicionais baseado nas opções selecionadas, no cenario proposto mesclar é indicado
- mesclado o nome e sobrenome usando uma funcionalidade do power BI mesclar coluna
- no power bi usei o mesclar para criar a representação dos employee e seus managers com as tabelas ssn e Superssn agregando os valores para gerar o resultado, depois exclui colunas repetidas

comando sql:
SELECT
  e1.Fname AS EmployeeName,
  e1.Ssn AS EmployeeSsn,
  e2.Fname AS ManagerName,
  e2.Ssn AS ManagerSsn
FROM
  employee e1
JOIN
  employee e2 ON e1.Super_ssn = e2.Ssn;

- realizei a mescla de nome do departamento com sua localização usando as tabelas departament e dept_locations, utilizei o Dnumber como denominador para a mescla das informações
- decidi criar uma tabela a mais para com o group by para ter mais informações

## Meu entendimento das Diferenças entre Acrescentar e Mesclar
- acrescentar basicamente pode se gerar uma nova tabela com dados de outras tabelas por exemplo tem tabelas clientes, fornecedor e funcionario e as 3 tabelas tem as colunas id, empresa, nome, telefone e endereço, quando usamos acresentar ele acrescenta os dados a essas colunas fornecendo novas linhas, um exemplo seria no caso de uma solicitação do RH da empresa aonde ele quer uma tabela com as informações dos 3.

- mesclar se eu quiser todas as informações em uma mesma tabela usa o mesclar para que eu veja consolidado em uma tabela. Mesclar basicamente é junção de dados de duas tabelas no caso uma tabela irá complementar a outra como se fosse dados faltantes para ter uma maior amplitude e controle sobre os dados e por isso ele precisa de uma condição de junção que pode ser o id. Mesclar aglutina os dados em uma unica tabela. resumindo mesclar ele vai adicionar novas colunas para complementar nossa tabela com os dados que desejamos das outras tabelas.