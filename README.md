# tailwind4 × Vite × React19 × ShadcnUI

## 1. プロジェクト作成

```bash
npm create vite@latest my-react-app -- --template react
```

## 2. ディレクトリ移動して npm install

```bash
cd my-react-app
npm install
```

## 3. tailwind4 のインストール

```bash
npm install tailwindcss @tailwindcss/vite
```

必要に応じて以下

```bash
npm install @tailwindcss/typography @tailwindcss/forms
```

## 4. vite.config.js を以下のように

```bash
import path from "path";
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import tailwindcss from "@tailwindcss/vite";

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), tailwindcss()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});

```

## 5. index.css を以下のように（これ以外は消すのがポイント）

```css
@import "tailwindcss";

@custom-variant dark (&:is(.dark *));

/* Plugins */
@plugin '@tailwindcss/forms';
@plugin '@tailwindcss/typography';

@plugin "tailwindcss-animate";

/* Class based dark mode */
@variant dark (&:where(.dark, .dark *));
```

## 6. 以下のコマンドで JSON ファイルを作成して中身を以下のように指定

```bash
touch jsconfig.json
```

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

## 7. 以下のコマンドで shadcn ui をインストール

```bash
npx shadcn@canary init
```

## 8. 以下で button コンポーネントインストール

```bash
npx shadcn@latest add button
```

これで tailwind4 も shadcnui もいけた
あとは npm run dev で起動
