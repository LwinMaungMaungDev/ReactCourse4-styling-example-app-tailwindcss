# React course by Maximilian Schwarzmüller

You can visit _https://tailwindcss.com/_ for documentation. Under Installation, choose Vite.

> npm install tailwindcss @tailwindcss/vite
> Configure the Vite plugin as shown.
> On VS Code, install Tailwind CSS IntelliSense and restart the VS Code.

Then we can start using it. Just read the docs for which class name does what.

```
export default function Header() {
  return (
    <header className="flex flex-col items-center mt-8 mb-16">
      <img
        src={logo}
        alt="A canvas"
        className="mb-8 w-44 h-44 object-contain"
      />
      <h1 className="text-4xl font-semibold tracking-widest text-center uppercase text-amber-800">
        ReactArt
      </h1>
      <p>A community of artists and art-lovers.</p>
    </header>
  );
}

```

## Installing Tailwind v3

The lecture was recorded with Tailwind v3. You can read the docs for installing v3. Just select the version on the top of the page and click Docs. Make sure to select Vite as the framework.

> npm install -D tailwindcss@3 postcss autoprefixer
> npx tailwindcss@3 init -p

After following the instructions, the _tailwind.config.js_ file looks like this.

```
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};

```

The index.css file looks like this.

```
@tailwind base;
@tailwind components;
@tailwind utilities;

```

In addition to these lines in index.css file, we can still add our custom CSS to bring back our nice background image.

```
body {
  background-color: #ffaa00;
  background-image: url("…");
  background-attachment: fixed;
  background-size: cover;
}

```

## Custom Fonts

For custom fonts, we already have the google fonts import in _index.html_ file.

In _tailwind.config.js_ file =>

```
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      fontFamily: {
        title: ['"Pacifico"', "cursive"],
      },
    },
  },
  plugins: [],
};

```

Then we can use it like this.

```
<h1 className="text-4xl font-semibold tracking-widest text-center uppercase text-amber-800 font-title">
  ReactArt
</h1>

```

## Tailwind: Media Queries & Pseudo Selectors

```
export default function Header() {
  return (
    <header className="flex flex-col items-center mt-8 mb-8 md:mb-16">
      <img
        src={logo}
        alt="A canvas"
        className="mb-8 w-44 h-44 object-contain"
      />
      <h1 className="text-xl md:text-4xl font-semibold tracking-widest text-center uppercase text-amber-800 font-title">
        ReactArt
      </h1>
      <p className="text-stone-500">A community of artists and art-lovers.</p>
    </header>
  );
}

```

For pseudo selectors…

```
export default function Button({ children, ...props }) {
  return (
    <button
      className="px-4 py-2 font-semibold uppercase rounded text-stone-900 bg-amber-400 hover:bg-amber-500"
      {...props}
    >
      {children}
    </button>
  );
}

```

## Tailwind: Conditional Styling

Nothing fancy here.

```
export default function Input({ label, invalid, ...props }) {
  let labelClasses = "block mb-2 text-xs font-bold tracking-wide uppercase";
  let inputClasses = "w-full px-3 py-2 leading-tight border rounded shadow";
  if (invalid) {
    labelClasses += " text-red-400";
    inputClasses += " text-red-500 bg-red-100 border-red-300";
  } else {
    labelClasses += " text-stone-300";
    inputClasses += " text-gray-700 bg-stone-300";
  }
  return (
    <p>
      <label className={labelClasses}>{label}</label>
      <input className={inputClasses} {...props} />
    </p>
  );
}

```
