## Структура сообщений 

Каждая операция базового так и расширенного протокола в распределенной сети сопровождается очередью транзакций. 

Каждая транзакция имеет следующую структуру:
 
<table>
  <tr>
   <td>0
   </td>
   <td><strong> hash </strong>
   </td>
   <td>Уникальный мульхеш (адрес объекта IPFS) сообщения
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td><strong> id[t, v] </strong>
   </td>
   <td>Тип транзакции и версия формата
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td><strong> address </strong>
   </td>
   <td>Адрес счета получателя или отправителя
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td><strong> message </strong>
   </td>
   <td>Сообщение, сформированное генератором подписи из приватного ключа счета и хеша <strong> trunk </strong>
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td><strong> source </strong>
   </td>
   <td>Хеш адрес смарт-контракта или хеш другого информационного ресурса, являющегося предметом транзакции
   </td>
  </tr>
  <tr>
   <td>5
   </td>
   <td><strong> value </strong>
   </td>
   <td>Размер отправления в единицах 
   </td>
  </tr>
  <tr>
   <td>6
   </td>
   <td><strong> timestamp </strong>
   </td>
   <td>Временная метка
   </td>
  </tr>
  <tr>
   <td>7
   </td>
   <td><strong> trunk </strong>
   </td>
   <td>Хеш адрес IPFS своего последнего пакета  транзакций, адресуемого от имени или себе пакета транзакций.
   </td>
  </tr>
  <tr>
   <td>8
   </td>
   <td><strong> branch[{h, p}] </strong>
   </td>
   <td>Массив объектов,  объединяющих уникальные хеш адреса IPFS  (h) пакетов транзакций первых в списке,  присланных в INBOX нодами, получившими право выбрать адресата в качестве валидатора, и подтверждений проверки их реверсивным анализом балансной цепочки (p)
   </td>
  </tr>
  <tr>
   <td>9
   </td>
   <td><strong> tag </strong>
   </td>
   <td>Информационное поле
   </td>
  </tr>
</table>
 

Нулевое поле формируется генератором хеш адресов модуля IPFS решая две залачи:
*   Криптозащиты содержимого сообщения;
*   Однозначной уникальной идентификации в сети IPFS.
   
Пример транзакций, в которой 3 EVEN переводятся с адреса Алисы на адрес Боба:
 
<table>
  <tr>
   <td>
<strong>hash</strong>
   </td>
   <td colspan="3" ><strong> Qmsdkakad09sad0f9 </strong>
   </td>
   <td><strong> id </strong>
   </td>
   <td colspan="2" > 0x0001, 0x001 
   </td>
   <td><strong> addr </strong>
   </td>
   <td colspan="2" > JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ 
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong> message </strong>
   </td>
   <td colspan="3" > QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD 
   </td>
   <td><strong> src </strong>
   </td>
   <td colspan="4" > YDDQVGFO9OTJQSRGESYLPWLIDYBTFHUFQJ9HINVQVJMIKCHXBRNNOO9EZXGDOYJZPCPCZUARJ9IXA9999 
   </td>
  </tr>
  <tr>
   <td><strong> val </strong>
   </td>
   <td><strong> 3 </strong>
   </td>
   <td><strong> timestamp </strong>
   </td>
   <td>
         1515494426 
   </td>
   <td colspan="2" ><strong> trunk </strong>
   </td>
   <td colspan="4" > QmAsaskakad09sad0f9 
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong> branch </strong>
   </td>
   <td colspan="2" >
 Y{QmJHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK}, {QmHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK} .. 
   </td>
   <td colspan="2" ><strong> tag </strong>
   </td>
   <td colspan="4" > TEST_TRANSAC 
   </td>
  </tr>
</table>
 


