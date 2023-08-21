```SQL
CREATE DATABASE tecinternet_escola_melissa CHARACTER SET utf8mb4;
--USE DATABASE tecinternet_escola_melissa;


CREATE TABLE cursos(
    id TINYINT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    titulo VARCHAR(30) NOT NULL,
    cargaHoraria TINYINT NOT NULL,
    professor_id TINYINT NULL
);

CREATE TABLE professores(
    id TINYINT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    nome VARCHAR(50) NOT NULL,
    areaAtuacao VARCHAR(35) NOT NULL,
    curso_id TINYINT NOT NULL
    --  ,cursos_professores_id TINYINT NOT NULL
);

CREATE TABLE alunos(
	id TINYINT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    nome VARCHAR(50) NOT NULL,
    dataNascimento DATE NOT NULL,
    primeiraNota DECIMAL(4,2) NOT NULL,
    segundaNota DECIMAL(4,2) NOT NULL,
    curso_id TINYINT NOT NULL
);



-- Adição da CONSTRAINT
ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores FOREIGN KEY (professor_id)
	REFERENCES professores(id);
    
ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos FOREIGN KEY (curso_id)
	REFERENCES cursos(id);


-- Mudança de tipo de dado de VARCHAR para ENUM
ALTER TABLE professores 
    MODIFY COLUMN areaAtuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL;
    
ALTER TABLE alunos
    ADD CONSTRAINT fk_alunos_cursos FOREIGN KEY (curso_id)
	REFERENCES cursos(id);


-- Dados inseridos Cursos e Professores

INSERT INTO cursos(titulo, cargaHoraria) VALUES
('Back-End', 80),
('UX/UI Design', 30),
('Figma',10),
('Redes de Computadores', 100);

INSERT INTO professores(nome, areaAtuacao, curso_id) VALUES
('Jon Oliva', 'infra', 5);

INSERT INTO professores(nome, areaAtuacao, curso_id) VALUES
('Lemmy Kilmister', 'design', 4),
('Neil Peart', 'design', 3),
('Ozzy Osbourne', 'desenvolvimento', 2),
('David Gilmour', 'desenvolvimento', 1);

-- Relação

UPDATE cursos SET professor_id = 5 WHERE id = 1;
UPDATE cursos SET professor_id = 4 WHERE id = 2;

UPDATE cursos SET professor_id = 3 WHERE id = 3;
UPDATE cursos SET professor_id = 2 WHERE id = 4;
UPDATE cursos SET professor_id = 1 WHERE id = 5;


-- Dados inseridos

INSERT INTO alunos(nome, dataNascimento, primeiraNota, segundaNota, curso_id) VALUES
('Ana', '20060201', 8.9, 8.0, 1),
('Roberto','20060415',6, 3.5, 1);

INSERT INTO alunos(nome, dataNascimento, primeiraNota, segundaNota, curso_id) VALUES
('Mariana', '2005-02-01', 9, 8.5, 2),
('Yasmin','2006-02-09',4, 4.5, 2);

UPDATE alunos SET primeiraNota = 7.00 WHERE id = 3;

INSERT INTO alunos(nome, dataNascimento, primeiraNota, segundaNota, curso_id) VALUES
('Fernanda', '2006-05-19', 10, 8.75, 3),
('Felipe','2007-07-21', 8, 9, 3);

UPDATE alunos SET dataNascimento = '2006-10-19' WHERE id = 5;

INSERT INTO alunos(nome, dataNascimento, primeiraNota, segundaNota, curso_id) VALUES
('Lucas', '2008-04-11', 5.55, 4.75, 4),
('João','2006-08-03', 6.0, 3.0, 4);

INSERT INTO alunos(nome, dataNascimento, primeiraNota, segundaNota, curso_id) VALUES
('Thomas', '2008-05-25', 9 , 9.25, 5),
('Debora','2006-04-08', 8.75, 5.25, 5);

UPDATE alunos SET primeiraNota = 7.25 WHERE id = 9;
```
