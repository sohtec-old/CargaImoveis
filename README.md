# Carga de Imóveis
API responsável em enviar a carga dos imóveis para a SOHTEC

### Login
Url: https://sohtec.com.br/services/api/login

Com a **chave(key)** do cliente fornecida pela SOHTEC siga os passos abaixo.

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
Content-Type: application/json
```

Enviar o json abaixo:
```javascript {.line-numbers}
{
  "key":"KEY_DO_CLIENTE"
}
```

Você receberá um retorno de um token, ele tem validade de **10 minutos** a partir da obtenção do mesmo, ou seja, sempre que for necessário repita a chamada no Login para renovar o token.
```javascript {.line-numbers}
{
    "token": "xxxxxxxxxxxxxxxxx"
}
```

### Adicionar Imóveis
Url: https://sohtec.com.br/services/api/AdicionaImoveis

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar o json abaixo via **POST** 
```javascript {.line-numbers}
{
    "Imoveis":[
        {            
            "Codigo":"0001", //Requerido
            "TipoImovel":"Apartamento",
            "Endereco":"Av. Fiqueiredo",
            "Numero":"530",
            "Complemento":"Casa 6",
            "Bairro":"Centro",
            "Cidade":"Porto Alegre",
            "Cep":"00000-000",
            "Estado":"RS",
            "Vagas": 1,
            "Dormitorios": 2,
            "UrlFoto":"http://www.dominio.com.br/foto.jpg", //Primeira foto do imóvel se existir.
            "UrlDetalheImovel":"http://www.dominio.com.br/detalhe/12345",
            "PrecoLocacao": 2400, //Requerido
            "PrecoVenda": 600000, //Requerido
            "ValorCondominio": 600.50,
            "ValorIptu": 830.20,
            "CaptadorNome":"Fulano",
            "CaptadorEmail":"xxxx@dominio.com.br",
            "ProprietarioNome":"Fulano",
            "ProprietarioEmail":"xxxx@dominio.com.br"
        }        
    ]
}
```
**Obs:** E-mails não formatados corretamente serão desconsiderados e não vinculados a captadores e proprieários. 

Se os dados estiverem ok o sistema retornará o seguinte JSON.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": null
}
```

### Ativar um imóvel dentro da SOHTEC
Url: https://sohtec.com.br/services/api/AtivarImoveis

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar o json abaixo via **POST** 
```javascript {.line-numbers}
{
    "Imoveis":[
        {
            "Codigo":"0002",
            "Finalidade":"LOCACAO"
        }
    ]
}
```

### Desativar um imóvel dentro da SOHTEC
Url: https://sohtec.com.br/services/api/DesativaImoveis

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar o json abaixo via **POST** 
```javascript {.line-numbers}
{
    "Imoveis":[
        {
            "Codigo":"0002",
            "Finalidade":"LOCACAO"
        }
    ]
}
```
