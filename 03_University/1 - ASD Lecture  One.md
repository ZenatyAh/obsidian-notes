
# 🎯 **ما المراحل التي يمر بها المنتج البرمجي من فكرة إلى منتج فعلي؟**

المنتج البرمجي لا يُبنى بشكل عشوائي؛ بل يمرّ خلال **دورة حياة التطوير Software Development Life Cycle – SDLC**.  
قد تختلف التفاصيل حسب المنهجية (Waterfall – Agile – Scrum)، ولكن **المراحل الأساسية ثابتة**.

أناقشها معك الآن بالترتيب المنهجي الصحيح:

---

# 🔶 **1) مرحلة جمع المتطلبات – Requirements Engineering**

هذه المرحلة هي **أهم مرحلة** في أي مشروع لأنها تترجم فكرة العميل إلى "مستند رسمي" يشرح:

- ماذا يريد العميل؟
    
- من هم المستخدمون؟
    
- ما الوظائف المطلوبة (Functional Requirements)؟
    
- ما القيود والجودة المطلوبة (Non-Functional Requirements)؟
    
- ما حدود النظام؟
    

**ناتج هذه المرحلة:**

- SRS – Software Requirements Specification
    
- User Stories (في Agile)
    

> الخطأ في هذه المرحلة يعني خراب باقي المشروع.

---

# 🔶 **2) مرحلة التصميم – System Design / Architecture**

بعد معرفة المتطلبات، ننتقل من "ما الذي نريده" إلى "كيف سنبنيه".

تشمل:

- تصميم الواجهات UX/UI
    
- تصميم الـArchitecture (Layered, Microservices …)
    
- رسم UML Diagrams:
    
    - Use Case
        
    - Class Diagram
        
    - Sequence
        
    - Activity
        

**ناتج المرحلة:**  
System Architecture + Design Document

---

# 🔶 **3) مرحلة البرمجة – Implementation / Coding**

الآن يبني الفريق النظام كما تم تصميمه بالضبط.

تشمل:

- كتابة الكود
    
- تطبيق الـDesign Patterns المناسبة
    
- بناء الـAPIs
    
- ربط الواجهة بالباك إند
    
- إدارة الـVersion Control (Git)
    

**ناتج المرحلة:**  
Product Source Code

---

# 🔶 **4) مرحلة الاختبار – Testing / QA**

تهدف إلى التأكد من أن المنتج:

- يعمل كما هو مكتوب في الـSRS
    
- خالٍ من البقز
    
- يلبي توقعات العميل
    

أنواع مهمة:

- Unit Testing
    
- Integration Testing
    
- System Testing
    
- Acceptance Testing (UAT)
    

**ناتج المرحلة:**  
Test Report + Verified Build

---

# 🔶 **5) مراجعة الجودة – Review**

تشمل:

- Code Review
    
- Security Review
    
- Architecture Review
    
- UX Review
    

تهدف لتحسين الجودة قبل الإطلاق.

---

# 🔶 **6) النشر – Deployment**

بعد اجتياز الاختبارات:

- يتم رفع النظام على بيئة الإنتاج
    
- إعداد السيرفرات
    
- إعداد قواعد البيانات
    
- تهيئة الـCI/CD
    

---

# 🔶 **7) الصيانة – Maintenance**

غالباً الطلاب ينسون هذه المرحلة رغم أنها الأكبر زمناً في العالم الحقيقي.

تشمل:

- إصلاح الأخطاء بعد الإطلاق
    
- تحسينات مستقبلية
    
- تحديثات أمنية
    
- دعم المستخدمين
    

---

# 🔶 **8) التطوير المستمر – Iterations**

إذا كنا نعمل وفق Agile/Scrum:  
كل أسبوعين يوجد Sprint يتكرر فيه:  
Requirements → Design → Coding → Testing → Deployment (Small)

---

# 📌 الترتيب النهائي النموذجي:

**Requirements → Design → Development → Testing → Review → Deployment → Maintenance**

---
# ما الفرق بين المتطلبات الوظيفية Functional والمتطلبات غير الوظيفية Non-Functional؟

## 🔹 **1) المتطلبات الوظيفية vs غير الوظيفية**

### ✔ إجابتك صحيحة

لكن أضيف لك طريقة أكاديمية دقيقة لشرحها:

### **Functional Requirements**

هي ما يجب على النظام أن يفعله.  
تعبر عن **السلوك Behavior** و **الوظائف الأساسية**.

مثالك جيد، ولو أعدناه بصياغة أكاديمية يصبح:

> "يجب أن يوفّر النظام وظيفة توليد كلمة مرور جديدة عند طلب المستخدم."

### **Non-Functional Requirements**

هي _كيف_ يجب أن يعمل النظام، وليس _ماذا يفعل_.  
تشمل: الأداء، السرعة، الأمان، قابلية التوسع، الجودة.

مثلاً:

> "يجب أن يتم توليد كلمة المرور خلال أقل من 1 ثانية"  
> "يجب تشفير بيانات المستخدمين عبر AES-256"

