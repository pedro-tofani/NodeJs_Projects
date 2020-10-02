# POST localhost:3001/user/login
* Login do usuário

# POST localhost:3001/user/register
* Registrar novo usuário

# GET localhost:3001/products
* Todos os produtos

# PATCH localhost:3001/user/profile
* Atualizar o nome do usuário.

# POST localhost:3001/products/checkout
* Criar o pedido.

# GET localhost:3001/user/Orders
* Todos os pedidos do usuário.

# GET localhost:3001/user
* Informações de usuário.

# GET localhost:3001/orders/:id
* Detalhe específico de uma receita.

# GET localhost:3001/orders/admin
* Todos os pedidos. Privilégios de admin.

# GET localhost:3001/orders/admin/:id
* Detalhes específicos de um pedido. Privilégios de admin.

# PATCH localhost:3001/orders/admin/:orderId/delivered
* Trocar o status de uma entrega para entregue

--------------------------------------------------------------------------------------------------------------------
# POST localhost:3001/user/login

## Request

```
body:
{
    "email": "email@gmail.com",
    "password": "123456"
}
```

## Responses

* Success
```
{
    "status": "success",
    "token": "JSON WEBTOKEN",
    "name": "Name",
    "email": "email@gmail.com",
    "role": "client" || "admin"
}
```
* Fail
```
{
    "status": "failed",
    "code": "unauthorized",
    "message": "User not found or wrong password"
}

{
    "status": "failed",
    "code": "invalid_data",
    "message": "Missing fields"
}
```

# POST localhost:3001/user/register

## Request

```
body:
{
    "email": "email@gmail.com",
    "password": "123456",
    "name": "Seu Nome",
    "admin": true || false
}
```

## Response

* Success

```
{
    "status": "success",
    "user": {
        "name": Seu Nome",
        "password": "123456",
        "id": 1,
        "email": "email@gmail.com",
        "role": "admin" || "client"
    }
}
```

* Fail

```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/products

## Response

* Success
```
{
    "status": "success",
    "products": [
        {
            "name": "Skol Lata 350ml",
            "productId": 1,
            "price": 2.200000047683716,
            "picture": "http://localhost:3001/images/Skol Lata 350ml.jpg"
        },
        {
            "name": "Heineken 600ml",
            "productId": 2,
            "price": 7.5,
            "picture": "http://localhost:3001/images/Heineken 600ml.jpg"
        },
        {
            "name": "Antarctica Pilsen 300ml",
            "productId": 3,
            "price": 2.490000009536743,
            "picture": "http://localhost:3001/images/Antarctica Pilsen 300ml.jpg"
        },
        {
            "name": "Brahma 600ml",
            "productId": 4,
            "price": 7.5,
            "picture": "http://localhost:3001/images/Brahma 600ml.jpg"
        },
        {
            "name": "Skol 269ml",
            "productId": 5,
            "price": 2.190000057220459,
            "picture": "http://localhost:3001/images/Skol 269ml.jpg"
        },
        {
            "name": "Skol Beats Senses 313ml",
            "productId": 6,
            "price": 4.489999771118164,
            "picture": "http://localhost:3001/images/Skol Beats Senses 313ml.jpg"
        },
        {
            "name": "Becks 330ml",
            "productId": 7,
            "price": 4.989999771118164,
            "picture": "http://localhost:3001/images/Becks 330ml.jpg"
        },
        {
            "name": "Brahma Duplo Malte 350ml",
            "productId": 8,
            "price": 2.7899999618530273,
            "picture": "http://localhost:3001/images/Brahma Duplo Malte 350ml"
        },
        {
            "name": "Becks 600ml",
            "productId": 9,
            "price": 8.890000343322754,
            "picture": "http://localhost:3001/images/Becks 600ml"
        },
        {
            "name": "Skol Beats Senses 269ml",
            "productId": 10,
            "price": 3.569999933242798,
            "picture": "http://localhost:3001/images/Skol Beats Senses 269ml"
        },
        {
            "name": "Stella Artois 275ml",
            "productId": 11,
            "price": 3.490000009536743,
            "picture": "http://localhost:3001/images/Stella Artois 275ml"
        }
    ]
}
```

* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}

```

# PATCH localhost:3001/user/profile

## Request
```
body
{
    "name": "Seu nome",
}
authorization: JWT
```

