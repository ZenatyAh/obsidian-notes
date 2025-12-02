
---
### 1. لماذا نستخدم React Router أصلاً؟ (The "Why")
دعنا نستكشف هذا الفرق الجوهري، لأنه الأساس الذي يُبنى عليه اختيارنا لأدوات مثل React Router أو Next.js.

الفرق الرئيسي يكمن في **"من يتولى مسؤولية الانتقال؟"** هل هو المتصفح والخادم (Server)، أم كود الجافا سكريبت (Client)؟

إليك التفاصيل:

### 1. Multi-Page Application (MPA) - التوجيه التقليدي

في التطبيقات التقليدية (مثل المواقع القديمة أو التي تعتمد كلياً على PHP/Laravel بدون أطر عمل حديثة للواجهة):

- **مكان التوجيه:** يتم على الخادم (Server-side Routing).
    
- **ماذا يحدث؟:** في كل مرة تنقر فيها على رابط، يقوم المتصفح بإرسال طلب (Request) جديد تماماً للخادم.
    
- **النتيجة:** الخادم يرسل صفحة HTML كاملة وجديدة. المتصفح يقوم بعمل **إعادة تحميل كاملة (Full Refresh)** للصفحة. ستلاحظ غالباً وميضاً أبيض سريعاً عند الانتقال.
    

### 2. Single-Page Application (SPA) - التوجيه الحديث

في تطبيقات مثل React (عند استخدام `react-router-dom`):

- **مكان التوجيه:** يتم على المتصفح (Client-side Routing).
    
- **ماذا يحدث؟:** عند النقر على رابط، الجافا سكريبت **يمنع** المتصفح من إرسال طلب جديد للخادم (يمنع الـ Default Behavior). بدلاً من ذلك، تقوم الجافا سكريبت بتغيير الرابط في الأعلى وتغيير المحتوى الذي تراه في الصفحة فقط.
    
- **النتيجة:** إحساس بالسرعة والسلاسة (مثل التطبيق)، لا يوجد إعادة تحميل للصفحة، ويتم استبدال المكونات (Components) فقط.
    

### تشبيه لتقريب الفكرة 💡

- **MPA:** كأنك في فندق، وفي كل مرة تريد الانتقال من غرفة النوم إلى المطبخ، يجب عليك الخروج من الفندق تماماً والدخول مرة أخرى من البوابة الرئيسية للوصول للمطبخ.
    
- **SPA:** أنت داخل الفندق بالفعل، وتنتقل بين الغرف بفتح الأبواب فقط دون الخروج للشارع.
    

---

بما أنك تتعلم React وتستخدم `react-router-dom`، دعني أسألك سؤالاً لنتأكد من ترسيخ المفهوم:

إذا قمتِ داخل مشروع React باستخدام وسم HTML التقليدي للروابط:

<a href="/about">About</a>

بدلاً من المكون الخاص بـ React Router:

<Link to="/about">About</Link>

**ما الذي سيحدث لتطبيق الـ SPA الخاص بك في هذه الحالة؟**
استخدام وسم `<a>` التقليدي يجعل المتصفح يتجاهل كود React ويتصرف بطبيعته، مما يؤدي إلى:

1. **إرسال طلب للخادم:** كما ذكرتِ، لطلب صفحة HTML جديدة.
    
2. **إعادة تحميل الصفحة (Full Reload):** مما يعني فقدان أي بيانات مخزنة في الذاكرة (State) وعودة "الوميض الأبيض" المزعج. وهذا يلغي ميزة الـ SPA.
---
في الماضي (الويب التقليدي)، كان التنقل يعمل كالتالي:

1. المستخدم يضغط على رابط `<a>`.
    
2. المتصفح يرمي الصفحة الحالية في القمامة (تختفي الذاكرة، المتغيرات، والـ State).
    
3. يطلب المتصفح صفحة HTML **جديدة كلياً** من السيرفر.
    
4. ننتظر التحميل... ثم تظهر الصفحة الجديدة.
    

**المشكلة:** هذا بطيء، ويُشعر المستخدم بـ "ومضة" بيضاء مزعجة، والأهم: **نفقد كل الـ State** المخزنة في الذاكرة.

#### الحل (React Router):

نحن نبني تطبيق صفحة واحدة (SPA - Single Page Application).

هذا يعني أننا لا نغادر صفحة index.html أبداً! نحن فقط نوهم المستخدم أنه انتقل لصفحة أخرى، لكننا في الحقيقة قمنا بتبديل Component بـ Component آخر في نفس المكان.Shutterstock

### 2. كيف تعمل تحت الستار؟ (Under the Hood)

قد تتساءل: _"إذا كنا لا نغير الصفحة، كيف يتغير الرابط في الأعلى (URL) وكيف يعمل زر 'الرجوع' في المتصفح؟"_

هنا يكمن سحر React Router DOM، وهي تعتمد على ميزة في المتصفح نفسه تسمى **History API**.

عندما تضغط على رابط في React Router:

1. **يمنع** المتصفح من إرسال طلب للسيرفر (`e.preventDefault()`).
    
2. يستخدم `window.history.pushState()` لتغيير الرابط في شريط العنوان "شكلياً" فقط.
    
3. يستمع للتغيير في الرابط، ثم يقرر: _"أوه، الرابط أصبح `/about`؟ إذن سأخفي مكون `Home` وأظهر مكون `About`"_.
    

كل هذا يحدث في المتصفح (Client-side) دون أن يدري السيرفر بذلك.

---

### 3. لنبدأ التأسيس (The Foundation)

لتحقيق هذا السحر، نحتاج لثلاث قطع "ليجو" أساسية. تخيل أنك تبني نظام أمن لمبنى:

1. **`BrowserRouter`**: هذا هو "مدير المبنى" أو البيئة المحيطة. يجب أن يغلف التطبيق بالكامل ليعطيه القدرة على مراقبة الرابط (URL History).
    
2. **`Routes`**: هذا هو "مكتب الاستقبال". عندما يتغير الرابط، هو من ينظر في القائمة ويقرر أي غرفة يجب فتحها.
    
3. **`Route`**: هذه هي "الغرف" أو القواعد. (مثلاً: إذا كان الرابط `/login`، اعرض المكون `<Login />`).
    

### خطوتك الأولى:

