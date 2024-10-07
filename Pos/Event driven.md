## Event notification

```json
{
  "id": 123,
  "event": "saved"
}
```

ou

```json
{
  "id": "123",
  "link": "<domain>/saveds/123"
}
```

## Event-Carried State Transfer

```json
{
  "street": "rua dos bobos",
  "number": "0",
  "zipcode": "123456000",
  "city": "las calles"
}
```

ou

```json
{
	"orderId": 12,
	"lineItems": [
		{
			"productId": 2,
		    "quantity": 3	  
		}
	]
}
```

## CQRS
Command Query Responsability Segregation

Separa modelo de escrita de modelo de leitura. Útil quando se escreve pouco e se lê muito.

