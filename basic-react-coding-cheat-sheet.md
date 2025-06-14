# **React Native Programming Basics Cheat Sheet**

A quick reference for foundational React Native concepts

---

## **Table of Contents**
1. Functions vs Components  
2. Callbacks with Properties  
3. Control Flow (`if`, `else`, `return`, `!==`, `!condition`)  
4. Logical Operators (`||`, `&&`, Truthy/Falsy)  
5. Arrays and `.map`  
6. Shallow Copy (Array/Object)  
7. Enums  
8. Interfaces  
9. `{}` in JSX  
10. Conditional JSX  
11. State Management (`useState`)  
12. State Management (`useReducer`)  

---

## **1. Functions vs Components**

| **Aspect**         | **Function**                          | **Component**                        |
|---------------------|---------------------------------------|---------------------------------------|
| **Purpose**         | Performs a task                      | Builds UI                            |
| **Return Type**     | Any value (e.g., number, string)      | JSX (UI elements)                    |
| **Usage**           | Called directly                      | Used as a tag (`<Component />`)      |

### **Examples**
#### **Function**
```tsx
const add = (a: number, b: number) => a + b;
console.log(add(2, 3)); // Output: 5
```

#### **Component**
```tsx
const Greeting = () => <Text>Hello, World!</Text>;
```

---

## **2. Callbacks with Properties**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Callback Props**  | Pass functions to handle events      | `<Component onPress={callback} />`   |
| **Dynamic Props**   | Pass data through callbacks          | `<Component onPress={() => callback(data)} />` |

### **Examples**
#### **Basic Callback**
```tsx
const Button = ({ onPress }: { onPress: () => void }) => (
  <TouchableOpacity onPress={onPress}>
    <Text>Click Me</Text>
  </TouchableOpacity>
);

const App = () => {
  const handlePress = () => console.log("Button Pressed!");
  return <Button onPress={handlePress} />;
};
```

#### **Callback with Properties**
```tsx
const Button = ({ onPress }: { onPress: (message: string) => void }) => (
  <TouchableOpacity onPress={() => onPress("Hello!")}>
    <Text>Click Me</Text>
  </TouchableOpacity>
);

const App = () => {
  const handlePress = (msg: string) => console.log(msg);
  return <Button onPress={handlePress} />;
};
```

---

## **3. Control Flow**

| **Keyword**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **`if`**            | Executes code if condition is true   | `if (x > 0) { console.log(x); }`     |
| **`else`**          | Executes code if condition is false  | `else { console.log("Negative"); }`  |
| **`return`**        | Exits function and returns value     | `return x + y;`                      |
| **`!==`**           | Checks inequality                    | `if (x !== 0) { console.log(x); }`   |
| **`!condition`**    | Negates a condition                  | `if (!isLoggedIn) { console.log("Not logged in"); }` |

### **Examples**
#### **Basic Control Flow**
```tsx
const checkEven = (num: number) => {
  if (num % 2 === 0) {
    return "Even";
  } else {
    return "Odd";
  }
};
console.log(checkEven(4)); // Output: Even
```

#### **Negation**
```tsx
const isLoggedIn = false;
if (!isLoggedIn) {
  console.log("User is not logged in");
}
```

---

## **4. Logical Operators**

| **Operator**        | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **`||`**            | Returns true if either condition is true | `if (x > 0 || y > 0) { console.log("Positive"); }` |
| **`&&`**            | Returns true if both conditions are true | `if (x > 0 && y > 0) { console.log("Both Positive"); }` |
| **Truthy**          | Values that evaluate to true         | `if ("Hello") { console.log("Truthy"); }` |
| **Falsy**           | Values that evaluate to false        | `if (null) { console.log("Falsy"); }` |

### **Examples**
#### **Logical OR (`||`)**
```tsx
const x = -1;
const y = 5;
if (x > 0 || y > 0) {
  console.log("At least one is positive");
}
```

#### **Logical AND (`&&`)**
```tsx
const x = 5;
const y = 10;
if (x > 0 && y > 0) {
  console.log("Both are positive");
}
```

