({}).toString()

/\*\*

- Выполнить предудыщее задание с использование рекурсии
- то есть необходимо заходить внутрь каждого дочернего элемента
-
- @param {Element} where - где искать
-
- @example
- после выполнения функции, дерево <span> <div> <b>привет</b> </div> <p>loftchool</p> !!!</span>
- должно быть преобразовано в <span><div><b></b></div><p></p></span>
  \*/
  function deleteTextNodesRecursive(where) {
  for (var i = 0; i < where.childNodes.length; i++) {
  if (where.childNodes[i].nodeType === 3) {
  where.removeChild(where.childNodes[i]);
  i--;
  } else if (where.childNodes[i].nodeType === 1) {
  deleteTextNodesRecursive(where.childNodes[i]);
  }
  }
  console.log(where);
  }

/\*\*

- **_ Со звездочкой _**
- Необходимо собрать статистику по всем узлам внутри элемента root и вернуть ее в виде объекта
- Статистика должна содержать:
- - количество текстовых узлов
- - количество элементов каждого класса
- - количество элементов каждого тега
- Для работы с классами рекомендуется использовать свойство classList
- Постарайтесь не создавать глобальных переменных
-
- @param {Element} root - где собирать статистику
- @return {{tags: Object<string, number>, classes: Object<string, number>, texts: number}}
-
- @example
- для html <div class="some-class-1"><b>привет!</b> <b class="some-class-1 some-class-2">loftschool</b></div>
- должен быть возвращен такой объект:
- {
- tags: { DIV: 1, B: 2},
- classes: { "some-class-1": 2, "some-class-2": 1 },
- texts: 3
- }
  \*/
  let obj = {
  text: 0,
  tags: {},
  classes: {}
  };

function collectDOMStat(root) {
for (let i = 0; i < root.childNodes.length; i++) {
if (root.childNodes[i].nodeType === 3) {
obj.text += 1;
} else if (root.childNodes[i].nodeType === 1) {
collectDOMStat(root.childNodes[i]);
obj.tags[root.childNodes[i].tagName] = 0;
if (root.childNodes[i].getAttribute("class")) {
var myArr = root.childNodes[i].getAttribute("class").split(" ");
obj.classes[root.childNodes[i].getAttribute("class")] = 0;
}
}
}

console.log(obj);

return obj;
}

/\*\*

- **_ Со звездочкой _**
- Функция должна отслеживать добавление и удаление элементов внутри элемента where
- Как только в where добавляются или удаляются элемента,
- необходимо сообщать об этом при помощи вызова функции fn со специальным аргументом
- В качестве аргумента должен быть передан объек с двумя свойствами:
- - type: типа события (insert или remove)
- - nodes: массив из удаленных или добавленных элементов (а зависимости от события)
- Отслеживание должно работать вне зависимости от глубины создаваемых/удаляемых элементов
- Рекомендуется использовать MutationObserver
-
- @param {Element} where - где отслеживать
- @param {function(info: {type: string, nodes: Array<Element>})} fn - функция, которую необходимо вызвать
-
- @example
- если в where или в одного из его детей добавляется элемент div
- то fn должна быть вызвана с аргументов:
- {
- type: 'insert',
- nodes: [div]
- }
-
- ***
-
- если из where или из одного из его детей удаляется элемент div
- то fn должна быть вызвана с аргументов:
- {
- type: 'remove',
- nodes: [div]
- }
  \*/
  function observeChildNodes(where, fn) {}
