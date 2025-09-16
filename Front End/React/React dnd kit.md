---
Created: 2025-07-27T17:38
---
## 1. **What is DnD Kit?**

`@dnd-kit/core` is a **lightweight, modern drag-and-drop library** for React.

It’s **headless** → gives you drag logic, you style/layout yourself.

You usually combine:

- `**@dnd-kit/core**` → base drag & drop events
- `**@dnd-kit/sortable**` → for sortable lists/grids
- `**@dnd-kit/modifiers**` → for constraints (e.g. restrict to vertical)

---

## 2. **Install**

```Shell
npm install @dnd-kit/core @dnd-kit/sortable @dnd-kit/modifiers
```

---

## 3. **Minimal Example – Sortable List**

```JavaScript
import React, { useState } from "react";
import {
  DndContext,
  closestCenter,
  PointerSensor,
  useSensor,
  useSensors,
} from "@dnd-kit/core";
import {
  arrayMove,
  SortableContext,
  verticalListSortingStrategy,
  useSortable,
} from "@dnd-kit/sortable";
import { CSS } from "@dnd-kit/utilities";

const SortableItem = ({ id }) => {
  const { attributes, listeners, setNodeRef, transform, transition } =
    useSortable({ id });

  const style = {
    transform: CSS.Transform.toString(transform),
    transition,
    padding: "10px",
    margin: "4px 0",
    background: "lightblue",
    borderRadius: "4px",
  };

  return (
    <div ref={setNodeRef} style={style} {...attributes} {...listeners}>
      {id}
    </div>
  );
};

export default function App() {
  const [items, setItems] = useState(["🍎 Apple", "🍌 Banana", "🍇 Grape"]);

  const sensors = useSensors(
    useSensor(PointerSensor) // detects mouse/touch
  );

  const handleDragEnd = (event) => {
    const { active, over } = event;
    if (active.id !== over.id) {
      setItems((items) => {
        const oldIndex = items.indexOf(active.id);
        const newIndex = items.indexOf(over.id);
        return arrayMove(items, oldIndex, newIndex);
      });
    }
  };

  return (
    <DndContextsensors={sensors}
      collisionDetection={closestCenter}
      onDragEnd={handleDragEnd}
    >
      <SortableContext items={items} strategy={verticalListSortingStrategy}>
        {items.map((item) => (
          <SortableItem key={item} id={item} />
        ))}
      </SortableContext>
    </DndContext>
  );
}
```

✅ **That’s the simplest sortable list with drag animations!**

---

## 4. **Key Components**

|Component|Purpose|
|---|---|
|`DndContext`|The top-level provider that manages drag events|
|`SortableContext`|Defines a sortable container|
|`useSortable()`|Hook to make an item draggable/sortable|
|`arrayMove()`|Helper to reorder arrays|
|`PointerSensor`|Sensor for mouse/touch drag|
|`closestCenter`|Collision detection algorithm (you can swap with `closestCorners`, etc.)|

---

## 5. **Drag End Event**

When drag finishes, `onDragEnd(event)` gives:

```JavaScript
{
  active: { id: "🍎 Apple" },  // dragged item
  over: { id: "🍇 Grape" }     // item it was dropped over
}
```

Then you reorder your state accordingly.

---

## 6. **Sorting Strategies**

When using `SortableContext`, you can define **layout strategy**:

- `verticalListSortingStrategy` → for vertical lists
- `horizontalListSortingStrategy` → for horizontal
- `rectSortingStrategy` → for grids

---

## 7. **Styling While Dragging**

DnD Kit uses **CSS transforms** for smooth dragging.

You can customize:

```JavaScript
const style = {
  transform: CSS.Transform.toString(transform),
  transition,
  opacity: isDragging ? 0.5 : 1,
};
```

---

## 8. **Gotchas**

✅ Must wrap **all draggable elements inside** `**SortableContext**`

✅ Each draggable needs a **unique** `**id**`

✅ `**useSortable**` **must be called in a component with a single root DOM element**

✅ DnD Kit is **headless** → you handle layout & styling yourself

✅ Use `useSensors()` for better touch + mouse support

---

## 9. **Quick Summary Table**

|Step|What to Do|
|---|---|
|1|Wrap your app in `<DndContext>`|
|2|Use `useSensors()` + `PointerSensor` for drag detection|
|3|Inside, use `<SortableContext items={items}>`|
|4|Make each item `useSortable({ id })`|
|5|On `onDragEnd`, reorder using `arrayMove()`|
|6|Style with `transform` + `transition` from `useSortable`|

---

## 10. **Real-World Example: Kanban Columns**

You can also have **multiple Droppable areas**:

- Each column is a `SortableContext`
- Cards are `SortableItem`s
- `onDragEnd` checks if `active` & `over` are in different containers

Would you like me to show a **multi-column Kanban board example with DnD Kit**?