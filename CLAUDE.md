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

React app with no routing, no state management library, and no backend. State is in-memory only — resets on page refresh.

**Component structure:**
- `App.jsx` — holds the `transactions` array in state, passes it down to children
- `Summary.jsx` — receives `transactions`, computes `totalIncome`, `totalExpenses`, and `balance` internally
- `TransactionForm.jsx` — owns its own form state, calls `onAdd(transaction)` prop on submit
- `TransactionList.jsx` — receives `transactions`, owns filter state internally

**Data model** — each transaction has: `id`, `description`, `amount` (number), `type` (`"income"` | `"expense"`), `category`, `date`

**Categories:** `food`, `housing`, `utilities`, `transport`, `entertainment`, `salary`, `other`

**Known issue:** Transaction #4 ("Freelance Work") is typed as `expense` but categorized as `salary` — data inconsistency. No delete functionality.
