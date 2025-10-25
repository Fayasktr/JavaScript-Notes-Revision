# JavaScript Notes – Quick Revision Guide (No OOP)

A concise, exam-focused summary of JavaScript essentials from basics to advanced (excluding OOP). Skim headings, scan code blocks, and review tips right before exams.

- Legend: // => comment, ❗ pitfalls, ✅ best practice
- Try snippets in your browser console or Node.js

1) Setup & Runtimes
- Runtimes: Browser (window, document), Node.js (global, require/import)
- Strict mode: 'use strict' at top to catch bugs
- Running code: <script>, modules: <script type="module">
- Console: console.log/info/warn/error, console.table(obj), console.time/console.timeEnd

2) Variables
- let: block-scoped, re-assignable
- const: block-scoped, not re-assigned (but object/array contents can change)
- var: function-scoped; avoid due to hoisting quirks
- Naming: camelCase for variables/functions; UPPER_SNAKE_CASE for constants

3) Data Types
- Primitive: string, number, boolean, null, undefined, symbol, bigint
- Reference: object, array, function, Date, RegExp, Map, Set, etc.
- typeof: typeof null === 'object' ❗ historic bug
- Check arrays: Array.isArray(x)

4) Type Conversion
- String(x), Number(x), Boolean(x)
- Parse: parseInt('42px', 10), parseFloat('3.14')
- Truthy/Falsy: falsy => 0, '', null, undefined, NaN, false

5) Operators
- Arithmetic: + - * / % **
- Assignment: = += -= *= /= %= **=
- Comparison: === !== (strict) over == != (loose) ❗
- Logical: && || !, nullish coalescing ??, optional chaining ?. 
- Ternary: cond ? a : b
- Spread/Rest: ...arr, function f(...args) {}
- Destructuring: const {a} = obj; const [x,y] = arr

6) Strings
- Template literals: `Hello ${name}`; multiline strings; expressions
- Useful methods: length, toUpperCase, toLowerCase, trim, slice, substring, includes, indexOf, startsWith, endsWith, split, replace/replaceAll, padStart/padEnd, repeat

7) Numbers & Math
- NaN: Number.isNaN(x) preferred over isNaN
- Safe integers: Number.MAX_SAFE_INTEGER
- Rounding: Math.round, floor, ceil, trunc
- Random: Math.random() [0,1). Example: min..max
  const randInt = (min, max) => Math.floor(Math.random()*(max-min+1))+min;
- Parsing: Number('3.2'), parseInt, parseFloat

8) Dates & Time
- Create: new Date(), new Date(ms), new Date('2020-01-01'), new Date(y,m,d)
- Methods: getFullYear, getMonth(0-11), getDate, getDay(0-6), getHours, etc.
- Timestamps: Date.now()
- Format: toISOString(), toLocaleString()

9) Booleans & Conditionals
- if/else, else if
- switch (use breaks)
- Short-circuit: a && doIfA(); b || setDefault(); x ?? defaultForNullOrUndefined

10) Loops & Iteration
- for (init; cond; step)
- while, do..while
- for..of for arrays/iterables; for..in for object keys (use with care)
- break, continue; label rarely used
- array.forEach(fn) for side effects (cannot break)

11) Functions
- Declarations: function name() {}
- Expressions: const fn = function() {}
- Arrow: const fn = (a) => a+1; implicit return if no braces
- Default params: function f(a=1) {}
- Rest params: function f(...args) {}
- Return early; pure functions for predictability

12) Scope, Closures, Hoisting
- Scope: global, function, block
- let/const are block-scoped; var is function-scoped
- Hoisting: var declarations hoisted as undefined; function declarations hoisted; let/const in TDZ
- Closures: inner functions capture outer variables
  function counter(){ let c=0; return ()=>++c }

13) Arrays
- Creation: [], new Array(n)
- Access: arr[i]; length; last: arr.at(-1)
- Add/Remove: push, pop, shift, unshift, splice
- Copy/Slice: slice, toSpliced (immutable), structuredClone(obj)
- Combine: concat, spread [...a, ...b]
- Search: indexOf, includes, find, findIndex, some, every
- Transform: map, filter, reduce, flat, flatMap
- Sort: sort(compareFn) ❗ mutates; shallow copy first: [...arr].sort()
- Iterate: for..of, forEach

14) Objects (Non-OOP usage)
- Literals: const user = {name:'A', age:20}
- Access: dot user.name or bracket user['name']
- Shallow copy/merge: Object.assign({}, a, b), {...a, ...b}
- Keys/Values/Entries: Object.keys, Object.values, Object.entries
- Optional chaining: obj?.prop?.[i]
- Nullish coalescing: obj.prop ?? default
- Freeze/Seal: Object.freeze(obj) prevents mutation

15) JSON
- Serialize: JSON.stringify(obj[, replacer[, space]])
- Parse: JSON.parse(str)
- Beware circular refs in stringify ❗