<table>
  <tr>
   <td><strong> hash </strong>
   </td>
   <td colspan="3" ><strong> Qmsdkakad09sad0f9 </strong>
   </td>
   <td><strong> id </strong>
   </td>
   <td colspan="2" > 0x0001, 0x001 
   </td>
   <td><strong> addr </strong>
   </td>
   <td colspan="2" > AJSAJKHSNXABONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXM 
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong> message </strong>
   </td>
   <td colspan="3" > QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD 
   </td>
   <td><strong> src </strong>
   </td>
   <td colspan="4" > YDDQVGFO9OTJQSRGESYLPWLIDYBTFHUFQJ9HINVQVJMIKCHXBRNNOO9EZXGDOYJZPCPCZUARJ9IXA9999 
   </td>
  </tr>
  <tr>
   <td><strong> val </strong>
   </td>
   <td><strong> -3 </strong>
   </td>
   <td><strong> timestamp </strong>
   </td>
   <td>
         1515494426 
   </td>
   <td colspan="2" ><strong> trunk </strong>
   </td>
   <td colspan="4" > QmAsaskakad09sad0f9 
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong> branch </strong>
   </td>
   <td colspan="2" >
 Y{QmJHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK}, {QmHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK} .. 
   </td>
   <td colspan="2" ><strong> tag </strong>
   </td>
   <td colspan="4" > TEST_TRANSAC 
   </td>
  </tr>
</table>

Перевод состоит из двух транзакций. Все транзакции в одной операции должны рассматриваться как элементарная единица. Это означает, что либо все транзакции пакета подтверждены, либо ни одна из них не подтверждена. 

Каждая транзакция в пакете не требует собственного PoS<sup>n</sup> (proof  of sign) подтверждения: одни подтверждаются пакетно, сразу все. 

Внутри пакета может быть 3 разных базовых типа транзакций:
*   Выходные транзакции. Транзакции, в которых токены отправляются на один или несколько адресов. Эти транзакции легко распознаются, потому что значение транзакции всегда больше 0 и адрес не принадлежит отправителю. 
*   Входные транзакции. Существует два типа входных транзакций: 
 1). Входные транзакции, где значение отрицательное. Это транзакции, на которые тратится полный баланс с адреса получателя. 
 2). Входные транзакции, где значение больше 0. Это транзакции, в которых неизрасходованные / неиспользованные токены  отправляются на новый адрес изменения в кошельке отправителей. 
 3). Мета-транзакции. Транзакции с нулевой стоимостью. 

Пакет может иметь одну транзакцию, например, когда приложение подключается к сети. 

Пакет может иметь также любое количество транзакций. 

Например:

*Алиса имеет кошелек с адресом от 0 до адреса 99, причем каждый адрес имеет один токен.*

*Когда Алиса переводит свой полный баланс кошелька Бобу, она создает пакет транзакций, содержащий 101 транзакцию:*
*   *1 транзакция для Боба,*
*   *100 транзакций, снимающих 1 EVEN с каждого адреса.*

*Каждая транзакция внутри пакета  содержит общее для него подтверждение подписью PoS<sup>n</sup>.*

*Хеш адреса транзакций, полученных нодой в DLT раздел INBOX, представляют собой ссылку на транзакции, предназначенные для проверки другими нодами.* 

*Для того, чтобы сделать PoS<sup>n</sup> для этого пакета, нода должна провести реверсивный подсчет баланса начиная с адреса trunk этих пакетов одновременно с реверсивным анализом своей trunk цепочки транзакций. В момент, когда хеши выходных транзакций совпадут при одинаковом реверсивном балансе - произойдет валидация. Хеш адрес полученной транзакции и ее пакета указывается в качестве подтверждения brunch.*

PoS<sup>n</sup> (p) - это хеш сообщения, в котором произошло решение уравнения валидации при подсчете баланса наследования в сообщении, хеш-адрес которого содержится в поле branch. 

Как это работает, рассматривается  далее на примере сценария создания сообщения.

*Пример сценария создания сообщения.*

_1_. *План*

Пользователь А имеет кошелек с адресом <_address_A_>, который содержит 100e на 4 разных счетах, относящихся к данному адресу :