✔ إجابتك 100%، فقط أعدنا صياغتها أكاديمياً.

---
# أعطني مثالين على مستندات تنتج من مرحلة التصميم، واذكر ما فائدة كل واحد منها ؟

## 🔹 **2) المستندات الناتجة عن مرحلة التصميم**

✔ **System Architecture**  
✔ **Design Document (UML & more)**

تمام عليك، فقط أضيف لك نقطتين مهمتين:

### **System Architecture Document**

يحتوي:

- Architecture Pattern (مثل Layered, Clean, Microservices)
    
- Technologies
    
- Components Diagram
    
- Deployment Diagram
    

### **Design Document**

يحتوي:

- UML Diagrams
    
- Class Diagram
    
- Sequence Diagram
    
- Activity Diagram
    
- Database ERD (أحياناً)
    
---
# إذا اكتشفت أن المتطلبات التي أعطاك إياها العميل غير واضحة أو غير مكتملة، ما أفضل طريقة (منهجية أو تقنية) لمعالجة ذلك قبل أن ينهار المشروع بالكامل؟

## 🔹 **3) إذا كانت المتطلبات غير واضحة**

إجابتك **ممتازة جداً** وتشبه الطرق المتبعة فعلاً في Requirement Engineering.

دعني أصيغها لك بطريقة "احترافية" كما تُكتب في التقارير:

### **طرق معالجة المتطلبات غير الكاملة:**

1. **Conduct stakeholder interviews**  
    مقابلات مع الطاقم أو المستخدمين المستهدفين.
    
2. **Workshops and brainstorming**  
    ورشات مع الفريق لتوليد أفكار وحلول.
    
3. **Observation**  
    مراقبة سير العمل الحقيقي (خصوصاً في المستشفيات والبنوك).
    
4. **Study similar systems**  
    مقارنة النظام بنظم موجودة للحصول على تصور واضح.
    
5. **Prototyping**  
    بناء نموذج أولي (Prototype) ليتفاعل معه العميل ويوضح المتطلبات.
    

✔ إجابتك قوية—أضف فقط “Prototyping” لأنها مهمة جداً عملياً.

---
# 🎯 **كيف تؤثر المتطلبات غير الوظيفية (NFRs) على تصميم وهيكلية النظام؟**

المتطلبات غير الوظيفية ليست مجرد “تفاصيل”؛  
هي **القوة التي تشكّل بنية النظام بالكامل**.

في الحقيقة:

> **80% من قرارات الـArchitecture تُتخذ بسبب NFRs وليس الـFunctional Requirements.**

### مثال بسيط:

- “النظام يقدم تقارير PDF” → Functional
    
- “يجب أن يخدم 100 ألف مستخدم متزامن” → Non-Functional  
    وهذا المتطلب الأخير سيغيّر كل شيء: طريقة التصميم، نوع قواعد البيانات، الـLoad Balancing، الكاش، السيرفرات…إلخ.
    

---

# 🔵 **أولاً: التأثير الإيجابي للـNFRs على تصميم النظام**

## 1) **تحسين قابلية التوسع (Scalability)**

إذا كان المتطلب:

- “النظام يجب أن يدعم 50 ألف مستخدم متزامن”
    

سيؤدي ذلك إلى:

- استخدام Microservices بدل Monolithic
    
- Use of Load Balancer
    
- استخدام NoSQL مثل MongoDB بدل SQL العادي
    
- استخدام Queue مثل RabbitMQ
    

👉 هذا تأثير **إيجابي** لأنه يؤدي لتصميم مرن وقابل للتوسع.

---

## 2) **تحسين الأداء (Performance)**

NFR مثل:

- “الاستجابة يجب أن تكون أقل من 200ms”
    

سيجعل المصمم:

- يستخدم Cache (Redis)
    
- يقلل الـAPI calls
    
- يختار خوارزميات أسرع
    
- يطبّق CDN
    

👉 هذا يرفع جودة الأداء.

---

## 3) **رفع مستوى الأمان Security**

NFR:

- “يجب تشفير كل البيانات أثناء النقل”
    

يؤدي إلى:

- استخدام HTTPS
    
- تشفير JWT
    
- Access Control Layers
    
- Identity Provider
    

👉 يؤدي إلى تصميم آمن وبنية أقوى.

---

## 4) **تحسين قابلية الصيانة (Maintainability)**

NFR:

- “النظام يجب أن يكون قابلاً للصيانة خلال أسبوع لأي ميزة جديدة”
    

سيجبر الفريق على:

- كتابة Clean Code
    
- تطبيق Design Patterns
    
- التقليل من الـCoupling
    
- العمل وفق Architecture واضحة (مثل Layered)
    

---

# 🔴 **ثانياً: التأثير السلبي (حين تكون الـNFRs غير منطقية أو مبالغ فيها)**

### أحياناً الـNFRs تسبب مشاكل… إذا كانت:

- غير واقعية
    
- غير قابلة للقياس
    
