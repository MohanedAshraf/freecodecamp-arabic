# كيف تعكس رقم باستخدام JavaScript

![How to reverse a number in JavaScript](https://cdn-media-1.freecodecamp.org/images/0*9bS6yWpHz8_tuY52)

by artismarti

#### أمثلة باستخدام دالة السهم(Arrow Function) والدالة العادية(Regular Function)

يعد عكس النص(String) أو الرقم(Number) أحد الأسئلة الشائعة التي يتم طرحها في مقابلات البرمجة. دعونا نلقي نظرة على كيفية القيام بذلك.

#### **القواعد / القيود**:

- الارقام السالبة يجب أن تظل سالبة.

**_مثال._** `12345-` _يصبح_ `54321-`

- يجب إزالة أي أصفار في بداية الرقم.

**_مثال._** `321000` _يصبح_ `123` ليس `000123`

- يمكن أن تقبل الدالة عددًا عشريًا (Float) أو عددًا صحيحًا (Integer).

**_مثال._** `543.2100` _يصبح_ `12.345`

- ستعيد الدالة الأعداد الصحيحة(Integers) كأعداد صحيحة(Integers).

**_مثال._** `54321` _يصبح_ `12345` ليس `12345.00`

#### **الحل باستخدام دالة السهم(Arrow Function):**

```js
const reversedNum = (num) =>
  parseFloat(num.toString().split('').reverse().join('')) * Math.sign(num);
```

#### **الحل باستخدام الدالة العادية (Regular Function):**

```js
function reversedNum(num) {
  return (
    parseFloat(num.toString().split('').reverse().join('')) * Math.sign(num)
  );
}
```

#### **_الاختلاف بين دالة السهم (Arrow Function) والدالة العادية(Regular Functio):_**

في هذا المثال ، الاختلاف الوحيد بين دالة السهم(Arrow Function) والدالة العادية(Regular Functio) هو أن الدالة العادية(Regular Function) تحتاج إلى توفير قيمة إرجاع (`return`) صريحة.

دوال الأسهم (Arrow Function) لهم قيمة إرجاع (`return`) ضمنية - عندما يتم كتابة محتوى الدالة في سطر واحد، دون الحاجة إلى الأقواس `{}`.

#### ** دعني أوضح لكَ الخطوات:**

- **حول الرقم(Number) إلى نص(String)**

دالة `()num.toString` تحول الرقم(Number) إلى نص(String). نقوم بذلك حتى نتمكن من استخدام دالة الانقسام (`split`) عليها بعد ذلك.

```js
let num = -5432100;
num.toString();

// num = '-5432100'
```

- **قسّم النص إلى مصفوفة(Array)**

دالة `('')num.split` تحول النص(String) إلى مصفوفة من الاحرف(Array of characters) . نقوم بذلك حتى نتمكن من استخدام دالة العكس (`reverse`) لأنها لا تعمل علي النص.

```js
// num = '-5432100'

num.split('');

// num = [ '-', '5', '4', '3', '2', '1', '0', '0' ]
```

- **اعكس المصفوفة(Array)**

دالة `()num.reverse` تعكس ترتيب العناصر في المصفوفة(Array).

```js
// num = [ '-', '5', '4', '3', '2', '1', '0', '0' ]

num.reverse();

// num = [ '0', '0', '1', '2', '3', '4', '5', '-' ]
```

- **حولها مرة أخرى إلى نص(String)**

دالة`('')num.join` تعيد تجميع الأحرف المعكوسة إلى نص(String).

```js
// num = [ '0', '0', '1', '2', '3', '4', '5', '-' ]

num.join('');

// num = '0012345-'
```

- **استخدام** [**Parse**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat) **لتحويل قيمة الادخال إلى عددًا عشريًا(Float):**

`parseFloat(num)` تحول `num` النص(String) إلى عددًا عشريًا(Float) .

```js
// num = '0012345-'

parseFloat(num);

// num = 12345
```

**ملاحظة**: دالة `parseFloat` تعمل في النهاية _(على الرغم من أنها في السطر الأول)_ على الرقم المعكوس وتزيل أي أصفار في البداية .

- **يضاعف الرقم الناتج بأشارة ([sign](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)) الرقم الاصلى — للحفاظ على القيمة السالبة .**

`num * Math.sign(num)` يضاعف الرقم بعلامة الرقم الأصلي.

```js
// original value of num = -5432100
// num = 12345

num * Math.sign(-5432100);

// num = -12345
```

وها هو لديك الرقم المعكوس بالنهاية!
