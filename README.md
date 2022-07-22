# Operações em DB com JDBC

Esse repositório serve como estudo das operações básicas para acesso a banco de dados MySQL utilizando o JDBC e padrão DAO (Data Access Object). O código documenta etapa a etapa do estudo através dos commits. Leia o histórico de commits para ir até a etapa do processo que está sendo procurada. 

Para analisar o conteúdo de cada commit, você pode fazê-lo pela própria interface do GITHUB ou passeando localmente entre os commits com `git checkout <hash do commit>`.

## Requisitos
  01. Instalar o mysql
  02. Criar uma database `coursejdbc`
  03. Alterar o arquivo `copy_db.properties` para `db.properties` e preencher os dados de acesso ao banco (`user` e `password`)
  04. Popular o banco de dados com o script abaixo (sugestão: rodar pelo MySQL Workbench ou DBeaver)

## Script SQL
```sql
CREATE TABLE department (
  Id int(11) NOT NULL AUTO_INCREMENT,
  Name varchar(60) DEFAULT NULL,
  PRIMARY KEY (Id)
);

CREATE TABLE seller (
  Id int(11) NOT NULL AUTO_INCREMENT,
  Name varchar(60) NOT NULL,
  Email varchar(100) NOT NULL,
  BirthDate datetime NOT NULL,
  BaseSalary double NOT NULL,
  DepartmentId int(11) NOT NULL,
  PRIMARY KEY (Id),
  FOREIGN KEY (DepartmentId) REFERENCES department (id)
);

INSERT INTO department (Name) VALUES 
  ('Computers'),
  ('Electronics'),
  ('Fashion'),
  ('Books');

INSERT INTO seller (Name, Email, BirthDate, BaseSalary, DepartmentId) VALUES 
  ('Bob Brown','bob@gmail.com','1998-04-21 00:00:00',1000,1),
  ('Maria Green','maria@gmail.com','1979-12-31 00:00:00',3500,2),
  ('Alex Grey','alex@gmail.com','1988-01-15 00:00:00',2200,1),
  ('Martha Red','martha@gmail.com','1993-11-30 00:00:00',3000,4),
  ('Donald Blue','donald@gmail.com','2000-01-09 00:00:00',4000,3),
  ('Alex Pink','bob@gmail.com','1997-03-04 00:00:00',3000,2);
```
