# Javascript-self-reference
Self reference to examples of useful functions of JS.


### Asynchronous study
```
//1
setTimeout(()=>{console.log('1', 'is the loneliest number')}, 0)
setTimeout(()=>{console.log('2', 'can be as bad as one')}, 10)

//2
Promise.resolve('hi').then((data)=> console.log('2', data))

//3
console.log('3','is a crowd')
```


### Find 
```
const finduuu = (arr, op) => {
    for (let i = 0; i < arr.length; i++) {
        if (op(arr[i], i, arr)) {
            return arr[i]
        }
    }
}
```

### Map
```
const mapuu = (arr, op) => {
    let array = []
    for (let i = 0; i < arr.length; i++) {
        array.push(op(arr[i], i, arr))
    }
    return array
}
```

### For Each
```
const forEachuu = (arr, op) => {
    for (let index = 0; index < arr.length; index++) {
        op(arr[index])
    }
}
```

### Filter
```
const filtuuu = (arr, op) => {
    let array = []
    for (let i = 0; i < arr.length; i++) {
        if (op(arr[i], i, arr)) {
            array.push(arr[i])
        }
    }
    return array
}
```

### Reduce
```
const reducuuu = (array, operacao, valorInicial) => {
    let acumulador = valorInicial
    for (let i = 0; i < array.length; i++) {
        acumulador = operacao(acumulador, array[i], i, array)
    }
    return acumulador
}
```


### Test Json
```
const fullReport = {
    "receber": [{
            "id": 1,
            "title": "Testezinho",
            "description": "...",
            "value": 5000,
            "status": true,
            "paymentDate": null,
            "createdAt": "2019-07-05T22:43:27.565Z",
            "updatedAt": "2019-07-05T22:43:27.565Z"
        },
        {
            "id": 2,
            "title": "Condomínio",
            "description": "...",
            "value": 380,
            "status": true,
            "paymentDate": null,
            "createdAt": "2019-07-05T22:44:44.581Z",
            "updatedAt": "2019-07-05T22:44:44.581Z"
        }
    ],
    "pagar": [{
            "id": 6,
            "title": "Computador",
            "description": "...",
            "value": 5000,
            "status": true,
            "paymentDate": null,
            "createdAt": "2019-07-08T02:52:49.585Z",
            "updatedAt": "2019-07-08T02:52:49.585Z"
        },
        {
            "id": 7,
            "title": "Agua",
            "description": "...",
            "value": 300,
            "status": false,
            "paymentDate": null,
            "createdAt": "2019-07-08T02:53:33.594Z",
            "updatedAt": "2019-07-08T02:53:33.594Z"
        },
        {
            "id": 8,
            "title": "Cartão de Crédito",
            "description": "...",
            "value": 500,
            "status": true,
            "paymentDate": null,
            "createdAt": "2019-07-08T02:53:53.125Z",
            "updatedAt": "2019-07-08T02:53:53.125Z"
        }
    ]
}
```


### Applying
```
const aPagar = fullReport.pagar
const aReceber = fullReport.receber

const contasAPagar = aPagar.filter((e) => e.status)
const contasPagas = aPagar.filter((e) => !e.status)
const contasAReceber = aReceber.filter((e) => e.status)
const contasRecebidas = aReceber.filter((e) => !e.status)

const ayyLmao = (acc, e) => acc + e.value

const totalAPagar = aPagar.filter((e) => e.status).reduce(ayyLmao, 0)
const totalPago = aPagar.filter((e) => !e.status).reduce(ayyLmao, 0)
const totalAReceber = aReceber.filter((e) => e.status).reduce(ayyLmao, 0)
const totalRecebido = aReceber.filter((e) => !e.status).reduce(ayyLmao, 0)

console.log(totalAPagar)
console.log(totalPago)
console.log(totalAReceber)
console.log(totalRecebido)

const contasAPagar = filtuuu(aPagar, (e) => e.status)
const contasPagas = filtuuu(aPagar, (e) => !e.status)
const contasAReceber = filtuuu(aReceber, (e) => e.status)
const contasRecebidas = filtuuu(aReceber, (e) => !e.status)
```

### Bad way
```
for (let i = 0; i < aPagar.length; i++) {
    const element = aPagar[i];
    if (element.status === true) {
        contasAPagar.push(element)
    } else {
        contasPagas.push(element)
    }
}

for (let i = 0; i < aReceber.length; i++) {
    const element = aReceber[i];
    if (element.status === true) {
        contasAReceber.push(element)
    } else {
        contasReceber.push(element)
    }
}
console.log('Contas a Pagar: ')
console.table(contasAPagar)
console.log('Contas Pagas: ')
console.table(contasPagas)
console.log('Contas a Receber: ')
console.table(contasAReceber)
console.log('Contas Recebidas: ')
console.table(contasRecebidas)
```


### Reverse
```
let numbers = [1, 4]
let revert = numbers.reverse()
// revert é agora [4, 1]
```
