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
