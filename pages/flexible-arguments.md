## Flexible Arguments

---
layout: two-cols
---

```js
// useCount.js
export default function() {
  const count = ref(0)

  function increment() {
    count.value++
  }

  function decrement() {
    count.value--
  }

  return { count, increment, decrement }
}
```

::right::

```js
// In some component
const {
  count,
  increment,
  decrement
} = useCount()
```

---
layout: two-cols
---

```js
// useCount.js
export default function(initial = 0) {
  const count = ref(initial)

  function increment() {
    count.value++
  }

  function decrement() {
    count.value--
  }

  return { count, increment, decrement }
}
```

::right::


```js
// In some component
const {
  count,
  increment,
  decrement
} = useCount(38)
```

---
layout: two-cols
---

```js
// useCount.js
export default function(initial = 0) {
  const count = ref(initial)

  function increment() {
    count.value++
  }

  function decrement() {
    count.value--
  }

  return { count, increment, decrement }
}
```

::right::


```js
// In some component
const myCount = useSomeStore();

const {
  increment,
  decrement
} = useCount(myCount)
```

---
layout: two-cols
---

```js {2,3}
// useCount.js
export default function(initial = 0) {
  const count = ref(initial)

  function increment() {
    count.value++
  }

  function decrement() {
    count.value--
  }

  return { count, increment, decrement }
}
```

::right::


```js {2,7}
// In some component
const myCount = useSomeStore();

const {
  increment,
  decrement
} = useCount(myCount)
```

---
layout: two-cols
---

```ts {1-8}
// useCount.ts
import type {
  MaybeRefOrGetter
} from 'vue'

export default function(
  initial: MaybeRefOrGetter<number> = 0
) {
  const count = ref(initial)

  // ...

  return { count, increment, decrement }
}
```

::right::


```js
// In some component
const myCount = useSomeStore();

const {
  increment,
  decrement
} = useCount(myCount)
```


---
layout: two-cols
---

```js
// useLogger.js
export default function(value) {
  watchEffect(() => {
    console.log(value);
  })
}
```

::right::

```js
// In some component
const someString = ref('Hello, world!');

useLogger(someString)
```

---
layout: two-cols
---

```js
// useLogger.js
export default function(value) {
  watchEffect(() => {
    console.log(value);
  })
}
```

::right::

```js
// In some component
const someString = ref('Hello, world!');

useLogger(someString)

someString.value = 'Hello, Vue Nation!'
```

---
layout: two-cols
---

```js
// useLogger.js
export default function(value) {
  watchEffect(() => {
    console.log(value);
  })
}
```

::right::

```js
// In some component
useLogger('Hello, world!')
```

---
layout: two-cols
---

```js {4}
// useLogger.js
export default function(value) {
  watchEffect(() => {
    console.log(value);
  })
}
```

::right::

```js
// In some component
useLogger('Hello, world!')
```

---
layout: two-cols
---

```js {4}
// useLogger.js
export default function(value) {
  watchEffect(() => {
    console.log(toValue(value));
  })
}
```

::right::

```js
// In some component
useLogger('Hello, world!')
```

---
layout: two-cols
---

```js
// useLogger.ts
export default function(
  value: MaybeRefOrGetter<string>
) {
  watchEffect(() => {
    console.log(toValue(value));
  })
}
```

::right::

```js
// In some component
useLogger('Hello, world!')
```

---
layout: center
---

## Use `ref` for inputs that need to be reactive

---
layout: center
---

## Use `toValue` for inputs that are *not* reactive

---
layout: center
---

## Use `toValue` for inputs that are *not* reactive

---
layout: center
---

## Your composables can be used in any way

