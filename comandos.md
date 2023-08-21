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

ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores FOREIGN KEY (professor_id)
	REFERENCES professores(id);
    
ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos FOREIGN KEY (curso_id)
	REFERENCES cursos(id);
    
ALTER TABLE alunos
    ADD CONSTRAINT fk_alunos_cursos FOREIGN KEY (curso_id)
	REFERENCES cursos(id);
```
