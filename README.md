# **Svelte 5 Navigation Progress Bar** 🚀

A **super smooth and customizable** **navigation progress bar** for **Svelte 5**, powered by:
- **🌀 Svelte 5 Runes** (`$state`, `$derived`)
- **🌊 svelte/motion** (`Tween`)
- **🎨 TailwindCSS**
- **🔮 tailwind-variants & tailwind-merge** for ultimate styling flexibility.

---

## **✨ Features**
✅ **Beautiful animated navigation progress**  
✅ **Fully customizable** 🖌️ (Size & Color Variants)  
✅ **Super optimized with Svelte 5 runes** ⚡  
✅ **Smooth easing animations with `cubicOut`** 🎢  
✅ **No dependencies (except Tailwind utilities)** 🎯

---

## **📸 Preview**
🎥 _Coming soon!_

---

## **🚀 Installation**
If you're using this in a SvelteKit project, install the necessary dependencies first:

```sh
npm install tailwind-merge tailwind-variants
```

---

## **🛠️ Usage**
### **Import the component & customize it!**
```svelte
<script>
	import NavProgress from "./progress.svelte";
</script>

<NavProgress size="md" color="green" />
```

#### **You can also control it dynamically:**
```svelte
<script>
	const size = "lg";
	const color = "rose";
</script>

<NavProgress {size} {color} />
```

---

## **🎨 Customization**
### **🌟 Sizes**
| Variant | Height |
|---------|--------|
| `"sm"`  | `0.5rem` |
| `"md"` (default) | `1rem` |
| `"lg"`  | `1.5rem` |

### **🌈 Colors**
| Variant | Gradient |
|---------|----------|
| `"blue"` | from-sky-700 to-indigo-700 |
| `"rose"` | from-rose-700 to-rose-500 |
| `"amber"` | from-amber-700 to-amber-500 |
| `"green"` | from-green-700 to-green-500 |
| `"purple"` | from-purple-700 to-purple-500 |
| `"indigo"` | from-indigo-700 to-indigo-500 |
| `"red"` | from-red-700 to-red-500 |
| `"yellow"` | from-yellow-700 to-yellow-500 |

---

## **💖 Why Use This?**
Because **who doesn’t love a beautiful, animated progress bar?** 😍  
It makes navigation **feel smoother, more dynamic, and polished!**

> "Good UI is invisible, but you can definitely feel when it's missing!" 🚀

---

## **📜 License**
📝 **MIT** – use it however you like! Just give some love back ❤️

---

## **🤝 Contributing**
👋 Found a bug or have an idea? Open an **issue** or **PR** – I’d love to see your improvements!