- أو مكلفة جداً بدون داعٍ
    

## 1) **زيادة التكلفة بلا داعٍ**

مثال:

- “النظام يجب أن يعمل 24/7 بدون أي Downtime”
    

هذا يتطلب:

- Servers redundant
    
- Load balancers
    
- Database replication
    
- DevOps متخصص
    
- Monitoring systems
    

لكن لو النظام “لإدارة مدرسة صغيرة” فهذا Overkill.

👉 تأثير سلبي: **زيادة التكلفة والتعقيد بدون فائدة.**

---

## 2) **تعقيد هندسي غير مبرّر (Over-Engineering)**

NFR:

- “النظام يجب أن يكون scalable لمليون مستخدم”
    

والعميل لديه 200 مستخدم فقط.

هنا الفريق سيذهب نحو:

- Microservices
    
- Distributed systems
    
- Message Queues
    
- Service mesh
    

مع أن الحاجة بسيطة.

👉 يؤدي إلى نظام معقد وصعب الصيانة.

---

## 3) **بطء في التطوير**

NFR مبالغ فيه مثل:

- “يجب أن يستجيب النظام في أقل من 10ms”
    

هذا سيؤدي إلى:

- اختيار تقنيات معقدة
    
- كتابة كود optimization صعب
    
- تأخير التسليم
    

👉 تأثير سلبي: **التطوير يصبح أبطأ وأكثر صعوبة.**

---

## 4) **التصادم بين NFRs أنفسها**

أحياناً NFR يضرب NFR آخر.

مثال:

- “النظام سريع جداً”
    
- “النظام آمن جداً”
    

الأمان يضيف:

- encryption
    
- token validation
    
- firewall
    

وهذه كلها تبطئ النظام.

👉 يؤثر سلباً إذا لم يتم تحقيق توازن.

---
# 🎯 **ما معنى أن الـDesign Patterns “متداخلة” بين مرحلة التصميم ومرحلة كتابة الكود؟**

الـDesign Patterns ليست شيئاً يحدث في مرحلة واحدة فقط من المشروع،  
بل هي **جسر يربط بين مرحلتي Design و Implementation**.

بشكل مبسط:

> **الـPattern يُفكَّر به أثناء التصميم… ويُطبَّق أثناء كتابة الكود.**

وهذا ما يخلق “التداخل”.

دعنا نفهمه بالتفصيل 👇

---

# 🔵 أولاً: في مرحلة التصميم (Design Phase)

في هذه المرحلة لا يوجد كود بعد.  
لكن المصمم (Architect / Senior) يحدد:

- كيف يتفاعل الكائنات مع بعضها؟
    
- أين أحتاج مرونة؟
    
- أين أحتاج فك ارتباط (Loose Coupling)؟
    
- هل النظام يحتاج Strategy؟
    
- هل أحتاج Factory لإدارة إنشاء الأشياء؟
    
- هل يجب حماية الوصول عبر Proxy؟
    

الـPatterns هنا تصبح **قرارات هندسية** فقط، مثل:

> “هنا نستخدم Strategy لأننا نريد استبدال الخوارزمية دون لمس الكود الأساسي.”

أو:

> “هنا Factory لأننا نريد التحكم بإنشاء الكائنات.”

هنا الـPattern مجرد **مفهوم وتصميم UML**.

---

# 🔵 ثانياً: في مرحلة البرمجة (Implementation)

الآن يأتي دور الـDeveloper…  
ويحوّل القرار التصميمي إلى كود فعلي:

- ينشئ Interface لـStrategy
    
- يكتب Concrete Strategies
    
- يربطها في الـContext
    
- يطبق Factory Method
    
- يكتب Singleton
    
- يطبق Observer
    

هنا الـPattern يصبح **Code Structure**.

---

# 🔶 إذن ما معنى أن الـPattern متداخل بين المرحلتين؟

معناه:

# 🟣 **Decision في التصميم → Implementation في الكود**

طالما أن الـPattern قرار Design،  
لكن لا يظهر أثره الحقيقي إلا عندما تكتب الكود،  
فهو إذن **متداخل بطبيعته بين المرحلتين**.

الـDesign Pattern ليس “تصميماً فقط”  
وليس “كوداً فقط”  
بل **فكرة Design تتحقق عبر كود فعلي**.

---

# 🟫 مثال بسيط يوضح التداخل

## ✨ أثناء التصميم:

تعمل UML وتقول:

`Duck (Context) FlyBehavior (Interface) FlyWithWings / FlyNoWay (Concrete Strategies)`

## ✨ أثناء البرمجة:

تكتب الكود:

`interface FlyBehavior {     void fly(); }  class FlyWithWings implements FlyBehavior {     public void fly() { System.out.println("Flying"); } }`

لاحظ:

- نفس البنية التي صممتها في UML
    
- هي نفسها التي كتبتها ككود
    

هذا هو **التداخل الحقيقي**.

---

# 🔴 لماذا _المساقات الجامعية_ تقول أنها “متداخلة”؟