لنبدأ بالتطبيق العملي. بما أنك تستخدم `npm`، قم بتثبيت المكتبة في مشروعك:

Bash

```
npm install react-router-dom
```

الآن، لنذهب إلى الملف الجذري لمشروعك (غالباً `main.tsx` أو `index.tsx` في React).

أريدك أن تقوم باستيراد `BrowserRouter` وتغليف تطبيقك `App` به. الكود سيبدو قريباً من هذا:

TypeScript

```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.tsx'
// 1. استدعاء المكتبة
import { BrowserRouter } from 'react-router-dom' 

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    {/* 2. تغليف التطبيق بالكامل */}
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>,
)
```

سؤال للتأكد من الفهم:

برأيك، لماذا قمنا بوضع BrowserRouter في أعلى مستوى ممكن (main.tsx) وليس داخل App.tsx مثلاً؟ (فكر في وظيفتها كـ "Context Provider").
بالضبط! إجابة موفقة جداً 🎯.

بما أنك ذكرت `App`، تخيل أن `BrowserRouter` هو خزان مياه رئيسي يغذي المنزل. يجب أن يكون في مكان أعلى من الأنابيب (المكونات) لكي يصل الماء (البيانات والـ Context) للجميع. إذا وضعت `Link` أو `Route` خارج هذا النطاق، ستحصل على خطأ لأنها ستحاول "الشرب" ولا تجد ماء!

---

### الخطوة التالية: مكتب الاستقبال والغرف (Routes & Route)

الآن وقد قمنا بتثبيت "مدير المبنى" (`BrowserRouter`) في `main.tsx`، لننتقل إلى `App.tsx` لنحدد القواعد.

نحتاج لاستيراد شيئين من المكتبة:

1. **`Routes`**: وعاء يجمع كل القواعد (كان يسمى `Switch` في الإصدارات القديمة). وظيفته البحث عن **أول** قاعدة تنطبق على الرابط الحالي واختيارها.
    
2. **`Route`**: القاعدة نفسها. وتأخذ خاصيتين أساسيتين:
    
    - `path`: شكل الرابط (مثلاً `"/"` أو `"/about"`).
        
    - `element`: المكون الذي نريد إظهاره (مثلاً `<Home />`).
        
---
### الخطوة التالية: المفاتيح (Navigation) 🔑

الآن الغرف مغلقة، ونحتاج لطريقة للدخول إليها. في HTML العادي نستخدم وسم `<a>`، لكن في React Router هذا **ممنوع** للتنقل الداخلي.
**سؤال:** برأيك، لماذا نتجنب استخدام `<a>` (مثل `<a href="/about">`) ونستخدم بدلاً منه مكون خاص يسمى `<Link>`؟ (تذكر ما تحدثنا عنه في البداية بخصوص الـ Refresh).
	مكون `<Link>` في الحقيقة يقوم برسم وسم `<a>` عادي في المتصفح (للحفاظ على سهولة الوصول "Accessibility" لمحركات البحث وقارئات الشاشة)، لكنه يضيف عليه "مستمع للحدث" (Event Listener) يقوم بـ:
	1. إيقاف التحديث الكامل للصفحة (`preventDefault`).
	2. تغيير الرابط في الأعلى باستخدام History API الذي تحدثنا عنه.

---
### الخطوة الثانية: التنقل الديناميكي (Dynamic Routing) 🔀

الآن، لنواجه مشكلة حقيقية. تخيل أن لديك تطبيقاً يحتوي على 1000 مستخدم. هل يعقل أن نكتب 1000 سطر `Route` لكل مستخدم؟ `path="/user/1"` `path="/user/2"` ... مستحيل!

الحل هو استخدام **المسارات المتغيرة (Dynamic Routes)**. نحن نستخدم الرمز `:` لنخبر React Router أن هذا الجزء من الرابط هو "متغير" (Variable) وليس كلمة ثابتة.

مثال: `path="/user/:userId"`

هنا `userId` يمكن أن يكون أي شيء (رقم 1، رقم 99، أو حتى اسم "ahmed").

---
### الخطوة التالية: التقاط البيانات (Hooks) 🪝

الآن الرابط يعمل، والمتصفح يعرض مكون `User`. لكن المشكلة أن المكون يعرض كلمة ثابتة "User Profile" ولا يعرف أننا نطلب المستخدم رقم `1`.

نحتاج لطريقة تجعل المكون `User` يمد يده إلى شريط العنوان (URL) ويسحب منه قيمة `userId`.

هذه الـ Hook تسمى **`useParams`**.

اسمها مشتق من "Parameters" (المعاملات)، ووظيفتها استخراج القيم المتغيرة التي وضعناها بعد النقطتين `:` في الـ Route.

**كيف تعمل؟** ⚙️ عندما يكون الرابط الحالي في المتصفح `/User/1`، وتكون القاعدة في الكود هي `/User/:userId`: تقوم `useParams` بإرجاع كائن (Object) يحتوي على المفتاح والقيمة، هكذا: `{ userId: '1' }`

---
### "خارطة الطريق" لعمل نظام Routing ناجح:

### 1. خطوة التجهيز (Installation & Setup)

قبل كتابة أي كود، نحتاج للأدوات.

- **الإجراء:** تثبيت المكتبة (`npm install react-router-dom`).
    
- **الهدف:** جلب الملفات اللازمة للمشروع.
    

### 2. خطوة التفعيل (Wrapping)

نحتاج لإخبار React بأن هذا التطبيق سيستخدم نظام التوجيه.

- **الإجراء:** تغليف التطبيق بـ `<BrowserRouter>`.
    
- **الهدف:** إعطاء التطبيق "قدرة" الاستماع لتغييرات الرابط في المتصفح (Browser URL).
    
- **المكان المعتاد:** في أعلى نقطة ممكنة في شجرة المكونات (غالباً ملف `main.tsx` أو `index.js`).
    

### 3. خطوة التخطيط (Defining Routes)

هنا نضع "قوانين" التنقل.

- **الإجراء:** استخدام المكونات `<Routes>` و `<Route>`.
    
- **الهدف:** ربط كل رابط (`path`) بالمكون (`element`) الذي يجب أن يظهر.
    
    - مثال: "عندما يكون الرابط `/about`، أظهر المكون `<About />`".
        

### 4. خطوة التنقل (Navigation)

