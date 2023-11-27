# BD_NORMALIZACAO

## ETAPA 1 -

-- Tabela para armazenar informações sobre locações --

CREATE TABLE LOCACAO (
    COD_LOCACAO INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    VEICULO_NOME VARCHAR(123) NOT NULL,
    COR VARCHAR(123) NOT NULL,
    PLACA VARCHAR(123) NOT NULL,
    DIARIA DECIMAL(9,2) NOT NULL,   
    CPF_CLIENTE VARCHAR(123) NOT NULL,
    DIA INT NOT NULL,
    TOTAL DECIMAL(9,2) NOT NULL,
    FOREIGN KEY (CPF_CLIENTE) REFERENCES CLIENTE(CPF)
);

-- Tabela para armazenar informações sobre clientes --

CREATE TABLE CLIENTE (
    CPF VARCHAR(123) PRIMARY KEY NOT NULL,
    NOME VARCHAR(123) NOT NULL,
    NASCIMENTO DATE
);

## ETAPA 2 -

-- Inserção de dados na tabela cliente --

INSERT INTO CLIENTE (CPF, NOME, NASCIMENTO) VALUES ('123.456.789-01', 'Ariano Sussuna', '2022-05-21');
INSERT INTO CLIENTE (CPF, NOME, NASCIMENTO) VALUES ('543.765.987-23', 'Grace Hopper', '2002-04-29');
INSERT INTO CLIENTE (CPF, NOME, NASCIMENTO) VALUES ('987.654.321-90', 'Richard Feynman', '2001-10-12');
INSERT INTO CLIENTE (CPF, NOME, NASCIMENTO) VALUES ('432.765.678-67', 'Edgar Poe', '1998-12-14');
INSERT INTO CLIENTE (CPF, NOME, NASCIMENTO) VALUES ('927.384.284-44', 'Gordon Freeman', '1984-11-26');

-- Seleção de todos os registros da tabela cliente --
SELECT * FROM CLIENTE;

-- Inserção de dados na tabela locacao --
INSERT INTO LOCACAO (VEICULO_NOME, COR, PLACA, DIARIA, CPF_CLIENTE, DIA, TOTAL) VALUES ('Fusca', 'Preto', 'WER-3456', 30.00, '123.456.789-01', 3, 90.00);
INSERT INTO LOCACAO (VEICULO_NOME, COR, PLACA, DIARIA, CPF_CLIENTE, DIA, TOTAL) VALUES ('Variante', 'Rosa', 'FDS-8384', 60.00, '543.765.987-23', 7, 420.00);
INSERT INTO LOCACAO (VEICULO_NOME, COR, PLACA, DIARIA, CPF_CLIENTE, DIA, TOTAL) VALUES ('Comodoro', 'Preto', 'CVB-9933', 20.00, '987.654.321-90', 1, 20.00);
INSERT INTO LOCACAO (VEICULO_NOME, COR, PLACA, DIARIA, CPF_CLIENTE, DIA, TOTAL) VALUES ('Deloriam', 'Azul', 'FGH-2256', 30.00, '123.456.789-01', 3, 90.00);
INSERT INTO LOCACAO (VEICULO_NOME, COR, PLACA, DIARIA, CPF_CLIENTE, DIA, TOTAL) VALUES ('Brasilia', 'Amarela', 'DDI-3948', 45.00, '927.384.284-44', 7, 315.00);

-- Seleção de todos os registros da tabela locacao --
SELECT * FROM LOCACAO;

-- Criação da view Todas_locacoes -- 
CREATE VIEW TODAS_LOCACOES AS
    SELECT * FROM LOCACAO
    JOIN CLIENTE ON CLIENTE.CPF = LOCACAO.CPF_CLIENTE;

-- Seleção de todos os registros da view Todas_locacoes --
SELECT * FROM TODAS_LOCACOES;
