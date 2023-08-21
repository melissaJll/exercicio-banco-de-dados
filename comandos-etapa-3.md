
## CRUD - Consultas


### 1) Alunos que nasceram antes do ano 2009

```sql
SELECT nome, dataNascimento FROM `alunos` WHERE dataNascimento < '2009-01-01';
```

---
### 2) Calculo da média das notas de cada aluno com duas casas decimais.

```sql
SELECT nome, ROUND((primeiraNota + segundaNota)/2,2) 'Média' FROM `alunos` GROUP BY nome;

```



---
### 3) Calculo do limite sendo 25% da carga horária. Em ordem crescente pelo título do curso.

```sql

SELECT titulo, cargaHoraria as 'Total de Horas' , cargaHoraria * 0.25 as 'Limite em hrs' FROM `cursos` ORDER BY titulo;

```



---
### 4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".

```sql
SELECT nome, areaAtuacao FROM `professores` WHERE areaAtuacao = 'desenvolvimento';
```



---
### 5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.

```sql

SELECT areaAtuacao as Area, COUNT(id) as 'Quantidade de Professores' FROM `professores` GROUP BY areaAtuacao;
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






