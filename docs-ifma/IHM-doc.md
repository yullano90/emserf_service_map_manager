<h5 align="center">
</br>
<img src="https://user-images.githubusercontent.com/40738499/168456236-ce8aac11-ddb7-4dbb-a540-00c39e10927b.png" width="250px" />
</br></br></br></br>

DEPARTAMENTO DE COMPUTAÇÃO</br>
SISTEMAS DE INFORMAÇÃO</br>
</br>

[![interação_homem_máquina](https://img.shields.io/badge/Interação_Homem_Máquina-Profa%20Eveline%20Sá-blue.svg)](url)</br>
<!-- [![engenharia_de_software](https://img.shields.io/badge/Engenharia_de_Software-Prof%20Daniel%20Lima%20Jr-blue.svg)](url)</br> -->
</br>

<h4 align="center">
  RELATÓRIO TÉCNICO DE PROTOTIPAÇÃO E MODELAGEM DE USUÁRIO</br>
  SISGAM • SISTEMA DE GERENCIAMENTO DE ALERTAS DE MANUTENÇÃO </br>
 </h4>
</br></br></br></br>

<h5 align="center">
VERSÃO 1.0.0 • JUNHO 2022
 <br/><br/>
SÃO LUÍS, MARANHÃO </br>
</h5>
</br></br></br></br>

---

<h3 align="center">
  FICHA TÉCNICA </br>
 </h3>

**Equipe Responsável pela Elaboração**

DIEGO RODIRGO TEIXEIRA  • Product Design </br>
IULANO SILVA DOS SANTOS • Server-side </br>
ODIVAL QUARESMA NETO • Client-side </br>
</br></br>

## Demanda: 
 
Empresas de grande porte que trabalham com manutenção, logística, gerenciamento de estoque, etc, geralmente possuem sistemas de informação que geram alertas para suas equipes, seja para manutenção de equipamentos, seja para informar atualização de estoque, manutenções urgentes e etc.

Nesse contexto, temos o cenário da **EMSERF** *Empresa Maranhense de Serviços Ferroviários*, que já possui um **Sistema Core** que gerencia toda a organização, e este possui um endpoint para gerar alertas de manutenção e atualização de estoque por e-mail, todavia o banco de dados que informa os técnicos que recebem alerta é atualizado manualmente. Isso se deve ao fato da empresa ter feito apenas a aquisição do ***serviço de envio de alertas sem comprar a interface*** (que na ocaisão teria um custo bastante elevado), por conta desse desvio a equipe de operações passou a seguir o seguinte fluxo: 
O setor de manutenção manda um *"Planilhão de Excel"* semanalmente com a relação de técnicos, por conseguinte, também de forma manual, o Administrador de Banco de Dados escreve consultas SQL (INSERT/UPDATE/DELETE) diretamente na base de dados, com os técnicos que, de fato, devem receber os alertas. Isso gera desgaste, sujeição à falha humana e sobretudo impacto direto no SLA das demandas do time de desenvolvimento EMSERF.

Como MVP, temos a proposta do **SISGAM • Sistema de Gerenciamento de Alertas de Manutenção**. Reiteramos que, o SISGAM não substitui o SISCORE, ele é apenas uma **Aplicação Satélite** desenvolvida especialmente para automatizar o processo e reduzir custos de implementação do fabricante do SISCORE, conforme diagram abaixo:

<div align="center">
<img src="https://user-images.githubusercontent.com/40738499/175784007-abc51aea-0a5f-4a59-ba36-1ca939e0efbc.png" width="700px" />
	<p>Diagrama da Solução</p>
</div>

## Público Alvo:

Esta aplicação é destinada aos gestores e pontos focais da equipe técnica de Manutenção Ferroviária do cliente EMSERF, podendo estes usuários através de uma interface Web e em tempo real, definir quais profissionais devem receber alertas de manutenção em sua região de atuação.

---
#### Release vs_0.0.1 - São Luís - MA, 16 de Maio de 2022
#### Release vs_0.1.0 - São Luís - MA, 23 de Junho de 2022
#### Versão vs_1.0.0 - São Luís - MA, 27 de Junho de 2022
---
</br>

## Seção 1.
### Descrição das Histórias de Usuários:

Histórias de usuários são um dos principais componentes em Desenvolvimento Ágil de Software, uma vez que colocam as pessoas como peça-chave na hora de se pensar no design e funcionalidade de uma aplicação.
Essas histórias usam linguagem não-técnica para dar contexto à equipe de desenvolvimento e suas iniciativas.
Menor unidade de trabalho na estrutura do Desenvolvimento Ágil, é uma explicação informal e geral sobre um recurso de software, articulado na forma de uma única tarefa que pode oferecer valor ao cliente ou _stakeholder_ da aplicação em tela.
Segue abaixo algumas histórias de usuários relacionadas ao desenvolvimento da aplicação para o cliente EMSERF:
| Categoria      | Descrição                                                                                                                                                                                         |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  			 NOTIFICAÇÃO 		 |  			 Como usuário eu quero poder informar facilmente quando houver necessidade de manutenção. 		                                                                                                       |
|  			 NOTIFICAÇÃO 		 |  			 Como usuário eu quero alertar rapidamente uma necessidade de manutenção. 		                                                                                                                       |
|  			 INTERFACE 		   |  			 Como usuário eu quero poder detalhar o item, local e tipo de manutenção necessária. 		                                                                                                            |
|  			 API 		         |  			 Como administrador quero poder revisar e editar qualquer uma das entradas de alerta gerados pelos usuários. 		                                                                                    |
|  			 INTERFACE 		   |  			 Como usuário quero poder visualizar os alertas e os técnicos escalados para cada demanda. 		                                                                                                      |
|  			 NOTIFICAÇÃO 		 |  			 Como técnico eu quero receber notificação de alertas automaticamente via email. 		                                                                                                                |
|  			 INTERFACE 		   |  			 Como técnico quero poder acessar a plataforma e visualizar o alerta e seus detalhes. 		                                                                                                           |
|  			 INTERFACE 		   |  			 Como usuário gostaria de ter uma tela que oferece visão geral dos alertas e unidades onde os alertas estão alocados. 		                                                                           |
|  			 ACESSO 		      |  			 Como usuário gostaria de poder ter um login próprio para que eu possa ter a garantia de que as movimentações feitas por mim ficaram registradas com segurança. 		                                                                    |
|  			 RELATORIA 		   |  			 Como administrador gostaria que a aplicação gere relatórios com base em critérios específicos como tipos de alerta e unidades alocadas. 		                                                        | 		 |
|  			 RELATORIA 		   |  			 Como administrador gostaria de ter um recurso que permita exportar os relatórios como planilhas de Excel ou documentos .xml.                                             

---
## Seção 2.
### Definição de Personas:

A definição de personas é fundamental para determinar se o produto oferecido será bem sucedido ou se ajustes precisam ser feitos pra que um modelo transversal seja desenvolvido para os usuários, baseado em seus objetivos, tarefas, perfil, facilidade ou dificuldade com determinada habilidade, entre outras características. Com base nesse levantamento, utilizamos o padrão **PROTO PERSONA**, que é uma "engenharia reversa do nosso produto", onde analisamos o conteúdo do nosso sistema, os requisitos do cliente EMSERF, ambiente de trabalho dos usuários, tarefas executadas entre outros atributos. </br>
Vide abaixo as duas personas que melhor representam a essência de quem é nosso usuário do sistema:

	• PERSONA 1:
	Nome: Maria Joana
	Idade: 41 anos;
	Formação Acadêmica: Bacharel em Engenharia Mecânica;
	Status da Graduação: Concluídos;
	Cargo no setor: Técnico Especializado em Manutenção;
	Tempo na empresa: 21 anos;
	Localidade: Trabalha em São Luís, Maranhão;
	Conhecimento em TI: Essencial;
	

	• PERSONA 2:
	Nome: Paulo Alberto
	Idade: 19 anos;
	Formação Acadêmica: Bacharel em Sistemas de Informação;
	Status da Graduação: Em andamento;
	Cargo no setor: Estagiário de Programação;
	Tempo na empresa: 8 meses;
	Localidade: Trabalha em Santa Inês, Maranhão;
	Conhecimento em TI: Avançado;
	


---
## Seção 3.
### Aplicação do PACT Framework:

<h5 align="center">
<img src="https://user-images.githubusercontent.com/40738499/169849587-0486cf4a-2b98-4f85-a9ba-6639c6ccf1ab.png" width="800px" />
</h5>

### **PESSOAS:**

A aplicação é projetada para ser simples e interativa para o usuário final, tornando-se de fácil manuseio.</br>
Importante frisar que seu acesso é permitido apenas para colaboradores da empresa **EMSERF**, por ser uma aplicação de contexto estritamente interno e passivo de autenticação em rede corporativa.</br>
O sistema é desenvolvido para rodar apenas via browser, pois as pessoas que irão acessá-lo não ficam em campo, apenas em salas de monitoramento operacional, não impactando no processo ergonômico de suas demais atividades, com utilização semanal. Além disso, a aplicação também foi pensada para pessoas que eventualmente sejam portadoras de *daltonismo* através da aplicação de paleta de cores adequadas, sem agredir o padrão de identidade visual da marca EMSERF.

### **ATIVIDADES:**

**Vamos destacar atividades de nossos usuários, com base em funcionalidades chave do sistema, assim fica mais fácil mapear cada atividade impactada:**

**a) Login/Autenticação:** </br>
Funcionalidade que permite o acesso do usuário ao sistema, coletando dele e-mail corporativo e senha. Após a verificação e confirmação do usuário de forma transparente, o servidor da aplicação verifica credenciais e retorna um **token** via backend, que por conseguinte, libera a aplicação. O acesso é disponibilizado pela equipe de TI com uma senha padrão que é resetada (pelo próprio usuário) após primeiro login.

A partir de então essa atividade tende a ser realizada semanalmente, pois a definiçao dos técnicos e sedes para receber é feita sempre uma reunião que ocorre uma vez por semana com duração entre 20 e 40 minutos, por isso o uso do sistema não impacta nas outras atividades do ponto focal ou gestor.

Uma outra possibilidade de utilização são nas movimentações de emergência, que esporadicamente ocorrem, portanto de fato o ciclo de login na aplicação tende a ser semanal.

**b) Dashboard:** </br>
Uma vez autenticado, usuário acessa a rota default da aplicação, que é um *dashbord* simples contendo um grid de cards, com todas as sedes de manutenção da EMSERF e seus respectivos técnicos distribuídos em campo.

Nos baseamos no padrão Google Classroom, pois é um modelo de interface altamente intuitiva e muito simples, desta forma a experiência do nosso usuário tende a ser excelente, onde poderá cliclar é um cartão e ir até a sede que deseja para vincular ou desvincular profissionais para receber alertas.

**c) Detalhes da Sede:** </br>
Cada cartão possui um botão chamado "Detalhes da Sede", cujo clique redireciona para uma matriz de dados, contendo os técnicos daquela sede selecionada e as opções de vincular e desvincular profissionais.

**d) Menu Retrátil:** </br>
Fica disponível durante a navegação um Menu Lateral Retrátil, onde o usuário pode navegar facilmente entre páginas. Neste menu o usuário poderá:

Retornar ao *dashbord* assim que desejar;
Exportar a síntese das movimentações realizadas para um arquivo .csv;
Deslogar do sistema;

Esses recursos foram pensados não apenas por estética, mas sobretudo para otimizar o tempo do usuário, fazendo com que o mesmo não precise "pensar muito" no que vai clicar pra atingir determinado objetivo.

**e) Logout:** </br>
O usuário finaliza a sessão, podendo logar assim que desejar.

### **CONTEXTO:**

**Contexto Organizacional:**
O acesso de dados não possui classificação pois somente pontos focais e gestores acessam o sistema na mesma hierarquia de usuário.

**Contexto Social:**
Um sistema de fácil usabilidade, prático e por isso tutoriais e manuais não se fazem essenciais. Uma única explanação já deixa o usuário da área apto ao uso.

### **TECNOLOGIA:**

Durante o desenvolvimento do projeto é utilizada a tecnologia de edição gráfica **Figma**, largamente aplicada para prototipagem de projetos de design baseados principalmente no navegador web e aplicações mobile.

**Execução**:
- Os sistemas operacionais Windows, MacOS, diferentes versões do Linux, Docker entre outros podem executar a aplicação e qualquer browser popular incluindo internet explorer 8 ou superior, podem renderizá-la sem problemas de compatibilidade.

