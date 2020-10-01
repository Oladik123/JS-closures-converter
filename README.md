# JS-closures-converter
<h2>Test task for Hot reload для Kotlin JS/WASM/Native project</h2>

<h3>Задание</h3>
Для JavaScript-подобного языка требуется преобразовать замыкания (функции, захватывающие внешние переменные) в простые функции верхнего уровня (в теле используются только параметры функции и объявленные внутри функции переменные, вложенные функции отсутствуют).

Пример:
function foo(a) {
  var b = 42;
  function bar(c) {
    return a + b + c;
  };
  return bar(24);
};


нужно преобразовать в

function bar(a, b, c) {
  return a + b + c;
};
function foo(a) {
  var b = 42;
  return bar(a, b, 24);
};

В тексте программы могут присутствовать объявления переменных (var x = y), декларации функций (function(x) {...}) на любых уровнях, вызовы функций, оператор “+”, числовые литералы, присваивания (x = y + 42). Другие синтаксические конструкции по желанию.
Для простоты можно считать, что функции только объявляются и вызываются. Других использований (в качестве аргументов вызова, возвращаемого значения, присваивания в переменные и т.д.) нет.