كيف سيتحرك المستخدم؟

- **الإجراء:** استبدال وسوم `<a>` بـ `<Link>` أو `<NavLink>`.
    
- **الهدف:** السماح للمستخدم بالانتقال بين الصفحات دون عمل Refresh (كما ناقشنا سابقاً).
    

---
### 1️⃣ `createBrowserRouter`

- هي دالة توفرها مكتبة **React Router v6.4+**.
    
- الهدف: إنشاء **Router object** يحتوي على كل مسارات التطبيق (**Routes**) والـ **loaders / actions / error elements** إذا احتجت.
    
- الفرق بينها وبين الطريقة القديمة (`<BrowserRouter>`) إنها **تتيح تعريف كل شيء في مكان واحد كـ object** بدل JSX فقط، وتدعم ميزات متقدمة مثل **data loading** و**error handling**.
    

مثال تخيلي:

```javascript
import { createBrowserRouter } from "react-router-dom";
import Home from "./Home";
import About from "./About";

const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
  },
  {
    path: "/about",
    element: <About />,
  },
]);
```

هنا أنشأنا **router** يحوي مسارين: `/` و`/about`.

---

### 2️⃣ `RouterProvider`

- بعد ما نخلق الـ router باستخدام `createBrowserRouter`، لازم **نوفره لتطبيق React**.
    
- هذه المهمة تكون عبر `<RouterProvider>` بدل `<BrowserRouter>`.
    
- هو **يعمل كمزود للسياق (context)** لكل التطبيق، بحيث كل المسارات والـ navigation تشتغل صح.
    

مثال:

```javascript
import { RouterProvider } from "react-router-dom";

function App() {
  return <RouterProvider router={router} />;
}
```

---

### 🔹 النقطة الأساسية:

- `createBrowserRouter` = تعريف كل مساراتك وخصائصها (object-based route config).
    
- `RouterProvider` = يربط الـ router بالتطبيق ويجعل الـ routes تعمل.
    

---
**رسم تخطيطي صغير** يوضح العلاقة بين `createBrowserRouter`, `RouterProvider` و`Route elements` بحيث يكون واضح بصرياً. 

![[Pasted image 20251202154230.png]]

---

### 1️⃣ ما هو `createRoutesFromElements`؟

`createRoutesFromElements` هو **دالة** من React Router (v6+) بتاخد **JSX elements** للـ `<Route>` وترجع لك **مصفوفة من كائنات Routes** اللي React Router يستخدمها داخليًا لتحديد المسارات.

يعني بدل ما تعمل:

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

تقدر تبني الـ routes بشكل برمجي أكثر مرونة باستخدام `createRoutesFromElements`.

---

### 2️⃣ شكل الاستخدام

```jsx
import { createRoutesFromElements, Route } from "react-router-dom";

const routes = createRoutesFromElements(
  <>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </>
);

console.log(routes);
```

هنا `routes` راح تكون **مصفوفة من كائنات**:

```json
[
  { "path": "/", "element": "<Home />" },
  { "path": "/about", "element": "<About />" }
]
```

---

### 3️⃣ ليش نستخدمه؟

- لو عندك routes ديناميكية أو محتاج تبنيها برمجيًا.
    
- يعمل تنسيق واحد إذا كنت تستخدم `useRoutes(routes)` لاحقًا.
    
- يسهّل التعامل مع **nested routes** برمجيًا بدل JSX مباشرة.
    

مثال مع nested routes:

```jsx
const routes = createRoutesFromElements(
  <Route path="/" element={<Layout />}>
    <Route index element={<Home />} />
    <Route path="about" element={<About />} />
  </Route>
);
```

النتيجة هنا كائنات routes متداخلة جاهزة للاستخدام مع `useRoutes(routes)`.

---

لو تحب، أقدر أعمل لك **رسم توضيحي بصري** يوضح الفرق بين JSX العادي و `createRoutesFromElements` عشان تحس الفكرة بصريًا.
![[Pasted image 20251202155949.png]]

---
## 1️⃣ المفهوم الأساسي: Layout & Nested Routes

في **React Router DOM**:

1. **Layout Route**:
    
    - هو **route** يحتوي على **واجهة مشتركة** لكل الصفحات اللي تحتها.
        
    - مثال: Navbar, Sidebar, Footer.
        
    - كل الصفحات الأخرى يتم عرضها داخل هذا الـ Layout.
        
2. **Nested Routes (Routes متداخلة)**:
    
    - هي Routes داخل Route آخر.
        
    - تستخدم لتقسيم التطبيق إلى أجزاء، كل جزء يمكن أن يرث Layout واحد.
        
    - تفيد جدًا عندما تريد واجهة متشابهة بين عدة صفحات.
        

**التشبيه:**  
تخيل موقعك عنده Navbar + Sidebar دائمًا ظاهر، ومحتوى الصفحة يتغير فقط حسب الرابط. الـ Layout هو الـ Navbar + Sidebar، وNested Routes هي المحتويات اللي بتتغير.

---

## 2️⃣ مثال عملي مبسط

### بنية الملفات:

```
src/
  pages/
    Dashboard.jsx
    Profile.jsx
    Settings.jsx
  components/
    Navbar.jsx
  App.jsx
```

### App.jsx مع Layout وNested Routes:

```jsx
import { BrowserRouter, Routes, Route, Outlet } from 'react-router-dom';
import Navbar from './components/Navbar';
import Dashboard from './pages/Dashboard';
import Profile from './pages/Profile';
import Settings from './pages/Settings';

// Layout component
function MainLayout() {
  return (
    <div>
      <Navbar />      {/* دائماً يظهر */}
      <div className="content">
        <Outlet />    {/* هنا سيظهر المحتوى حسب الـ route */}
      </div>
    </div>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        {/* هذا الـ Layout الرئيسي */}
        <Route path="/" element={<MainLayout />}>
          <Route index element={<Dashboard />} /> {/* / */}
          <Route path="profile" element={<Profile />} /> {/* /profile */}
          <Route path="settings" element={<Settings />} /> {/* /settings */}
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### نقاط مهمة:

1. `<Outlet />` هو المكان اللي رح يظهر فيه **الصفحات الفرعية**.
    
2. `index` route يعني الصفحة الرئيسية للـ Layout.
    
3. كل صفحة فرعية (Nested Route) سترث الـ Layout تلقائيًا.
    

---

## 3️⃣ مثال أكثر تعقيدًا: Nested Nested Routes

إذا أردت صفحة Settings تحتوي على تبويبات (Tabs):

```
/settings/profile
/settings/security
```

```jsx
function SettingsLayout() {
  return (
    <div>
      <h2>Settings Page</h2>
      <Outlet /> {/* سيظهر محتوى كل تاب */}
    </div>
  );
}