لأن الـPatterns:

- **تُفهم في التصميم**
    
- **تُطبق في الكود**
    

فهي ليست 100% Design → وليست 100% Code  
بل **جزء من كليهما**.

---
# 🍝 **ما هو Spaghetti Code؟**

**Spaghetti Code** هو مصطلح يُستخدم لوصف كود:

- غير منظم
    
- معقد
    
- مترابط بشكل فوضوي بين أجزائه
    
- صعب القراءة
    
- صعب التعديل
    
- أي تغيير بسيط فيه قد يسبب انهيار أجزاء أخرى
    

سُمّي “سباغيتي” لأنه يشبه طبق السباغيتي:  
**مجموعة خطوط متشابكة لا تعرف أين يبدأ الواحد منها وأين ينتهي الآخر.**

---

# 🔴 **خصائص Spaghetti Code**

1. **لا يوجد فصل للمهام (No Separation of Concerns)**  
    كلاس واحد يفعل كل شيء.
    
2. **High Coupling**  
    كل جزء يعتمد على كل جزء → أي تغيير يؤدي لانهيارات.
    
3. **لا يوجد Design Patterns**  
    لا Strategy  
    لا Factory  
    لا Observers  
    لا SOLID  
    فقط كود ملخبط.
    
4. **أسماء متغيرات ودوال غير واضحة**  
    مثل:
    

`function x(a, b) { ... }`

5. **تكرار الأكواد (Duplicated Code)**  
    نفس الـlogic مكتوب 4 مرات.
    
6. **غياب التعليقات والـDocumentation**
    

---

# 🔥 **أمثلة على Spaghetti Code**

## مثال بسيط (JavaScript)

`function calculateTotal(a, b, tax) {   if (tax) {     return a + b + (a + b) * 0.16;   } else {     return a + b;   } }`

بعد فترة… شخص آخر يحتاج خصم:

`function calculateTotal(a, b, tax, discount) {   if (tax) {     if (discount) {       return a + b + (a + b) * 0.16 - discount;     } else {       return a + b + (a + b) * 0.16;     }   } else {     if (discount) {       return a + b - discount;     } else {       return a + b;     }   } }`

هكذا يبدأ السباغيتي الحقيقي:  
**شروط داخل شروط داخل شروط → كود غير قابل للفهم ولا التطوير.**

---

# 🟢 **ما سبب ظهور Spaghetti Code؟**

1. استعجال في التطوير
    
2. غياب الArchitecture
    
3. عدم استخدام Design Patterns
    
4. فريق غير منسق
    
5. متطلبات تتغير كثيراً دون refactoring
    
6. مطور جديد لا يعرف الـSOLID
    

---

# 🟦 **كيف نمنع Spaghetti Code؟**

- تطبيق **SOLID**
    
- اعتماد **Design Patterns** المناسبة
    
- كتابة كود نظيف Clean Code
    
- فصل المهام (Layered Architecture)
    
- استخدام OOP بشكل صحيح
    
- عمل Refactoring مستمر

---
# موضوع   `design pattern` مترابط بموضوع `oop` لذلك سنقوم بمراجعة له

## **1️⃣ Introduction to OOP & UML**

- **OOP (Object-Oriented Programming)**: طريقة تفكير وتصميم البرمجيات تعتمد على **الكائنات (Objects)** التي تمثل مفاهيم حقيقية أو منطقية.
    
- **UML (Unified Modeling Language)**: لغة نمذجة تستخدم لتصميم النظام قبل كتابة الكود. تساعد على **تصور النظام وفهم علاقات الكائنات**.
    

**Key Idea:** UML ليس للكود نفسه، بل لتمثيل الهيكلية والسلوكيات بطريقة **مرئية ومنظمة**.

- فكر فيها كخريطة قبل أن تبني المدينة.
    

---

## **2️⃣ Class Diagrams**

- **Class Diagram**: يوضح الكلاسات في النظام وارتباطاتها.
    
- **Class (الفئة):** وصف لمجموعة من الكائنات التي تشترك في **خصائص (attributes)** و**سلوكيات (operations)**.
    
- **Graphical Representation:** مستطيل يحتوي على 3 أقسام:
    
    1. الاسم في الأعلى
        
    2. الخصائص في المنتصف
        
    3. العمليات في الأسفل
        

**مثال:**

```pgsql
+-----------------+
| Person          |   <-- Class Name
+-----------------+
| + name: String  |   <-- Attributes
| # birthdate:Date|
| - ssn: Id       |
+-----------------+
| + getName():Str |   <-- Operations
| + setName(name) |
+-----------------+
```

---
## **Modifiers in UML & OOP: public, private, protected**

### **1️⃣ Public (`+`)**

- **الوصف:** الكائن أو الخاصية متاحة **لأي كلاس آخر في البرنامج**.
    
- **الهدف:** إعطاء الوصول الكامل من أي مكان.
    
- **مثال UML:**
    

`+ name: String`

- **في Java:**
    