---

## **5. Arrays and `.map`**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Single Array**    | Stores a list of values              | `const arr = [1, 2, 3];`             |
| **2D Array**        | Stores values in rows and columns    | `const board = [[1, 2], [3, 4]];`    |
| **`.map`**          | Transforms array elements            | `arr.map((x) => x * 2)`              |
| **Render with `.map`** | Dynamically create components      | `arr.map((item) => <Text>{item}</Text>)` |

### **Examples**
#### **Render with `.map`**
```tsx
const fruits = ["Apple", "Banana", "Cherry"];
const FruitList = () => (
  <View>
    {fruits.map((fruit, index) => (
      <Text key={index}>{fruit}</Text>
    ))}
  </View>
);
```

---

## **6. Shallow Copy (Array/Object)**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Array Copy**      | Copies top-level elements            | `const newArr = [...arr];`           |
| **Object Copy**     | Copies top-level properties          | `const newObj = { ...obj };`         |
| **Rerendering**     | Triggers rerender with `useState`    | `setState([...state]);`              |

### **Examples**
#### **Shallow Copy of Array**
```tsx
const arr = [1, 2, 3];
const newArr = [...arr];
newArr[0] = 99;
console.log(arr); // Output: [1, 2, 3]
console.log(newArr); // Output: [99, 2, 3]
```

#### **Shallow Copy of Object**
```tsx
const obj = { name: "John", age: 30 };
const newObj = { ...obj, age: 31 };
console.log(obj.age); // Output: 30
console.log(newObj.age); // Output: 31
```

#### **Rerendering with Shallow Copy**
```tsx
const App = () => {
  const [items, setItems] = useState([1, 2, 3]);

  const updateItem = () => {
    const newItems = [...items];
    newItems[0] = 99;
    setItems(newItems); // Triggers rerender
  };

  return (
    <View>
      {items.map((item, index) => (
        <Text key={index}>{item}</Text>
      ))}
      <Button title="Update" onPress={updateItem} />
    </View>
  );
};
```

---

## **7. Enums**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Definition**      | Define a set of named constants      | `enum GameStatus { IN_PROGRESS, WON, DRAW }` |
| **Usage**           | Use constants for better readability | `GameStatus.IN_PROGRESS`             |

### **Examples**
#### **Define Enum**
```tsx
enum GameStatus {
  IN_PROGRESS,
  WON,
  DRAW,
}
```

#### **Use Enum**
```tsx
const status: GameStatus = GameStatus.IN_PROGRESS;
if (status === GameStatus.WON) {
  console.log("Game Over!");
}
```

---

## **8. Interfaces**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Definition**      | Define the shape of an object        | `interface Props { name: string; age: number }` |
| **Usage**           | Use for props or objects             | `<Component {...props} />`           |

### **Examples**
#### **Define Interface**
```tsx
interface Props {
  name: string;
  age: number;
}
```

#### **Use Interface for Props**
```tsx
const Greeting = ({ name, age }: Props) => (
  <Text>Hello, {name}! You are {age} years old.</Text>
);
```

---

Here’s the continuation of the cheat sheet, covering **step 9 to 12** with sample code for each concept:

---

## **9. `{}` in JSX**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Dynamic Values**  | Embed variables in JSX               | `<Text>{name}</Text>`                |
| **Expressions**     | Embed JavaScript expressions         | `<Text>{x + y}</Text>`               |

### **Examples**
#### **Embed Variables**
```tsx
const name = "John";
const Greeting = () => <Text>Hello, {name}!</Text>;
```

#### **Embed Expressions**
```tsx
const x = 5;
const y = 10;
const Sum = () => <Text>Sum: {x + y}</Text>;
```

#### **Embed Function Calls**
```tsx
const getGreeting = (name: string) => `Hello, ${name}!`;
const Greeting = () => <Text>{getGreeting("John")}</Text>;
```

---