function ProfileSettings() { return <div>Profile Settings</div>; }
function SecuritySettings() { return <div>Security Settings</div>; }

<Route path="settings" element={<SettingsLayout />}>
  <Route path="profile" element={<ProfileSettings />} />
  <Route path="security" element={<SecuritySettings />} />
</Route>
```

هنا:

- `/settings/profile` → يظهر ProfileSettings داخل SettingsLayout.
    
- `/settings/security` → يظهر SecuritySettings داخل نفس Layout.
    

---

## ✅ خلاصة:

- **Layout Route** = واجهة ثابتة مشتركة.
    
- **Nested Routes** = الصفحات الفرعية التي تظهر داخل الـ Layout.
    
- `<Outlet />` = مكان ظهور الصفحات الفرعية.
    
- يمكن تداخل الـ Nested Routes أكثر من مستوى.
    

---

لو تحب، أقدر أرسم لك **خريطة رسومية** توضح Layout + Nested Routes + كل رابط بمكانه، بحيث يكون سهل تتخيله بصريًا.

تمام يا أحمد، خلّيني أعطيك **الخريطة الرسومية (Visual Map)** بشكل واضح وبسيط… وبعدها أسألك سؤال صغير أتأكد إنك فاهم قبل ما نكمل للجزء العملي.

---

# 🌐 خريطة Layout + Nested Routes (رسم بسيط وواضح)

## **المستوى الأول – Layout الرئيسي**

```
/
└── MainLayout
      ├── Navbar (دائم)
      ├── Sidebar (اختياري)
      └── <Outlet />  ← هنا تتغير الصفحات
```

## **المستوى الثاني – الصفحات الرئيسية داخل الـ Layout**

```
MainLayout
│
├── (index) /           → Dashboard
├── /profile            → Profile Page
└── /settings           → SettingsLayout
```

## **المستوى الثالث – Nested داخل Settings**

```
/settings
└── SettingsLayout
       ├── Title: “Settings”
       └── <Outlet /> ← تبويبات داخل الإعدادات
             ├── /settings/profile  → ProfileSettings
             └── /settings/security → SecuritySettings
```

---

# 🧠 الصورة الكاملة (بشكل شجرة)

```
/
└── MainLayout
      ├── Dashboard (index)
      ├── Profile
      └── SettingsLayout
             ├── ProfileSettings
             └── SecuritySettings
```

---

# 🎯 كيف يتنقّل المستخدم فعليًا؟

- يزور `/` → يظهر Dashboard داخل MainLayout
    
- يزور `/profile` → تظهر صفحة Profile داخل نفس MainLayout
    
- يزور `/settings/profile` → يظهر:
    
    - MainLayout
        
    - SettingsLayout
        
    - ProfileSettings
        

---

ميزة **`errorElement`** في React Router DOM (تحديداً في الإصدار v6.4 وما بعده) هي بمثابة "صمام الأمان" أو "شبكة النجاة" لتطبيقك. هي الطريقة الحديثة للتعامل مع الأخطاء (Errors) التي تحدث أثناء التنقل بين الصفحات، أو تحميل البيانات (Loaders)، أو تنفيذ الإجراءات (Actions).

بدلاً من أن "ينهار" التطبيق بالكامل وتظهر شاشة بيضاء فارغة للمستخدم عند حدوث خطأ، تقوم React Router بعرض مكوّن خاص (Component) قمت أنت بتصميمه مسبقاً (مثل صفحة "حدث خطأ ما" أو "404 غير موجود").

إليك شرح مفصل لكيفية عملها واستخدامها:

-----

### 1\. الفكرة الأساسية: كيف تعمل؟

تخيل أن `errorElement` تعمل تماماً مثل جملة `catch` في البرمجة (`try...catch`).
عندما يحدث خطأ في أي `Route` (سواء كان الخطأ في الـ `element` نفسه، أو في دالة `loader` لجلب البيانات)، تقوم React Router بإيقاف عرض المكون الحالي فوراً، وبدلاً منه، تقوم بعرض الـ `errorElement` المحدد لهذا المسار.

### 2\. كيفية الاستخدام (خطوة بخطوة)

لتفعيل هذه الميزة، نحتاج إلى أمرين:

1.  إنشاء مكوّن (Component) لعرض الخطأ.
2.  ربط هذا المكوّن بالمسار (Route) في إعدادات الراوتر.

#### أ) إنشاء صفحة الخطأ (Error Page) واستخدام `useRouteError`

توفر React Router خطافاً (Hook) يسمى `useRouteError`. وظيفته هي التقاط تفاصيل الخطأ الذي حدث لكي تتمكن من عرضه للمستخدم (مثل رسالة الخطأ أو رمز الحالة 404).

```jsx
import { useRouteError, isRouteErrorResponse } from "react-router-dom";

export default function ErrorPage() {
  const error = useRouteError(); // التقاط الخطأ
  console.error(error); // طباعته في الكونسول للمطور

  let errorMessage = "حدث خطأ غير متوقع";

  // التحقق مما إذا كان الخطأ هو استجابة (مثل 404) أو خطأ برمجي
  if (isRouteErrorResponse(error)) {
    // خطأ من الراوتر (مثل صفحة غير موجودة)
    errorMessage = `${error.status} ${error.statusText}`;
  } else if (error instanceof Error) {
    // خطأ برمجي (مثل متغير غير معرف)
    errorMessage = error.message;
  }

  return (
    <div id="error-page" style={{ textAlign: "center", marginTop: "50px" }}>
      <h1>أوه! حدث خطأ ما.</h1>
      <p>عذراً، لقد حدث خطأ غير متوقع.</p>
      <p>
        <i>{errorMessage}</i>
      </p>
    </div>
  );
}
```

#### ب) ربط الـ ErrorPage بالـ Router

الآن، عند تعريف المسارات باستخدام `createBrowserRouter`، نضيف خاصية `errorElement`.

```jsx
import { createBrowserRouter, RouterProvider } from "react-router-dom";
import Home from "./Home";
import ErrorPage from "./ErrorPage"; // استدعاء صفحة الخطأ

