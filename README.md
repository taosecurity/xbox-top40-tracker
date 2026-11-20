# Xbox Top 40 Tracker

Xbox Top 40 Tracker shows how Starfield and ten other big RPG and open-world games have placed each week in the TrueAchievements Xbox top 40 since September 2023. The other games are Cyberpunk 2077, Skyrim, Fallout 76, Fallout 4, Fallout 3, Baldur's Gate 3, No Man's Sky, Star Wars Outlaws, Oblivion Remastered and The Outer Worlds 2. Each game gets a single score, so you can see which has held players' attention best over time.

Open the site: https://taosecurity.github.io/xbox-top40-tracker/

For AI assistants: step-by-step instructions are in [AGENTS.md](AGENTS.md).

## Example

To see how Starfield did the week after Shattered Space came out (2024-09-30), open the site and scroll to **Every week**. The newest week is at the top, so scroll down the table to the row for 2024-10-06:

    Week        Starfield  FO76  C2077  BG3
    2024-10-06  10         35    39     26
    2024-09-29  19         33    38

Starfield climbed from #19 to #10 that week, which earned it 31 points (40 points for 1st place down to 1 point for 40th). An empty cell means the game was outside the top 40. On the rank chart under "Where has each game placed, week by week?", the same jump sits just after the dashed line that marks the release of Shattered Space.

What's new: see the top of the [live page](https://taosecurity.github.io/xbox-top40-tracker/).

## What the page shows

- **This week:** each game's rank, with its change from the week before.
- **Scores:**
  - Total points, scored the track-meet way: 40 points for 1st place down to 1 point for 40th, added up week by week.
  - Points per week since each game came out on Xbox, which is fair to games released during the tracking period.
  - Weeks in the top 40, best rank, average rank and the last 12 weeks.
- **Charts:** a rank-over-time chart where you pick one or more games to highlight, one small chart per game, and points by year. Each game keeps one color throughout the page, and Starfield is always blue. Dashed lines mark the releases of Shattered Space and of Free Lanes with Terran Armada.
- **Microsoft Store:** Starfield's place on the store's "most popular" list, shown separately and never added to the points.
- **Every week:** a table of each week's ranks, linked to that week's TrueAchievements article.

## About the data

- **Sources:**
  - Ranks come from the weekly [TrueAchievements Xbox chart](https://www.trueachievements.com/xbox-chart), which ranks games by play time across a large sample of Xbox accounts.
  - Store places come from the [Microsoft Store most popular Xbox games](https://www.microsoft.com/en-us/store/most-popular/games/xbox?skipitems=100&source=lp&target=games..all) list.
  - Both are typed in by hand each week.
- The page's "About this data" section lists known gaps, such as missing weeks and weeks with no chart.

Found a mistake? Open an issue: https://github.com/taosecurity/xbox-top40-tracker/issues

## Credits and License

Richard Bejtlich of [Richard Presents Starfield Essentials](https://www.youtube.com/@RichardBejtlich) made this page. I am the developer, and Claude is the programmer. More Starfield tools and references are on the [Richard Presents Development Hub](https://taosecurity.github.io/).

This is an unofficial page, not made or endorsed by TrueAchievements, Microsoft or any game's publisher.

The page is a single self-contained `index.html` with no external dependencies, and all its data is built in. Its code (layout and charts) is MIT licensed; see [LICENSE](LICENSE).
