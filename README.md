# React Native Assessment – Ansh Patel

**Ansh Patel** | Founder & CEO – APM Marketing | Full Stack Web Developer  
📧 ioansh.co@gmail.com | 🔗 [LinkedIn](https://linkedin.com/in/ansh24k) | 🐙 [GitHub](https://github.com/AnshPatel24k) | 🌐 [Portfolio](https://anshpatel24k.github.io/Ansh.co)

---

## Q1: How do you prevent unnecessary re-renders in a large flat list?

To prevent unnecessary re-renders in a large flat list, I apply the following techniques:

- **`React.memo`** — Wrap list item components so they only re-render when their props actually change.
- **`useCallback`** — Memoize event handlers (e.g., `onPress`) passed as props to avoid creating new function references on every render.
- **Stable `keyExtractor`** — Use unique, stable IDs (not array indexes) so React can reconcile the list efficiently.
- **`getItemLayout`** — When item height is fixed/known, this prop skips dynamic measurement and significantly speeds up scrolling in `FlatList`.
- **`initialNumToRender` & `windowSize`** — Control how many items are rendered initially and kept in memory to reduce load.
- **Avoid inline objects/functions as props** — e.g., avoid `style={{ marginTop: 10 }}` directly in JSX, as this creates a new object reference every render.

> In my freelance projects, I've applied similar memoization and render-optimization patterns in React.js for e-commerce storefronts with large product listings, ensuring smooth, performant UIs across devices.

---

## Q2: Briefly explain what the "Bridge" is in React Native. Why does it matter for app performance?

The **Bridge** in React Native is the communication layer between the **JavaScript thread** and the **Native (platform) thread**.

Since JS and native code run on completely separate threads, any interaction — such as updating the UI, triggering animations, or accessing device APIs — must pass through this bridge as **serialized JSON messages**.

### Why it matters for performance:
- The serialization/deserialization process is **asynchronous** and adds overhead.
- When bridge calls are frequent or heavy (e.g., complex animations, gesture handling), it becomes a **bottleneck**, causing frame drops and UI lag.
- Keeping bridge traffic minimal is key to a smooth 60fps experience.

### The Solution — New Architecture (JSI):
React Native's **JSI (JavaScript Interface)** replaces the old bridge with **direct, synchronous JS-to-native calls**, eliminating serialization overhead and significantly improving performance — especially for animations and real-time interactions.

---

*Submitted by Ansh Patel*
