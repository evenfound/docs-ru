## Кросс-чейн обмен цифровыми активами

Задачи кросс-чейн обмена цифровыми ресурсами решает алгоритм расширенного протокола _CIP - common interaction protocol_. В общем случае алгоритм его работы по организации обмена состоит из следующих этапов:
*   Мониторинг _нод_, предлагающих свои депозиты из внешних сетей для обмена;
*   Динамическая генерация мульти-подписи для вновь создаваемого прокси-счета во внешней сети, создание прокси счета,
*   Извещение заказчиков о создании прокси-счета,
*   Мониторинг биржевых транзакций и управление прокси-счетами,
*   Закрытие прокси-счетов, распределение комиссии,

В работе с расширенным протоколом главное избежать федерализации _нод_. Весь алгоритм должен быть построен на использовании крипто-защищенных транзакций базового и расширенного протокола. 

_Рассмотрим пример работы алгоритма._

_Создание прокси счета._

Для того, чтобы _нода_ могла выполнить обмен цифрового актива или выставить его на продажу, она должна удовлетворять двум условиям:
*   Иметь счет в сети, статус информационного ресурса которого хочет изменить _нода_,
*   Иметь мультивалютный кошелек приватной сети. 

Примерно в мультивалютном кошельке счета будут выглядеть следующим образом:


<table>
  <tr>
   <td>
#1
   </td>
   <td>S98C7CSSD9CJSCSMADKDSCJKJ
   </td>
   <td>EVEN
   </td>
   <td><strong>56.034</strong>
   </td>
  </tr>
  <tr>
   <td>#2
   </td>
   <td>
    028732468uhd2nun2imxmcmweokwg
   </td>
   <td>BTC
   </td>
   <td><strong>3.0012</strong>
   </td>
  </tr>
  <tr>
   <td>#3
   </td>
   <td>
    aakjdhcknieuuwfqvqjwcnsjdnjvsdvjdsvn
   </td>
   <td>Eth
   </td>
   <td><strong>43.45</strong>
   </td>
  </tr>
</table>

После того, как _нода_ станет располагать этими возможностями и желает выставить часть монет на торги,, он оправляет в shared область виртуальной файловой системы приватной сети сообщение следующего содержания:

<table>
  <tr>
   <td><strong>hash</strong>
   </td>
   <td colspan="3" ><strong>Qmsdkakad09sad0f9</strong>
   </td>
   <td><strong>id</strong>
   </td>
   <td colspan="2" >0x0001, 0x011
   </td>
   <td><strong>addr</strong>
   </td>
   <td colspan="2" >JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>message</strong>
   </td>
   <td colspan="3" >QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD
   </td>
   <td><strong>src</strong>
   </td>
   <td colspan="4" >QmGadjasdajxasbancsij
   </td>
  </tr>
  <tr>
   <td><strong>val</strong>
   </td>
   <td><strong>-1</strong>
   </td>
   <td><strong>timestamp</strong>
   </td>
   <td>
        1515494426
   </td>
   <td colspan="2" ><strong>trunk</strong>
   </td>
   <td colspan="4" >QmAsaskakad09sad0f9
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>branch</strong>
   </td>
   <td colspan="2" >
   </td>
   <td colspan="2" ><strong>tag</strong>
   </td>
   <td colspan="4" >CIP_TRANSAC
   </td>
  </tr>
</table>

Её поля заполняются следующим образом (поле hash - это мульти-хеш транзакции в IPFS и создается ей при публикации):  



*   Id: версия и тип транзакции - запрос на размещение депозита в биткойнах,
*   Addr: адрес ноды инициатора запроса,
*   Message: подпись с использованием приватного ключа и адреса trunk, 
*   Src: адрес смарт контракта, который управляет прокси-счетом,
*   Val: размер размещаемого депозита в BTC,
*   Timestamp: время создания транзакции,
*   Trunk: хеш адрес последней служебной транзакции (см. п4),
*   Tag: в принципе можно не заполнять.

Публикацие данной транзакции _нода_ извещает сеть о готовности внести депозит для осуществления операций обмена. 
_Ноды,_ которые обладают необходимыми возможностями для работы в расширенном протоколе обмена, постоянно мониторят наличие таких транзакций, так как в этом им есть прямая выгода - за обменные операции после вывода депозита взимается брокерская комиссия  комиссия.
Смарт-контракт сделан по типовому шаблону и используем API функции генерации сигнатуры мультиподписи DKG. 
_Ноды_, способные построить межсетевой мост и управление производят следующие операции:
*   Находят такую транзакцию, 
*   Вызывают в адресном пространстве своей виртуальной машины бинарный код смарт-контракта, адрес которого указан в ней,
*   Передают ему в качестве аргумента полуфабрикат своей части сигнатуры на базе своего приватного ключа. Формально эта часть рассчитывается по следующим формулам (подробнее см. “_Мультиподпись Schnorr с валидацией ECDSA_”):
1. $L(i)=H(P_i)$- хэш публичного ключа каждого участника;
2. Вводится переменная $X=\sum\limits_{i=0}^NH(L_i,P_i)P_i$;
3. Каждый подписант вычисляет свой уникальный $r_i$ и вычисляет свой уникальный $R_i=r_iG$, а  $R_\Sigma=\sum\limits_{i=0}^NP_i$ - сумма  всех $P_i$;
4. $c$ также меняется от уравнения $BN$. $c_i=H(X,R_\Sigma,z)*\alpha$. Введена новая переменная $\alpha$, где каждый участник использует свой уникальный открытый ключ для вычисления $\alpha=H(L_i,P_i)$. Таким образом,  $c_i=H(X,R_\Sigma,z)*H(L_i,P_i)$;
5. Каждый участник теперь должен вычислить свой собственный $s_i=r_i+c_ix_i$.

