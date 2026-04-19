# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start dev server (Vite, default port 5173)
npm run build     # Production build
npm run lint      # ESLint
npm run preview   # Preview production build
```

## Architecture

This is a single-file React app — all logic and UI lives in `src/App.jsx`. There are no components, no routing, no state management library, and no backend.

**Known bugs and issues (intentional):**
- `amount` is stored as a string, so `totalIncome` and `totalExpenses` use string concatenation instead of numeric addition — balance is wrong
- Transaction #4 ("Freelance Work") is typed as `expense` but categorized as `salary` — data inconsistency
- No delete functionality

**Data model** — each transaction has: `id`, `description`, `amount` (string), `type` (`"income"` | `"expense"`), `category`, `date`

**Categories:** `food`, `housing`, `utilities`, `transport`, `entertainment`, `salary`, `other`

State is in-memory only — resets on page refresh.
