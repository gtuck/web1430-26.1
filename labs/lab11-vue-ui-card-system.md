# Lab 11 – Vue UI Card System

## Purpose

Components are the core building block of Vue. This lab introduces Single File Components by building a reusable card system and composing those cards from a reactive data array in the parent. The focus is on understanding how data flows down through props and how the template reacts automatically when data changes.

## Skills practiced

- Creating Vue Single File Components (`.vue` files)
- Declaring reactive data with `ref()` and arrays
- Passing data to child components using `defineProps`
- Rendering lists with `v-for` and `:key`
- Conditional rendering with `v-if` and `v-else`
- Dynamic attribute binding with `:class` and `:disabled`
- Keeping component templates focused and readable

## What you're building

A **Team Directory** for a fictional campus department. Each team member is displayed as a card showing their name, role, department, and availability status. A filter control in the parent component allows filtering by department. All data is reactive — changing the filter updates the displayed cards with no manual DOM manipulation.

---

## Part 1: Scaffold the Vue project

In `labs/`, run:

```bash
npm create vite@latest lab11 -- --template vue
cd lab11
npm install
npm run dev
```

Verify the default Vue app runs in the browser. Then:
- Delete the contents of `src/App.vue` (you will rewrite it)
- Delete `src/components/HelloWorld.vue`
- Create `src/components/MemberCard.vue` (empty for now)
- Add `node_modules/` and `dist/` to `.gitignore`

---

## Part 2: Team data

In `src/App.vue`, inside `<script setup>`, define the following reactive data:

```js
import { ref, computed } from 'vue';

const members = ref([
  { id: 1, name: 'Dr. Sarah Chen', role: 'Professor', department: 'Computer Science', available: true },
  { id: 2, name: 'Marcus Johnson', role: 'Lab Assistant', department: 'Computer Science', available: false },
  { id: 3, name: 'Priya Patel', role: 'Advisor', department: 'Student Services', available: true },
  { id: 4, name: 'Tom Rivera', role: 'Technician', department: 'IT Support', available: true },
  { id: 5, name: 'Aisha Williams', role: 'Professor', department: 'Computer Science', available: true },
  { id: 6, name: 'Jake Morrison', role: 'Counselor', department: 'Student Services', available: false },
  { id: 7, name: 'Keiko Tanaka', role: 'Help Desk', department: 'IT Support', available: true },
  { id: 8, name: 'Luis Garcia', role: 'Professor', department: 'Computer Science', available: false },
]);

const selectedDepartment = ref('All');

const departments = computed(() => {
  const depts = [...new Set(members.value.map(m => m.department))];
  return ['All', ...depts];
});

const filteredMembers = computed(() => {
  if (selectedDepartment.value === 'All') return members.value;
  return members.value.filter(m => m.department === selectedDepartment.value);
});
```

---

## Part 3: MemberCard component

In `src/components/MemberCard.vue`:

```vue
<script setup>
defineProps({
  name: {
    type: String,
    required: true,
  },
  role: {
    type: String,
    required: true,
  },
  department: {
    type: String,
    required: true,
  },
  available: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <article class="member-card" :class="{ 'member-card--unavailable': !available }">
    <header class="member-card__header">
      <h2 class="member-card__name">{{ name }}</h2>
      <span
        class="member-card__status"
        :class="available ? 'status--available' : 'status--unavailable'"
        :aria-label="available ? 'Available' : 'Not available'"
      >
        {{ available ? 'Available' : 'Unavailable' }}
      </span>
    </header>

    <p class="member-card__role">{{ role }}</p>
    <p class="member-card__department">{{ department }}</p>

    <button
      class="member-card__btn"
      :disabled="!available"
      :aria-disabled="!available"
    >
      Schedule Meeting
    </button>
  </article>
</template>

<style scoped>
.member-card {
  border: 1px solid #ddd;
  border-radius: 0.5rem;
  padding: 1rem;
}

.member-card--unavailable {
  opacity: 0.6;
}

.member-card__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 0.5rem;
}

.status--available { color: green; }
.status--unavailable { color: #999; }

.member-card__btn:disabled {
  cursor: not-allowed;
  opacity: 0.5;
}
</style>
```