**Frontend e Backend**: 
Escolhemos a Stack Javascript para desenvolver o software, tanto do lado do cliente quanto do lado do servidor, pois é uma tecnologia estável, performática em browser, os frameworks Nodejs (Backend) e Reactjs (Frontend) possuem boa aprovação pelos times de governança de TI dos grandes players de Tecnologia em auditorias cibernéticas, além de ter o suporte de uma das maiores comunidades do planeta.

**Requisitos básicos para bom funcionamento:**
- 32GB de armazenamento ou Superior;
- 2GB de RAM ou superior;
- Processador Quad-Core ou Superior;
- Internet de 1 megabyte ou superior;

**Suporte e Tempo de Entrega da aplicação**:
A infraestrutura de TI é do próprio cliente EMSERF, e os Desenvolvedores fazem parte também do time de TI EMSERF, sendo assim torna-se mais fácil entender as dores e limitações do cliente, além disso o tempo estimado para desenvolver e entregar a aplicação está entre 08 a 12 semanas (dias corridos expurgando feriados), pois na esteira entram: Prototipagem, Reuniões com o cliente, Frontend, Backend (API), Testes de Estress da app, Testes de aceitação com o cliente, Conteinerização e Deployment do sistema em infratestrutura corporativa EMSERF.

**Dispositivos de Entrada:**  Dizem respeito a maneira como as pessoas irão inserir dados e instruções em um sistema de forma segura. No caso deste sistema, o uso dos dedos para o manuseio e seleção dos campos do sistema – login, senha, clique em cartões ou ícones, etc. Também é necessário o teclado físico ou virtual do PC/Notebook utilizado.

