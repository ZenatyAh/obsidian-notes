---
Subject: Advanced React
Teacher: Sharehan monia
Time: "2: 10 : 00"
Start Date: 13 / 01 / 2026
---
---

> [!NOTE] Best Practice
> Push `empty file` to you Reop isn't best practice 
> Using built-in library and function is best  practice

## Dependency Inversion Principle (DIP):

The dependency inversion principle states that high level module don't depends on low level implementation details ,  instead both should demand on Abstraction.

DIP isn't just front-end Principle , it programming principle.


- الفكرة الرئيسية من هذا المفهوم: 
	- أن المكونات في الكود ليس لها أي وصول أو علاقة بكيفية جلب البيانات أو تخزينها.
	- أن لا يكون لهذا المكون وصول إلى البيانات التي تم جلبها من  `API` ,والتي لا يتعامل معها، وبيانه الآتي:
		يعني لو عندي مكون يعرض بيانات محددة تصل له من `API` ، و `API` يرسل بيانات أكثر مما يحتاج المكون لعرضه، فمفهوم `DIP` يقدم للمكون البيانات التي يحتاج لعرضها فقط دوناً عن باقي البيانات التي تم إرسالها.
- ما فائدة مفهوم `DIP` ؟
	1. المرونة `flexibility`  
	2. تساعد في اختبار الكود `Testing`
	3. يعتبر من المفاهيم الأساسية في `moduler based architecture` 
- من مظاهر عدم استخدام هذا المفهوم في الكود:
	- استخدام `useEffect` داخل `component` وإنشاء دالة `fetch API`.

كلما كنت قادر على الفصل `isolated` بين `high level & low level`  والاعتماد على `Abstraction`، كلما كان تطبيق مفهوم `DIP` أكبر وأفضل.


---
# Data Transfer object:

#### فوائد الاستخدام:
- وضع شكل كتابة البيانات وفق رغبة الفرونت اند ، وتجنب فرض شكل البيانات من الباك اند، فمثلاً : لو كانت البيانات من السيرفر مكتوبة بصيغة `Snack_Case` ، وفي الفرونت اند مكتوبة بصيغة `CamleCase` ، فهذا المفهوم يعطيني المرونة لكتابة شكل البيانات وفق رغبتي.
- أي تغيير في شكل البيانات من السيرفر يتم تغييره في ملف واحد في الفرونت، دون حاجة للتغير في كل الملفات التي استخدمت البيانات بشكلها القديم.
- استخلاص البيانات يلي محتاجها فقط من البيانات القادمة من السيرفر، والتغيير بشكلها وفق الحاجة. 
- عزل `business logic` عن المكونات وعدم تطرق المكون لتفاصيلها. repository

- في التطبيق العملي للمفهوم، قمنا بتغيير اسم مجلد `APIs` إلى `repository` لأن هذا المجلد أصبح يحتوي على منطقين : `APIs & Abstractions` .
- مجلد `APIs` يمكنك تسميته `restComponent.ts` لتطبيق `APIs`
- تم إنشاء مجلد آخر  تحت اسم `ComponentsRepository.ts`  لتطبيق `Abstraction` ، وفي هذا المجلد نقوم بإنشاء `TS Interface` تحتوي بداخلها على كل الدوال التي سيتم استخدامها عند التعامل بين `Component & APIs`

لاحظ في الكود الآتي، كيفية تسمية الدوال التي تم تعريفها ، حيث تم الاستناد الى اسم الأب كمرجعية دون تمييز كامل للاسم.
```ts
export interface Productsrepository {
getAll : Promise<Product[]>
// getAllProducts : Promise <Product[]> // falsy nameing
}
```

### Steps for create DIP :
1. create abstraction
2. create APIs fetch
3. Inject code
4. create custom hook
5. import hook in main module component file `index.ts`
6. inject Abstraction  in main module file `index.ts`

   ```ts
   const ProductsContext = createContext<Productsrepository | null>(null);
	type ProductsProviderProps = PropsWithChildren<{
	value: Productsrepository;
}>;
   ```
   
7. edit `ProductsProvider` in `main.ts` file
---
```ts
import type { Productsrepository } from "./repositoryProducts";

import type { Product } from "../Types/product";

const BaseUrl = "https://dummyjson.com/products";

  

export const restProducts = (): Productsrepository => {

return {

getAll: async (): Promise<Product[]> => {

const response = await fetch(BaseUrl);

  

if (!response.ok) {

throw new Error("Failed to fetch data");

}

  

return response.json().then((data) => data.products);

/*

const data = await response.json();

return data.products;

*/

},

};

};
```

## الفكرة العامة للكود

هذا الملف يبني **Repository** (مستودع بيانات) اسمه `restProducts`:

- هدفه يتعامل مع API خارجي (REST)
    
