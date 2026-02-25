# Arquitetura - Modelo C4

## 1. Contexto

```plantuml
@startuml BibliotecaContext
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

Person(usuario, "Usuário", "Usuário que interage com o sistema")
System(sistemaGestao,"Sistema de Gestão de Biblioteca", "Sistema que gerencia o catálogo de livros e empréstimos")
System_Ext(servicoPagamento, "Sistema de Pagamentos", "Sistema externo para processamento de pagamentos")
System_Ext(servicoNotificacao, "Serviço de Notificações","Serviço externo para enviar notificacões")

Rel(usuario, sistemaGestao, "Usa")
Rel(sistemaGestao, servicoPagamento, "Processa pagamentos")
Rel(sistemaGestao, servicoNotificacao, "Envia notificações")

@enduml
```

## 2. Containers

```plantuml
@startuml BibliotecaContext
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

Person(usuario, "Usuário", "Usuário que interage com o sistema")
System(sistemaGestao,"Sistema de Gestão de Biblioteca", "Sistema que gerencia o catálogo de livros e empréstimos")
System_Ext(servicoPagamento, "Sistema de Pagamentos", "Sistema externo para processamento de pagamentos")
System_Ext(servicoNotificacao, "Serviço de Notificações","Serviço externo para enviar notificacões")

Rel(usuario, sistemaGestao, "Usa")
Rel(sistemaGestao, servicoPagamento, "Processa pagamentos")
Rel(sistemaGestao, servicoNotificacao, "Envia notificações")

@enduml
```

## 3. Componente

```plantuml
@startuml BibliotecaComponent
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Component.puml


Container(api, "API Backend", "Spring Boot", "API REST para funcionalidades de backend") {
    Component(controller, "Controladro REST", "Controlador Spring MVC", "Recebe requisições HTTP")
    Component(service, "Serviço", "Classe de Serviço", "Contém a lógica de negócio")
    Component(repository, "Repositório", "Interface JPA", "Gerencia operações de banco de dados")    
}

Rel(controller, service, "Chamada de Métodos")
Rel(service, repository, "Consulta ao BD")

@enduml
```

## 4.Código

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Deployment.puml

class Book {
    - String title
    - String author
    - Date publishedDate
    - boolean isAvailable

    + getTitle() : String
    + getAuthor() : String
    + getPublishedDate() : Date
    + checkAvailability() : boolean
}

@enduml
```