16) DOM Basics (Browser)
- Select: document.getElementById, querySelector, querySelectorAll
- Create/Insert: document.createElement, append, prepend, before, after, remove
- Classes/Attrs: classList.add/remove/toggle, setAttribute/getAttribute, dataset
- Content: textContent, innerHTML (be wary of XSS) ❗

17) Events
- Listen: element.addEventListener('click', handler)
- Remove: element.removeEventListener
- Event object: e.target, e.currentTarget, e.preventDefault, e.stopPropagation
- Delegation: parent.addEventListener('click', e=>{ if(e.target.matches('button')){} })

18) Forms & Validation
- Access: form.elements, input.value, checked, files
- Built-in validation attrs: required, min, max, pattern
- Submit: form.addEventListener('submit', e=>{ e.preventDefault(); })

19) Fetch API & HTTP
- Basic: fetch(url).then(r=>r.json())
- Options: method, headers, body(JSON.stringify(data))
- Errors: fetch only rejects on network errors; check r.ok; r.status
- Abort: const c=new AbortController(); fetch(url,{signal:c.signal}); c.abort()
- CORS: server must allow; browsers enforce

20) Promises
- new Promise((resolve, reject)=>{ ... })
- then/catch/finally chain; return values forward
- Promise.all, allSettled, race, any

21) Async/Await
- Use inside async function
  async function get(){ try{ const r=await fetch('/api'); if(!r.ok) throw new Error(r.status); const d=await r.json(); return d; } catch(e){ console.error(e) } }
- Parallel: const [a,b]=await Promise.all([pa, pb])

22) Error Handling
- try/catch/finally
- Throw: throw new Error('message')
- Custom errors by extending Error (OOP excluded here; concept only)

23) Modules
- ES modules: export const x=1; export default function(){}
- Import: import x, {y as z} from './m.js'
- In browser: <script type="module" src="m.js"></script>
- In Node (ESM): package.json {"type":"module"}
- CommonJS: require/module.exports (legacy in Node)

24) ES6+ Highlights
- let/const, arrow funcs, template literals
- Destructuring, default params, rest/spread
- Classes (OOP) – excluded from this guide
- Map/Set, WeakMap/WeakSet
- Optional chaining (?.), nullish coalescing (??)
- BigInt: 123n; operations with BigInt only
- Modules, async/await, generators (advanced)

25) Map, Set, WeakMap, WeakSet
- Map: ordered key-value; keys of any type
  const m=new Map([["a",1]]); m.set("b",2); m.get("a")
- Set: unique values
  const s=new Set([1,2,2]); s.has(2); s.add(3)
- WeakMap/WeakSet: keys must be objects; weakly held; not iterable

26) Regex (Quick)
- Literals: /pattern/flags e.g., /\d+/g
- Test/Match: re.test(str), str.match(re), str.replace(re, repl)
- Useful: \d digit, \w word, . any, ^ start, $ end, [] set, () group, + * ? quantifiers

27) Storage
- localStorage: persistent key/value strings
  localStorage.setItem('k', JSON.stringify(v)); JSON.parse(localStorage.getItem('k'))
- sessionStorage: per-tab lifetime
- Cookies: document.cookie='k=v; path=/; max-age=3600'

28) Performance & Microtasks
- Debounce/Throttle (concepts): control frequency of handlers
- Event loop: call stack, queue, microtask queue (Promise callbacks)
- requestAnimationFrame for visual updates

29) Accessibility & Semantics
- Use semantic HTML, ARIA wisely
- Focus management, keyboard handlers

30) Small but Handy
- Optional defaulting: a ||= b; a &&= b; a ??= b
- Object utils: hasOwn(obj, key) or Object.hasOwn(obj, key)
- Nullish vs OR: 0 || 5 => 5, 0 ?? 5 => 0
- Number formatting: (12345.6).toLocaleString('en-IN')
- Intl.DateTimeFormat/NumberFormat for i18n

31) Common Patterns
- IIFE: (()=>{ /* scoped */ })()
- Module pattern (ESM preferred)
- Fetch with timeout via AbortController

32) Debugging Tips
- Breakpoints in DevTools, watch expressions
- console.assert(cond, 'msg'), console.dir(obj)
- Source maps when bundling

33) Tooling Mentions
- npm/yarn/pnpm, package.json scripts
- Bundlers: Vite, Webpack, Parcel; Transpiler: Babel
- Linters/Formatters: ESLint, Prettier

Quick Recipes
- Copy array: const b=[...a]
- Merge objects: const c={...a,...b}
- Remove item from array immutably: const r=a.filter(x=>x!==target)
- Unique array: [...new Set(arr)]
- Deep clone: structuredClone(obj) or JSON.parse(JSON.stringify(obj)) (❗ loses methods/Date)

Practice Tasks
- Build a todo with localStorage
- Fetch API list with loading/error states
- Form validation with regex and events

Good luck on your exam! Review this once more and try a few snippets.
