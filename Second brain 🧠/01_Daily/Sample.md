# 📅 2025-06-18

## 🚀 Goals
- Investigate tooltip bug from CD-1234
- Set up vector embedding for Obsidian vault

## 🧠 Notes
- Chroma was easier to set up locally than Pinecone.
- Embedding markdown chunks with 500 token windows works best so far.
- Tooltip bug likely tied to component remount.

## 🔁 What I learned
- I need to add `useRef` to preserve state across renders in modal context.
- GPT-4o handles context from 3-4 docs better than GPT-3.5.

## 🛠 Work Log
- Refactored tooltip logic
- Logged experiment in `/Prompts/embedding tests.md`
- Added 3 new notes to `/Knowledge`

## 🧱 Blockers
- Not sure how to embed only “important” chunks. Too much noise right now.