`public String name;`

- **متى نستخدمه؟**
    
    - للخصائص أو الدوال التي يحتاج أي كلاس آخر الوصول إليها مباشرة، مثل `getName()` في الكائنات العامة.
        

---

### **2️⃣ Private (`-`)**

- **الوصف:** الكائن أو الخاصية متاحة **فقط داخل الكلاس نفسه**.
    
- **الهدف:** حماية البيانات ومنع أي كلاس خارجي من تعديلها مباشرة.
    
- **مثال UML:**
    

`- ssn: Id`

- **في Java:**
    

`private String ssn;`

- **متى نستخدمه؟**
    
    - للبيانات الحساسة أو التي يجب التحكم بها فقط من خلال **Methods** داخل الكلاس.
        
    - مثال: رقم الهوية أو كلمة المرور.
        

---

### **3️⃣ Protected (`#`)**

- **الوصف:** الكائن أو الخاصية متاحة **داخل الكلاس نفسه وأيضًا subclasses الموروثة منه**.
    
- **الهدف:** السماح بالوراثة دون فتح الوصول العام.
    
- **مثال UML:**
    

`# birthdate: Date`

- **في Java:**
    

`protected Date birthdate;`

- **متى نستخدمه؟**
    
    - عندما تريد للكلاسات الموروثة أن تتعامل مع الخاصية مباشرة، لكن تمنع الوصول من كائنات أخرى خارج الهيكل الوراثي.
        

---

### **مقارنة بسيطة (جدول)**

|Modifier|الوصول|مثال UML|مثال Java|
|---|---|---|---|
|public|أي كلاس|`+ name: String`|`public String name;`|
|private|نفس الكلاس فقط|`- ssn: Id`|`private String ssn;`|
|protected|الكلاس + subclasses|`# birthdate: Date`|`protected Date birthdate;`|

**نصيحة تصميمية:**

- دائمًا اجعل البيانات **private** ووفّر **getter/setter methods** للوصول الآمن.
    
- استخدم **protected** فقط للوراثة، و **public** للواجهات Methods التي يجب أن يعرفها الجميع.
    

---
#   ضوابط التسمية في `class, arrtibute & behaviour` ؟

## **1️⃣ Naming Conventions for Classes**

- **الهدف:** جعل الاسم واضحًا ويدل على الكائن أو المفهوم الذي يمثله.
    
- **ضوابط:**
    
    1. **اسم مفرد:** عادة يمثل **مفهوم واحد**، مثال: `Person`، `Car`, `Invoice`.
        
    2. **Capitalization:** **PascalCase** (كل كلمة تبدأ بحرف كبير)، مثال: `BankAccount`, `StudentRecord`.
        
    3. **Avoid abbreviations:** إلا إذا كانت معروفة عالميًا، مثال: استخدم `Customer` وليس `Cust`.
        
    4. **اسم معبر:** يجب أن يوضح **المسؤولية أو الدور** للكلاس، مثال: `OrderProcessor` واضح أنه مسؤول عن معالجة الطلبات.

---

## **2️⃣ Naming Conventions for Attributes (Properties/Fields)**

- **الهدف:** وصف بيانات الكائن بوضوح.
    
- **ضوابط:**
    
    1. **اسم مفرد:** يعكس خاصية واحدة، مثال: `name`, `birthDate`, `accountNumber`.
        
    2. **camelCase:** تبدأ بحرف صغير، مثال: `firstName`, `totalAmount`.
        
    3. **Avoid ambiguity:** الاسم يجب أن يكون **مفهومًا بدون الحاجة لشرح إضافي**.
        
    4. **Optional type annotation:** في UML تكتب `attributeName: Type`, مثال: `name: String`.
    
---

## **3️⃣ Naming Conventions for Behaviors (Operations/Methods)**

- **الهدف:** وصف السلوك أو الفعل الذي ينفذه الكائن.
    
- **ضوابط:**
    
    1. **Action verb:** اسم الفعل يعكس ما تقوم به الدالة، مثال: `calculateSalary()`, `deposit(amount)`, `sendEmail()`.
        
    2. **camelCase:** تبدأ بحرف صغير، مثال: `getName()`, `setAddress()`.
        
    3. **Parameters clear:** إذا هناك مدخلات، سميها بوضوح، مثال: `deposit(amount: double)`.
        
    4. **No abbreviations unless obvious:** مثال: استخدم `calculateInterest()` وليس `calcInt()`.
        
- **مثال UML:
```scss
+ getName(): String
+ setAddress(address: Address)
```

|Element|Naming Style|Example UML|Notes|
|---|---|---|---|
|Class|PascalCase|`BankAccount`|اسم مفرد وواضح|
|Attribute|camelCase|`firstName: String`|يعكس خاصية واحدة|
|Operation|camelCase + Verb|`calculateSalary(): double`|يعكس الفعل والسلوك|

---
## **استنباط Class Diagram (من أين تأتي الكلاسات والعلاقات)**

### **1️⃣ المصادر الأساسية للكلاس دياجرام**