const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
    errorElement: <ErrorPage />, // <--- هنا نضع صمام الأمان
    children: [
      {
        path: "dashboard",
        element: <Dashboard />,
        // إذا حدث خطأ هنا ولم نضع errorElement خاصاً، 
        // سيصعد الخطأ (Bubble up) إلى الأب ويستخدم ErrorPage الخاصة بالأب
      },
    ],
  },
]);

function App() {
  return <RouterProvider router={router} />;
}
```

-----

### 3\. مميزات مهمة (Bubbling)

من أقوى مميزات `errorElement` هي أنها تتبع التسلسل الهرمي (Hierarchy).

  * **الخطأ يصعد للأعلى (Bubbling):** إذا حدث خطأ في مسار فرعي (Child Route) ولم يكن له `errorElement` خاص به، سيصعد الخطأ إلى المسار الأب (Parent Route) ويستخدم الـ `errorElement` الخاص به.
  * **التحكم الدقيق:** يمكنك وضع `errorElement` عام في الجذر (Root) ليمسك بكل أخطاء التطبيق، ويمكنك وضع `errorElement` مخصص لمسار معين (مثلاً داخل جزء "لوحة التحكم") لكي لا ينهار التطبيق بالكامل، بل يظهر الخطأ فقط في هذا الجزء بينما تبقى القائمة الجانبية (Sidebar) والترويسة (Header) تعمل بشكل سليم.

### ملخص الفوائد:

1.  **تجربة مستخدم أفضل (UX):** لا شاشات بيضاء مخيفة.
2.  **مركزية التعامل مع الأخطاء:** مكان واحد لتصميم شكل الأخطاء.
3.  **دعم للـ Async Errors:** تلتقط الأخطاء التي تحدث أثناء جلب البيانات (APIs) في الـ Loaders تلقائياً.

-----
الـ **`useNavigate`** هو "عجلة القيادة" البرمجية في React Router.

بينما نستخدم المكون `<Link>` للانتقال عند نقر المستخدم على رابط (مثل قائمة التنقل)، نستخدم `useNavigate` عندما نريد الانتقال إلى صفحة أخرى **بناءً على كود برمجي** (Programmatically)، أي بعد حدوث عملية معينة مثل نجاح تسجيل الدخول أو إرسال نموذج (Form).

إليك الشرح بالتفصيل:

### 1\. الوظيفة الأساسية

هو **Hook** يعطيك دالة (Function). عند استدعاء هذه الدالة، يمكنك توجيه المستخدم إلى أي مسار تريده.

### 2\. طريقة الاستخدام (Syntax)

أولاً، نستورد الـ Hook ونخزنه في متغير:

```jsx
import { useNavigate } from "react-router-dom";

function LoginPage() {
  // 1. استدعاء الـ hook
  const navigate = useNavigate();

  const handleLogin = () => {
    // افترض أننا قمنا بعملية تسجيل دخول هنا وتأكدنا من البيانات
    console.log("تم تسجيل الدخول بنجاح!");

    // 2. استخدام الدالة للتوجيه
    navigate("/dashboard"); 
  };

  return (
    <button onClick={handleLogin}>تسجيل الدخول</button>
  );
}
```

-----

### 3\. سيناريوهات استخدام `Maps`

تأخذ دالة `Maps` وسيطين (arguments):

1.  **المسار (To):** إلى أين تريد الذهاب.
2.  **الخيارات (Options):** (اختياري) للتحكم في كيفية الانتقال.

#### أ) الانتقال المباشر لصفحة أخرى

```jsx
navigate("/home"); // يذهب للصفحة الرئيسية
navigate("/users/123"); // يذهب لصفحة مستخدم معين
```

#### ب) العودة للخلف (مثل زر Back في المتصفح)

يمكنك تمرير رقم لتقليد حركة المتصفح (History Stack):

```jsx
navigate(-1); // العودة خطوة واحدة للخلف (Go Back)
navigate(-2); // العودة خطوتين للخلف
navigate(1);  // الذهاب خطوة للأمام (Go Forward)
```

#### ج) الانتقال مع استبدال التاريخ (`replace: true`)

هذا الخيار **مهم جداً** في صفحات مثل "تسجيل الدخول".
عندما ينجح المستخدم في الدخول، لا تريده أن يضغط على زر "رجوع" في المتصفح ويعود لصفحة الدخول مرة أخرى. لذلك نستخدم `replace: true` لمسح الصفحة الحالية من التاريخ واستبدالها بالجديدة.

```jsx
// بدلاً من إضافة صفحة Dashboard فوق صفحة Login
// نقوم بتبديل صفحة Login بصفحة Dashboard في سجل المتصفح
navigate("/dashboard", { replace: true });
```

#### د) تمرير بيانات خفية (`state`)

يمكنك إرسال بيانات مع الانتقال دون أن تظهر في شريط الرابط (URL):

```jsx
navigate("/profile", { state: { userId: 5, from: "home_page" } });
```

*(يمكنك استقبال هذه البيانات في الصفحة التالية باستخدام `useLocation`).*

-----

### 4\. متى أستخدم `<Link>` ومتى أستخدم `useNavigate`؟

| الميزة      | استخدم `<Link>`                                | استخدم `useNavigate`                                |
| :---------- | :--------------------------------------------- | :-------------------------------------------------- |
| **التفاعل** | عندما يضغط المستخدم بنفسه (قائمة علوية، فوتر). | عندما يقرر الكود الانتقال (بعد fetch، بعد timeout). |
| **النوع**   | تنقل تعريفي (Declarative).                     | تنقل أمري (Imperative).                             |
| **مثال**    | "اضغط هنا لقراءة المزيد"                       | "تم الحفظ بنجاح، جاري تحويلك..."                    |

-----

### مثال عملي سريع

تخيل زر "إلغاء" في نموذج:

```jsx
const RegisterForm = () => {
  const navigate = useNavigate();

  return (
    <form>
      {/* حقول الإدخال... */}
      
      <button type="submit">تسجيل</button>
      
      {/* عند الضغط على إلغاء، نعود للصفحة السابقة مباشرة */}
      <button type="button" onClick={() => navigate(-1)}>
        إلغاء
      </button>
    </form>
  );
};
```

---
الـ **`NavLink`** هو ببساطة "النسخة الذكية" من المكون `<Link>`.

بينما نستخدم `<Link>` للانتقال العادي (مثل رابط في وسط مقال)، نستخدم **`NavLink`** حصراً **لقوائم التنقل (Navbars & Sidebars)**.

لماذا؟ لأنه يمتلك ميزة خاصة جداً: **هو "يعرف" ما إذا كان الرابط الذي يمثله نشطاً (Active) حالياً أم لا.**

إليك التفاصيل:

### 1. المشكلة التي يحلها

تخيل أن لديك شريط تنقل علوي يحتوي على: "الرئيسية"، "عن الموقع"، "اتصل بنا".

عندما يضغط المستخدم على "عن الموقع"، تريد أن يتغير لون هذا الزر أو يصبح الخط عريضاً ليعرف المستخدم أنه موجود في هذه الصفحة حالياً.

- مع `<Link>` العادي: ستحتاج لكتابة كود معقد للتحقق من الرابط الحالي وتغيير الستايل يدوياً.
    
- مع `<NavLink>`: يقوم هو بهذا الأمر تلقائياً!
    

---

### 2. كيفية الاستخدام (في الإصدار v6 وما بعده)

في الإصدارات الحديثة، خاصيتا `style` و `className` داخل `NavLink` تقبلان **دالة (Function)** بدلاً من مجرد نص. هذه الدالة تعطيك متغيراً مهماً جداً اسمه `isActive`.

#### أ) استخدام `className` (الأكثر شيوعاً)

هنا نقول للراوتر: "إذا كان الرابط نشطاً، أضف كلاس `active`، وإلا اتركه عادياً".

JavaScript

```
import { NavLink } from "react-router-dom";

