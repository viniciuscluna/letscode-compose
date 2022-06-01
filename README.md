# **Aplicação de venda de cursos**

## **Projetos envolvidos**

 - *Sales* [viniciuscluna/letscode-venda (github.com)](https://github.com/viniciuscluna/letscode-venda)
 - *Product Catalog* [jmmoura/letscode-product-catalog (github.com)](https://github.com/jmmoura/letscode-product-catalog)
 - *Customer* [Sogolonmvj/e-commerce-customer-microservice (github.com)](https://github.com/Sogolonmvj/e-commerce-customer-microservice)
 - *Discovery* [viniciuscluna/letscode-discovery (github.com)](https://github.com/viniciuscluna/letscode-discovery)
 - *Gateway* [viniciuscluna/letscode-gateway (github.com)](https://github.com/viniciuscluna/letscode-gateway)
 - *Config* [viniciuscluna/annysantos-dev/e-commerce-letscode (github.com)](https://github.com/annysantos-dev/e-commerce-letscode/tree/master/config-server/config-server)

## **Participantes**
 - Sogolon Vieira <https://github.com/Sogolonmvj> 
 - Josiel Moura <https://github.com/jmmoura> 
 - Joseanny Santos <https://github.com/annysantos-dev> 
 - Vinícius Luna <https://github.com/viniciuscluna>

 ## **Arquitetura**

![Arquitetura do projeto](https://raw.githubusercontent.com/viniciuscluna/letscode-compose/main/img/Arquitetura-ECommerce.jpg)

## **Tecnologias utilizadas**
 - Spring Web
 - Spring Webflux
 - MongoDB
 - Postgresql
 - Kafka
 - MailDev
 - Docker
 - Eureka
 - Prometheus
 - Grafana
 - Spring Actuator
 -  Spring Security
 - Resilience4J
 - Api Gateway
 - Api Config
## **Objetivo do Projeto**

Uma aplicação para efetivar uma venda de curso. Para fins de aprendizagem trabalhamos com arquitetura de micro serviços nesse projeto juntamente com resiliência, mensageira e abordagem reativa. 

## **Como executar**

**É necessário docker instalado na máquina**

Com o terminal de sua preferência na raiz desse projeto, execute:

    docker-compose up

## **Como realizar uma venda**

Primeiramente é necessário cadastrar um usuário no sistema, um token será gerado e é necessário confirmar o email
Endpoint: 
`http://localhost:8080/api/user/create (POST):`

    Request
    {
	    "firstName":  "User",
		"lastName":  "Test",
		"cep":  "31400",
		"cpf":  "123.123.123-12",
		"email":  "test@gmail.com",
		"password":  "wHoKn05?"
	}

Para confirmar o email, basta acessar:
`http://localhost:1080`

Depois disso, precisamos cadastrar um produto:
Endpoint: 
`http://localhost:8080/api/product/create (POST):`

    Request
    {
	    "name":  "Curso Java",
	    "price":  "300",
	    "description":  "Full Stack",
	    "imageUrl":  "https://qualquer"
    }

Após isso, precisamos consultar a api de produto para descobrir seu id:
   Endpoint: 
`http://localhost:8080/api/product/(GET):`

Para efetivar a venda, seguimos o seguinte procedimento:

Endpoint: 

    http://localhost:8080/api/sale/ (POST)

Request:

    {
	    "email":"test@gmail.com",
	    "products":["qwerty"]
    }


## **Endpoints adicionais**

**User**

*Consulta por email*

	http://localhost:8080/api/user/test@gmail.com (GET)

*Consultar todos*

    http://localhost:8080/api/users (GET)

**Product**

*Consulta por id*

	http://localhost:8080/api/product/id (GET)

*Consultar todos*

    http://localhost:8080/api/product/ (GET)

**Sale**

*Consulta por id*

	http://localhost:8080/api/sale/id (GET)

*Consultar todos*

    http://localhost:8080/api/sale/ (GET)

## Sobre o Kafka

Utilizamos o kafka para realizar a baixa do produto quando a venda é finalizada.

## Observabilidade

Estamos utilizando o prometheus e grafana para observabilidade app é possível acessar os ambientes pelos seguintes links. Por meio dessas apps é possível realizar diversos filtros e configurações referente as aplicações.

Prometheus

	http://localhost:9090

Grafana 

     http://localhost:3000

