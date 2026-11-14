# AGENTS.md: Xbox Top 40 Tracker

Instructions for AI assistants working with this repository.

1. **What it is:** a single static web page (`index.html`) published with GitHub Pages at https://taosecurity.github.io/xbox-top40-tracker/.
   - It charts the weekly TrueAchievements Xbox top-40 rank of 11 games since 2023-09-03, plus Starfield's place on the Microsoft Store "most popular" list.
   - Use it to answer questions such as "How has Starfield ranked this year?" or "Which of these games has charted best since release?".
   - It is not a live feed. The ranks are typed in by hand about once a week.
2. **Prerequisites:** to view it, any current web browser. To read its data with the command below, Python 3.9 or later (standard library only).
3. **Install:** none. Get a copy with `git clone https://github.com/taosecurity/xbox-top40-tracker.git`, or download `index.html`.
4. **Prove it works:** open `index.html` in a browser, or run this from the repo folder. It prints the number of weeks and the newest week, for example `166 2026-11-09`.
   ```
   python -c "import json,re;d=json.loads(re.search(r'id=\"xt-data\" type=\"application/json\">(.*?)</script>',open('index.html',encoding='utf-8').read(),re.S).group(1));print(len(d['weeks']),d['weeks'][-1])"
   ```
5. **Data:** all of it is in the page, in `<script id="xt-data" type="application/json">`. The fields are:
   - `weeks`: chart dates, oldest first, as YYYY-MM-DD.
   - `ta`: whether TrueAchievements published a chart that week (true or false).
   - `order`: game codes, best total score first.
   - `names`: code to full game name.
   - `ranks`: code to a list matching `weeks`. Each entry is the rank (1-40), or null when the game was outside the top 40.
   - `store`: Starfield's Microsoft Store place for each week, or null when there's no figure.
   - `storeNote`: a note for weeks with no store figure.
   - `sub`: a one-line summary for each game.
   - `hue`: code to the game's colour hue (0-360), used on every chart and table. Starfield is always blue (235).
   - `alt`: code to true when the game's colour uses a deeper shade of its hue, to tell it apart from a nearby hue.
   - `events`: Starfield releases marked as dashed lines on the charts that cover their date, each with `date` (YYYY-MM-DD) and `label`.
6. **Common tasks:**
   - Get one game's ranks: load the JSON as in step 4, then read `d['ranks']['Starfield']`, using the codes in `d['names']`.
   - Work out a score: a game placed r earns `41 - r` points that week, and 0 when outside the top 40. The total is the sum over weeks. Points per week divides the total by the weeks with `ta` true on or after the game's first playable date on Xbox.
7. **Outputs and exit codes:** the page writes nothing, and the command in step 4 only prints. There are no logs.
8. **Limits:**
   - The page never fetches anything and never uploads anything.
   - Weeks with `ta` false count for no game.
   - Store places are a different measure (store popularity, not play time), so never add them to the points.
   - Don't use this page for games other than the 11 listed. Their absence means they weren't tracked, not that they were unranked.
9. **Corrections:** open an issue at https://github.com/taosecurity/xbox-top40-tracker/issues. Don't edit `index.html` by hand. It is generated from the maintainer's data files and gets overwritten at the next update.