function Navbar() {
  return (
    <nav>
      <NavLink
        to="/home"
        className={({ isActive }) => (isActive ? "my-link active-link" : "my-link")}
      >
        الرئيسية
      </NavLink>
      
      <NavLink
        to="/about"
        className={({ isActive }) => (isActive ? "my-link active-link" : "my-link")}
      >
        عن الموقع
      </NavLink>
    </nav>
  );
}
```

_في ملف CSS، تقوم بتنسيق الكلاس `.active-link` (مثلاً لون أحمر)._

#### ب) استخدام `style` (تنسيق مباشر Inline)

JavaScript

```
<NavLink
  to="/profile"
  style={({ isActive }) => {
    return {
      fontWeight: isActive ? "bold" : "normal",
      color: isActive ? "red" : "black",
    };
  }}
>
  ملفي الشخصي
</NavLink>
```

---

### 3. خاصية `end` (مهمة جداً للصفحة الرئيسية)

هناك مشكلة شائعة تسمى "Partial Matching" (التطابق الجزئي).

بما أن المسار / (الرئيسية) هو جزء من كل المسارات (مثلاً /about تحتوي على /)، فإن رابط "الرئيسية" سيبقى نشطاً (مضاءً) دائماً حتى لو كنت في صفحة أخرى!

لحل هذه المشكلة، نضيف كلمة `end` لرابط الصفحة الرئيسية. هذا يخبر الراوتر: "لا تجعل هذا الرابط نشطاً إلا إذا كان المسار ينتهي تماماً عند `/`".

JavaScript

```
<NavLink to="/" end className="...">
  الرئيسية
</NavLink>
```

---

### ملخص الفرق بين الثلاثة

|**المكون**|**الوظيفة**|**متى أستخدمه؟**|
|---|---|---|
|**Link**|رابط عادي ينقلك لصفحة أخرى دون إعادة تحميل المتصفح.|في الأزرار العادية، روابط داخل النصوص، روابط الفوتر.|
|**NavLink**|رابط يعرف حالته (نشط أم لا).|في القائمة العلوية (Navbar)، القائمة الجانبية (Sidebar)، التبويبات (Tabs).|
|**useNavigate**|دالة برمجية للتنقل.|بعد تسجيل الدخول، عند إرسال فورم، أو التنقل التلقائي.|

---
الـ **Dynamic Routes** (المسارات الديناميكية) هي الطريقة التي تجعل تطبيقك قابلاً للتوسع للتعامل مع آلاف الصفحات باستخدام "قالب" مسار واحد فقط.

تخيل لو أنك تبني متجراً إلكترونياً يحتوي على 10,000 منتج. هل من المعقول أن تكتب 10,000 سطر كود لتعريف مسار لكل منتج؟

- `/product/1`
    
- `/product/2`
    
- ...
    
- `/product/10000`
    

بالطبع لا! هنا يأتي دور المسارات الديناميكية.

---

### 1. الفكرة الأساسية

المسار الديناميكي هو مسار يحتوي على متغير (Variable) أو "مكان محجوز" (Placeholder).

بدلاً من كتابة الرقم 1 أو 2، نضع علامة خاصة تخبر الراوتر: "أي شيء يكتب هنا، اعتبره متغيراً واقبله".

الرمز السحري هنا هو **النقطتان الرأسيتان (`:`)**.

### 2. كيفية الاستخدام (3 خطوات)

#### الخطوة 1: تعريف المسار في الراوتر

عند تعريف الـ path، تضع `:` قبل اسم المتغير الذي تريده.

JavaScript

```
// في ملف تعريف الراوتر
{
  // هنا نقول: أي شيء يأتي بعد كلمة user هو متغير سنسميه id
  path: "/user/:id", 
  element: <UserProfile />,
}
```

هذا المسار سيطابق:

- `/user/1`
    
- `/user/ahmed`
    
- `/user/555`
    

#### الخطوة 2: إنشاء الروابط (Link)

عندما ترسل المستخدم لهذا المسار، تضع القيمة الحقيقية.

JavaScript

```
// في صفحة قائمة المستخدمين
<Link to="/user/101">عرض ملف المستخدم 101</Link>
<Link to="/user/202">عرض ملف المستخدم 202</Link>
```

#### الخطوة 3: استقبال البيانات (`useParams`)

الآن، داخل صفحة UserProfile، كيف نعرف ما هو الـ ID الذي طلبه المستخدم؟

نستخدم Hook اسمه useParams.

JavaScript

```
import { useParams } from "react-router-dom";

