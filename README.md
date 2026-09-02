<!-- SECTION B: BIO BANNER -->
<p align="center">
  <img src="WhatsApp GIF 2026-08-14 at 18.03.05.gif" width="100%" alt="Bio Banner" />
</p>


<!-- SECTION C: TECHNOLOGIES -->
### Technologies

<p align="left">
  <img src="https://img.shields.io/badge/PYTHON-000000?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FASTAPI-000000?style=for-the-badge&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL-000000?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/JAVASCRIPT-000000?style=for-the-badge&logo=javascript&logoColor=white" />
  <img src="https://img.shields.io/badge/HTML5-000000?style=for-the-badge&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/CSS3-000000?style=for-the-badge&logo=css3&logoColor=white" />
  <img src="https://img.shields.io/badge/JSX-000000?style=for-the-badge&logo=react&logoColor=white" />
</p>



<code>[+] PYTHON     [████████████████░░░░] 30% </code><br />
<code>[+] FASTAPI    [████████████████░░░░] 80% </code><br />
<code>[+] SQL        [██████████░░░░░░░░░░] 50% </code><br />
<code>[+] JS         [██████████░░░░░░░░░░] 50% </code><br />
<code>[+] HTML       [██████████░░░░░░░░░░] 50% </code><br />
<code>[+] CSS        [██████████░░░░░░░░░░] 50% </code><br />
<code>[+] JSX        [██████████░░░░░░░░░░] 50% </code><br />

<!-- SECTION D: STATISTICS & CONTRIBUTION GRAPH -->
### Statistics

<table border="0" width="100%">
  <tr>
    <!-- Kolom Kiri: GIF Estetik (Ganti NAMA_GIF_KAMU.gif dengan file gif milikmu) -->
    <td width="35%" align="center" valign="middle">
      <img src="WhatsApp Image 2026-08-14 at 18.25.47.jpeg" width="100%" alt="Stats GIF" />
    </td>
    <!-- Kolom Kanan: Kartu Streak Stats -->
    <td width="65%" align="center" valign="middle">
      <img src="https://streak-stats.demolab.com/?user=kaomineus&theme=dark&background=000000&border=000000&v=1" width="100%" alt="GitHub Streak" />
    </td>
  </tr>
</table>

### Contribution Graph

<!--CONTRIB:START-->
<pre>
┌────────────────────────────────────────────────────────────────┐
│ ▂▃▂▅▆█▆▅▂▁▂▃▂▅▆█▆▅▂▁▂▃▂▅▆█▆▅▂▁▂▃▂▅▆█▆▅▂▁▂▃▂▅▆█▆▅▂▁▂▃▂▅▆█▆▅▂▁▂ │
│ ────────────────────────────────────────────────────────────── │
│ KONTRIBUSI HARIAN · 62 HARI · AUTO-REGEN 24H                   │
└────────────────────────────────────────────────────────────────┘
</pre>
<!--CONTRIB:END-->
name: contrib-strip

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/github-script@v7
        with:
          script: |
            const { owner, repo } = context.repo;
            const res = await github.graphql(
              `query($login: String!) {
                user(login: $login) {
                  contributionsCollection {
                    contributionCalendar {
                      weeks { contributionDays { contributionCount date } }
                    }
                  }
                }
              }`,
              { login: owner }
            );
            const days = res.user.contributionsCollection.contributionCalendar.weeks
              .flatMap((w) => w.contributionDays)
              .sort((a, b) => a.date.localeCompare(b.date))
              .slice(-62);
            const bars = "▁▂▃▄▅▆▇█";
            const lvl = (n) => (n <= 0 ? 0 : n === 1 ? 1 : n <= 2 ? 2 : n <= 3 ? 3 : n <= 5 ? 4 : n <= 7 ? 5 : n <= 9 ? 6 : 7);
            const row = days.map((d) => bars[lvl(d.contributionCount)]).join("");
            const W = row.length;
            const caption = "KONTRIBUSI HARIAN · 62 HARI · AUTO-REGEN 24H";
            const art = [
              "┌" + "─".repeat(W + 2) + "┐",
              "│ " + row + " │",
              "│ " + "─".repeat(W) + " │",
              "│ " + caption.padEnd(W) + " │",
              "└" + "─".repeat(W + 2) + "┘",
            ].join("\n");
            const { data: file } = await github.rest.repos.getContent({ owner, repo, path: "README.md" });
            const md = Buffer.from(file.content, "base64").toString("utf8");
            const S = "<!--CONTRIB:START-->", E = "<!--CONTRIB:END-->";
            const i = md.indexOf(S), j = md.indexOf(E);
            if (i < 0 || j < 0) throw new Error("markers tidak ditemukan");
            const next = md.slice(0, i + S.length) + "\n<pre>\n" + art + "\n</pre>\n" + md.slice(j);
            await github.rest.repos.createOrUpdateFileContents({
              owner, repo, path: "README.md",
              message: "chore: regen ascii contrib chart",
              content: Buffer.from(next).toString("base64"),
              sha: file.sha,
            });
            console.log("chart updated");

<!-- FEATURED PROJECTS (STABIL 100%) -->
### Featured Projects

<table width="100%">
  <tr>
    <td width="50%" align="center">
      <br />
      <a href="https://github.com/Kaomineus/options-pricing-engine">
        <img src="https://img.shields.io/badge/OPTIONS--PRICING--ENGINE-000000?style=for-the-badge&logo=python&logoColor=white" alt="Options Pricing Engine" />
      </a>
      <br /><br />
      <sub><b>Python Options Pricing Engine & Financial Models</b></sub>
      <br /><br />
    </td>
    <td width="50%" align="center">
      <br />
      <a href="https://github.com/Kaomineus/cyphertrace">
        <img src="https://img.shields.io/badge/CYPHERTRACE-000000?style=for-the-badge&logo=typescript&logoColor=white" alt="Cyphertrace" />
      </a>
      <br /><br />
      <sub><b>Crypto Forensic & On-Chain Investigation Terminal</b></sub>
      <br /><br />
    </td>
  </tr>
</table>

---

> `[SYS_LOG]` **"In math and code we trust, everything else is noise."**