- ويوفّر دوال جاهزة (هنا فقط: `getAll`)
    
- ويرجع بيانات المنتجات على شكل `Product[]`
    

يعني بدل ما كل مكان بالتطبيق يكتب `fetch(...)`، أنت تحطها هنا، والباقي يستدعي `getAll()` فقط.

---

## شرح سطر بسطر

### 1) استيراد أنواع فقط (Type-only imports)

`import type { Productsrepository } from "./repositoryProducts"; import type { Product } from "../Types/product";`

- `import type` يعني: **استيراد للأنواع فقط** (Types) وليس كود فعلي وقت التشغيل.
    
- TypeScript يستخدمها للتأكد من صحة الأنواع (type checking)، لكنها ما تدخل في ملف JS النهائي عند البناء.
    

**Productsrepository** غالبًا هو interface مثل:

`export interface Productsrepository {   getAll: () => Promise<Product[]>; }`

و**Product** هو type/واجهة تمثل شكل المنتج (id, title, price … إلخ).

---

### 2) ثابت رابط الـ API

`const BaseUrl = "https://dummyjson.com/products";`

هذا رابط endpoint يرجع بيانات المنتجات من موقع dummyjson.

---

### 3) تعريف دالة `restProducts`

`export const restProducts = (): Productsrepository => {`

- `export` يعني تقدر تستوردها في ملفات ثانية.
    
- `restProducts` دالة **ترجع كائن** مطابق لـ `Productsrepository`.
    
- `(): Productsrepository` معناها: TypeScript يتوقع إن الناتج يطابق شكل الـ repository المطلوب.
    

يعني لما تكتب:

`const repo = restProducts();`

`repo` بيكون عنده دوال زي `getAll`.

---

### 4) إرجاع كائن فيه دالة getAll

`return {   getAll: async (): Promise<Product[]> => {     ...   }, };`

هذا object literal فيه مفتاح `getAll`.

- `getAll` عبارة عن دالة `async`
    
- ترجع `Promise<Product[]>`
    

يعني: لما تنادي `getAll()` لازم تستخدم `await` أو `.then()`.

---

## داخل getAll بالتفصيل

### 5) إرسال طلب fetch

`const response = await fetch(BaseUrl);`

- `fetch` يرسل HTTP request للرابط.
    
- يرجع `Response` object.
    
- `await` توقف التنفيذ لين يرجع الرد.
    

---

### 6) التأكد إن الرد ناجح

`if (!response.ok) {   throw new Error("Faild to fetch data"); }`

- `response.ok` تكون `true` إذا الحالة HTTP بين 200 و 299.
    
- إذا فشل الطلب (مثلاً 404 أو 500) يرمي `Error`
    
- رمي الخطأ يعني أي كود يستدعي `getAll()` لازم يكون عنده try/catch أو يعالج الخطأ.
    

---

### 7) تحويل الرد إلى JSON ثم استخراج المنتجات

`return response.json().then((data) => data.product);`

هنا نقطتين مهمتين:

1. `response.json()` ترجع Promise فيها البيانات كـ object
    
2. `.then((data) => ...)` تاخذ البيانات بعد ما تتحول
    

لكن… **فيه احتمال كبير إن هذا السطر فيه خطأ**.

### ✅ dummyjson endpoint يرجع عادة:

`https://dummyjson.com/products` يرجع شيء مثل:

`{   "products": [ ... ],   "total": 100,   "skip": 0,   "limit": 30 }`

يعني المفتاح هو **products** وليس **product**.

فالغالب الصحيح يكون:

`return response.json().then((data) => data.products);`

أو بأسلوب أوضح وأبسط باستخدام await بالكامل (أفضل):

`const data = await response.json(); return data.products;`

---

## نسخة محسّنة (أوضح + بدون then)

هذه نفس فكرتك لكن أسهل قراءة وأقل أخطاء:

`export const restProducts = (): Productsrepository => {   return {     getAll: async (): Promise<Product[]> => {       const response = await fetch(BaseUrl);        if (!response.ok) {         throw new Error("Failed to fetch data");       }        const data = await response.json();       return data.products; // لاحظ products     },   }; };`

---

## كيف يُستخدم هذا الكود؟

مثال:

`const repo = restProducts();  async function load() {   try {     const products = await repo.getAll();     console.log(products);   } catch (e) {     console.error(e);   } }`

---

## خلاصة سريعة

- `restProducts` يبني Repository للتعامل مع REST API
    
- `getAll` تنفذ fetch وتتحقق من النجاح
    
- تحول الرد JSON وترجع مصفوفة `Product[]`
    
- **غالبًا لازم تغير `data.product` إلى `data.products`**

---

**inject = أحقن / أمرّر / أزوّد**

برمجيًا:

> **أعطي كودًا كودًا آخر شيء يحتاجه بدل ما يبنيه بنفسه**\

---