function UserProfile() {
  // هذا الاسم يجب أن يطابق الاسم الذي اخترته في الخطوة 1 بعد النقطتين
  const { id } = useParams(); 

  return (
    <div>
      <h1>ملف المستخدم رقم: {id}</h1>
      {/* هنا عادة نستخدم هذا الرقم لجلب بيانات المستخدم من السيرفر
         fetch(`https://api.example.com/users/${id}`)
      */}
    </div>
  );
}
```

---

### 3. مثال عملي لمشروعك (Rick and Morty)

بما أنك تبني تطبيق Rick and Morty، فأنت ستحتاج لهذا بالتأكيد عند الضغط على بطاقة الشخصية (Character Card) لرؤية تفاصيلها.

**أ) تعريف المسار:**

JavaScript

```
{
  path: "/character/:charId", // سميناه charId
  element: <CharacterDetails />,
}
```

**ب) الرابط في البطاقة:**

JavaScript

```
// داخل الـ map function للقائمة
<Link to={`/character/${character.id}`}>
  View Details
</Link>
```

**ج) صفحة التفاصيل (Component):**

JavaScript

```
import { useParams } from "react-router-dom";
import { useQuery } from "@tanstack/react-query"; // بما أنك تستخدم TanStack

function CharacterDetails() {
  const { charId } = useParams(); // نحصل على الـ ID من الرابط

  // استخدام الـ ID لجلب البيانات
  const { data, isLoading } = useQuery({
    queryKey: ["character", charId],
    queryFn: () =>
      fetch(`https://rickandmortyapi.com/api/character/${charId}`).then((res) =>
        res.json()
      ),
  });

  if (isLoading) return <div>Loading...</div>;

  return (
    <div>
      <h1>{data.name}</h1>
      <img src={data.image} alt={data.name} />
      <p>Status: {data.status}</p>
    </div>
  );
}
```

---

### ملاحظات سريعة:

1. **الاسم مهم:** إذا سميت المسار `path="/blog/:slug"`، فيجب أن تستقبله بـ `const { slug } = useParams()`.
    
2. **تعدد المتغيرات:** يمكنك وضع أكثر من متغير في نفس المسار:
    
    - المسار: `path="/store/:category/:productId"`
        
    - الرابط: `/store/electronics/99`
        
    - الاستقبال: `const { category, productId } = useParams()`
        

---



هذا سؤال ممتاز وجوهري لفهم كيفية بناء الروابط بشكل صحيح في React Router. الفرق بين **المسار المطلق (Absolute)** و **المسار النسبي (Relative)** يشبه الفرق بين إعطاء شخص "عنواناً كاملاً" وإعطائه "اتجاهات من مكانه الحالي".

الفرق التقني البسيط جداً هو: **هل يبدأ الرابط بعلامة `/` أم لا؟**

إليك الشرح بالتفصيل الممل مع الأمثلة:

-----

### 1\. المسار المطلق (Absolute Path)

**العلامة المميزة:** يبدأ دائماً بـ شرطة مائلة `/`.

المسار المطلق هو عنوان كامل وثابت. عندما تستخدمه، فأنت تقول للمتصفح: **"لا يهمني أين أنا الآن، أريدك أن تبدأ من جذر الموقع (Root) وتذهب لهذا العنوان"**.

  * **مثال واقعي:** "اذهب إلى شارع الملك فيصل، بناية رقم 5". (عنوان ثابت لا يتغير بتغير مكانك).

#### مثال برمجي:

تخيل أن المستخدم حالياً يتصفح هذا الرابط العميق:
`domain.com/dashboard/users/settings/privacy`

وأنت تريد وضع زر "الرئيسية" في الـ Navbar.

```jsx
// ✅ هذا مسار مطلق
<Link to="/">الرئيسية</Link> 
// النتيجة: سيحذف كل الرابط الحالي ويذهب إلى domain.com/

// ✅ هذا مسار مطلق آخر
<Link to="/about">عن الموقع</Link>
// النتيجة: سيذهب إلى domain.com/about مباشرة بغض النظر عن مكانك
```

**متى نستخدمه؟**

  * في القائمة الرئيسية (Navbar).
  * عندما تريد الخروج من قسم كامل والذهاب لقسم آخر (مثلاً من لوحة التحكم `/dashboard` إلى صفحة الدخول `/login`).

-----

### 2\. المسار النسبي (Relative Path)

**العلامة المميزة:** **لا** يبدأ بـ `/`.

المسار النسبي يعتمد كلياً على **مكانك الحالي (Parent Route)**. هو يقوم بـ "إضافة" المسار الجديد فوق المسار الحالي.

  * **مثال واقعي:** "اذهب للغرفة المجاورة". (وجهتك تعتمد على الغرفة التي تقف فيها الآن).

#### مثال برمجي (السيناريو الأشهر):

لنفترض أنك تبني لوحة تحكم (Dashboard). الرابط الحالي هو:
`domain.com/dashboard`

وتريد عمل رابط لصفحة "Profile".

**الخيار أ (مطلق):**

```jsx
<Link to="/profile">الملف الشخصي</Link>
// ❌ النتيجة: domain.com/profile 
// (خرجنا من الداشبورد! وهذا غالباً خطأ إذا كانت الصفحة فرعية)
```

**الخيار ب (نسبي):**

```jsx
<Link to="profile">الملف الشخصي</Link> 
// ✅ النتيجة: domain.com/dashboard/profile
// (لاحظ أنه أضاف كلمة profile لنهاية الرابط الحالي)
```

-----

### 3\. الحالات الخاصة للمسارات النسبية (`..` و `.`)

في المسارات النسبية، يمكننا استخدام رموز تشبه نظام الملفات في الكمبيوتر للتنقل للأعلى أو الخلف.

#### أ) الرجوع للأب (`..`)

الرمز `..` يعني: "اصعد مستوى واحداً للأعلى" (Go up one level).

**المثال:**
أنت الآن في صفحة تعديل منتج:
`domain.com/products/55/edit`

تريد عمل زر "إلغاء" يعيدك لصفحة تفاصيل المنتج (تحذف `edit` فقط).

```jsx
// إذا استخدمنا مساراً مطلقاً سنضطر لكتابة الرابط كاملاً
// <Link to="/products/55"> 