<table>
 <tr>
   <td>
#1
   </td>
   <td>
    AAAAAAAAA
   </td>
   <td>10
   </td>
  </tr>
  <tr>
   <td>#2
   </td>
   <td>
    BBBBBBBBBB
   </td>
   <td>5
   </td>
  </tr>
  <tr>
   <td>#3
   </td>
   <td>
    CCCCCCCCCCC
   </td>
   <td>25
   </td>
  </tr>
  <tr>
   <td>#4
   </td>
   <td>
    DDDDDDDDDD
   </td>
   <td>60
   </td>
  </tr>
  <tr>
   <td>#5
   </td>
   <td>
    EEEEEEEEEEE
   </td>
   <td>0
   </td>
  </tr>
</table>



Пользователь B имеет кошелек с адресом <_address_B_> которое содержит 0i в своем адресе:


<table>
  <tr>
   <td>#1
   </td>
   <td>
    QQQQQQQQQ
   </td>
   <td>0
   </td>
  </tr>
</table>

Пользователь А хочет отправить 80e на адрес Лица В #1:  QQQQQQQQQ .


### 

_2. Формирование  очереди транзакций_


Особенностью защиты целостности цепочки транзакций в нашем распределенном блокчейне является хеширование IPFS trunk адреса внутри транзакции, из чего следует, что пакет транзакций начинает формироваться с последней транзакции в очереди. 

В случае примера очевидно, что первой необходимо сформировать unspend транзакцию (получить ”сдачу”) на новый адрес пользователя A, так как 10 + 5 + 25 + 60 = 100 EVEN - входов и 80 EVEN - выходов. 

Для этого нужно взять IPFS хеш адрес любой выходной транзакции из списка, полученного модулем кошелька ноды при подсчете баланса, например (упрощенно):

<table>
  <tr>
   <td><strong> QmN </strong>
   </td>
   <td>
    AAAAAAAAA
   </td>
   <td>
    +60
   </td>
   <td>Trunk: <strong> QmN-1 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>

Далее, формируем транзакцию сдачи:  

* вставляем в её поле trunk адрес  QmN </strong>,
* генерируем подпись из него и приватного ключа и вставляем результат в поле message,
* Генерируем (он уже есть в таблице) новый адрес на основе seed модуля кошелька и вносим в поле value значение сдачи - 20e,
* Вставляем  PoS<sup>n   </sup>валидацию в поле branch,
* Генерируем хеш адрес файла транзакции IPFS.

<table>
  <tr>
   <td>
<strong> QmN+1 </strong>
   </td>
   <td>
    EEEEEEEEEEE
   </td>
   <td>
    +20
   </td>
   <td>Trunk: <strong> QmN </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>

Далее, похожим образом формируем цепочку транзакций дальше. 
Сначала входные с расходом:

<table>
  <tr>
   <td><strong> QmN+2 </strong>
   </td>
   <td>
    DDDDDDDDD
   </td>
   <td>
    -60
   </td>
   <td>Trunk: <strong> QmN+1 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong> QmN+3 </strong>
   </td>
   <td>
    CCCCCCCCC
   </td>
   <td>
    -25
   </td>
   <td>Trunk: <strong> QmN+2 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong> QmN+4 </strong>
   </td>
   <td>
    BBBBBBBBBB
   </td>
   <td>
    -5
   </td>
   <td>Trunk: <strong> QmN+3 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong> QmN+5 </strong>
   </td>
   <td>
    AAAAAAAAAA
   </td>
   <td>
    -10
   </td>
   <td>Trunk: <strong> QmN+4 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>

И последней - выходную:  

<table>
  <tr>
   <td><strong> QmN+6 </strong>
   </td>
   <td>
    QQQQQQQQ
   </td>
   <td>
    +80
   </td>
   <td>Trunk: <strong> QmN+5 </strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>


После этого пакет подготовлена и можно отправлять адрес последней транзакции валидатору или публиковать в сеть.