## **10. Conditional JSX**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Ternary Operator** | Render based on condition           | `{isLoggedIn ? <Text>Welcome</Text> : <Text>Please Log In</Text>}` |
| **Logical AND (`&&`)** | Render if condition is true        | `{isLoggedIn && <Text>Welcome</Text>}` |
| **Logical OR (`||`)** | Render fallback if condition is false | `{isLoggedIn || <Text>Please Log In</Text>}` |

### **Examples**
#### **Ternary Operator**
```tsx
const App = ({ isLoggedIn }: { isLoggedIn: boolean }) => (
  <View>
    {isLoggedIn ? <Text>Welcome Back!</Text> : <Text>Please Log In</Text>}
  </View>
);
```

#### **Logical AND (`&&`)**
```tsx
const App = ({ isLoggedIn }: { isLoggedIn: boolean }) => (
  <View>
    {isLoggedIn && <Text>Welcome Back!</Text>}
  </View>
);
```

#### **Logical OR (`||`)**
```tsx
const App = ({ isLoggedIn }: { isLoggedIn: boolean }) => (
  <View>
    {isLoggedIn || <Text>Please Log In</Text>}
  </View>
);
```

---

## **11. State Management (`useState`)**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Initial State**   | Define initial state                | `const [state, setState] = useState(initialValue)` |
| **Update State**    | Update state and trigger rerender   | `setState(newValue)`                 |

### **Examples**
#### **Basic State Management**
```tsx
const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increment" onPress={() => setCount(count + 1)} />
    </View>
  );
};
```

#### **State with Arrays**
```tsx
const App = () => {
  const [items, setItems] = useState([1, 2, 3]);

  const addItem = () => {
    setItems([...items, items.length + 1]); // Add new item
  };

  return (
    <View>
      {items.map((item, index) => (
        <Text key={index}>{item}</Text>
      ))}
      <Button title="Add Item" onPress={addItem} />
    </View>
  );
};
```

#### **State with Objects**
```tsx
const App = () => {
  const [user, setUser] = useState({ name: "John", age: 30 });

  const updateAge = () => {
    setUser({ ...user, age: user.age + 1 }); // Update age
  };

  return (
    <View>
      <Text>Name: {user.name}</Text>
      <Text>Age: {user.age}</Text>
      <Button title="Increase Age" onPress={updateAge} />
    </View>
  );
};
```

---

## **12. State Management (`useReducer`)**

| **Aspect**         | **Purpose**                          | **Example**                          |
|---------------------|---------------------------------------|---------------------------------------|
| **Initial State**   | Define initial state                | `const initialState = { count: 0 };` |
| **Reducer**         | Function to handle state updates    | `function reducer(state, action) {}` |
| **Dispatch Actions** | Trigger state updates              | `dispatch({ type: "increment" });`   |

### **Examples**
#### **Basic Reducer**
```tsx
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return initialState;
    default:
      throw new Error("Unknown action type");
  }
}

const Counter = () => {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <View>
      <Text>Count: {state.count}</Text>
      <Button title="Increment" onPress={() => dispatch({ type: "increment" })} />
      <Button title="Decrement" onPress={() => dispatch({ type: "decrement" })} />
      <Button title="Reset" onPress={() => dispatch({ type: "reset" })} />
    </View>
  );
};
```

#### **Reducer with Complex State**
```tsx
const initialState = { items: [1, 2, 3] };

function reducer(state, action) {
  switch (action.type) {
    case "addItem":
      return { items: [...state.items, action.payload] };
    case "removeItem":
      return { items: state.items.filter((item) => item !== action.payload) };
    default:
      throw new Error("Unknown action type");
  }
}

const App = () => {
  const [state, dispatch] = useReducer(reducer, initialState);

  const addItem = () => dispatch({ type: "addItem", payload: state.items.length + 1 });
  const removeItem = () => dispatch({ type: "removeItem", payload: state.items[0] });

  return (
    <View>
      {state.items.map((item, index) => (
        <Text key={index}>{item}</Text>
      ))}
      <Button title="Add Item" onPress={addItem} />
      <Button title="Remove Item" onPress={removeItem} />
    </View>
  );
};
```

---
