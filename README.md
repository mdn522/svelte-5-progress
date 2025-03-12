# **Svelte 5 Navigation Progress Bar** 🚀

A **super smooth and customizable** **navigation progress bar** for **Svelte 5**, powered by:

- **🌀 Svelte 5 Runes** (`$state`, `$derived`)
- **🌊 svelte/motion** (`Tween`)
- **🎨 TailwindCSS v4**
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

![image](https://github.com/user-attachments/assets/e9fc2689-f35e-41e7-bf10-158db5d17eed)


---

## **🚀 Installation**

If you're using this in a SvelteKit project, install the necessary dependencies first:

```sh
npm install @friendofsvelte/progress
```

In `app.css`:

Use `@source` to explicitly register source paths relative to the stylesheet:

```css
@source "../node_modules/@friendofsvelte/progress/dist";
```

> Read more about [@source register](https://tailwindcss.com/docs/detecting-classes-in-source-files#explicitly-registering-sources)


---

## **🛠️ Usage**

### **Import the component & customize it!**

```svelte
<script>
	import { Progress } from "@friendofsvelte/progress";
</script>

<Progress size="md" color="green" />
```

#### **You can also control it dynamically:**

```svelte
<script>
	const size = "lg";
	const color = "rose";
</script>

<Progress {size} {color} />
```

---

## **🎨 Customization**

### **🌟 Sizes**

| Variant          | Height   |
|------------------|----------|
| `"sm"`           | `0.5rem` |
| `"md"` (default) | `1rem`   |
| `"lg"`           | `1.5rem` |

### **🌈 Colors**

| Variant    | Gradient                      |
|------------|-------------------------------|
| `"blue"`   | from-sky-700 to-indigo-700    |
| `"rose"`   | from-rose-700 to-rose-500     |
| `"amber"`  | from-amber-700 to-amber-500   |
| `"green"`  | from-green-700 to-green-500   |
| `"purple"` | from-purple-700 to-purple-500 |
| `"indigo"` | from-indigo-700 to-indigo-500 |
| `"red"`    | from-red-700 to-red-500       |
| `"yellow"` | from-yellow-700 to-yellow-500 |

---

Sure! Here's a **cute** and **fun** way to let them know they **can** customize the navigation logic, but *seriously,
why would they?* because **this component is already perfect!** 😎✨

---

### **🎨 Custom component (but like, do you even need to?)** 💅

Okay, okay—*we get it.* You love control. You want to tweak everything.

🌟 **Guess what?** You *can*! If you're feeling adventurous, you can create your own progress component using `let nav`
state.

```svelte
<script lang="ts">
    type Nav = {
      is_navigating: boolen,
      progress: Tween, 
    }
	import { nav } from "@friendofsvelte/progress";
</script>
<div custom-nav-progress ...></div>
```

But let's be real— **you probably won’t need to**.  
Why? Because **this component already does all the magic for you!** 🪄✨

Unless you have some **wild** navigation setup (*like, interdimensional travel?* 🚀), you can just sit back, relax, and
let this **super smooth, stylish progress bar** do all the heavy lifting for you.

> "Customization is great, but perfection is effortless. Let **Progress** do its thing." – Some wise Svelte Wizard 🧙‍♂️

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