## Response
* Success
```
{
    "status": "success"
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# POST localhost:3001/products/checkout
## Request
```
body
{
    "street": "rua 1",
    "streetNumber": 12,
    "products": [
        {
            "id": 1,
            "quantity": 5
        },
        {
            "id": 3,
            "quantity": 7
        }
    ]
}
authorization: JWT
```

## Response
* Success
```
{
    "status": "success"
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/user/Orders

## Request
```
authorization: JWT
```
## Response

* Succcess
```
{
    "status": "success",
    "orders": [
        {
            "orderId": 2,
            "total": 15.39,
            "day": "15",
            "month": "11"
        },
        {
            "orderId": 3,
            "total": 10.98,
            "day": "08",
            "month": "12"
        }
    ]
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/user

## Request
```
authorization: JWT
```

## Response
* Success
```
{
    "status": "success",
    "name": "Pedro",
    "email": "pedro@gmail.com"
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/orders/:id

## Request
```
authorization: JWT
```

## Response
* Success:
```
{
    "status": "success",
    "order": {
        "orderId": 2,
        "day": 15,
        "month": 10,
        "products": [
            {
                "name": "Skol Lata 350ml",
                "qty": 6,
                "price": 2.200000047683716,
                "total": 13.200000286102295
            },
            {
                "name": "Skol 269ml",
                "qty": 1,
                "price": 2.190000057220459,
                "total": 2.190000057220459
            }
        ],
        "total": 15.390000343322754
    }
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/orders/admin

## Request
```
authorization: JWT
```

## Response
* success
```
{
    "status": "success",
    "orders": [
        {
            "orderId": 1,
            "adress": "Rua 1, 22",
            "day": 15,
            "month": 4,
            "products": [
                {
                    "name": "Skol Lata 350ml",
                    "qty": 2,
                    "price": 2.200000047683716,
                    "total": 4.400000095367432
                },
                {
                    "name": "Antarctica Pilsen 300ml",
                    "qty": 4,
                    "price": 2.490000009536743,
                    "total": 9.960000038146973
                },
                {
                    "name": "Brahma 600ml",
                    "qty": 1,
                    "price": 7.5,
                    "total": 7.5
                }
            ],
            "total": 21.860000133514404,
            "deliver": 1
        },
        {
            "orderId": 2,
            "adress": "Rua 2, 820",
            "day": 15,
            "month": 11,
            "products": [
                {
                    "name": "Skol Lata 350ml",
                    "qty": 6,
                    "price": 2.200000047683716,
                    "total": 13.200000286102295
                },
                {
                    "name": "Skol 269ml",
                    "qty": 1,
                    "price": 2.190000057220459,
                    "total": 2.190000057220459
                }
            ],
            "total": 15.390000343322754,
            "deliver": 1
        },
        {
            "orderId": 3,
            "adress": "Rua 3, 52",
            "day": 8,
            "month": 12,
            "products": [
                {
                    "name": "Skol Lata 350ml",
                    "qty": 3,
                    "price": 2.200000047683716,
                    "total": 6.6000001430511475
                },
                {
                    "name": "Skol 269ml",
                    "qty": 2,
                    "price": 2.190000057220459,
                    "total": 4.380000114440918
                }
            ],
            "total": 10.980000257492065,
            "deliver": 0
        }
    ]
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# GET localhost:3001/orders/admin/:id
## Request
```
authorization: JWT
```

## Response
* Success
```
{
    "status": "success",
    "order": [
        {
            "orderId": 2,
            "adress": "Rua 2, 820",
            "day": 15,
            "month": 11,
            "products": [
                {
                    "name": "Skol Lata 350ml",
                    "qty": 6,
                    "price": 2.200000047683716,
                    "total": 13.200000286102295
                },
                {
                    "name": "Skol 269ml",
                    "qty": 1,
                    "price": 2.190000057220459,
                    "total": 2.190000057220459
                }
            ],
            "total": 15.390000343322754,
            "deliver": 1
        }
    ]
}
```
* Fail
```
{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```

# PATCH localhost:3001/orders/admin/:orderId/delivered

## Request
```
authorization: JWT
```

## Response
```
{
    "status": "success"
}

{
    "status": "failed",
    "code": "Código do erro",
    "message": Mensagem do erro"
}
```