---

## Part 4: App.vue template

```vue
<script setup>
// (data from Part 2)
import MemberCard from './components/MemberCard.vue';
</script>

<template>
  <div class="app">
    <header class="app-header">
      <h1>Department Directory</h1>
    </header>

    <main>
      <div class="filter-bar" role="group" aria-label="Filter by department">
        <button
          v-for="dept in departments"
          :key="dept"
          :class="['filter-btn', { 'filter-btn--active': selectedDepartment === dept }]"
          :aria-pressed="selectedDepartment === dept"
          @click="selectedDepartment = dept"
        >
          {{ dept }}
        </button>
      </div>

      <p class="result-count" aria-live="polite">
        Showing {{ filteredMembers.length }} of {{ members.length }} members
      </p>

      <div class="member-grid" v-if="filteredMembers.length > 0">
        <MemberCard
          v-for="member in filteredMembers"
          :key="member.id"
          :name="member.name"
          :role="member.role"
          :department="member.department"
          :available="member.available"
        />
      </div>

      <p v-else class="empty-state">No members in this department.</p>
    </main>
  </div>
</template>

<style>
/* Global styles in App.vue or a separate main.css */
.member-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}
</style>
```

---

## Part 5: Required additions

After the base app works, add the following enhancements:

### 5.1 Available-only toggle

Add a checkbox above the grid:

```vue
<label>
  <input type="checkbox" v-model="showAvailableOnly">
  Show available only
</label>
```

Update `filteredMembers` to also filter by `showAvailableOnly`:

```js
const showAvailableOnly = ref(false);

const filteredMembers = computed(() => {
  let result = members.value;
  if (selectedDepartment.value !== 'All') {
    result = result.filter(m => m.department === selectedDepartment.value);
  }
  if (showAvailableOnly.value) {
    result = result.filter(m => m.available);
  }
  return result;
});
```

### 5.2 Result count

The `aria-live="polite"` result count (`"Showing X of Y members"`) should update automatically as the filter and toggle change. No additional code needed — it uses `filteredMembers` which is already reactive.

---

## Testing requirements

- [ ] All 8 cards display on initial load
- [ ] Clicking a department filter button shows only members from that department
- [ ] "Show available only" checkbox filters out unavailable members
- [ ] Both filters work together (e.g., CS department + available only)
- [ ] The result count updates with each filter change
- [ ] `v-if` empty state shows when no members match
- [ ] "Schedule Meeting" button is visually disabled for unavailable members
- [ ] `:key` is present on both `v-for` loops (departments and members)

---

## Deliverable

Commit the `labs/lab11/` Vue project (excluding `node_modules/` and `dist/`). Push to GitHub. Deploy to Netlify or Vercel.

Submit to Canvas: live URL, repo URL.

---

## Process reflection (in `labs/lab11/notes.md`)

Answer in 4–6 sentences:
- When you changed `selectedDepartment.value`, what happened in the template and why?
- What is the difference between `ref()` and `computed()` — when would you use each?
- What does `:key` do in a `v-for`, and what happens if you omit it?

---

## Rubric

| Criterion | Excellent (4) | Proficient (3) | Developing (2) | Incomplete (1) |
|-----------|--------------|----------------|----------------|----------------|
| **MemberCard component** | All four props typed with `defineProps`; all fields rendered; disabled button; status class | Three props; most fields rendered | Two props; some rendering | Not componentized |
| **Reactivity** | `computed` for filtering; both filter controls update the DOM automatically | Computed used; one filter works | One filter works with direct logic | Manual DOM updates |
| **v-for and :key** | Both `v-for` loops have correct `:key` values | One loop missing `:key` | `:key` absent | No `v-for` |
| **v-if / empty state** | `v-if` on grid, `v-else` empty state, both work correctly | `v-if` works; no empty state | Partial conditional | No conditional rendering |
| **Accessibility** | `aria-live` on count; `aria-pressed` on filter buttons; `aria-disabled` on card button | Two of three ARIA attributes | One | None |
| **Reflection** | Specific; all three prompts addressed | Two prompts | Vague | Missing |
