## Подключение ноды к приватной сети

Повторюсь, что единственным электронным документом, подтверждающим правомерность действий пользователя в нашей сети является подписанная совместимой с протоколом приватным ключом транзакция в блокчейне.
Для подключения к сети нода публикует в сети первую транзакцию о намерении стать её участником следующего вида. 
Валидировать её кому-то, кроме самого инициатора - не надо. 

<table>
  <tr>
   <td><strong><code>hash</code></strong>
   </td>
   <td colspan="3" ><strong><code>Qmsdkakad09sad0f9</code></strong>
   </td>
   <td><strong><code>id</code></strong>
   </td>
   <td colspan="2" ><code>0x0001, 0x002</code>
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
   <td colspan="4" >
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
<code>Y</code>
   </td>
   <td colspan="2" ><strong><code>tag</code></strong>
   </td>
   <td colspan="4" ><code>NEW_REG</code>
   </td>
  </tr>
</table>



О том, какие операции производит _нода_ - подробнее:


*   Модуль кошелька генерирует детерминированную ключевую пару для идентификации в сети и управления _всем_: счетами, транзакциями и т.д;
*   Создает приватный раздел INBOX и получает его IPFS адрес и вставляет его в поле trunk,
*   Генерирует подпись, используя приватный ключ и адрес trunk, помещает ее в поле message,
*   Указывает тип транзакции 0x002 (все типы просто сведем в таблицу далее),
*   Формирует объект IPFS и публикует транзакцию в сети.

    Что на самом деле произошло?


    Сеть получила подтвержденное уникальным ключом сообщение о том, что: “Раздел по адресу **<code>QmAsaskakad09sad0f9 </code></strong>принадлежит <strong><code>JHYLDJCBBTSFGVTBONTIVOWURCWMWBGGVRTOAMTKKFHWJAJHKKPWEYTAVDXMUSJBIUYEVZMO9LXBWHTUZ </code></strong>и он готов к работе”.


    Все последующие мета-транзакции, связанные с:

*   Изменением статуса ноды,
*   Демонстрации действий или намерений,
*   Сохранением служебной информации, статистики и отладочной информации

    будут ссылаться в корне именно на эту транзакцию.


