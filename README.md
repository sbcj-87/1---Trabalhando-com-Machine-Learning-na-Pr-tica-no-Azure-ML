# 1---Trabalhando-com-Machine-Learning-na-Pr-tica-no-Azure-ML

# Trabalhando com Machine Learning na Prática no Azure ML

Passo a passo do projeto Trabalhando com Machine Learning na Prática no Azure ML da DIO.

Links importantes:

- [Explore Azure AI Services](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/02-content-safety.html)
- [Explore Automated Machine Learning in Azure Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)
- Fonte dos dados: [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals) ou [dados](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/main/data/ml/daily-bike-share.csv)

## Passo 1: Criando recurso do Azure Machine Learning

Primeiro criei um recurso de Machine Learning. Para isso, cliquei em "Criar recurso" e depois pesquisei por Azure Machine Learning no marketplace. Após identificar o recurso, criei.

![Img](./imgs/img1.gif)

## Passo 2: Configurando o recurso do Azure Machine Learning

Na aba de Noções básicas, Detalhes do recurso, informei a assinatura para cobrança no campo Assinatura e depois informei o Grupo de recursos que vai englobar o recurso que será criado.

Após, em Detalhes da área de trabalho, informei os tais detalhes do workspace que será criado. Como foi um lab, as configurações foram mínimas. Por fim, foi criado o recurso clicando em Consultar + criar. Após a validação ser aprovada, cliquei em "Criar".

![Img](./imgs/img2.png)

Após o recurso ser criado, cliquei no botão "Ir para o recurso" para poder acessar a página do recurso.

![Img](./imgs/img3.png)

Nessa página, existe o botão "Iniciar o estúdio" que me redirecionou para a página de estúdio do Azure Machine Learning.

![Img](./imgs/img4.png)

## Passo 3: Criando o modelo

No estúdio, na página do workspace criado de antemão, acessei a opção do menu ML automatizado e na página aberta, cliquei na opção "Novo trabalho de ML automatizado".

![Img](./imgs/img5.gif)

Em "Configurações básicas", foi preenchido os campos "Nome do trabalho", "Novo nome do experimento" e "Descrição". Após isso, cliquei em "Avançar".

No passo "Tipo de tarefa e dados", foi selecionado o tipo de tarefa como Regressão e logo após, em "Selecionar dados", cliquei em "Criar". No modal aberto, em "Tipos de dados", foram preenchidos os campos "Nome", "Descrição" e escolhi "Tipo" como Tabular. Cliquei em "Avançar" e no passo "Fonte de dados", foi escolhido "De arquivos da Web" e cliquei em avançar.

No passo "URL da Web", informei o endereço [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals) do conjunto de dados. No passo "Configurações", foram preenchidas as configurações do conjunto e após avançar para "Esquema", foi verificado os tipos de dados. Finalmente, ao avançar, verifiquei as configurações criadas para o ativo de dados e cliquei em criar.

![Img](./imgs/img6.gif)

Em "Configurações de tarefas", foi escolhido o conjunto de dados importado. Após, em "Coluna de destino" escolhi a coluna `rentals` como target.

Nos campos de "Limite", preenchi com os valores abaixo e marquei "Habilitar encerramento antecipado".

![Img](./imgs/img7.png)

Em "Validar e testar", em "Tipo de validação" foi escolhido "Divisão de validação de treinamento".

Ao avançar, em Computação, mantive os valores demostrados na imagem abaixo.

![Img](./imgs/img8.png)

Após avançar e examinar as configurações do trabalho, cliquei em "Enviar trabalho de treinamento".

Após finalizar o trabalho de treinamento, precisei criar um modelo. Para isso, acessei a página do trabalho realizado e cliquei em "Modelo de registro". Deixei as opções padrões para "Selecionar saída". Em "Configurações do modelo", somente foi preenchido o nome e a versão. Após isso, cliquei em criar o modelo.

![Img](./imgs/img12.gif)

Por fim, o modelo fica acessível na opção de menu "Modelo".

![Img](./imgs/img9.png)

## Passo 4: Métricas do modelo

Para acessar as métricas do modelo treinado, na página do modelo, acesso o link informado em "Criado por trabalho". Também é possível acessar o trabalho informado na opção do menu chamado "Tarefas (jobs)".

Na página da tarefa, foi acessado a aba métricas.

![Img](./imgs/img10.gif)

## Passo 5: Teste do modelo

Na página do modelo, foi acessado a aba "Pontos de extremidade" e em seguida cliquei em "Implantar". Porém, por algum motivo o botão não funcionou. Então, para criar o ponto de extremidade para esse modelo, acessei "Pontos de extremidade" no menu lateral, e cliquei em "Criar". Em seguida marquei o modelo e deixei todos os campos seguintes como os valores padrões, exceto "Contagem de instâncias" que deixei como 1. Então cliquei em "Implantar".

![Img](./imgs/img13.gif)

Logo após a implantação, que demora em média de 9 a 10 minutos, acessei a aba "Testar" do ponto de extremidade criado para o meu modelo.

Para o teste, utilizei o json abaixo:

```json
{
  "input_data": {
    "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]
  }
}