// ولكن بالمسار النسبي:
<Link to="..">إلغاء</Link>
// النتيجة: يعيدك إلى domain.com/products/55
// (حذف آخر جزء من الرابط)
```

#### ب) المسار الحالي (`.`)

الرمز `.` يعني "المسار الحالي". استخدامه نادر في الروابط المباشرة ولكنه مفيد لإنهاء التفرع (end branch).

-----

### 4\. مثال شامل ومعقد (Nested Routes)

لنطبق هذا على مشروعك **Rick and Morty**. تخيل هيكل الراوتر التالي:

```jsx
// الهيكل:
// /characters          (قائمة الشخصيات)
// /characters/:id      (تفاصيل شخصية)
// /characters/:id/episodes (حلقات هذه الشخصية)
```

أنت الآن داخل صفحة تفاصيل الشخصية رقم 1 (`/characters/1`). وتريد وضع رابط لصفحة الحلقات (`episodes`).

**مقارنة الكود:**

| النوع | الكود | الرابط الناتج | النتيجة |
| :--- | :--- | :--- | :--- |
| **Absolute** | `<Link to="/episodes">` | `/episodes` | ❌ خطأ (صفحة غير موجودة) |
| **Relative** | `<Link to="episodes">` | `/characters/1/episodes` | ✅ صحيح (أضافها للرابط الحالي) |
| **Relative (Up)** | `<Link to="..">` | `/characters` | ✅ عودة لقائمة الشخصيات |

-----

### ملخص القاعدة الذهبية

1.  إذا كنت تريد الذهاب لمكان محدد ومعروف من أي مكان في التطبيق (مثل: Home, Login, Contact) -\> **استخدم Absolute (`/`)**.
2.  إذا كنت داخل قسم (مثل Dashboard أو Details) وتريد التنقل لصفحات فرعية داخل نفس القسم -\> **استخدم Relative (بدون `/`)**.
3.  إذا كنت تريد العودة خطوة للخلف في الهرمية -\> **استخدم `..`**.

---
الـ **Index Route** هو ببساطة "الصفحة الافتراضية" للمسار الأب (Parent Route).

فكر فيه مثل ملف `index.html` في مواقع الويب القديمة. عندما تدخل مجلداً، يقوم السيرفر بعرض `index.html` تلقائياً. في React Router، الـ **Index Route** يقوم بنفس المهمة: هو ما يظهر داخل الـ `<Outlet />` عندما يكون الرابط هو رابط الأب تماماً.

إليك الشرح بالتفصيل:

---

### 1. المشكلة التي يحلها (مشكلة الـ Outlet الفارغ)

تخيل أن لديك تخطيطاً (Layout) لصفحة "لوحة التحكم" (`/dashboard`). هذا التخطيط يحتوي على قائمة جانبية (Sidebar) ومكان لعرض المحتوى (`<Outlet />`).

JavaScript

```
// المسار الأب
path: "/dashboard",
element: <DashboardLayout />, // فيها Sidebar + Outlet
children: [
  { path: "settings", element: <Settings /> }, // /dashboard/settings
  { path: "profile", element: <Profile /> },   // /dashboard/profile
]
```

السؤال: ماذا سيظهر في الـ Outlet إذا فتح المستخدم الرابط /dashboard فقط (بدون settings أو profile)؟

الإجابة: سيظهر الـ Sidebar، ولكن الـ Outlet سيكون فارغاً تماماً! ستبدو الصفحة كأنها مكسورة أو ناقصة.

### 2. الحل: Index Route

نريد أن نقول للراوتر: "إذا دخل المستخدم على `/dashboard` فقط، اعرض له صفحة 'ملخص الإحصائيات' تلقائياً داخل الـ Outlet".

هنا نستخدم **`index: true`** بدلاً من `path`.

---

### 3. كيفية الكتابة (Syntax)

JavaScript

```
const router = createBrowserRouter([
  {
    path: "/dashboard",
    element: <DashboardLayout />, // الأب
    children: [
      // 👇 هذا هو الـ Index Route
      {
        index: true, 
        element: <DashboardHome /> // ستظهر عند زيارة /dashboard
      },
      
      // هذه مسارات فرعية عادية
      {
        path: "settings",
        element: <Settings />
      },
    ],
  },
]);
```

### 4. نقاط جوهرية للفهم

1. **بدون مسار (No Path):** لاحظ أن الـ Index Route لا يحتوي على خاصية `path`. هو يشارك الأب في نفس المسار تماماً.
    
2. **الموقع:** هو يظهر دائماً في الـ `<Outlet />` الخاص بالأب.
    
3. **الاستخدام الشائع:** يستخدم للصفحات الرئيسية (Home Pages) داخل أقسام الموقع، أو لعرض الصفحة الترحيبية عند فتح الموقع لأول مرة (`/`).
    

---

### 5. مثال عملي لمشروعك (Rick and Morty)

تخيل هيكل موقعك كالتالي: لديك `RootLayout` يحتوي على الـ Navbar (الشعار والروابط)، وتحته `Outlet` لباقي المحتوى.

أنت تريد:

1. عندما يفتح المستخدم الموقع `my-site.com/` (الرئيسية)، تظهر له صفحة "Hero Section" ترحيبية.
    
2. عندما يذهب لـ `my-site.com/characters`، تظهر القائمة.
    

هنا، الصفحة الترحيبية هي الـ **Index Route** للمسار الجذري `/`.

JavaScript

```
const router = createBrowserRouter([
  {
    path: "/",
    element: <RootLayout />, // فيه Navbar + Outlet
    errorElement: <ErrorPage />,
    children: [
      // 1. الصفحة الافتراضية (الرئيسية)
      {
        index: true,
        element: <HomeHeroSection />, // تظهر عند فتح الموقع مباشرة
      },
      // 2. صفحة الشخصيات
      {
        path: "characters",
        element: <CharactersList />,
      },
      // 3. صفحة تفاصيل شخصية (Dynamic)
      {
        path: "characters/:id",
        element: <CharacterDetails />,
      },
    ],
  },
]);
```

### الخلاصة:

الـ **Index Route** هو الحشو الافتراضي للـ `Outlet` عندما لا يختار المستخدم أي مسار فرعي آخر.

---
















