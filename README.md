
# Projeto Integrador 5º Semestre

## :orange_book: <b>Desafio do PI 5º Semestre:</b>

O desafio trazido pelos professores do 5º semestre de BD era trazer uma API com a finalidade de gerenciar cursos remotamente, com base no método que foi utilizado pela Fatec SJC durante a pandemia, através da plataforma Teams. Foi destacado a necessidade de tratar logs e demonstrá-los em gráficos, usando ETL e DW, como obrigatoriedade de matérias do semestre.

### Planejamento

Para fazer o planejamento foi utilizado a metodologia de "Design Thinking". Segundo o wikipedia, Design Thinking é o conjunto de ideias e insights para abordar problemas, relacionados a futuras aquisições de informações, análise de conhecimento e propostas de soluções.
O design thinking consiste em 5 partes ciclicas: empatia, definição, ideação, prototipo, teste.

-   A primeira etapa (empatia) do primeiro ciclo foi realizada junto ao cliente.
-   A etapa de definição é realizada durante as plannings do projeto.
-   A etapa de ideação e prototipo são realizadas durante a sprint e
-   A etapa de teste é realizada sempre que um prototipo vira funcionalidade através do fluxo de CI (continuous integration) e CD (continuous deploy/delivery) do projeto.

### Cronograma

-   16/08/2021 até 22/08/2021 - Kick Off do Projeto
-   30/08/2021 até 19/09/2021 - Sprint 1
-   20/09/2021 até 10/10/2021 - Sprint 2
-   18/10/2021 até 07/10/2021 - Sprint 3
-   08/11/2021 até 28/11/2021 - Sprint 4
-   29/11/2021 até xx/12/2021 - Sprint Apresentação Final
-   xx/xx/2021 até xx/xx/2021 - Sprint Feira de Soluções

<a name="backlog"></a>
### :memo: BACKLOG

### USER STORIES
Na descrição dos story cards, temos 4 personas: Aluno, Tutor, Gestor e Administrado.

- Como aluno, eu sou capaz de acessar o chat em tempo real para interagir/discutir com outros alunos e tutores;;
- Como tutor, eu sou capaz de acessar o chat do aluno para interagir/discutir com outros alunos;
- Como aluno, eu sou capaz de acessar o chatbot da plataforma para buscar orientações rápidas;
- Como aluno/tutor, eu sou capaz de acessar o sistema de LMS;
- Como gestor, eu sou capaz de adicionar/editar/excluir cursos;
- Como tutor, eu sou capaz de acessar um dashboard com painéis informativos específicos para tutoria;
- Como gestor, eu sou capaz de acessar um dashboard com painéis informativos específicos para gestão;
- Como administrador, eu sou capaz de acessar um dashboard com painéis informativos específicos para administração;

### Requisitos Funcionais

#### :black_medium_square: Sprint 1
<strong>1</strong> - Definir as tabelas FATO do Data Warehouse;

<strong>2</strong> - Definir as dimensões e granularidade do Data Warehouse;

<strong>3</strong> - Desenvolver um chat em tempo real com capacidade de até 1000 usuários simultâneos, capaz de gerar log das mensagens;

<strong>4</strong> - Definir ferramentas para o pipeline ETL;

#### :black_medium_square: Sprint 2

<strong>5</strong> - Criar rotinas ETL da plataforma e do chat para alimentar o DW;

<strong>6</strong> - Criar os dashboards OLAP com os indicadores requisitados;

####  :black_medium_square: Sprint 3

<strong>7</strong> - Definir os gráficos para visualização dos Dashboards;

<strong>8</strong> - Criar um sistema OLAP com visualizações (com dados de testes) diferentes para os 3 tipos de usuário (Tutor, Gestor e ADM);

<strong>9</strong> - Integrar o sistema OLAP com o Data Warehouse.

<strong>10</strong> - Reestruturar os logs da aplicação de acordo com as métricas esperadas no Data Warehouse ( Ativação, Engajamento, Desempenho, Participação, Avaliação de reação, Registro do tempo de participação no curso)

#### :white_medium_square: Sprint 4

<strong>11</strong> - Refatorar a plataforma de  LMS desenvolvida pela turma do 3º semestre de banco de dados (no primeiro semestre de 2021), para armazenar os dados dos logs em um banco de dados não-relacional;

<strong>12</strong> - Criar rotinas para carregar os dados no Data Warehouse.

### :white_square_button: Requisitos não Funcionais

- Documentação completa e clara
- Facilidade de uso
- Segurança
- Escalabilidade

# <b>:dart: Objetivo da Aplicação Nemosys - Remote Courses:</b>


Desenvolver uma solução de dados voltada ao ensino à distância para a gestão e oferta de conhecimento, dando suporte às mais diversas arquiteturas de aprendizagem, alinhado com os objetivos estratégicos a serem alcançados por cada organização que atendemos como clientes. Fazer a gestão de logs para alimentar um Data Warehouse afim de possibilitar a melhor gestão estratégica do negócio.

