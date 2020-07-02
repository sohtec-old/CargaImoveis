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
            "Endereco":"XXXXX",
            "Numero":"000",
            "Complemento":"XXXXX",
            "Bairro":"XXXXX",
            "Cidade":"XXXXX",
            "Estado":"XXXXX",
            "Vagas":"1",
            "Dormitorios":"2",
            "UrlFoto":"http://www.dominio.com.br/foto.jpg",
            "UrlDetalheImovel":"http://www.dominio.com.br/detalhe/12345",
            "PrecoLocacao": 2400, //Requerido
            "PrecoVenda": 600000, //Requerido
            "ValorCondominio": 600,
            "ValorIptu": 800,
            "CaptadorNome":"Fulano",
            "CaptadorEmail":"xxxx@dominio.com.br",
            "ProprietarioNome":"Fulano",
            "ProprietarioEmail":"xxxx@dominio.com.br"
        }        
    ]
}
```

Se os dados estiverem ok o sistema retornará o seguinte JSON.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": null
}
```
