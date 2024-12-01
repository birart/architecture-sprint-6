# Описание решения

## Исходное API
Исходное API позволяет получать данные клиента, список его документов и родственников.
Оперирует сущностями Client, Document, Relative. 

В файле [по ссылке](client-info-api.graphql) описаны сущности, их параметры и корневой объект Query.

## Примеры query

Учитывая описание схемы могут быть выполнены следующие запросы:

1. Получение данных клиента без документов и родственников:
```graphql
query Client {
    client(id: "client-id-101") {
        name
        age
    }
}
```

2. Получение документов клиента:

```graphql
query Client {
    client(id: "client-id-101") {
        name
        age
        documents {
            type
            number
            issueDate
            expiryDate
        }
    }
}
```

3. Получение родственников клиента:

```graphql
query Client {
    client(id: "client-id-101") {
        name
        age
        relatives {
            relationType
            name
            age
        }
    }
}
```

3. Получение родственников и документов клиента:

```graphql
query Client {
    client(id: "client-id-101") {
        name
        age
        documents {
            number
            issueDate
            expiryDate
            type
        }
        relatives {
            relationType
            name
            age
        }
    }
}
```