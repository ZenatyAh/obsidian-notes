
# SDLC – Software Development Life Cycle

يمر المنتج البرمجي عبر دورة حياة التطوير التالية:

1) Requirements Engineering
   - فهم فكرة العميل
   - جمع وتحليل المتطلبات
   - كتابة SRS أو User Stories

2) System Design
   - تصميم الـArchitecture
   - تصميم الواجهات UX/UI
   - UML Diagrams (Use Case, Class, Sequence)

3) Implementation (Coding)
   - كتابة الكود وتطبيق Design Patterns
   - تطوير الواجهة والباك إند
   - إدارة النسخ عبر Git

4) Testing / QA
   - Unit, Integration, System, UAT
   - التأكد من مطابقة المتطلبات

5) Review
   - Code Review + Architecture Review + UX Review

6) Deployment
   - نشر المنتج على بيئة الإنتاج
   - تهيئة السيرفرات و CI/CD

7) Maintenance
   - إصلاح الأخطاء
   - تحسينات وتحديثات مستقبلية

*هذه المراحل قد تكون خطية (Waterfall) أو متكررة (Agile/Scrum).*

---
# Requirements Types

Functional Requirements:
- تمثل الوظائف الأساسية التي يجب أن ينفذها النظام (What the system should do).
- مثال: يجب أن يوفر النظام وظيفة توليد كلمة مرور عند طلب المستخدم.

Non-Functional Requirements:
- تمثل الخصائص والقيود المتعلقة بجودة النظام (How the system should perform).
- تشمل: الأداء، السرعة، الأمان، قابلية التوسع، الاعتمادية.

# Design Phase Outputs

1) System Architecture Document:
   - يشرح هيكلية النظام والتقنيات المستخدمة.
   - يحتوي على: Components, Deployment Diagram, Architecture Pattern مثل Layered/Microservices.

2) Design Document:
   - يحتوي على مخططات UML (Class, Use Case, Sequence, Activity).
   - قد يشمل ERD وقواعد البيانات.

# Handling unclear or incomplete requirements

- عقد مقابلات مع أصحاب العلاقة (Stakeholders Interviews).
- ورشات عمل وعصف ذهني مع الفريق.
- مراقبة سير العمل الفعلي (Observation).
- دراسة نظم مشابهة (Competitive Analysis).
- بناء Prototype للحصول على ملاحظات العميل مبكراً.

---
# تأثير المتطلبات غير الوظيفية (NFRs) على تصميم وهيكلية النظام

تتحكم المتطلبات غير الوظيفية بشكل مباشر بقرارات الـArchitecture، وغالباً تشكل 80% من التصميم.

## التأثير الإيجابي:
1) Scalability
   - يؤدي لاختيار Microservices, Load Balancers, NoSQL.
2) Performance
   - استخدام Caching, CDN, تحسين الخوارزميات.
3) Security
   - HTTPS، التشفير، إدارة الهوية.
4) Maintainability
   - Clean Code, Low Coupling, تطبيق Design Patterns.

## التأثير السلبي:
1) زيادة التكلفة دون حاجة
   - مثل طلب High Availability لا يناسب حجم المشروع.
2) Over-Engineering
   - تصميم معقد بسبب NFR مبالغ فيها.
3) بطء التطوير
   - نتيجة متطلبات أداء أو أمان غير واقعية.
4) تضارب بين NFRs
   - مثل تعارض السرعة مع الأمان أو التعقيد مع قابلية الصيانة.

الخلاصة: NFRs يمكن أن تبني نظاماً قوياً أو تدمره إذا كانت غير واقعية أو غير قابلة للقياس.

---
# Design Patterns بين مرحلة التصميم ومرحلة كتابة الكود

Design Patterns ليست مفهوماً يخص مرحلة واحدة فقط، 
بل هي تداخل طبيعي بين مرحلتي Design و Implementation.

1) في مرحلة التصميم (Design):
   - يتم اتخاذ القرار باستخدام Pattern معيّن (Strategy, Factory, Observer...).
   - يظهر ذلك في مخططات UML وعلاقات الكائنات.
   - الهدف: تحديد شكل الهيكلية وطريقة تفاعل الأجزاء.

2) في مرحلة البرمجة (Implementation):
   - يتم ترجمة القرار التصميمي إلى كود فعلي.
   - عبر إنشاء Interfaces، Classes، Composition، Inheritance.
   - الهدف: تنفيذ البنية التي تم التخطيط لها أثناء التصميم.

الخلاصة:
Design Patterns = فكرة تصميم (Design Decision) + تطبيق برمجي (Code Structure)

وهذا ما يجعلها متداخلة بين كلا المرحلتين.

---
# Spaghetti Code

هو كود غير منظم ومتشابك بشكل فوضوي، يشبه خيوط السباغيتي. 
يتميز بالتعقيد العالي، وصعوبة القراءة، وصعوبة التطوير أو الصيانة.

خصائص Spaghetti Code:
- High Coupling وعدم وجود فصل للمهام.
- غياب Design Patterns و SOLID.
- منطق متكرر ومتشابك.
- شروط متداخلة كثيرة.
- غياب التوثيق وأسماء المتغيرات السيئة.

