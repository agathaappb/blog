---
title: "Vamos falar sobre MVVM ?"
datePublished: Fri Jul 05 2024 01:51:35 GMT+0000 (Coordinated Universal Time)
cuid: cly81i0ma00020al78yom3zy9
slug: vamos-falar-sobre-mvvm
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720144202943/d2326178-f038-479f-92cc-faa417fade6d.png
tags: android, mvvm

---

Em sua jornada como mochileiro android, é importante conhecer as principais arquiteturas e como elas funcionam, o que elas agregam de valor para o seu projeto, seja ele de estudos ou no seu dia-a-dia dentro da empresa em que trabalha.  
Vamos começar do básico, pelo próprio nome você já sabe que essa arquitetura é separada por três camadas: Model, View e ViewModel, certo?

![Desenho - MVVM](https://github.com/agathaappb/blog/blob/main/img/MVVM/Desenho_MVVM.png?raw=true)

Existem dois pontos que valem a pena destacar de ganhos dessa arquitetura para desenvolvimento de aplicativos nativos android, que são: persistência de estado e testabilidade.

## View 🧐
Quem viu, viu, quem não viu não vê mais 😁
Deixando a brincadeira de lado, o nosso componente de View é a camada de apresentação, ou seja, é a tela que vai visualizar e interagir no app. 

## Model 🧐
Essa é a sua camada de dados e lógica de negócios, simples assim, ela pode fornecer dados remotos, locais ou até mesmo mocks. 

## ViewModel 🤩
Essa é a camada intermediária entre a view e a model, ou seja, ela é a responsável por solicitar para a camada de model os dados, para a viewmodel não importa de onde a cama de model vai buscar esses dados, ele só se preocupa com os valores retornados p ele; pois quando tiver os valores solicitados ele consegue nofiticar todos os seus ouvintes e atualiza-los de que teve alteração nesses dados. 

Ainda não entendeu? 🤔
Então vamos por partes explorar ainda mais essa camada, pois ela é a
camada intermediária que veio para resolver os seus problemas, pequeno gafanhoto! 😁

### 1º Ponto - Não tem referência view 😶‍🌫️

O ViewModel não tem nenhuma referência da camada de view (camada de UI), ele processa a regra de negócio internamente e devolve os dados a quem estiver ouvindo. Não fazer referência a view tem um ganho para os testes unitários, já que não precisamos lidar com ciclo de vida da view ou componentes nativos, aí o foco fica totalmente na regra que está sendo validada naquele cenário de teste. 

### 2º Ponto - Ciclo de vida 👀
Essa camada é potente, ela tem seu próprio ciclo de vida e não está atrelado ao ciclo de vida da activity; com isso, se ocorrer da activity ser recriada, como no caso de uma rotação de tela por exemplo, o ciclo de vida do viewmodel é mantido. Mas tudo que é bom, pode ficar ainda melhor, lembra que comentei que o viewmodel devolve os dados a quem estiver ouvindo? pois bem, isso é possível quando o viewmodel tem um aliado que é o design pattern chamado observer. 

### 3º Ponto - Observadores  🕵🏻
Mas como isso é possível?
Na verdade isso é bem legal, dentro do viewModel, podemos ter uma variável do tipo LiveData, como o próprio nome diz, ela é um dado vivo, e com isso pode ser observada. Isso é como um sistema pub-sub, temos um ouvinte que se registra para receber as notificações e do outro lado quem vai notificar. 

[Click aqui e saiba mais sobre o pattern Observer no Refactoring Guru](https://refactoring.guru/pt-br/design-patterns/observer)

### 4º Ponto - Persistencia de estados 🤔
Os pontos dois e três trazem grandes ganhos de persistencia de estados dos dados exibidos em tela, já que a activity podendo ser recriada, isso não altera em nada o ciclo de vida do viewmodel, mas como nem tudo são flores, e se o ciclo de vida do viewmodel for recriado.👀
 
E agora, quem poderá nos salvar ? ou melhor dizendo, quem poderá salvar os dados do viewmodel? 

![Chapolin Colorado](https://github.com/agathaappb/blog/blob/main/img/MVVM/ChapolinAstuciaGIF.gif?raw=truer)

Brincadeiras a parte, podemos salvar os dados do viewmodel utitlizando o SavedStateHandle; com ele podemos salvar vários tipos de dados do viewmodel em um formato de chave valor e recuperá-los novamente depois. 

### ✨Bonus do viewModel!!! 🎉✨
O viewmodel tem uma flexibilidade que antes com o padrão MVP não existia, no MVP tínhamos a relação de 1 para 1, uma camada de View para uma de Presenter; mas no MVVM temos a relação de 1 para muitos, ou seja, podemos ter várias views relacionada com um ViewModel e isso traz alguns pontos bem interessantes a nível de projeto já que podemos reutilizar um método de um viewModel específico em várias views sem precisar ficar replicando aquele método em várias partes do projeto. 


# Projeto  🚀
Em construção...🚧