**Dispositivos de Saída:** Dizem respeito a maneira como o conteúdo será exibido para as pessoas interessadas. No caso desse sistema, haverá o uso da tela do monitor do PC ou Notebook para a visualização dos dados que serão mostrados de acordo com o manuseio do software.

**Consideração Importante**: *Quando o cliente EMSERF declara os requisitos, fica claro que nossa aplicação é do tipo "Satélite", ou seja, já existe um Sistema Core, que dispara os alertas, contudo a necessidade está em automatizar o processo de gerenciamento de usuários que de fato devem receber os alertas.*

---
## Seção 4.
### Lista de Requisitos:
Requisitos são solicitações e demandas que se espera de uma dada aplicação projetada. Os requisitos expressam de forma técnica e objetiva as propriedades que um _software_ exibe ou precisa exibir para satisfazer um objeto, comportamento ou atender um determinado objetivo.
Estes podem ser divididos em duas grandes categorias, a saber, __requisitos funcionais__ e __requisitos não funcionais__.

#### Requisitos Funcionais

Requisitos funcionais são a materialização de uma necessidade ou solicitação realizada pelo _software_. Estes descrevem os comportamentos básicos do sistema sob condições específicas, seus requisitos de funcionamento e restrições.
Segue abaixo os requisitos funcionais do sistema em tela:
| __RF001__                     | Recuperação de Senha                                                                                                                                                                                    |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                               | O sistema deve permitir que usuários mesmo recebendo acesso do time de TI, possam sempre que conveniente resetar sua senha e receber por email um código de confirmação.                                                                                                                                   |
|  			 __Ator:__                   | Usuário                                                                                                                                                                                           |
|  			 __Prioridade:__             | Importante                                                                                                                                                                                         |
|  			 __Entrada e pré-condições__ | Conexão com internet e banco de dados                                                                                                                                                             |
|  			 __Saída e pós-condições__   |  			 Request para o backend após validações retornar um código para validar a solicitação. 		                                                                                                                                                  |
|  			 __Fluxo de Eventos:__       | 1. O usuário com senha "esquecida" clica no botão para recuperação de senha; 				 2. O sistema solicita criação de uma id e senha; 				 3. O sistema dispara uma web request para o back-end, que envia para o email corporativo um código de recuperação de senha. 			 		 |