Class Diagram لا يُكتب من الفراغ، بل يُستنبط من:

1. **Requirements / Use Cases (المتطلبات وحالات الاستخدام)**
    
    - عندما تحدد **ماذا يفعل النظام**، يمكنك استخراج الكائنات (Objects) التي يحتاجها النظام.
        
    - مثال: إذا كان لدينا نظام مصرفي:
        
        - Use Case: “Deposit Money”
            
        - Objects: `Account`, `Customer`, `Transaction`
            
    - هنا كل Object يصبح Class محتمل.
        
2. **Analysis Models (نماذج التحليل)**
    
    - أثناء التحليل، تصنع **Conceptual Model** أو **Domain Model**:
        
        - تمثل الكائنات والمفاهيم الأساسية في العالم الحقيقي.
            
        - مثال: في نظام مستشفى، الكائنات: `Patient`, `Doctor`, `Appointment`.
            
3. **Real-World Entities / Business Objects**
    
    - الكائنات التي توجد فعليًا في المجال الذي تصممه.
        
    - مثال: Bookstore → `Book`, `Publisher`, `Author`.
        
4. **Interactions / Relationships**
    
    - بعد تحديد الكلاسات، تفكر **كيف تتفاعل مع بعضها**:
        
        - Association: `Customer` has `Account`
            
        - Aggregation / Composition: `Book` composed of `Chapter`
            
        - Generalization: `SavingsAccount` extends `Account`
            

---

### **2️⃣ خطوات عملية لاستنباط Class Diagram**

1. **جمع المتطلبات بدقة**
    
    - قوائم Use Cases، قصص المستخدم، الوثائق.
        
2. **تحديد الكائنات الأساسية (Candidate Classes)**
    
    - كل noun (اسم) في متطلباتك غالبًا يمثل Class محتمل.
        
    - مثال: “Customer places Order” → Classes: `Customer`, `Order`.
        
3. **تحديد الخصائص والسلوكيات**
    
    - Attributes: data (الصفات)
        
    - Operations: behaviors (الدوال / الأفعال)
        
4. **تحديد العلاقات بين الكائنات**
    
    - Association, Aggregation, Composition, Inheritance, Dependency
        
5. **مراجعة وضبط التصميم**
    
    - إزالة الكلاسات غير الضرورية
        
    - دمج الكلاسات المتشابهة
        
    - التحقق من أن كل علاقة منطقية
        

---

### **3️⃣ ملاحظة مهمة**

- UML Class Diagram **هو نموذج تحليلي وتصميمي**:
    
    - لا يعتمد فقط على الكود، بل على **الفهم العميق للنظام ومجاله**.
        
- أي تغيّر في المتطلبات أو في المجال سيؤدي غالبًا إلى تعديل الكلاس دياجرام.

---
## **1️⃣ Class Diagram في مرحلة Requirements**

### **الهدف:**

- فهم **ما هي الكائنات الأساسية في النظام** وكيفية ارتباطها ببعضها البعض **بدون تفاصيل التنفيذ**.
    
- تركز على **المجال (domain)**، أي العالم الواقعي أو الأعمال التي يحاكيها النظام.
    

### **خصائصها:**

1. **High-level / Conceptual**: مستوى تجريدي، يصف المفاهيم وليس الكود.
    
2. **No implementation details**:
    
    - لا تحتوي على data types دقيقة، لا visibility (`+,-,#`) غالبًا.
        
    - العمليات (Operations) قد تكون مجرد أسماء عامة أو حتى لا تُكتب.
        
3. **Objects focus**: تُركز على الكائنات المهمة في مجال النظام.
    
4. **Example:**
    
    - نظام مستشفى:
    ```lua
    Patient -- has --> Appointment
	 Doctor -- schedules --> Appointment
    ```
        
    - هنا لا نهتم بـ private/protected أو methods معينة.
        

**خلاصة:** مرحلة المتطلبات **لتحليل المجال وفهم الكائنات والعلاقات**، ليس لتحديد تفاصيل الكود.

---

## **2️⃣ Class Diagram في مرحلة Design**

### **الهدف:**

- الانتقال من **التحليل إلى التنفيذ**: تصميم الكود الذي سيتم كتابته.
    
- تركز على **الهيكلية البرمجية** والتفاصيل اللازمة للتنفيذ.
    

### **خصائصها:**

1. **Detailed / Low-level**: مستوى تفصيلي، يصف **كيفية بناء الكلاسات**.
    
2. **Includes Implementation Details:**
    
    - Attributes مع types (`name: String`)
        
    - Methods مع parameters و return types
        
    - Visibility modifiers (`+,-,#`)
        
    - Associations, Aggregation, Composition, Dependency, Generalization
        
3. **Reflects Design Choices:**
    
    - الوراثة، استخدام Interfaces، تبسيط العلاقات، تطبيق Patterns.
        
