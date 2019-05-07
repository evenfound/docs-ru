<!----- Conversion time: 3.319 seconds.


Using this Markdown file:

1. Cut and paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β17
* Tue May 07 2019 04:26:35 GMT-0700 (PDT)
* Source doc: https://docs.google.com/open?id=1iV82EfYm8xiWmssDzkx4_55PZCjipMkiqmAVIu8-too
* This is a partial selection. Check to make sure intra-doc links work.
----->


**_3. Структура сообщений _**


    Каждая операция базового так и расширенного протокола в распределенной сети сопровождается очередью транзакций. 


    Каждая транзакция имеет следующую структуру:


<table>
  <tr>
   <td>0
   </td>
   <td><strong><code>hash</code></strong>
   </td>
   <td>Уникальный мульхеш (адрес объекта IPFS) сообщения
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td><strong><code>id[t, v]</code></strong>
   </td>
   <td>Тип транзакции и версия формата
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td><strong><code>address</code></strong>
   </td>
   <td>Адрес счета получателя или отправителя
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td><strong><code>message</code></strong>
   </td>
   <td>Сообщение, сформированное генератором подписи из приватного ключа счета и хеша <strong><code>trunk</code></strong>
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td><strong><code>source</code></strong>
   </td>
   <td>Хеш адрес смарт-контракта или хеш другого информационного ресурса, являющегося предметом транзакции
   </td>
  </tr>
  <tr>
   <td>5
   </td>
   <td><strong><code>value</code></strong>
   </td>
   <td>Размер отправления в единицах 
   </td>
  </tr>
  <tr>
   <td>6
   </td>
   <td><strong><code>timestamp</code></strong>
   </td>
   <td>Временная метка
   </td>
  </tr>
  <tr>
   <td>7
   </td>
   <td><strong><code>trunk</code></strong>
   </td>
   <td>Хеш адрес IPFS своего последнего пакета  транзакций, адресуемого от имени или себе пакета транзакций.
   </td>
  </tr>
  <tr>
   <td>8
   </td>
   <td><strong><code>branch[{h, p}]</code></strong>
   </td>
   <td>Массив объектов,  объединяющих уникальные хеш адреса IPFS  (h) пакетов транзакций первых в списке,  присланных в INBOX нодами, получившими право выбрать адресата в качестве валидатора, и подтверждений проверки их реверсивным анализом балансной цепочки (p)
   </td>
  </tr>
  <tr>
   <td>9
   </td>
   <td><strong><code>tag</code></strong>
   </td>
   <td>Информационное поле
   </td>
  </tr>
</table>



    Нулевое поле формируется генератором хеш адресов модуля IPFS решая две залачи:



*   Криптозащиты содержимого сообщения;
*   Однозначной уникальной идентификации в сети IPFS.
*   

    Пример транзакций, в которой 3 EVEN переводятся с адреса Алисы на адрес Боба:


<table>
  <tr>
   <td>
<strong><code>hash</code></strong>
   </td>
   <td colspan="3" ><strong><code>Qmsdkakad09sad0f9</code></strong>
   </td>
   <td><strong><code>id</code></strong>
   </td>
   <td colspan="2" ><code>0x0001, 0x001</code>
   </td>
   <td><strong><code>addr</code></strong>
   </td>
   <td colspan="2" ><code>JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ</code>
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong><code>message</code></strong>
   </td>
   <td colspan="3" ><code>QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD</code>
   </td>
   <td><strong><code>src</code></strong>
   </td>
   <td colspan="4" ><code>YDDQVGFO9OTJQSRGESYLPWLIDYBTFHUFQJ9HINVQVJMIKCHXBRNNOO9EZXGDOYJZPCPCZUARJ9IXA9999</code>
   </td>
  </tr>
  <tr>
   <td><strong><code>val</code></strong>
   </td>
   <td><strong><code>3</code></strong>
   </td>
   <td><strong><code>timestamp</code></strong>
   </td>
   <td>
        <code>1515494426</code>
   </td>
   <td colspan="2" ><strong><code>trunk</code></strong>
   </td>
   <td colspan="4" ><code>QmAsaskakad09sad0f9</code>
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong><code>branch</code></strong>
   </td>
   <td colspan="2" >
<code>Y{QmJHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK}, {QmHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK} ..</code>
   </td>
   <td colspan="2" ><strong><code>tag</code></strong>
   </td>
   <td colspan="4" ><code>TEST_TRANSAC</code>
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong><code>hash</code></strong>
   </td>
   <td colspan="3" ><strong><code>Qmsdkakad09sad0f9</code></strong>
   </td>
   <td><strong><code>id</code></strong>
   </td>
   <td colspan="2" ><code>0x0001, 0x001</code>
   </td>
   <td><strong><code>addr</code></strong>
   </td>
   <td colspan="2" ><code>AJSAJKHSNXABONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXM</code>
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong><code>message</code></strong>
   </td>
   <td colspan="3" ><code>QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD</code>
   </td>
   <td><strong><code>src</code></strong>
   </td>
   <td colspan="4" ><code>YDDQVGFO9OTJQSRGESYLPWLIDYBTFHUFQJ9HINVQVJMIKCHXBRNNOO9EZXGDOYJZPCPCZUARJ9IXA9999</code>
   </td>
  </tr>
  <tr>
   <td><strong><code>val</code></strong>
   </td>
   <td><strong><code>-3</code></strong>
   </td>
   <td><strong><code>timestamp</code></strong>
   </td>
   <td>
        <code>1515494426</code>
   </td>
   <td colspan="2" ><strong><code>trunk</code></strong>
   </td>
   <td colspan="4" ><code>QmAsaskakad09sad0f9</code>
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong><code>branch</code></strong>
   </td>
   <td colspan="2" >
