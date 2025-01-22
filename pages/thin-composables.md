# Thin Composables

---
layout: center
---

````md magic-move
```js
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}
```

```js {8-11}
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}
```

```js
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}
```

```js
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```

```js {15-20}
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```

```js
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(() => {
    if (!user.value.name) return 'Hello, Guest!'
    return `Hello, ${user.value.name}!`
  })

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```

```js
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'
import { generateGreeting } from './lib/userLogic'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(
    () => generateGreeting(user.value.name)
  )

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```

```js {10}
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'
import { generateGreeting } from './lib/userLogic'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(
    () => generateGreeting(user.value.name)
  )

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```

```js {10}
// useGreeting.js
import { computed } from 'vue'
import { useUserStore } from './useUserStore'
import { generateGreeting } from './lib/userLogic'

export function useGreeting() {
  const { user } = useUserStore()

  const greeting = computed(
    () => generateGreeting(toValue(user).name)
  )

  return { greeting }
}

// lib/userLogic.js
export function generateGreeting(name) {
  if (!name) return 'Hello, Guest!'
  return `Hello, ${name}!`
}
```
````