4. **Example:**
    ```js
    class Patient {
    - ssn: String
    - birthDate: Date
    + getName(): String
    + setName(name: String)
}

class Appointment {
    + date: Date
    + schedule(patient: Patient, doctor: Doctor)
}

Patient "1" <---> "*" Appointment
Doctor "1" <---> "*" Appointment

    ```
    

- هنا يوضح **كيفية كتابة الكود فعليًا** وليس مجرد المفاهيم.
---
### **3️⃣ مقارنة سريعة بين المرحلتين**:
| Aspect            | Requirements Class Diagram      | Design Class Diagram                                                                          |
| ----------------- | ------------------------------- | --------------------------------------------------------------------------------------------- |
| **Focus**         | Domain concepts (المجال)        | Implementation (الكود)                                                                        |
| **Details**       | High-level, no types/visibility | Detailed, includes types, methods, modifiers                                                  |
| **Relationships** | Conceptual                      | Concrete, with multiplicity, aggregation, composition                                         |
| **Purpose**       | فهم النظام وما يحتويه           | توجيه عملية كتابة الكود الفعلي                                                                |
| **Example**       | Patient has Appointment         | Patient class with attributes and methods, Appointment class, relationships with multiplicity |

---
## **1️⃣ ما هو Function Signature؟**

**Function Signature** هو **الوصف الفريد لدالة أو عملية (Method)** داخل الكلاس، بحيث يميزها عن أي دالة أخرى.

يتكون عادة من:

1. **اسم الدالة (Method Name)**
    
    - يصف ما تقوم به الدالة
        
    - مثال: `calculateSalary`, `deposit`, `getName`
        
2. **قائمة المعاملات (Parameters / Arguments)**
    
    - اسم كل معامل + نوعه (Type)
        
    - تحدد البيانات التي تحتاجها الدالة للعمل
        
    - مثال: `(amount: double)`, `(patient: Patient, doctor: Doctor)`
        
3. **نوع القيمة المرجعة (Return Type)**
    
    - يحدد نوع النتيجة التي ترجعها الدالة
        
    - مثال: `: String`, `: double`, `: void` إذا لم ترجع قيمة
        

**ملاحظة:** الـ **access modifier** مثل `+` أو `-` لا يعتبر جزءًا من الـ signature في بعض التعريفات، لكنه يظهر في UML Class Diagram.

## **2️⃣ مثال UML**

```js
+ deposit(amount: double): void
- calculateInterest(rate: double): double
# getName(): String
```
**تفسير:**

- `deposit(amount: double): void`
    
    - اسم الدالة: `deposit`
        
    - معاملات: `amount` من النوع `double`
        
    - القيمة المرجعة: `void` (لا ترجع شيئًا)
        
    - Public (`+`)
        
- `calculateInterest(rate: double): double`
    
    - Private (`-`)
        
    - ترجع قيمة من نوع `double`

## **3️⃣ لماذا Function Signature مهم؟**

1. **تمييز الدوال:**
    
    - داخل نفس الكلاس قد توجد عدة دوال بنفس الاسم لكن تختلف المعاملات (Overloading) → الـ signature يميزها.
        
2. **التواصل مع الكائنات:**
    
    - Client يعرف كيفية استدعاء الدالة، أي اسم، معاملات، وقيمة مرجعة.
        
3. **تطبيق Design Patterns:**
    
    - عند تصميم Patterns مثل Command أو Template Method، فهم الـ signature ضروري لتنفيذ السلوكيات بشكل صحيح.
---
# Relationship between classes:

# 🔵 أوّلاً: ما هي **Association**؟

**Association = علاقة تواصل بين كائنين (objects) أو كلاسّين (classes)** داخل النظام.  
يعني: **كلاس يتفاعل مع كلاس آخر** لغرض ما.

تفكيرها بسيط جدًا:

- _Class A_ بده يحكي مع _Class B_ → إذن في بينهم association.
    
- ممكن يكون اتصال، مشاركة معلومة، استخدام method، تخزين object للثاني… إلخ.
    

🎯 **Association = BYN CLASSين في علاقة عامة بدون ملكية قوية**  
يعني كل واحد موجود لحاله، بس بينهم علاقة "شغل".

### مثال من حياتك:

- الطالب **يأخذ** مادة.
    
- الدكتور **يُدرّس** مادة.
    
- الموظف **يستخدم** جهاز.
    

مش واحد "جزء" من الثاني… فقط علاقة تعامل.

### في UML:

تمثل بخط بين الكلاسين:
```js
Student  ─────── Course
```
ممكن تضيف **سهم (navigability)** إذا العلاقة باتجاه واحد فقط.

---
# 🟣 ما هي **Self-Association**؟

هذا النوع يظهر عندما **الكلاس يعمل علاقة مع نفسه**.

يعني object من نفس النوع مرتبط بـ object آخر من نفس النوع.

🎯 **Self Association = العلاقة بين كائنات من نفس الكلاس.**

### أمثلة:

1. **Employee – leads – Employee**
    
    - موظف يقود موظفين آخرين.
        
