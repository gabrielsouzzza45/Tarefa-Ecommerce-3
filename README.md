# E-commerce — Projeto 3

Projeto de E-commerce desenvolvido com Node.js, TypeScript, Express, Prisma e InversifyJS.

Nesta etapa, a aplicação utiliza Docker Compose para executar a API e o banco de dados PostgreSQL em containers.

## Como rodar

Pré-requisitos

Docker instalado.

Docker Compose disponível.

1. Configurar o ambiente

Clone o repositório e entre na pasta do projeto.

Crie o arquivo .env a partir do exemplo:

```bash
cp .env.example .env
```

2. Iniciar a aplicação
```bash
docker compose up --build
```

O próprio comando npm start, executado pelo Dockerfile, realiza a criação das tabelas, o cadastro inicial dos produtos e a inicialização do servidor.

Após a inicialização, a API estará disponível em:

http://localhost:3000

### Como testar

Os testes podem ser realizados utilizando PowerShell, Postman ou Insomnia. Teste com:

Testando a API com Insomnia

Os testes da API podem ser realizados pelo Insomnia, uma ferramenta que permite enviar requisições HTTP e visualizar as respostas.

Com os containers em execução (docker compose up --build), siga os passos abaixo:

Abra o Insomnia e crie uma nova requisição.

Selecione o método POST.

Utilize a URL:

http://localhost:3000/orders

Na aba Body, selecione JSON.

Insira os dados do pedido no formato esperado pela API.

```bash
{
  "customer": "cliente@teste.com",
  "items": [
    {
      "productId": 1,
      "quantity": 1
    }
  ],
  "paymentMethod": "pix"
}
```

Clique em Send e verifique a resposta.

2. Consultar um pedido pelo ID

Crie uma nova requisição no Insomnia.

Selecione o método GET.

Utilize a URL, substituindo ID_DO_PEDIDO pelo ID retornado na criação:

http://localhost:3000/orders/ID_DO_PEDIDO

Ou seja, se o por exemplo o IDorder do pedido for 1, utilize:

http://localhost:3000/orders/1 para ver o primeiro pedido.

Clique em Send.

Verifique se a API retorna os dados do pedido correspondente.

3. Testar um pedido inexistente

Crie outra requisição com o método GET.

Utilize uma URL com um ID que não exista:

http://localhost:3000/orders/999999

Clique em Send.

Verifique se a API retorna o status 404 Not Found.

## Estrutura

```
src/
├── container/      # Configuração das dependências
├── domain/         # Entidades e regras de negócio
├── repositories/   # Interfaces e implementações dos repositórios
├── providers/      # Provedores de serviços
├── payments/       # Formas de pagamento
├── services/       # Regras de negócio
├── controllers/    # Controle das requisições HTTP
└── app.ts          # Configuração das rotas
```

---