Смарт-контракт постепенно производит решение сигнатуры и промежуточные результаты отправляет в сеть в виде транзакций такого содержания. 

<table>
  <tr>
   <td> <strong> hash </strong> </td>
   <td colspan="3" ><strong>Qmsdkakad09sad0f9</strong>
   </td>
   <td><strong>id</strong>
   </td>
   <td colspan="2" >0x0001, 0x013
   </td>
   <td><strong>addr</strong>
   </td>
   <td colspan="2" >JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>message</strong>
   </td>
   <td colspan="3" >QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD
   </td>
   <td><strong>src</strong>
   </td>
   <td colspan="4" >JHGHGJHGHBHJHHHHBHBHBHBHBHBHBHBJHBHJBHJBJHBHYTFRDSEEWZXCHBIYUVVYCTYDYREXSYXYTCG
   </td>
  </tr>
  <tr>
   <td><strong>val</strong>
   </td>
   <td><strong>0.6</strong>
   </td>
   <td><strong>timestamp</strong>
   </td>
   <td>
        1515494426
   </td>
   <td colspan="2" ><strong>trunk</strong>
   </td>
   <td colspan="4" >QmAsaskakad09sad0f9
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>branch</strong>
   </td>
   <td colspan="2" >
   </td>
   <td colspan="2" ><strong>tag</strong>
   </td>
   <td colspan="4" >CIP_DKG_PARTH
   </td>
  </tr>
</table>


Её поля заполняются следующим образом (поле hash - это мульти-хеш транзакции в IPFS и создается ей при публикации):  
*   Id: версия и тип транзакции -часть сигнатуры мультиподписи,
*   Addr: адрес ноды валидатора,
*   Message: подпись с использованием приватного ключа и адреса trunk, 
*   Src: буфер, содержащий корень решения уравнения DKG  для ноды ,
*   Val: рейтинг ноды,
*   Timestamp: время создания транзакции,
*   Trunk: хеш адрес последней служебной транзакции (см. п4),
*   Tag: в принципе можно не заполнять.

После запуска, перед выполнением очередного расчета, смарт-контракт подсчитывает свой “баланс” решенных частей и рейтинга их валидаторов, и делает последнюю операцию  - создает прокси счет в сети Биткойн и генерирует квитанцию об этом в виде транзакции в сеть.

<table>
  <tr>
   <td>
<strong>hash</strong>
   </td>
   <td colspan="3" ><strong>Qmsdkakad09sad0f9</strong>
   </td>
   <td><strong>id</strong>
   </td>
   <td colspan="2" >0x0001, 0x015
   </td>
   <td><strong>addr</strong>
   </td>
   <td colspan="2" >JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>message</strong>
   </td>
   <td colspan="3" >QL9RL9BRVGUKNOS9BJPEZNW9NWXSJCBKOJLGASARQMPXVZYXMAYOJDXTSNRX9KMWZNTJRZMONURODNXSD
   </td>
   <td><strong>src</strong>
   </td>
   <td colspan="4" >JHGHGJHGHBHJHHHHBHBHBHBHBHBHBHBJHBHJBHJBJHBHYTFRDSEEWZXCHBIYUVVYCTYDYREXSYXYTCG
   </td>
  </tr>
  <tr>
   <td><strong>val</strong>
   </td>
   <td><strong>0</strong>
   </td>
   <td><strong>timestamp</strong>
   </td>
   <td>
        1515494426
   </td>
   <td colspan="2" ><strong>trunk</strong>
   </td>
   <td colspan="4" >QmAsaskakad09sad0f9
   </td>
  </tr>
  <tr>
   <td colspan="2" ><strong>branch</strong>
   </td>
   <td colspan="2" >
   </td>
   <td colspan="2" ><strong>tag</strong>
   </td>
   <td colspan="4" >CIP_PROXY_READY
   </td>
  </tr>
</table>

Её поля заполняются следующим образом (поле hash - это мульти-хеш транзакции в IPFS и создается ей при публикации):  
*   Id: версия и тип транзакции - Биткойн прокси счет для ноды addr готов,
*   Addr: адрес _ноды_, заказчика депозитного прокси счета,
*   Message: подпись с использованием приватного ключа последней ноды, которая выполнила открытие счета и адреса её trunk, 
*   Src: адрес прокси счета,
*   Val: ничего, 0,
*   Timestamp: время создания транзакции,
*   Trunk: хеш адрес последней служебной транзакции (см. п4) последней ноды, которая выполнила открытие счета ,
*   Tag: в принципе можно не заполнять.

После очередного подсчета баланса в кошельке _ноды_ будет приблизительно такая картина:

<table>
  <tr>
   <td>
#1
   </td>
   <td>S98C7CSSD9CJSCSMADKDSCJKJ
   </td>
   <td>EVEN
   </td>
   <td><strong>56.034</strong>
   </td>
  </tr>
  <tr>
   <td>#2
   </td>
   <td>
    028732468uhd2nun2imxmcmweokwg
   </td>
   <td>BTC
   </td>
   <td><strong>3.0012</strong>
   </td>
  </tr>
  <tr>
   <td>#3
   </td>
   <td>
    aakjdhcknieuuwfqvqjwcnsjdnjvsdvjdsvn
   </td>
   <td>Eth
   </td>
   <td><strong>43.45</strong>
   </td>
  </tr>
</table>

Брокерские счета:

<table>
<tr>
  <td>#1

   </td>
   <td>
    03l|KZmkmcalm4caskmI23mxslmxasc

   </td>
   <td>BTC

   </td>
   <td><strong>0.0</strong>

   </td>
</tr>
</table>