De acordo com o planejamento do time, foram levantadas as seguintes entidades:
 
- Cadastro de Alunos/Usuários;
- Cadastro de Disciplinas;
- Cadastro de Aulas;
- Cadastro de Cursos;
- Cadastro de Matrículas;
- Cadastro de Turmas;
- Cadastro de Notas;
- Registro de Login na plataforma;

A modelagem do Data Warehouse ficou da seguinte forma:

![image](https://raw.githubusercontent.com/api-fatec-bd/api/main/dw/untitled3.png)
Abaixo o fluxo da aplicação:

![image](https://raw.githubusercontent.com/api-fatec-bd/api/feature/sprint_03_atualiza%C3%A7%C3%A3o/.github/Fluxo%20da%20Aplica%C3%A7%C3%A3o.png)
#

## ⚙️ <b>Tecnologias Adotadas na Solução:</b>

-   Python - Para a criação do ETL foi definido pelo time a utilização da linguagem python, por ter fácil implementação com MongoDB e PostgreSQL;
- MongoDB - Foi utilizado para registrar os Logs da aplicação, onde posteriormente seriam tratados e enviados para o DW através do ETL;
- PostgreSQL - Foi utilizado devido à necessidade de ter um banco relacional para tratar tabelas de usuários, aulas, disciplinas e etc...
- RocketChat - Foi utilizado como chat nas aulas, para fácil comunicação entre alunos e professores;
- Docker - Para containerizar MongoDB e RocketChat;
- Data Studio - Para demonstrar o OLAP;
- Linux Ubuntu Server - Utilizado em 2 instâncias para manter as aplicações escaláveis e seguras. Foi utilizado o crontab do linux para criar rotinas de extração do ETL;

## :wrench: <b>Contribuições individuais/pessoais</b>

A minha contribuição neste projeto foi tratar o ETL, onde a meta era extrair dados do MongoDB, prepará-los de acordo com o planejado pela equipe de DW e carregá-lo em um banco relacional(PostgreSQL).

Inicialmente levantamos várias ferramentas de ETL, no qual algumas delas seriam: 

- Data Stage;
- Decision Streem;
- ETL Extract;
- OWB - Oracle Warehouse Builder;
- Apache Airflow;

Após os testes realizados em cada uma destas ferramentas, chegamos na conclusão de utilizar o Apache Airflow, mas era algo muito extenso e a nossa necessidade não era algo que necessitasse algo tão poderoso. 

Após alguns debates, planejamos "codar" o ETL na mão e através da linguagem Python.

Foram extraidos os Logs abaixo para o modelo dimensional:
- Dim Aula;
- Dim Curso;
- Dim Disciplina;
- Dim Turma;
- Dim Usuários;

Foram extraidos e implementados em tabelas fato os seguintes Logs:
- Acessos;
- Aluno presente nas aulas e quanto tempo;
- Registro de mensagens no chat e tempo de duração;
- Matriculas realziadas em determinado período;
- Notas de cada aluno e análise periódica;
- Login e Logout nos chats das aulas;


Inicialmente foram criadas as conexões com o MongoDB e PostgreSQL:

```python
def mongoConnection():

	mongo_conn = MongoClient('mongodb://157.245.243.16:3004/?retryWrites=false')
	return mongo_conn

def postgreeConnection():

	sql_conn = psycopg2.connect(host='157.245.243.16', database='PROJETO_API_NEMO',
	user='username', password='password')
	sql_conn.autocommit = True
	return sql_conn.cursor()
```

Posteriormente realizamos as extrações, tratamento e carregamento dos dados em destinos criados para o DW, como o código de exemplo abaixo:

```python
import sys
sys.path.append("..")
from connections import connections
from aux_functions import aux_functions
from datetime import datetime
import psycopg2

################################################################# INSERT FACT USUARIO CHAT #################################################################

def insertFactUsuarioChat(id_usuario_chat, id_usuario, id_chat, data_login, data_logoff, quantidade_mensagens, data_ultima_msg, tempo_participacao):
	try:
		connection = connections.conexaoBanco()
		cursor = connection.cursor()
		comando_insert = """ INSERT INTO fact_usuario_chat (id_usuario_chat, id_usuario, id_chat, data_login, data_logoff, quantidade_mensagens, data_ultima_msg, tempo_participacao) VALUES (%s,%s,%s,%s, %s, %s, %s, %s)"""
		values = (id_usuario_chat, id_usuario, id_chat, data_login, data_logoff, quantidade_mensagens, data_ultima_msg,
tempo_participacao)
		cursor.execute(comando_insert, values)
		connection.commit()
		print("INSERT FACT USUARIO CHAT OK: ", values)
		return "Usuario Chat inserido com sucesso!"
		except (Exception, psycopg2.Error) as error:
		print("Failed to insert record into mobile table", error)
		return error
	finally:
		if connection:
			cursor.close()
			connection.close()
		  print("PostgreSQL connection is closed")

##########################################################################################################################################################

# CRIAR FILTRO PARA ALIMENTAR TABELA FACT_USUARIO_CHAT

"""""""""

Campos: ID_USUARIO_CHAT; ID_USUARIO; ID_CHAT; DATA_LOGIN; DATA_LOGOFF; TEMPO_PARTICIPACAO; DATA_ULTIMA_MSG; QUANTIDADE_MENSAGENS;

"""""""""

def filtroFactUsuarioChat():
		collection_usuarios = connections.mongoConnection()['Logs']['Usuario'].find()
		collection_message = connections.mongoConnection()['rocketchat']['rocketchat_message']
		id_usuario_chat = 0
		for usuario in collection_usuarios:
			mensagens_usuario = list(collection_message.find({'username': usuario['USERNAME'], "etl": {'$exists': False}}))
			#print("mensagens_usuario: ", mensagens_usuario)
			#PRIMEIRA MENSAGEM; ULTIMA MENSAGEM, TEMPO DURACAO; DA ROOM SELECIONADA NO USUÁRIO SELECIONADO
			salas = ["GENERAL", "SALA2", "SALA1"]
			for sala in salas:
				print("Sala: ", sala)
				vetor_mensagensPorSalaUsuario = []
				for mensagemUsuario in mensagens_usuario:
					print("SalamensagemUsuario: ", mensagemUsuario['rid'])
					if mensagemUsuario['rid'] == sala:
						vetor_mensagensPorSalaUsuario.append(mensagemUsuario)
					else:
						None
		if vetor_mensagensPorSalaUsuario != []:
			print("Teste vetor_mensagensPorSalaUsuario: ", vetor_mensagensPorSalaUsuario)
			id_usuario_chat = id_usuario_chat + 1
			data_login = datetime.strptime(vetor_mensagensPorSalaUsuario[0]['_updateAt'], '%d-%m-%Y %H:%M:%S')
			data_logoff = datetime.strptime(vetor_mensagensPorSalaUsuario[-1]['_updateAt'], '%d-%m-%Y %H:%M:%S')
			tempo_participacao = (data_logoff - data_login).total_seconds() / 60
			tempo_participacao = "{:.2f}".format(tempo_participacao)
			# QUANTIDADE DE MENSAGENS
			quantidade_mensagens = len(vetor_mensagensPorSalaUsuario)
			print("data_login: ", data_login)
			print("data_logoff: ", data_logoff)
			print("tempo_participacao: ", tempo_participacao)
			print("quantidade_mensagens: ", quantidade_mensagens)
			print("sala: ", vetor_mensagensPorSalaUsuario[0]['rid'])
			result = insertFactUsuarioChat(id_usuario_chat, usuario['IDUSUARIO'], vetor_mensagensPorSalaUsuario[0]['rid'],
			data_login, data_logoff, quantidade_mensagens, data_logoff, tempo_participacao)

			for mensagemPorSala in vetor_mensagensPorSalaUsuario:
				# INSERÇÃO DA FLAG 1 PARA DADO INSERIDO CORRETAMENTE E FALHA 0
				_id = mensagemPorSala['_id']
				if result == "Usuario Chat inserido com sucesso!":
					aux_functions.atualizaFlag(_id, 'rocketchat', 'rocketchat_message', 1)
				elif "duplicate key value violates unique constraint" in str(result):
					aux_functions.atualizaFlag(_id, 'rocketchat', 'rocketchat_message', 1)
				else:
					aux_functions.atualizaFlag(_id, 'rocketchat', 'rocketchat_message', 0)

filtroFactUsuarioChat()
```

## 🧠 <b>Aprendizados Efetivos</b>

* Aprendizado sobre ETL e Data Warehouse: Neste projeto foram divididos times que iriam ficar com determinadas tarefas para a conclusão do projeto, mas ao mesmo tempo auxiliando outros times caso tivessem problema. Devido eu ter ficado com a parte de ETL, foi possível entender como é feito o processo e criação, desde a extração dos dados até o preparo e envio para a equipe de DW. Tivemos a matéria de DW e isso auxiliou muito no aprendizado. Aprendemos diversas ferramentas de ETL, e também a criação de um ETL do zero através da linguagem Python. Foi possível aprender sobre task scheduler, no qual é utilizado para ser como um gatilho de funções da aplicação, com horários e dias pré-definidos.

* Aprendizado com MongoDB: Particularmente já havia trabalhado com MondoDB em outros projetos, porém, desta vez, foi pensando em extração e tratamento de Logs, onde é preciso criar uma análise bem feita para que a informação passada não seja incorreta. Agregou muito em minhas skills, pois trabalho como SysAdmin e a vivência com Logs é bem alta.

* Aprendizado em Data Warehouse: Devido ao contato com a equipe de DW, foi possível aprender muito sobre as tabelas Dimensão e tabelas Fato. Acrescentou muito no conhecimento e que isso iria melhorar o conhecimento em OLAP. 

* Testes unitários: Como parte das requisições de entrega, era necessário criar os testes unitários, onde foi possível aprender sobre TTL.

