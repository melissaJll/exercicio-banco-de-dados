
## CRUD - Consultas


### 1) Alunos que nasceram antes do ano 2009

```sql
SELECT nome Nome, dataNascimento FROM `alunos` WHERE dataNascimento < '2009-01-01';
```
![primeira consulta](/imagens/exerc01.png)

---
### 2) Calculo da média das notas de cada aluno com duas casas decimais.

```sql
SELECT nome Nome, ROUND((primeiraNota + segundaNota)/2,2) 'Média' FROM `alunos` GROUP BY nome;
```



---
### 3) Calculo do limite sendo 25% da carga horária. Em ordem crescente pelo título do curso.

```sql

SELECT titulo, cargaHoraria as 'Total de Horas' , cargaHoraria * 0.25 as 'Limite em hrs' FROM `cursos` ORDER BY titulo;

```



---
### 4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".

```sql
SELECT nome 'Nome', areaAtuacao 'Área de atuação' FROM `professores` WHERE areaAtuacao = 'desenvolvimento';
```



---
### 5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.

```sql

SELECT areaAtuacao as 'Área', COUNT(id) as 'Quantidade de Professores' FROM `professores` GROUP BY areaAtuacao;
```

---
### 6) Faça uma consulta que mostre o nome dos alunos, o título e a carga horária dos cursos que fazem.

```sql
SELECT alunos.nome as Nome, cursos.titulo Curso, cursos.cargaHoraria as 'Carga Horária' FROM `alunos` 
INNER JOIN cursos 
	ON alunos.curso_id = cursos.id;
```

---
### 7) Faça uma consulta que mostre o nome dos professores e o título do curso que lecionam. Classifique pelo nome do professor.

SELECT professores.nome Nome, cursos.titulo 'Curso Lecionado'
FROM `professores`INNER JOIN cursos 
	ON professores.curso_id = cursos.id;

---


### 8) Faça uma consulta que mostre o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso.


```sql
SELECT alunos.nome Aluno, professores.nome Professor, cursos.titulo 'Curso Lecionado'
FROM `professores`INNER JOIN cursos 
	ON professores.curso_id = cursos.id
INNER JOIN alunos 
	ON alunos.curso_id = cursos.id;

```
---

### 9) Faça uma consulta que mostre a quantidade de alunos que cada curso possui. Classifique os resultados em ordem descrecente de acordo com a quantidade de alunos.

```sql
SELECT cursos.titulo Curso, COUNT(alunos.id) as 'Quantidade de Alunos' FROM `alunos` 
INNER JOIN cursos 
	ON alunos.curso_id = cursos.id GROUP BY cursos.titulo ORDER BY COUNT(alunos.id) desc;
```

---

### 10) Faça uma consulta que mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre os resultados classificados pelo nome do aluno.
```sql
SELECT alunos.nome Nome, alunos.primeiraNota 'NOTA 1', alunos.segundaNota 'NOTA 2', ROUND((primeiraNota + segundaNota)/2,2) as 'Média', cursos.titulo Curso FROM `alunos` 
INNER JOIN cursos 
	ON alunos.curso_id = cursos.id WHERE titulo ='Front-End' or titulo = 'Back-End' ORDER BY alunos.nome;
```
---

### 11) Faça uma consulta que altere o nome do curso de Figma para Adobe XD e sua carga horária de 10 para 15.

```sql
UPDATE cursos SET titulo = 'Adobe XD' WHERE id = 4;
UPDATE cursos SET cargaHoraria = 15 WHERE id = 4;
```

---

### 12) Faça uma consulta que exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI.

```sql
DELETE FROM alunos WHERE id = 10;
DELETE FROM alunos WHERE id = 11;
```

---

### 13) Faça uma consulta que mostre a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno.

SELECT alunos.nome as Nome, cursos.titulo Curso FROM `alunos` 
INNER JOIN cursos 
	ON alunos.curso_id = cursos.id ORDER BY alunos.nome;
---





