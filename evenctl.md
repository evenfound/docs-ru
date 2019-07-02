**evenctl** - Это клиентская программа для управления демоном `EvenGo` посредством протокола `gRPC`

## Использование

`evenctl [COMMANDS] [OPTIONS]`

#### evenctl file
 Команда | Описание  
------------ | -------------
create | Создает новый файл по имени и источнику
mkdir | Создает новый каталог по имени 
stat |  Выдает информацию файла по имени 
fidn | Ищет файл  в сети по хешу 

## Пример создания файла
```sh
$ evenctl file create -n abc -s /bin/bash

$ evenctl file stat -n abc 
Hash QmXsutKqDKZ3aZVM9r4KxbfkzfmQHUsi4TFMU8rWBNWJ4Q
BlockSize 0
CumulativeSize 1113822
DataSize 26
NumLinks 5
LinksSize 222
```

#### evenctl Wallet
 Команда | Описание  
------------ | -------------
create | Создает новый кошелек по имени , паролю и сид фразу 
generate  | Создает новый кошелек по имени и паролю 
nextaccount |  Создает новый аккаунт по имени и паролю 
privkey |  Выдает приватный ключ аккаунта
pubkey |  Выдает публичный ключ аккаунта 
balance |  Выдает баланс акаунта 
tx | Создает новую транзакцию 

## Пример создания счета и кошелька
```sh
$ evenctl wallet create -n wallet1 -p wallet1 -s "abc def"
2019/06/26 15:47:34 wallet1

$ evenctl wallet generate -n wallet1 -p wallet1 
2019/06/26 15:48:08 donate dose erupt mirror modify secret swap close vast ankle timber quit

$ evenctl wallet nextaccount -n wallet1 -p wallet1
2019/06/26 15:49:02 mpi2PrWtyJQT8UKLwWijBBCFGpSCeNTLiC

```
#### evenctl peer
 Команда | Описание  
------------ | -------------
list | Выдает список всех пиров в сети 
id  | Выдает идентификатор нода 
add |  Добавляет новый пир в конфиге 
send |  Отправляет хэш всем участникам в сети

## Пример получения списка пиров в сети
```sh
$ evenctl peer list
Peer : QmZ2j9AjjNsHUyRWAJRZSpDtxrK793LS5eZUpu5gkXHmN3
Peer : QmRPrkQh5pB7nyKQRwpqunjB5H1XnjgAVSQhfGSyZ2r83V
Peer : Qma4FJWJiKGuY9J9js7YzJxhDsWLSVBeqhhmTVcrWbosGK
Peer : QmNhHxi1u6tK1pgRrFsBSUegsXrMAYsux2r4QM3ARFN2sU

$ evenctl peer id
QmZ2j9AjjNsHUyRWAJRZSpDtxrK793LS5eZUpu5gkXHmN3

$ evenctl peer add /ip4/127.0.0.1/tcp/4001/QmZ2j9AjjNsHUyRWAJRZSpDtxrK793LS5eZUpu5gkXHmN3

$ evenctl peer send --hash QmXsutKqDKZ3aZVM9r4KxbfkzfmQHUsi4TFMU8rWBNWJ4Q
Sending hash QmXsutKqDKZ3aZVM9r4KxbfkzfmQHUsi4TFMU8rWBNWJ4Q to peers 
```

#### evenctl test
 Команда | Описание  
------------ | -------------
call | Вызов смарт контракта по содержимому 
sign   | Подписание сообщения
verify  |  Проверить подписанное сообщение
folder |  Создание специальных папок



