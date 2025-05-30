# 📓 Styling Cheat Sheet

This cheat sheet summarizes the key utilities and concepts from the lessons. Use it as a quick reference while working on your project!

---

## 🎨 Learning about Flexbox

### Key Utilities:

| Utility     | Purpose                           |
| ----------- | --------------------------------- |
| `flex-row`  | Arrange children horizontally.    |
| `flex-col`  | Arrange children vertically.      |
| `flex-wrap` | Wrap children onto the next line. |
| `justify-*` | Align items along the main axis.  |
| `items-*`   | Align items along the cross axis. |

### Example:

```xml
<View className="flex-1 flex-row justify-center items-center bg-gray-100">
  <View className="w-16 h-16 bg-red-500"></View>
  <View className="w-16 h-16 bg-blue-500"></View>
  <View className="w-16 h-16 bg-green-500"></View>
</View>
```

---

## 🧱 Working with View blocks and sizing

### Key Utilities:

| Utility     | Purpose                    |
| ----------- | -------------------------- |
| `w-[value]` | Set width (e.g., `w-1/3`). |
| `h-[value]` | Set height (e.g., `h-20`). |
| `w-full`    | Full parent width.         |
| `h-full`    | Full parent height.        |

### Example:

```xml
<View className="flex-1 flex-wrap flex-row bg-gray-100">
  <View className="w-1/3 h-1/3 bg-pink-300"></View>
  <View className="w-1/3 h-1/3 bg-red-500"></View>
  <View className="w-1/3 h-1/3 bg-yellow-500"></View>
</View>
```

---

## 📏 More sizing tips

### Key Utilities:

| Utility         | Purpose         |
| --------------- | --------------- |
| `min-w-[value]` | Minimum width.  |
| `max-w-[value]` | Maximum width.  |
| `min-h-[value]` | Minimum height. |
| `max-h-[value]` | Maximum height. |

### Example:

```xml
<View className="flex-1 bg-gray-100">
  <View className="w-[40vw] h-[120px] bg-blue-500"></View>
  <View className="w-[300px] h-[50vh] bg-green-500"></View>
</View>
```

---

## ✅ Dynamic Flex Sizing with `basis`, `grow`, and `shrink`

### Key Utilities:

| Utility         | Purpose                            |
| --------------- | ---------------------------------- |
| `basis-[value]` | Starting size (e.g., `basis-1/2`). |
| `grow`          | Allow the element to expand.       |
| `shrink`        | Allow the element to shrink.       |

### Example:

```xml
<View className="flex-1 flex-row bg-gray-100">
  <View className="basis-1/2 grow bg-pink-300"></View>
  <View className="basis-1/3 shrink bg-red-500"></View>
  <View className="basis-1/3 bg-yellow-500"></View>
</View>
```

---

## 🧱 Working with Margins and Paddings

### Key Utilities:

| Utility      | Purpose               |
| ------------ | --------------------- |
| `m-[value]`  | Margin on all sides.  |
| `mx-[value]` | Horizontal margin.    |
| `my-[value]` | Vertical margin.      |
| `p-[value]`  | Padding on all sides. |
| `px-[value]` | Horizontal padding.   |
| `py-[value]` | Vertical padding.     |

### Example:

```xml
<View className="flex-1 bg-gray-100">
  <View className="w-1/3 h-1/3 mx-4 my-8 bg-purple-300"></View>
  <View className="w-1/3 h-1/3 p-4 bg-yellow-300"></View>
</View>
```

---

## 🧱 How Views Expand with Content

### Key Utilities:

| Utility         | Purpose                         |
| --------------- | ------------------------------- |
| `max-w-[value]` | Restrict horizontal expansion.  |
| `max-h-[value]` | Restrict vertical expansion.    |
| `flex-wrap`     | Wrap content when it overflows. |

### Example:

```xml
<View className="bg-blue-300 p-4 max-w-[300px]">
  <Text className="text-white text-center">I’m a very long text that demonstrates the view expanding horizontally.</Text>
</View>
```

---

## 📝 Styling Text with NativeWind CSS

### Key Utilities:

| Utility         | Purpose                                |
| --------------- | -------------------------------------- |
| `text-[color]`  | Set text color (e.g., `text-red-500`). |
| `text-[size]`   | Set font size (e.g., `text-lg`).       |
| `font-[weight]` | Set font weight (e.g., `font-bold`).   |
| `text-[align]`  | Align text (e.g., `text-center`).      |
| `underline`     | Underline text.                        |
| `italic`        | Italicize text.                        |

### Example:

```xml
<Text className="text-purple-500 text-2xl font-black text-center underline">
  I’m a beautifully styled text block! 🌟
</Text>
```

---
