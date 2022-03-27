
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

* Aprendizado no que se trata uma API:

	*	Eu já havia feito Programação e Desenvolvimento de Sistemas em 2010 e quando comecei a estudar 
na Fatec, foi quando eu retornei aos estudos na área de programação. Com isso, mesmo com a minha
bagagem de experiência na área de Infra de Redes, o termo e o que é API foi algo bem complexo 
de entender e aplicar em prática. Foi algo muito divertido, envolvente e desafiador aplicar a
criação de API em nosso projeto.


* Aprendizado em trabalhar com requisições GET, PUT, POST e DELETE utilizando a linguagem Javascript:

	*	Após entender como era o funcionamento e como criava uma API no back-end, mais precisamente
utilizando o Django Rest Framework, criamos por meio do JavaScript as funções de requisições,
fazendo com que a gente conseguisse coletar, deletar, criar ou atualizar dados diretamente no 
banco de dados, utilizando credenciais de acesso da aplicação como segurança.
	
		Algumas das dificuldades que tive na criação da API, foi utilizá-la em servidores em nuvem, no qual foi necessário entender que era necessário utilizar parâmetros no cabeçalho para métodos de POST, DELETE E PUT para que a conexão fosse de fato estabelecida e confiável. Um exemplo desse cabeçalho em Javascript:
		
	![image](https://user-images.githubusercontent.com/62898187/139694311-3873a323-7f25-46ff-8aa6-a750737a0dd7.png)

	Com este cabeçalho configurado, foi possível hospedar a aplicação na nuvem e trabalhar normalmente.


* Aprendizado em HTML e CSS:

	*	Para quem nunca havia entrado no mundo de desenvolvimento Web, apenas Desktop, foi um desafio bem grande como era a criação de templates em HTML e utilizar CSS para dar estilo. Foi muito animador e muito prazeroso aprender sobre esse assunto e hoje eu utilizo muito para a criação de minhas aplicações profissionais e educacionais.

		Um dos desafios mais interessantes que eu enfrentei com o trabalho de desenvolver o Front-End, foi, sem dúvida, criar os projetos, inserir as tarefas nesse projeto e diferenciá-los com cores, para que fosse possível diferenciar um projeto do outro com uma maior facilidade. Um exemplo do código que foi utilizado para criar essa funcionalidade foi a função:

```javascript
1 function add_prj_menu_esquerdo(jsonprj){
2 document.getElementById("prj_cadastrados").innerHTML = ''; 
3 vetor_prjcadastrados = [];
4  
5 for(i = 0;i<json.length;i++){
6 /*CARREGA VETOR PARA CADASTRAR PROJETO NO MENU LATERAL ESQUERDO */
7 
8 //CRIA VALOR PARA ADICIONAR NA DIV "prj_cadastrados"
9 add_btn_prj_menu_esquerdo = [json[i]['prj_id'],"<div class='div_shadow' 
10 style='background-color:"+json[i]['prj_color']+"'><input id='cb_prj"+json[i]['prj_id']+"' 
11 type='checkbox' ><button id='btn_prj"+json[i]['prj_id']+"' 
12 onClick='expandeTrf(this.id);dadosProjeto(this.id);'class='btn_shadow0' style='background-
13 color:"+json[i]['prj_color']+"'>"+json[i]['prj_nome']+"</button></div> "];
14
15 //ADICIONA LINHA PARA CRIAÇÃO DO BTN DE PROJETO
16 vetor_prjcadastrados.push(add_btn_prj_menu_esquerdo);
17 ///////////////////
18 }
19 /*ENVIA PROJETO AO MENU LATERAL ESQUERDO*/
20
21 //ZERA DIV PARA NOVOS BUTTONS
22 document.getElementById("prj_cadastrados").innerHTML = ''; 
23
24 // VARREDURA DO VETOR CRIADO COM OS INSERTS PARA A DIV
25 for(i = 0; i<vetor_prjcadastrados.length;i++){ 
26	//ADICIONA OS INSERTS NA DIV 
27	 document.getElementById("prj_cadastrados").innerHTML +=  vetor_prjcadastrados[i][1];
28  //CRIA NOVA DIV PARA RECEBER TAREFAS CORRESPONDENTES AO PROJETO CRIADO
29	 novaDivTrf = document.createElement("div");
30  //NOME DA DIV PARA RECEBER AS TAREFAS
31	 novaDivTrf.id = "trf_cadastradas_prj"+vetor_prjcadastrados[i][0]+"";
32  //ADICIONA A DIV ABAIXO DO PROJETO CRIADO
33	 document.getElementById("prj_cadastrados").appendChild(novaDivTrf);
34 ////////////////////////////////// 
35 }
36  
37 //FUNÇÃO ABAIXO INSERE AS TAREFAS NO PROJETO SELECIONADO PASSANDO O JSON COMO PARÂMETRO
38 vetorTrfCadastrados(json, null); 
39 }	
```
Nesta etapa, é realizada a inserção das tarefas no projeto criado acima:
```javascript
1 /*EXPANDE TAREFAS MENU CENTRAL ESQUERDO*/
2 recebe_vetorprojeto = [];
3 recebe_vetortarefa = [];
4 ///FUNÇÃO ATRIBUÍDA PARA O BTN GRAVAR TAREFA
5 function vetorTrfCadastrados(vetor_projeto, vetor_tarefa){
6  vetor_trfcadastrados = [];
7  if(vetor_projeto != null){
8  recebe_vetorprojeto = vetor_projeto;
9  }
10 if(vetor_tarefa != null){
11 recebe_vetortarefa = vetor_tarefa;
12 }
13 if(recebe_vetorprojeto != '' && recebe_vetortarefa != ''){
14 for(i=0;i<recebe_vetorprojeto.length;i++){//VARREDURA NOS PROJETOS CADASTRADOS
15 recebeCodPrj = recebe_vetorprojeto[i]['prj_id'];  //SELECIONA O CODIGO DO PROJETO 
16 for(x=0; x<recebe_vetortarefa.length;x++){ //VARREDURA NAS TAREFAS CADASTRADAS
17 if(recebeCodPrj == recebe_vetortarefa[x]['fk_prj_id']){//VALIDA O CODIGO DO PROJETO DO CADASTRO DE PROJETO AO CODIGO DO PROJETO NO CADASTRO DE TAREFA E CRIA UM VETOR PARA INSERIR NA DIV CRIADA.
18  
19 codTrf = recebe_vetortarefa[x]['trf_id']; //CODIGO DA TAREFA - TABELA TAREFA
20  
21 recebeNomeTrf = recebe_vetortarefa[x]['trf_name']; //NOME DA TAREFA - TABELA TAREFA 
22 corProjeto = recebe_vetorprojeto[i]['prj_color']; //COR DO PROJETO - TABELA PROJETO 
23 add_btn_trf_menu_esquerdo = [recebeCodPrj,"<button id='btn_trf"+codTrf+"' onClick='dadosTarefa(this.id)' class='btn_shadow3' style='border-color:"+corProjeto+"'>"+recebeNomeTrf+"</button>"]; // CRIA LINHA PARA NOVOS BOTÕES DE TAREFAS, ABAIXO DO PROJETO CORRESPONDENTE
24  
25 vetor_trfcadastrados.push(add_btn_trf_menu_esquerdo);//ADICIONA NO VETOR AS TAREFAS CADASTRADAS E SEUS RESPECTIVOS BOTÕES, COM O ID DO PROJETO NO ÍNDICE 0 
26 } 
27 } 
28 }
29 //console.log(vetor_trfcadastrados);//VERIFICA INTEGRIDADE DO VETOR 
30 }
31 }	

```

Esta função expande o projeto criado, mostrando quais tarefas foram inseridas nele.
```javascript
1 ///FUNÇÃO ATRIBUÍDA PARA O BTN PROJETO NO MENU LATERAL ESQUERDO
2 function expandeTrf(nomeBtn){
3  
4  divideBtn = nomeBtn.substr(7);//REMOVE E DEIXA APENAS O NÚMERO DE IDENTIFICAÇÃO DO BOTÃO DE CADA TAREFA "btn_trf'num exemplo'"
5   
6  selecionaDiv = document.getElementById('trf_cadastradas_prj'+divideBtn+'').textContent;//SELECIONA A DIV DE CADA PROJETO E VERIFICA SE TEM CONTEÚDO DENTRO
7  if(selecionaDiv == ''){//CASO NÃO TENHA CONTEÚDO
8   
9  for(i=0;i<vetor_trfcadastrados.length;i++){//FAZ VARREDURA NOS BOTÕES DAS TAREFAS
10  
11  
12 if(divideBtn == vetor_trfcadastrados[i][0]){ //CASO O NÚMERO DE IDENTIFICAÇÃO DO BTN DA TAREFA SEJA IGUAL AO ID DE CADA PROJETO, É ADICIONADO O BOTÃO NA DIV CORRESPONDENTE
13  
14 document.getElementById('trf_cadastradas_prj'+divideBtn+'').innerHTML += vetor_trfcadastrados[i][1];//ADICIONA OS BOTÕES DAS TAREFAS NAS DIV'S DOS PROJETOS CORRESPONDENTES
15 } 
16 }
17 }else{
18 document.getElementById('trf_cadastradas_prj'+divideBtn+'').remove() //CASO TENHA CONTEÚDO NA DIV, ELE É ELIMINADO. ISSO FOI FEITO PARA CRIAR O RECUO.
19 add_prj_menu_esquerdo();//ADICIONA NOVAMENTE A DIV DO PROJETO
20 getAllProjects();
21 }
22 }
```
* Aprendizado em Django Rest Framework:

	*	Após entender o que era API e como uma API funcionava, era partir para a parte prática. Utilizamos o Django Rest Framework como Framework para a criação da API. Utilizamos como método de autenticação as credenciais de acesso da própria aplicação.

		O método de autenticação é configurado no arquivo settings.py do Django e a nossa configuração ficou da seguinte forma:
		![image](https://user-images.githubusercontent.com/62898187/139694944-7da04e01-480b-4467-a820-66e703fae2a2.png)

Com esta configuração, foi possível trabalhar tanto com autenticação da aplicação, quanto Token.

* Aprendizado em Models, Views e Templates do Django:

	*	O modelo MVC e MVT eram termos que eu ainda não conhecia que são termos do mundo de desenvolvimento de aplicações web. Ao estudar Django mais a fundo, descobri que é utilizado o modelo MVT, onde Model é utilizado para a criação de tabela em banco de dados, Views é utilizado para trabalhar com a "transmissão" e "recebimento" de dados com os templates (Front-End: HMTL; CSS; JS;)

* Aprendizado em implementação de dados do Django conectando ao banco de dados SQLite3:

	*	Foi entendido que o Django utiliza de drivers desenvolvidos em python para a conexão e administração do banco de dados através do Model do Django. Alguns deles seriam: Psycopg2; Pymongo; pyodbc; SqlLite;	
	![image](https://user-images.githubusercontent.com/62898187/139695726-cb2faff6-5c6b-4097-8c77-7db7df27ac90.png)
	Este é um exemplo de Connection String do Django para o SQLite3, no qual é criado um arquivo .sql na pasta do projeto.
 
		 ![image](https://user-images.githubusercontent.com/62898187/139696059-ee21c915-5fc4-43cd-9052-e2619ee98222.png)
Este é um exemplo de um model que foi criado em nosso projeto. O Django faz a conexão com o banco e cria automaticamente o model, com as colunas programadas de acordo com o que é passado no próprio model.

* Aprendizado no sistema operacional Linux com base Debian:

	*	Ao trabalhar com a linguagem Python e com o framework Django, entendi que era hora de desenvolver em ambiente Linux, no qual eu já era familiarizado por trabalhar com esse O.S. 

* Aprendizado em trabalhar em equipe utilizando a metodologia ágil SCRUM:
	
	* Como no projeto anterior, foi utilizado a metodologia SCRUM como metodologia ágil. Desta forma, conseguimos praticar ainda mais esta metodologia e aplicar novos conceitos. 
	
* Aprendizado em utilização de repositórios de código utilizando comandos do GIT:

	* Em todo o projeto, utilizamos do GitLab como repositório de arquivos. Com isso, praticamos ainda mais o seu uso e a sua aplicabilidade. 	

* Deploy Heroku:

	*	Para que pudéssemos publicar a nossa aplicação, utilizamos de uma plataforma gratuita Heroku, e que ainda temos ele de pé do servidor em nuvem: http://pi-gantt-planner.herokuapp.com

