# 🍳 Recipe Finder App

A small React + Tailwind app to quickly find meals from TheMealDB by ingredient.

Taylor can type one or more ingredients and get matching recipes with thumbnails. Includes loading/error states, responsive grid, and an optional details modal.

## Features
- Search by ingredient(s)
- Match mode: AND (all ingredients) or OR (any ingredient)
- Responsive, clean UI (1 → 3 columns)
- Recipe cards with hover effect
- “View Details” modal (ingredients + instructions)
- Graceful handling for empty input, no results, and network errors

## Tech
- React 18 + Vite 5
- Tailwind CSS 3 (PostCSS + Autoprefixer)
- No external state libs (only useState/useEffect)

## API
- Filter by ingredient (used for search)
  - https://www.themealdb.com/api/json/v1/1/filter.php?i={ingredient}
- Lookup meal details (used by modal)
  - https://www.themealdb.com/api/json/v1/1/lookup.php?i={mealId}

Note: TheMealDB expects exact ingredient names (e.g., okra instead of ladies finger, eggplant instead of aubergine, cilantro instead of coriander leaves).

## Getting Started (Local)
Prerequisites: Node.js 18+ and npm

- Install dependencies:
  - `npm install`
- Start the dev server:
  - `npm run dev`
- Open the local URL printed in the terminal (default http://localhost:5173/)

Build & preview:
- `npm run build`
- `npm run preview`

## Usage
- Enter one or more ingredients separated by commas, e.g.:
  - `chicken`
  - `chicken, onion`
  - `beef, tomato`
- Choose “Match all” (AND) to only show meals that contain all ingredients, or “Match any” (OR) to show meals that contain any of them.
- Click “Search” or press Enter.
- Click “View Details” on a card to see ingredients and instructions.

## Deploy (Free, instant)

### StackBlitz
1. Zip this folder (right-click → Send to → Compressed (zipped) folder).
2. Go to https://stackblitz.com → sign in.
3. “Create Project” → “Upload Project” (drag-drop ZIP).
4. It auto-installs and starts Vite; share the live URL.

### CodeSandbox
1. Zip this folder.
2. Go to https://codesandbox.io → sign in.
3. “Create Sandbox” → “Import” → “Upload ZIP”.
4. It installs and starts. If asked for a start command, use `npm run dev`.

Optional: add a start script to package.json
```
{
  // ...existing fields...
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "start": "vite"
  }
}
```

## Project Structure
```
reciepe ideas/
├─ index.html
├─ package.json
├─ postcss.config.js
├─ tailwind.config.js
├─ vite.config.js
├─ src/
│  ├─ index.css
│  ├─ index.js           # React root (no JSX; uses React.createElement)
│  ├─ App.jsx            # Main UI + logic
│  └─ components/
│     └─ RecipeCard.jsx  # Reusable card
```

## Troubleshooting
- JSX parse error for `src/index.js`:
  - We intentionally avoided JSX there so the file can stay `.js`. If you prefer JSX, rename it to `src/index.jsx` and update `index.html` to load `/src/index.jsx`.
- No results for valid combos:
  - Try switching to “Match any”. TheMealDB datasets don’t always overlap across ingredients.
  - Check exact ingredient names (e.g., `potato`, `onion`, `garlic`, `okra`).

## Attribution
- Data from TheMealDB (https://www.themealdb.com/)