الأسباب:
- الاستعجال في التطوير.
- غياب التصميم الجيد (Architecture).
- عدم استخدام OOP أو Patterns.
- متطلبات متغيرة بدون refactoring.

طرق تجنّبه:
- تطبيق SOLID.
- استخدام Design Patterns.
- Clean Code.
- Layered Architecture.
- Refactoring مستمر.

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

**ملاحظة على الرموز:**

**Access Modifiers in UML / OOP:**

- **Public (+):** الوصول من أي مكان. مثال: `+name: String`
    
- **Private (-):** الوصول داخل الكلاس فقط. مثال: `-ssn: Id`
    
- **Protected (#):** الوصول داخل الكلاس و subclasses فقط. مثال: `#birthdate: Date`
---
#   ضوابط التسمية في `class, arrtibute & behaviour` ؟

**Naming Conventions in UML / OOP:**

1. **Classes:**
    - PascalCase، اسم مفرد ومعبر عن الكائن
        
    - مثال: `Invoice`, `CustomerRecord`
        
2. **Attributes:**
    
    - camelCase، اسم مفرد يعكس خاصية الكائن
        
    - مثال: `firstName: String`, `totalAmount: double`
        
3. **Behaviors/Operations:**
    
    - camelCase، يبدأ بفعل يعكس السلوك
        
    - مثال: `getBalance(): double`, `deposit(amount: double)`

|Element|Naming Style|Example UML|Notes|
|---|---|---|---|
|Class|PascalCase|`BankAccount`|اسم مفرد وواضح|
|Attribute|camelCase|`firstName: String`|يعكس خاصية واحدة|
|Operation|camelCase + Verb|`calculateSalary(): double`|يعكس الفعل والسلوك|

---
**استنباط Class Diagram:**

1. **المصادر:**
    
    - Requirements / Use Cases
        
    - Analysis / Domain Models
        
    - Real-world Entities / Business Objects
        
2. **الخطوات العملية:**
    
    - جمع المتطلبات
        
    - تحديد الكلاسات المرشحة (nouns → classes)
        
    - تحديد الخصائص والسلوكيات (Attributes & Operations)
        
    - تحديد العلاقات (Association, Aggregation, Composition, Inheritance, Dependency)
        
    - مراجعة وضبط التصميم
        
3. **ملاحظة:**
    
    - UML Class Diagram يعكس **الفهم والتحليل** وليس الكود فقط.

---
# **Difference between Class Diagram in Requirements vs Design:**

1. **Requirements (Analysis / Conceptual):**
    
    - Focus: Domain concepts
        
    - Level: High-level
        
    - Details: No types, visibility, or methods
        
    - Purpose: Understand system objects and relationships
        
2. **Design (Detailed / Implementation):**
    
    - Focus: Implementation
        
    - Level: Low-level / detailed
        
    - Details: Attributes with types, operations, visibility, detailed relationships
        
    - Purpose: Guide actual coding and design decisions
---
## **Function / Method Signature in UML / OOP:**

- **Definition:** الوصف الفريد لدالة داخل الكلاس.
    
- **Components:**
    
    1. Method Name (اسم الدالة)
        
    2. Parameters with Types (المعاملات مع النوع)
        
    3. Return Type (نوع القيمة المرجعة)
        
- **Examples:**
```js
+ deposit(amount: double): void
- calculateInterest(rate: double): double
# getName(): String
```
- **Purpose:** تمييز الدوال، توضيح كيفية الاستدعاء، دعم التصميم والتحليل.
---
# 🟡 class relationship :

**Association:**  
علاقة عامة بين كائنين أو كلاسين تشير إلى وجود تعامل أو تواصل بينهما بدون ملكية أو احتواء.

**Self‑Association:**  
علاقة يكون فيها الكلاس مرتبطًا بنفسه؛ أي أن كائن من نفس النوع يتفاعل مع كائن آخر من نفس النوع (مثل موظف يقود موظفًا، أو مساق يحتاج لمساق آخر).

**Multiplicity:**  
قيمة عددية توضّح كمية الكائنات المرتبطة من الطرف الآخر، مثل (1, 0..1, 1.._, 0.._, 2..4).  
تستخدم لتحديد "كم كائنًا يرتبط بكائن واحد؟".

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

![[Pasted image 20251127020740.png]]

**Aggregation**
#### ملاحظة : الأوبجكت الجزء يتم إنشاؤه خارج الأوبجكت الأب ، ثم يتم تمريره عبر `constructor as parameter`
- تعريف: علاقة “has-a” بين كلاس الكل وكلاسات الأجزاء حيث يمكن للأجزاء أن تعيش مستقلة عن الكل.
    
- UML: ◊ على طرف الكل، خط يربط الجزء.
    
- الحياة: الأجزاء لا تعتمد على حياة الكل.
    
- مثال: `Airliner` يحتوي على `CrewMember`، الطاقم يمكن أن يوجد بدون الطائرة.
    
- فرق عن Composition: في Composition الأجزاء تموت مع الكل، في Aggregation الأجزاء مستقلة.
    

---
