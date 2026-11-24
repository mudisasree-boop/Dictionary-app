# Bookworms

Keep the words you meet in books. Look one up, save it to a shared list, and practise until it's yours.

**Live app:** https://claude.ai/artifact/52YaZrWWwiCS32tkpHbTBi (a claude.ai page; `bookworms.html` is its source)

## What it does
- **Look up:** type a word (plus where you found it and the sentence, optionally) to get a dictionary entry with meanings, IPA, a Listen button, examples, synonyms, origin and usage tips.
- **Page photo:** take or choose a photo of a page. Claude suggests one word at a time, with underlined or circled words first. You can look it up, skip it or pick a different word. Claude also explains the passage. You can add the book title and author (both optional) so Claude can explain it in the context of the book, and a "Search on Google" button opens a related search. Choose "No words, only explanation" to save nothing. The photo and explanation are never stored.
- **Shared list:** one word list for everyone the page is shared with. Each word shows who added it. Only the owner sees Edit and Delete.
- **Practice:** Mixed, Fill in the blank, Situations (pick the scenario that fits the word), Meanings, and Write a sentence (with Claude's feedback). Choose 5, 10 or 15 words: weakest first, most recent, or any. Progress is shared, and a word counts as mastered after 3 right answers in a row.
- **Conversation:** choose 3, 5 or 8 words (weakest first, most recent or any) and how long to talk: once, twice, three times or until you stop. In each round Claude says something, you reply using at least 2 of the words, and Claude gives feedback on the words you used, specific corrections and a smoother version, then carries on. Words used correctly or wrongly count toward practice progress. At the end you get scores (clarity, grammar, vocabulary, naturalness), strengths, things to work on, and an honest comparison with your earlier conversations. Each person's conversation history is private to them (`data/users/<id>/`).

## How it's built
One HTML file with no build step, using claude.ai artifact runtime capabilities:
- `sample` (with images): Claude writes entries, reads photos, writes exercises and gives sentence feedback, using each viewer's own Claude account.
- `db`: shared storage. Words live at `words/<userId>/items/<id>`, and practice progress at `progress/<userId>__<id>`. The rules let each person write only under their own `words/<id>`, and let only the owner change anyone's words.
- `user`: names for "added by".
- `tts`: pronunciation, falling back to the browser's speech synthesis on phones.

## Updating
Edit `bookworms.html` and republish it to the same artifact URL.