| __RF002__                     | Edição da grade de unidades                                                                                                                                                                                                                                                                                                     |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                               | O sistema deve permitir que administradores adicionem, editem ou deletem unidades da empresa em uma grade na tela principal.                                                                                                                                                                                                 |
|  			 __Ator:__                   | Administrador                                                                                                                                                                                                                                                                                                                |
|  			 __Prioridade:__             | Essencial                                                                                                                                                                                                                                                                                                                    |
|  			 __Entrada e pré-condições__ | Conexão com internet e privilégios de administração                                                                                                                                                                                                                                                                          |
|  			 __Saída e pós-condições__   | Modificação na configuração da grade de unidades                                                                                                                                                                                                                                                                             |
|  			 __Fluxo de Eventos:__       | 1. Administrador loga no sistema e vai para página principal; 2. Administrador clica no ícone de edição nos elementos que representam as unidades da empresa (dispostos em forma de grade); 3. Uma nova tela se abre oferecendo opções para editar detalhes numa unidade específica, há opção para deletar a unidade também. |


| __RF003__                     | Gerenciamento de usuários que devem receber alertas                                                                                                                                                                                                                               |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                               | O sistema deve permitir que usuários habilitados possam vincular ou desvincular gerenciando quem de fato deve receber alertas de manutenção.                                                                                                                                                              |
|  			 __Ator:__                   | Administrador                                                                                                                                                                                                                                |
|  			 __Prioridade:__             | Importante                                                                                                                                                                                                                                   |
|  			 __Entrada e pré-condições__ | Estar logado no sistema, ter um alerta aberto                                                                                                                                                                                                |
|  			 __Saída e pós-condições__   | Modificação em um alerta específico                                                                                                                                                                                                          |
|  			 __Fluxo de Eventos:__       | 1. O administrador seleciona uma unidade da empresa na tela principal; 2. Na listagem de técnicos da unidade escolhida ele pode então vincular ou desvincular técnicos na sede de manutenção selecionada e a partir de então o sistema core de alertas passa automaticamente a disparar alertas para o usuário vinculado a determinada sede, pois ele enxerga apenas o banco de dados, cumprindo assim o seu papel de "Aplicação Satélite". |


| __RF004__                     | Geração de relatório das movimentações realizadas                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                               | O sistema deve gerar relatório com arquivo pode ser impresso ou salvo em disco com extensão .csv, com as movimentações realizadas.                                                                                                                                                                                                                                                                                                                   |
|  			 __Ator:__                   | Usuário                                                                                                                                                                                                                                                                                                                                                                                                                |
|  			 __Prioridade:__             | Importante                                                                                                                                                                                                                                                                                                                                                                                                             |
|  			 __Entrada e pré-condições__ | Acesso ao sistema 		                                                                                                                                                                                                                                                                                                                                                                                                     |
|  			 __Saída e pós-condições__   | Um arquivo com extensão .pdf ou .csv		                                                                                                                                                                                                                                                                                                                                                                                     |
|  			 __Fluxo de Eventos:__       | 1. O usuário clica no ícone de "Export Excel" no Menu Lateral Retrátil; 2. O sistema executa método de exportação do array resultante das movimentações aplicadas. |

#### Requisitos Não Funcionais

Requisitos não funcionais por sua vez definem o que o sistema fará, como cada comportamento será realizado. São as próprias premissas e restrições técnicas de um projeto. Segue abaixo lista de requisitos não-funcionais do sistema em tela:

| __Id.:__ | NF001 |
|---|---|
| __Categoria:__ | Usabilidade |
| __Nome:__ | Uso de Design Responsivo nas interfaces gráficas |
| __Descrição:__ | As telas do sistema serão construídos para rodar em ambiente web e, portanto, devem possuir um design responsivo. A interface do sistema deverá se comportar de modo adequado independentemente de tamanho de tela ou configuração da janela – lembrando que o sistema deve ser utilizado na própria empresa, em desktop próprio da companhia. Ao longo do desenvolvimento serão realizados testes de usabilidade para validar este requisito. |
| __Prioridade:__ | Importante |

| __Id.:__ | NF002 |
|---|---|
| __Categoria:__ | Segurança |
| __Nome:__ | Autenticação de usuário |
| __Descrição:__ | As APIs do sistema podem ser acessadas por externamente pelos usuários, este acesso precisa ser seguro com autenticação em nível do servidor e em nível da aplicação. Para autenticação no nível do servidor o IP de cada usuário deve ser cadastrado no servidor web onde o sistema está hospedado. No nível da aplicação a autenticação deve ser realizada através de cadastro dos usuários, com login e senha próprias. A senha deve ser gravada e protegida por meio de um algoritmo de criptografia. |
| __Prioridade:__ | Essencial |

| __Id.:__ | NF003 |
|---|---|
| __Categoria:__ | Compatibilidade |
| __Nome:__ | Compatibilidade do sistema com navegadores |
| __Descrição:__ | Uma vez que o sistema é acessado via website, ele deve ser compatível com os principais navegadores – Firefox, Chrome, Internet Explorer e Edge. |
| __Prioridade:__ | Importante |

| __Id.:__ | NF004 |
|---|---|
| __Categoria:__ | Padrões |
| __Nome:__ | Divisão arquitetural do sistema em módulos |
| __Descrição:__ | O projeto do sistema deve ser orientado observando os princípios de design de desacoplamento e alta coesão, dividindo tanto quanto possível as responsabilidades entre suas diferentes partes. O projeto será arquitetado de forma modular, onde cada módulo contém apenas os algoritmos pertinentes à sua responsabilidade. |
| __Prioridade:__ | Essencial |


---

## Seção 5.
### Prototipação:

A criação do protótipo foi feita com a Tecnologia Figma, software recomendado pela professora Eveline Sá, onde pudemos gerar um modelo de Alta Fidelidade.

Os componentes IHC analisados e utilizados foram: 

**As primitivas:** 

- Arranjo ou layout onde focamos em proporcionar ao usuário um equilíbrio nas telas, distribuindo os elementos de forma balanceada;

- Fundos ou background onde optamos por fundos de telas e janelas com cores neutras, pensando em usuários com desvios visuais como o Daltonismo, Astigmatismo entre outros. Desta forma a aplicação possui dois temas:
- *Emserf Theme:* Paleta de cores brandes em referência a bandeira do Maranhão).
- *Dark Theme:* Cores mais escuras com paletas espefícas para daltônicos e pessoas com sensibilidade a luz.

**Diálogo:** 

- Ação onde o enfoque foi proporcionar ao usuário uma linguagem simples e objetiva e por ser um sistema satélite a resposta é bem rápida; 

**Objetos de Interação**: 

- Planos de fundo, primeiro plano, janelas e bordas bem definidas;

**Sistema de significados:** 

- Utilizamos ícones em várias partes da interface, reduzindo a máximo o volume de textos, tornando a comunicação limpa e sobretudo que usuário não tenha que "pensar muito" onde precisa clicar pra atingir determinado objetivo. Essa relação simbólica foi usada de forma simples e respeitando seus significados, visando uma interpretação clara, partindo do ponto que os ícones estão sujeitos a interpretações individuais de cada pessoa, e por conseguintes atribuimos a eles funcionalidades coerentes.</br>

</br>A ideia central do sistema foi desde o início conseguir transmitir ao usuário uma clara interpretação baseando-se pelos princípios de design que tratam sobre **Organizar e Comunicar**. 

Sobre a organização, visamos ter um layout de tela muito bem definido que conseguisse facilitar a vida do usuário, prezamos por uma boa navegalidade e foco na atenção. Com a comunicação, buscamos uma compreensão clara das ações do sistema, mostrando simplicidade, evitando densidade, ter objetividade e uma clara comunicação visual, utilizando ícones de fácil identificação e interpretação. 

