# Quran Word Quiz

A static, community-friendly Quranic word quiz. The site loads the quiz interface once and fetches one Surah JSON file at a time.

## Project structure

```text
index.html             Surah list / landing page
quiz.html              Reusable quiz page
data/surahs.json       Metadata shown on the landing page
data/surah-1.json      Quiz data for Surah 1
data/surah-N.json      Add future Surahs here
styles.css             Existing shared stylesheet (optional)
```

## Add a Surah

1. Create `data/surah-N.json`, where `N` is the Surah number.
2. Use the same structure as `data/surah-1.json`:

```json
{
  "id": 2,
  "name": "سورة البقرة",
  "englishName": "Al-Baqarah",
  "ayahs": [
    [
      {
        "word": "...",
        "transliteration": "...",
        "rootWord": "...",
        "correctMeaning": "...",
        "options": ["...", "...", "...", "..."]
      }
    ]
  ]
}
```

3. Add its metadata to `data/surahs.json`:

```json
{"id": 2, "name": "سورة البقرة", "englishName": "Al-Baqarah", "ayahCount": 286}
```

The Surah list will link to `quiz.html?surah=2`, and the quiz will load `data/surah-2.json` automatically.

## Free hosting with GitHub Pages

1. Create a GitHub account and a new **public** repository.
2. Upload these files, preserving the `data` folder.
3. Open repository **Settings → Pages**.
4. Select **Deploy from a branch**, choose `main`, folder `/ (root)`, then save.
5. GitHub will provide the public website URL.

The site must be hosted over HTTP/HTTPS for `fetch()` to load JSON files. Opening `index.html` directly from a computer may block those requests.

## Version control and community contributions

Recommended workflow:

1. Keep `main` deployable at all times.
2. Create an issue describing each change or Surah contribution.
3. Contributors create a branch, for example `add-surah-2` or `fix-mobile-layout`.
4. They make a small change and submit a Pull Request.
5. Review the JSON, spelling, Arabic text, and quiz answers before merging.
6. Merge to `main`; GitHub Pages publishes the update automatically.

Use meaningful commits such as:

```text
Add Surah 2 quiz data
Improve mobile answer layout
Fix incorrect root word for Surah 1
```

## Content review

For Quranic content, require at least one independent review before merging. Keep source/citation information in a separate content note or issue, and avoid silently changing verified Arabic text.

## Future backend

This static version is suitable for the first public release. Add authentication, saved progress, usage metrics, and leaderboards later with a backend such as Supabase. Do not store passwords or trust scores sent directly from the browser.