<code>Y{QmJHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK}, {QmHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ, ASHASHGAJSGK} ..</code>
   </td>
   <td colspan="2" ><strong><code>tag</code></strong>
   </td>
   <td colspan="4" ><code>TEST_TRANSAC</code>
   </td>
  </tr>
</table>



    Перевод состоит из двух транзакций. Все транзакции в одной операции должны рассматриваться как элементарная единица. Это означает, что либо все транзакции пакета подтверждены, либо ни одна из них не подтверждена. 


    Каждая транзакция в пакете не требует собственного PoS<sup>n</sup> (proof  of sign) подтверждения: одни подтверждаются пакетно, сразу все. 


    Внутри пакета может быть 3 разных базовых типа транзакций:



*   Выходные транзакции. Транзакции, в которых токены отправляются на один или несколько адресов. Эти транзакции легко распознаются, потому что значение транзакции всегда больше 0 и адрес не принадлежит отправителю. 
*   Входные транзакции. Существует два типа входных транзакций: 
1. Входные транзакции, где значение отрицательное. Это транзакции, на которые тратится полный баланс с адреса получателя. 
2. Входные транзакции, где значение больше 0. Это транзакции, в которых неизрасходованные / неиспользованные токены  отправляются на новый адрес изменения в кошельке отправителей. 
3. Мета-транзакции. Транзакции с нулевой стоимостью. 

    Пакет может иметь одну транзакцию, например, когда приложение подключается к сети. 


    Пакет может иметь также любое количество транзакций. 


    Например: 


    Алиса имеет кошелек с адресом от 0 до адреса 99, причем каждый адрес имеет один токен. 


    Когда Алиса переводит свой полный баланс кошелька Бобу, она создает пакет транзакций, содержащий 101 транзакцию:

*   1 транзакция для Боба,
*   100 транзакций, снимающих 1 EVEN с каждого адреса. 

    Каждая транзакция внутри пакета  содержит общее для него подтверждение подписью PoS<sup>n</sup>. 


    Хеш адреса транзакций, полученных нодой в DLT раздел INBOX, представляют собой ссылку на транзакции, предназначенные для проверки другими нодами. 


    Для того, чтобы сделать PoS<sup>n</sup> для этого пакета, нода должна провести реверсивный подсчет баланса начиная с адреса trunk этих пакетов одновременно с реверсивным анализом своей trunk цепочки транзакций. В момент, когда хеши выходных транзакций совпадут при одинаковом реверсивном балансе - произойдет валидация. Хеш адрес полученной транзакции и ее пакета указывается в качестве подтверждения brunch.


    PoS<sup>n</sup> (p) - это хеш сообщения, в котором произошло решение уравнения валидации при подсчете баланса наследования в сообщении, хеш-адрес которого содержится в поле branch. 


    Как это работает, рассматривается  далее на примере сценария создания сообщения.


    _Пример сценария создания сообщения._

1. _План_

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
   <td><strong><code>QmN</code></strong>
   </td>
   <td>
    AAAAAAAAA
   </td>
   <td>
    +60
   </td>
   <td>Trunk: <strong><code>QmN-1</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



    Далее, формируем транзакцию сдачи:  



*   вставляем в её поле trunk адрес **<code>QmN</code></strong>,
*   генерируем подпись из него и приватного ключа и вставляем результат в поле message,
*   Генерируем (он уже есть в таблице) новый адрес на основе seed модуля кошелька и вносим в поле value значение сдачи - 20e,
*   Вставляем  PoS<sup>n   </sup>валидацию в поле branch,
*   Генерируем хеш адрес файла транзакции IPFS.

<table>
  <tr>
   <td>
<strong><code>QmN+1</code></strong>
   </td>
   <td>
    EEEEEEEEEEE
   </td>
   <td>
    +20
   </td>
   <td>Trunk: <strong><code>QmN</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



    Далее, похожим образом формируем цепочку транзакций дальше. 


    Сначала входные с расходом:


<table>
  <tr>
   <td><strong><code>QmN+2</code></strong>
   </td>
   <td>
    DDDDDDDDD
   </td>
   <td>
    -60
   </td>
   <td>Trunk: <strong><code>QmN+1</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong><code>QmN+3</code></strong>
   </td>
   <td>
    CCCCCCCCCCC
   </td>
   <td>
    -25
   </td>
   <td>Trunk: <strong><code>QmN+2</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong><code>QmN+4</code></strong>
   </td>
   <td>
    BBBBBBBBBB
   </td>
   <td>
    -5
   </td>
   <td>Trunk: <strong><code>QmN+3</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong><code>QmN+5</code></strong>
   </td>
   <td>
    AAAAAAAAA
   </td>
   <td>
    -10
   </td>
   <td>Trunk: <strong><code>QmN+4</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



    И последней - выходную:  


<table>
  <tr>
   <td><strong><code>QmN+6</code></strong>
   </td>
   <td>
    QQQQQQQQ
   </td>
   <td>
    +80
   </td>
   <td>Trunk: <strong><code>QmN+5</code></strong>
   </td>
   <td>Branch
   </td>
  </tr>
</table>



    После этого пакет подготовлена и можно отправлять адрес последней транзакции валидатору или публиковать в сеть.


<!-- Docs to Markdown version 1.0β17 -->