O sistema tem um ótimo modelo conceitual, evitando que o usuário opere cegamente sem conseguir identificar o efeito de suas ações. Temos alguns *padrões em cada frame*, como: as paletas de cores visando dois fatores, abranger usuários com desvios visuais e cores que fizessem referência ao **Maranhão** e um menu lateral com a utilização de ícones de fácil interpretação, buscando uma melhor navegabilidade.

**1° Frame:** Uma interface limpa onde o nosso usuário tem acesso ao sistema
<div align="center">
<img src="https://user-images.githubusercontent.com/40738499/173443250-97f6e4d5-0fe5-4486-bf06-b5d775076ebc.gif" width="700px" />
</div>

**2° Frame:** Nessa nossa primeira tela pós login, temos uma interface com janelas buscando os seguintes princípios de design, boa navegabilidade e com bastante foco na atenção; bordas arredondadas visando um layout mais atual, aqui o usuário pode também ter um acesso a informações mais detalhadas de cada sede.

<div align="center">
<img src="https://user-images.githubusercontent.com/40738499/173443445-633714a1-1d59-4110-8f87-f8e04b7fd39d.gif" width="700px" />
</div>

**3° Frame:** Tela com uma comunicação buscando objetividade e simplicidade, nesse frame temos os técnicos alocados em cada sede e através de um ícone de fácil interpretação é possível realocar outros técnicos pra essa localidade.

<!-- <div align="center">
<img src="https://user-images.githubusercontent.com/84028669/173393823-c7b60715-8c00-4cac-9e13-bc41fcac23ae.jpeg"width="900px" />
</div> -->

**4° e 5° Frame:** Duas telas onde continuamos propondo um design simples, é mostrado a facilidade de compreenção das acões do sistema, possibilitando deletar apenas um técnico ou todos da sede, e um ícone de representatividade universal para significar o termo "deletar".

</br>
<div align="center">
<img src="https://user-images.githubusercontent.com/40738499/174424686-785f8635-d321-459f-bd25-1745c82395be.gif" width="900px" />
</div>

<!-- <div align="center">
<img src="https://user-images.githubusercontent.com/84028669/173394174-d355f65b-04e8-4e1b-93ad-2069dfe36abb.jpeg"width="900px" />
</div>
</br>
<div align="center">
<img src="https://user-images.githubusercontent.com/84028669/173394370-cd585cb4-5443-4b44-9d10-33ea8b705028.jpeg"width="900px" />
</div> -->


**6° Frame:** Nesse frame é onde o usuário tem uma visão geral sobre as alocações em cada sede, podendo exportar um documento em Excel ao final de suas ações no sitema.

<div align="center">
<img src="https://user-images.githubusercontent.com/40738499/174424704-b0edc611-7660-43e9-a4f4-40b10d1d791b.gif"width="900px" />
</div>
<br/>

---

## Seção 6.

### Pesquisa UX:

<a href="https://docs.google.com/forms/d/e/1FAIpQLSeNK915CZaDpIhgumv9YWdxGEW-oY90FjKTZW1briknAPw7pA/viewform"> **Formulário da Pesquisa** </a> <br/>
<a href="https://docs.google.com/forms/d/1uoUeZNKSXIeKx9c8seaA5VYIKzpwjhWXilgovIvwZgo/viewanalytics"> **Resultados da Pesquisa** </a> <br/>
Principais oportunidades de melhoria:
X, y, z...

---

## Seção 7.
### Protótipo Final:

<a href="https://www.figma.com/file/8nohgZFsrHimifrt5FvQzy/Projeto-EMSERF?node-id=0%3A1"> **Protótipo Melhorado** </a> <br/>
<a href="https://www.figma.com/proto/8nohgZFsrHimifrt5FvQzy/Projeto-EMSERF?node-id=5%3A2&scaling=contain&page-id=0%3A1&starting-point-node-id=5%3A2"> **Demo** </a> <br/>