2. **Course – prerequisites – Course**
    
    - مساق يحتاج لمساق آخر من نفس النوع.
        

### UML:

```js
Course
  ↑
  |  0..3
  |--------- (prerequisite)
  |
Course
```

لكن بشكل مختصر UML يرسم سهم يلف لنفس الكلاس.

---
# 🟢 ما هي **Multiplicity**؟ (العَدَد / الكارديناليّة)

هي **عدد الكائنات** من الطرف الآخر التي يمكن أن ترتبط بكائن واحد من هذا الطرف.

بمعنى:  
"كم Object من الكلاس X مرتبط مع Object واحد من الكلاس Y؟"
### أشهر القيم:
| القيمة   | المعنى                           |
| -------- | -------------------------------- |
| **1**    | واحد فقط                         |
| **0..1** | إما صفر أو واحد                  |
| **0..*** | أي عدد (ولا واحد، واحد، أو أكثر) |
| **1..*** | واحد أو أكثر                     |
| **5**    | بالضبط خمسة                      |
| **2..4** | بين ٢ و٤                         |

### مثال من الملف:
Instructor → Student
```js
Instructor        Student
   1           1..*
```

المدرّس الواحد يدرّس 1 أو أكثر من الطلاب،
والطالب الواحد لديه مدرّس واحد فقط.

---
# 🔥 الآن نربط الثلاث مفاهيم معًا:

### Association:
علاقة عامة بين كلاسين.
### Self‑Association:
نفس الفكرة، لكن علاقة داخلية مع نفس الكلاس.
### Multiplicity:
ببساطة: **كم عدد؟**  
كم object من الطرف الآخر يرتبط مع object من هذا الطرف.

![[Pasted image 20251127022129.png]]

---
# 🎓 أمثلة توضيحية سريعة:

## مثال 1: Student – Course
```js
Student        Course
1..*           3..7
```

✓ الطالب يأخذ من 3 إلى 7 مواد.  
✓ كل مادة فيها 1 أو أكثر طلاب.

## مثال 2: Employee – leads – Employee (self association)
```js
Employee
  |\
  | \ leads
  |  \ 0..*
  |   \
  ---- Employee
```

✓ الموظف يقود 0..* موظفين  
✓ كل موظف يمكن أن يكون لديه قائد واحد أو لا يملك

![[Pasted image 20251127020804.png]]

---
# Aggregation:

### 1️⃣ التعريف

**Aggregation** هي نوع من العلاقة بين الكلاسات في **Object-Oriented Programming** و **UML**، وتصف علاقة **“has-a”** أو "يحتوي على" بين كائنين.

- الكلاس **الكل (Whole)** يحتوي على كائنات أخرى **الأجزاء (Parts)**.
    
- العلاقة **ضعيفة**: الأجزاء يمكن أن توجد **بمفردها** حتى لو اختفى الكل.
    
- يرمز لها في **UML** بـ **هول دياموند (◊) على طرف الكل**.

#### ملاحظة : الأوبجكت الجزء يتم إنشاؤه خارج الأوبجكت الأب ، ثم يتم تمريره عبر `constructor as parameter


**مثال واقعي:**

- طائرة تحتوي على طاقم (**Airliner → CrewMember**)
    
    - الطائرة لها طاقم، لكن الطاقم يمكنه أن يعمل على طائرة أخرى أو بدون طائرة.
        
- سيارة تحتوي على محرك (**Car → Engine**)
    
    - إذا كانت Aggregation، المحرك قد يعيش بمفرده أو يُستخدم في سيارة أخرى.
        

---

### 2️⃣ Aggregation vs Composition

| الخاصية             | Aggregation            | Composition          |
| ------------------- | ---------------------- | -------------------- |
| الحياة (Life cycle) | الأجزاء تعيش بدون الكل | الأجزاء تموت مع الكل |
| قوة العلاقة         | ضعيفة                  | قوية (strong)        |
| UML                 | ◊ (hollow diamond)     | ◆ (filled diamond)   |
| مثال                | Airliner → CrewMember  | House → Room         |

---

### 3️⃣ مثال بالكود (Java)

**Aggregation**: (مثل كودك السابق)

```java
public class Airliner {
    private ArrayList<CrewMember> crew; // الأجزاء موجودة خارج الطائرة

    public Airliner() {
        crew = new ArrayList<CrewMember>();
    }

    public void addCrewMember(CrewMember member) {
        crew.add(member);
    }
}
```

- هنا `Airliner` **يحتوي** على `CrewMember`.
    
- إذا حذفت `Airliner`، أعضاء الطاقم ما زالوا موجودين.
    
- هذا الفرق الأساسي مع **Composition**، حيث إذا حذفت الكل، الأجزاء تُحذف أيضاً.
    

---

### 4️⃣ UML Representation

```
Airliner ◊---- CrewMember
0..*        1..*
```

- **Airliner** هو الكل (Whole)
    
- **CrewMember** هو الجزء (Part)
    
- الهول دياموند ◊ يدل على Aggregation

---
















