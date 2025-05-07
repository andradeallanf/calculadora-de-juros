# **Calculadora de Juros e Amortização**

Uma aplicação construída com **Java 17** e **Spring Boot** que calcula juros e amortização de empréstimos. O projeto utiliza um banco de dados **H2** em memória para armazenar informações e oferece uma API REST para realizar os cálculos.

---

## **Funcionalidades**

- **Cálculo de Juros e Amortização**
  - Calcular juros e amortização de empréstimos com base em parâmetros fornecidos
  - Gerar tabela de amortização com detalhes de cada período
  - Calcular saldo devedor, juros acumulados e valores de parcelas
  - Processar datas de pagamento e períodos entre datas

- **Tratamento de Exceções**
  - Validação de datas
  - Validação de valores de empréstimo
  - Validação de taxas de juros
  - Tratamento de erros de cálculo

---

## **Tecnologias Utilizadas**

- **Java 17**
- **Spring Boot 3.4**
  - Spring Web
  - Spring Data JPA
- **Banco de Dados**
  - H2 (em memória)
- **Swagger/OpenAPI**
  - Documentação interativa da API
- **Lombok**
  - Simplificação de código com geração automática de getters, setters e construtores
- **MapStruct**
  - Conversão entre entidades e DTOs

---

## **Configuração do Banco de Dados H2**

O banco de dados H2 está configurado para rodar em memória e pode ser acessado via console web.

### **Credenciais**
- **URL do Banco:** `jdbc:h2:mem:calculadora`
- **Usuário:** `sa`
- **Senha:** *(vazia)*

### **Acesso ao Console H2**
- URL: [http://localhost:8080/h2-console](http://localhost:8080/h2-console)
- **Driver Class:** `org.h2.Driver`
- **JDBC URL:** `jdbc:h2:mem:calculadora`
- **User Name:** `sa`

---

## **Endpoints Disponíveis**

### **Calculadora de Juros**

| Método | Endpoint                | Descrição                          |
|--------|--------------------------|------------------------------------|
| GET    | `/calculadora/calcular` | Calcular juros e amortização de empréstimo |

#### Parâmetros da requisição:
- `dataInicio` - Data de início do cálculo (formato: dd/MM/yyyy)
- `dataFim` - Data final do cálculo (formato: dd/MM/yyyy)
- `primeiroPagamento` - Data do primeiro pagamento (formato: dd/MM/yyyy)
- `valorEmprestimo` - Valor do empréstimo
- `taxaJuros` - Taxa de juros anual (%)

---

## **Como Executar o Projeto**

1. **Pré-requisitos:**
   - Java 17 instalado
   - Maven instalado

2. **Clone o Repositório:**
   ```bash
   git clone https://github.com/seu-usuario/calculadora-de-juros.git
   cd calculadora
   ```

3. **Compilar e Executar:**
   ```bash
   ./mvnw clean install
   ./mvnw spring-boot:run
   ```

   Ou no Windows:
   ```bash
   mvnw.cmd clean install
   mvnw.cmd spring-boot:run
   ```

4. **Acessar a Aplicação:**
   - A aplicação estará disponível em: [http://localhost:8080](http://localhost:8080)
   - A documentação Swagger estará disponível em: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

---

## **Exemplo de Uso da API**

### Calcular Juros e Amortização

**Requisição:**
```
GET /calculadora/calcular?dataInicio=01/01/2023&dataFim=31/12/2023&primeiroPagamento=15/01/2023&valorEmprestimo=100000&taxaJuros=5.5
```

**Resposta:**
```json
[
  {
    "dataCompetencia": "2023-01-01",
    "valorEmprestimo": 100000.0,
    "saldoDevedor": 100000.0,
    "consolidada": "",
    "parcela": 0.0,
    "total": 0.0,
    "amortizacao": 0.0,
    "saldo": 100000.0,
    "provisao": 0.0,
    "acumulado": 0.0,
    "pago": 0.0
  },
  {
    "dataCompetencia": "2023-01-15",
    "valorEmprestimo": 0.0,
    "saldoDevedor": 99166.67,
    "consolidada": "1/120",
    "parcela": 1291.67,
    "total": 0.0,
    "amortizacao": 833.33,
    "saldo": 99166.67,
    "provisao": 458.34,
    "acumulado": 0.0,
    "pago": 458.34
  },
  // ... outros períodos
]
```

---

## **Estrutura do Projeto**

```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── example/
│   │           └── teste/
│   │               └── calculadora/
│   │                   └── api/
│   │                       ├── Application.java
│   │                       ├── config/
│   │                       ├── controller/
│   │                       ├── dto/
│   │                       ├── exceptions/
│   │                       ├── service/
│   │                       └── util/
│   └── resources/
│       └── application.properties
└── test/
    └── java/
        └── com/
            └── example/
                └── teste/
                    └── calculadora/
                        └── api/
                            └── tests/
```

---

## **Contribuição**

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Faça commit das suas alterações (`git commit -m 'Adiciona nova feature'`)
4. Faça push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

---
