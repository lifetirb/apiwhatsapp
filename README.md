<h1 style="text-align: center"> Api Whatsapp Multi Usuário</h1>
<p style="text-align: center">
<a href="#"><img title="skynet" src="https://img.shields.io/badge/whatsapp api nodejs Multi Device-black?style=for-the-badge" alt=""></a>
</p>
<p style="text-align: center">
<a href="https://github.com/salman0ansari"><img title="Author" src="https://img.shields.io/badge/Author-Mohd Salman Ansari-black.svg?style=for-the-badge&logo=github" alt=""></a>
</p>
<p style="text-align: center">
<a href="https://github.com/salman0ansari/whatsapp-api-nodejs"><img title="Followers" src="https://img.shields.io/github/followers/salman0ansari?color=black&style=flat-square" alt=""></a>
<a href="https://github.com/salman0ansari/whatsapp-api-nodejs"><img title="Stars" src="https://img.shields.io/github/stars/salman0ansari/whatsapp-api-nodejs?color=black&style=flat-square" alt=""></a>
<a href="https://github.com/salman0ansari/whatsapp-api-nodejs/network/members"><img title="Forks" src="https://img.shields.io/github/forks/salman0ansari/whatsapp-api-nodejs?color=black&style=flat-square" alt=""></a>

---

Uma implementação de [Baileys](https://github.com/adiwajshing/Baileys/) como um serviço de API RESTful simples com suporte a vários dispositivos apenas `download`, `install` e `start` usando, `simples` assim.

# Bibliotecas usadas

-   [Baileys](https://github.com/adiwajshing/Baileys/)
-   [Express](https://github.com/expressjs/express)

# Instalação

1. Baixe ou clone este repositório.
2. Entre no diretório do projeto.
3. Execute `yarn install ou npm Install` para instalar as dependências.
4. Copia `.env.example` para `.env` e defina as variáveis ​​de ambiente.

# Docker Composer

1. Siga o procedimento de [Instalação](#instalação)
2. Atualizar `.env` e definir 
```
MONGODB_ENABLED=true
MONGODB_URL=mongodb://mongodb:27017/whatsapp_api
```
3. Defina seu `TOKEN=` para uma string aleatória.
4. Executar 
```
docker-compose up -d
```

# Configuração

Editar variáveis ​​de ambiente em `.env`

```a
Importante: Você deve definir TOKEN= como uma string aleatória para proteger a rota de inicialização.
```

```env
# ==================================
# CONFIGURAÇÃO DE SEGURANÇA
# ==================================
TOKEN=RANDOM_STRING_HERE
```

# Usar

1. `DEVELOPMENT:` Execute `yarn dev`
2. `PRODUCTION:` Execute `yarn start`

## Gerar instância básica usando chave aleatória

To generate an Instance Key  
Using the route:

```bash
curl --location --request GET 'localhost:3333/instance/init?token=RANDOM_STRING_HERE' \
--data-raw ''
```

Response:

```json
{
    "error": false,
    "message": "Initializing successfull",
    "key": "d7e2abff-3ac8-44a9-a738-1b28e0fca8a5"
}
```

## Generate custom instance with custom key and custom webhook

To generate a Custom Instance  
Using the route:

```bash
curl --location --request GET 'localhost:3333/instance/init?token=RANDOM_STRING_HERE&key=CUSTOM_INSTANCE_KEY_HERE&webhook=true&webhookUrl=https://webhook.site/d7114704-97f6-4562-9a47-dcf66b07266d' \
--data-raw ''
```

Response:

```json
{
    "error": false,
    "message": "Initializing successfull",
    "key": "CUSTOM_INSTANCE_KEY_HERE"
}
```

# Using Key

Save the value of the `key` from response. Then use this value to call all the routes.

## Postman Docs

Todas as rotas estão disponíveis como uma coleção de Postman.

-   https://documenter.getpostman.com/view/12514774/UVsPQkBq

## QR Code

Visit [http://localhost:3333/instance/qr?key=INSTANCE_KEY_HERE](http://localhost:3333/instance/qr?key=INSTANCE_KEY_HERE) to view the QR Code and scan with your device. If you take too long to scan the QR Code, you will have to refresh the page.

## Enviar Messagem

```sh
# /message/text?key=INSTANCE_KEY_HERE&id=PHONE-NUMBER-WITH-COUNTRY-CODE&message=MESSAGE

curl --location --request POST 'localhost:3333/message/text?key=INSTANCE_KEY_HERE' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'id=919999999999' \
--data-urlencode 'message=Hello World'
```

Veja todas as rotas aqui [src/api/routes](https://github.com/salman0ansari/whatsapp-api-nodejs/tree/main/src/api/routes)

# Observação
Não posso garantir ou ser responsabilizado se você for bloqueado ou banido ao usar este software. O WhatsApp não permite que bots usem métodos não oficiais em sua plataforma, portanto, isso não deve ser considerado totalmente seguro.

# Jurídico

- Este código não é de forma alguma afiliado, autorizado, mantido, patrocinado ou endossado pela WA (WhatsApp) ou por qualquer uma de suas afiliadas ou subsidiárias.
- O site oficial do WhatsApp pode ser encontrado em https://whatsapp.com. "WhatsApp", bem como nomes, marcas, emblemas e imagens relacionados, são marcas registradas de seus respectivos proprietários.
- Este é um software independente e não oficial Use por sua conta e risco.
- Não faça spam com isso.
