# 🧪 Urban.Grocers API Testing

## 📌 Project Overview

Projeto de testes de API REST desenvolvido para validação das novas funcionalidades do back-end do Urban.Grocers.

O **Urban Grocers** é uma aplicação baseada em API REST voltada para operações de e-commerce e delivery, permitindo gerenciamento de produtos, kits e serviços de entrega através de endpoints HTTP.

## 🎯 Objective
O principal objetivo é validar funcionalidades relacionadas a:

* Gerenciamento de kits
* Serviços de entrega Order and Go
* Regras de negócio da API
* Validação de status HTTP
* Tratamento de erros
* Limites de requisição




## 🚀 Tecnologias e Ferramentas

* Postman
* REST API
* JSON
* HTTP
* Jira
* Google Sheets




## 🔍 Funcionalidades Testadas

### 📦 Kits API

Endpoint:
POST /api/v1/kits/{id}/products

### Cenários testados:

* Adição válida de produtos
* Validação de payload
* Limite máximo de produtos
* Retorno de erros
* Status codes
* Boundary testing

---

### 🚚 Delivery API

Endpoint:
POST /order-and-go/v1/delivery

### Cenários testados:

* Disponibilidade do serviço
* Cálculo de entrega
* Campos obrigatórios
* Validação de endereço
* Requisições inválidas



## 📊 Bugs Encontrados e Impacto no Negócio

Durante a execução dos testes funcionais da API Urban.Grocers foram identificados 21 bugs relacionados à validação de dados, tratamento de exceções e regras de negócio da aplicação.


* Total de bugs reportados: 21
* Bugs críticos: 11
* Bugs médios: 7
* Bugs baixos: 3


## 🔴 Bugs Críticos

### Retorno de 500 Internal Server Error para entradas inválidas

Diversos cenários inválidos retornaram erro interno do servidor (`500 Internal Server Error`) em vez de mensagens controladas de validação (`400 Bad Request`).

### Casos identificados

* Letras latinas no campo ID
* Letras não latinas no campo ID
* Caracteres especiais no campo ID
* Campo ID vazio
* Número excessivamente longo no campo ID
* Letras no campo Quantity
* Caracteres especiais no campo Quantity
* Estrutura inválida do productsList
* Letras no parâmetro de URL
* Caracteres especiais no parâmetro de URL

---
### Impacto técnico

Esse comportamento indica falha no tratamento de exceções da API e ausência de validação adequada antes do processamento da requisição.

 O servidor está permitindo que entradas inválidas atinjam camadas internas da aplicação, causando falhas inesperadas.

---

### Impacto para o negócio

* Instabilidade da aplicação
* Redução da confiabilidade da API
* Maior risco de indisponibilidade do serviço
* Possível aumento de custos com suporte técnico
* Dificuldade de integração com sistemas externos

---
### Impacto para o usuário

Quando o sistema retorna erro 500, o usuário não recebe orientação adequada sobre o problema da requisição.

Isso prejudica diretamente:

* experiência de uso
* previsibilidade do sistema
* confiança na plataforma

Além disso, falhas internas podem interromper fluxos críticos da aplicação, impedindo o usuário de concluir operações corretamente.

---

## 🟠 Bugs Médios

### Falha na validação de regras de negócio

A API aceitou dados inválidos que deveriam ser bloqueados pela camada de validação.

### Casos encontrados

* IDs negativos aceitos
* Quantity negativa aceita
* Campo ID nulo aceito
* Quantity nulo aceito
* Body vazio aceito
* productsList vazio aceito
* Campo obrigatório ausente aceito

---

### Impacto técnico

Esses problemas demonstram inconsistência nas validações de entrada da API.

A ausência de validação adequada pode permitir gravação de dados inválidos e gerar inconsistências no sistema.

---

### Impacto para o negócio

* Dados inconsistentes no banco
* Problemas de integridade de informação
* Comportamentos inesperados em produção
* Aumento da complexidade de manutenção

---

## 🟡 Bugs Baixos

### Retornos HTTP inconsistentes

Alguns endpoints retornaram status HTTP incompatíveis com o comportamento esperado da operação.

---

### Impacto

Embora não interrompam totalmente a funcionalidade, esses problemas dificultam:

* monitoramento da API
* debugging
* integração entre serviços
* previsibilidade para aplicações consumidoras

---

## 📌 Conclusão

Os testes realizados permitiram identificar falhas importantes relacionadas à estabilidade, validação e tratamento de erros da API.

Os principais riscos observados estão concentrados em:

* tratamento incorreto de entradas inválidas
* ausência de validações críticas
* exposição de erros internos do servidor

A correção desses problemas é importante para garantir maior confiabilidade, estabilidade e qualidade da experiência do usuário.

# 🔗 Acesso ao Projeto

Todos os artefatos de teste foram documentados e estão disponíveis para revisão:

* Checklist de testes → [definição dos cenários](https://docs.google.com/spreadsheets/d/1tIppz-5Ph5_I9-ovggIraF98fUvIf60V/edit?gid=222111639#gid=222111639)
* Bugs reportados → [Jira](https://daniela-faustino.atlassian.net/browse/KAN-48)

Esses documentos refletem o processo completo de QA aplicado no projeto.

