# **React Native FlatList Cheat Sheet**

A quick reference for using FlatList in React Native, covering its props, features, and common use cases.

---

## **Table of Contents**
1. What Is FlatList?  
2. FlatList Props  
3. Rendering Items  
4. Optimizing Performance  
5. Handling State Updates  
6. Advanced Features (Headers, Footers, Refreshing, etc.)  
7. FlatList vs `Array.map`  

---

## **1. What Is FlatList?**

`FlatList` is a React Native component optimized for rendering large lists efficiently. It handles lazy loading, view recycling, and other performance optimizations.

---

## **2. FlatList Props**

| **Prop**            | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **`data`**          | Array of items to render             | `data={[1, 2, 3]}`                   |
| **`renderItem`**    | Function to render each item         | `renderItem={({ item }) => <Text>{item}</Text>}` |
| **`keyExtractor`**  | Unique key for each item             | `keyExtractor={(item, index) => index.toString()}` |
| **`extraData`**     | Additional data to trigger rerender  | `extraData={state}`                  |
| **`ListHeaderComponent`** | Component to render at the top | `<Text>Header</Text>`                |
| **`ListFooterComponent`** | Component to render at the bottom | `<Text>Footer</Text>`              |
| **`onRefresh`**     | Callback for pull-to-refresh         | `onRefresh={() => fetchData()}`      |
| **`refreshing`**    | Boolean to indicate refreshing state | `refreshing={true}`                  |

---

## **3. Rendering Items**

### **Basic Example**
```tsx
import React from "react";
import { FlatList, Text, View } from "react-native";

const App = () => {
  const data = ["Apple", "Banana", "Cherry"];

  return (
    <FlatList
      data={data}
      renderItem={({ item }) => <Text>{item}</Text>}
      keyExtractor={(item, index) => index.toString()}
    />
  );
};
```

---

### **Rendering with Custom Styles**
```tsx
const App = () => {
  const data = [
    { id: "1", name: "Apple", selected: false },
    { id: "2", name: "Banana", selected: false },
    { id: "3", name: "Cherry", selected: false },
  ];

  return (
    <FlatList
      data={data}
      renderItem={({ item }) => (
        <Text style={{ color: item.selected ? "green" : "black" }}>
          {item.name}
        </Text>
      )}
      keyExtractor={(item) => item.id}
    />
  );
};
```

---

## **4. Optimizing Performance**

### **Use `keyExtractor`**
Ensure each item has a unique key to avoid unnecessary rerenders.
```tsx
keyExtractor={(item) => item.id}
```

---

### **Use `extraData`**
Pass additional state to trigger rerenders only for affected items.
```tsx
extraData={data}
```

---

### **Lazy Loading**
FlatList renders items as they come into view, reducing memory usage for large lists.

---

## **5. Handling State Updates**

### **Updating Items**
Use `map` to update specific items in the list.
```tsx
const toggleSelection = (id) => {
  const updatedData = data.map((item) =>
    item.id === id ? { ...item, selected: !item.selected } : item
  );
  setData(updatedData);
};
```

---

### **Adding Items**
Use `useState` or `useReducer` to append new items.
```tsx
const addItem = () => {
  setData([...data, { id: "4", name: "New Item", selected: false }]);
};
```

---

### **Removing Items**
Filter out the item you want to remove.
```tsx
const removeItem = (id) => {
  setData(data.filter((item) => item.id !== id));
};
```

---

## **6. Advanced Features**

### **Headers and Footers**
```tsx
<FlatList
  data={data}
  renderItem={({ item }) => <Text>{item}</Text>}
  ListHeaderComponent={<Text>Header</Text>}
  ListFooterComponent={<Text>Footer</Text>}
/>
```

---

### **Pull-to-Refresh**
```tsx
<FlatList
  data={data}
  renderItem={({ item }) => <Text>{item}</Text>}
  onRefresh={() => fetchData()}
  refreshing={isRefreshing}
/>
```

---

### **Separators**
```tsx
<FlatList
  data={data}
  renderItem={({ item }) => <Text>{item}</Text>}
  ItemSeparatorComponent={() => <View style={{ height: 1, backgroundColor: "gray" }} />}
/>
```

---

## **7. FlatList vs `Array.map`**

| **Aspect**              | **FlatList**                          | **Array.map**                        |
|--------------------------|---------------------------------------|---------------------------------------|
| **Purpose**              | Optimized for large lists            | General-purpose array iteration      |
| **Performance**          | Handles lazy loading and recycling   | Renders all items at once            |
| **Built-in Features**    | Scrolling, refreshing, separators    | Requires manual implementation       |
| **Customization**        | Highly customizable via props        | Limited customization                |

---

### **When to Use FlatList vs `Array.map`**

| **Scenario**        | **Use FlatList**                     | **Use Array.map**                    |
|---------------------|---------------------------------------|---------------------------------------|
| **Large Lists**      | ✅                                   | ❌                                   |
| **Small Lists**      | Optional                             | ✅                                   |
| **Scrolling**        | ✅                                   | ❌                                   |
| **Pull-to-Refresh**  | ✅                                   | ❌                                   |

---

### **Key Takeaways**
- Use **FlatList** for large lists or when you need features like scrolling, pull-to-refresh, or lazy loading.
- Use **Array.map** for small lists or simple rendering.

---

This cheat sheet focuses entirely on **FlatList** and its features. Let me know if you'd like further refinements or additional examples!