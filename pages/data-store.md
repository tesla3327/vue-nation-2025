# Data Store Pattern

---
layout: center
---

Three main problems with managing state between components:

<v-clicks>

1. Prop drilling
1. Event frothing
1. Cousin components

</v-clicks>

---
layout: center
---

## 1. Prop Drilling

<img src="/prop-drilling.svg" class="max-w-sm" />

---
layout: center
---

## 2. Event Frothing

<img src="/event-frothing.svg" class="max-w-sm" />

---
layout: center
---

## 3. Cousin Components

<img src="/cousin-components.svg" class="max-w-sm" />

---
layout: center
---

## Data Store Pattern

<img src="/datastore.svg" class="max-w-sm" />

---
layout: center
---

Use a composable to create a shareable data store.

It has 3 parts:

<v-clicks>

1. A global state singleton
1. Exporting some or all of this state
1. Methods to access and modify the state

</v-clicks>

---
layout: center
---

## 1. Global State Singleton

````md magic-move
```ts
// useUserSettings.js
export default () => {
  const state = reactive({
    darkMode: false,
    sidebarCollapsed: false,
    theme: 'nord',
  });

  // ...
}
```

```ts
// useUserSettings.js
const state = reactive({
  darkMode: false,
  sidebarCollapsed: false,
  theme: 'nord',
});

export default () => {
  // ...
}
```

```ts
// useUserSettings.js
const state = reactive({
  darkMode: false,
  sidebarCollapsed: false,
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed } = toRefs(state);

  // ...

  return {
    darkMode,
    sidebarCollapsed,
  };
}
```

```ts {9,13-16}
// useUserSettings.js
const state = reactive({
  darkMode: false,
  sidebarCollapsed: false,
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed } = toRefs(state);

  // ...

  return {
    darkMode,
    sidebarCollapsed,
  };
}
```
````

---
layout: center
---

```html
<!-- SomeComponent.vue -->
<script setup>
import useUserSettings from '~/composables/useUserState';
const { darkMode } = useUserSettings();
const toggleDarkMode = () => {
  darkMode.value = !darkMode.value;
}
</script>
```

---
layout: center
---

````md magic-move
```ts
// useUserSettings.js
const state = reactive({
  // ...
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed, theme } = toRefs(state);

  // ...

  return {
    // ...
    theme: readonly(theme),
  };
}
```

```ts
// useUserSettings.js
const state = reactive({
  // ...
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed, theme } = toRefs(state);

  const changeTheme = (newTheme) => {
    if (themes.includes(newTheme)) {
      // Only update if it's a valid theme
      state.theme = newTheme;
    }
  }

  return {
    // ...
    theme: readonly(theme),
  };
}
```

```ts
// useUserSettings.js
const state = reactive({
  // ...
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed, theme } = toRefs(state);

  const changeTheme = (newTheme) => {
    if (themes.includes(newTheme)) {
      // Only update if it's a valid theme
      state.theme = newTheme;
    }
  }

  return {
    // ...
    theme: readonly(theme),
    changeTheme,
  };
}
```

```ts {10-15}
// useUserSettings.js
const state = reactive({
  // ...
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed, theme } = toRefs(state);

  const changeTheme = (newTheme) => {
    if (themes.includes(newTheme)) {
      // Only update if it's a valid theme
      state.theme = newTheme;
    }
  }

  return {
    // ...
    theme: readonly(theme),
    changeTheme,
  };
}
```

```ts {4,10-15,19-20}
// useUserSettings.js
const state = reactive({
  // ...
  theme: 'nord',
});

export default () => {
  const { darkMode, sidebarCollapsed, theme } = toRefs(state);

  const changeTheme = (newTheme) => {
    if (themes.includes(newTheme)) {
      // Only update if it's a valid theme
      state.theme = newTheme;
    }
  }

  return {
    // ...
    theme: readonly(theme),
    changeTheme,
  };
}
```
````

---


## What about Pinia?

<v-clicks>

- Understand what Pinia is doing
- Simpler method of state management
- More flexible
- No support for SSR, etc.

</v-clicks>
