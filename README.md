# AI Visibility Checker: a Claude Skill

**Find out if ChatGPT, Claude, Gemini and Perplexity recommend your business, who they recommend instead, and exactly what to fix.**

*Created by **Ayushi Gupta** · © 2026 Ayushi Gupta · Licensed under [CC BY-ND 4.0](LICENSE)*

> ### ⬇️ [Download ai-visibility.skill](https://github.com/ayushi-gupta-04/ai-visibility-skill/raw/main/ai-visibility.skill)
> This one file is all you need, for both the Claude app / claude.ai and Claude Code.
>
> - **Claude app or claude.ai** → [Install in the Claude app / claude.ai](#option-a-claude-app--claudeai) (upload the file, about 2 minutes)
> - **Claude Code** → [Install in Claude Code](#option-b-claude-code) (unzip the file into a folder, about 3 minutes)
> - **More AI platforms (optional)** → [Add API keys](#api-keys-optional) · [Where to save the `.env` file](#-where-to-save-the-env-file)

> ⚠️ Don't use GitHub's green **`<> Code` → Download ZIP** button. You only need the **`ai-visibility.skill`** file above.

---

## What it does

When people ask an AI assistant *"best digital marketing agency in Jaipur"* or *"which dentist should I choose in Pune"*, does your business appear? This skill finds out and turns the answer into a branded, client-ready report.

1. **Writes realistic buyer questions** for the business, its city and its competitors (you approve them first).
2. **Asks the AI platforms** those questions with live web search, and records whether the business is **mentioned** or **cited as a source**, along with every competitor.
3. **Audits the website** for AI readiness: whether AI bots are blocked, whether the content is readable without JavaScript, schema, sitemap and llms.txt.
4. **Builds a report** (HTML + PDF) with scores, share of voice, question-by-question results, the sources AI trusts, and a prioritised action plan.

### Report includes
- AI discovery score and AI-readiness score
- Visibility per platform (ChatGPT, Claude, Gemini/Google, Perplexity)
- Share of voice vs competitors
- Question-by-question results matrix
- "Sources AI trusts": where to get listed or reviewed
- Website AI-readiness audit (14 AI crawlers checked)
- Prioritised recommendations with evidence
- Your agency branding (name, colours, contact), plus **Download PDF / Download HTML** buttons
- "Skill by Ayushi Gupta" credit and page numbers on every PDF page

### Problems it solves
- Not knowing whether AI recommends the business, or who it recommends instead
- AI repeating wrong details (for example the wrong city) or negative threads
- Websites that unknowingly block AI crawlers or can't be read without JavaScript
- Not knowing which directories, review sites or content will move the needle
- Proving progress to clients with monthly re-runs

---

## Requirements

| | Needed? |
|---|---|
| Claude (Pro, Max, Team or Enterprise) **or** Claude Code | Yes |
| Node.js 18+ | Yes for Claude Code (claude.ai's sandbox already has it) |
| API keys | **Optional.** See [API keys](#api-keys-optional) |
| Microsoft Edge or Google Chrome | Optional: saves the PDF automatically in Claude Code |

---

## Installation

**Never put API keys inside the `.skill` file or the skill folder.** Keys always go in a separate `.env` file (see [API keys](#api-keys-optional)).

### Option A: Claude app / claude.ai

1. **[Download `ai-visibility.skill`](https://github.com/ayushi-gupta-04/ai-visibility-skill/raw/main/ai-visibility.skill)**.
2. Open Claude and go to **Settings → Capabilities**.
3. Turn on **Code execution and file creation**. Skills need it.
4. Scroll to **Skills** and click **Upload skill** (or **+ Add → Upload a skill**).
5. Select **`ai-visibility.skill`**. Upload it as-is, without unzipping, renaming or editing it.
6. Make sure **ai-visibility** appears in your skills list and is **on**.
7. Start a **new chat** and type, for example:
   > Check AI visibility of example.com, a dental clinic in Pune

Notes for the Claude app / claude.ai:
- **No keys needed.** Claude measures its own answers with its built-in web search, and runs the website audit.
- **To add ChatGPT / Gemini / Perplexity**, save a `.env` file anywhere on your computer and **attach it to your chat message** each time you ask for a report. See [Where to save the `.env` file](#-where-to-save-the-env-file). **Never paste API keys as text in a chat.**
- **If Claude says it can't reach a website or AI service**, your code sandbox is blocking internet access. Go to **Settings → Capabilities → code execution network access** and allow:
  `api.openai.com`, `api.anthropic.com`, `api.perplexity.ai`, `generativelanguage.googleapis.com`, and the website you're checking.
- On Team/Enterprise plans an admin may need to allow skills or network access for the organisation.
- **Updating to a new version:** in **Skills**, click **⋮** next to ai-visibility → delete it, then upload the new `.skill` file.

### Option B: Claude Code

Claude Code (desktop app Code tab, terminal, or IDE) loads skills from a folder named **`.claude\skills`**. If you don't have one yet, that's normal: you'll create it below. The `.skill` file is a zip, so you just unzip it into that folder.

**First decide where to install:**

| Install for… | Skills folder |
|---|---|
| **One project only** (e.g. `D:\my-project`) | `D:\my-project\.claude\skills\` |
| **All your projects** | Windows: `C:\Users\<you>\.claude\skills\`<br>macOS/Linux: `~/.claude/skills/` |

#### Windows: using PowerShell (easiest)

1. **[Download `ai-visibility.skill`](https://github.com/ayushi-gupta-04/ai-visibility-skill/raw/main/ai-visibility.skill)** (it goes to your **Downloads** folder).
2. Press **Start**, type **PowerShell**, open it, and run these one at a time. They assume your project is **`D:\my-project`**, so change the path if yours differs.

   Create the skills folder (safe to run even if it already exists):
   ```powershell
   New-Item -ItemType Directory -Force "D:\my-project\.claude\skills"
   ```
   Unzip the skill into it:
   ```powershell
   Copy-Item "$env:USERPROFILE\Downloads\ai-visibility.skill" "$env:TEMP\ai-visibility.zip" -Force
   Expand-Archive "$env:TEMP\ai-visibility.zip" "D:\my-project\.claude\skills" -Force
   ```
   Check it worked (should print **True**):
   ```powershell
   Test-Path "D:\my-project\.claude\skills\ai-visibility\SKILL.md"
   ```

*For all projects, use `"$env:USERPROFILE\.claude\skills"` in place of `"D:\my-project\.claude\skills"` in these commands.*

#### Windows: using File Explorer

1. **[Download `ai-visibility.skill`](https://github.com/ayushi-gupta-04/ai-visibility-skill/raw/main/ai-visibility.skill)**.
2. Rename it from `ai-visibility.skill` to **`ai-visibility.zip`**. If you can't see the `.skill` ending, turn on **View → Show → File name extensions**.
3. Right-click `ai-visibility.zip` → **Extract All…** → **Extract**. This gives you a folder that contains an **`ai-visibility`** folder.
4. Open your project folder (e.g. `D:\my-project`). If there's no **`.claude`** folder: **New → Folder** and name it **`.claude.`** (*with a dot at the end*). Windows removes the last dot and keeps `.claude`. It can refuse names that start with a dot otherwise.
5. Open `.claude` and create a folder named **`skills`**.
6. Copy the **`ai-visibility`** folder (the one that directly contains `SKILL.md`) into `skills`.

#### macOS / Linux: Terminal

```bash
# one project:
mkdir -p ~/my-project/.claude/skills
unzip -o ~/Downloads/ai-visibility.skill -d ~/my-project/.claude/skills
# or all projects:
mkdir -p ~/.claude/skills
unzip -o ~/Downloads/ai-visibility.skill -d ~/.claude/skills
```

#### ✅ The result must look exactly like this

```
my-project/
└── .claude/
    └── skills/
        └── ai-visibility/
            ├── SKILL.md        ← must be directly here
            ├── scripts/
            └── references/
```
⚠️ A common mistake is ending up one folder too deep (`skills/ai-visibility/ai-visibility/SKILL.md`). `SKILL.md` must be directly inside `skills/ai-visibility/`.

#### Finish setup

1. Check Node.js is installed: run `node --version` (needs 18 or newer). If it's missing, install the LTS version from https://nodejs.org.
2. *(Optional)* Add API keys: save a `.env` file in your **project folder** (e.g. `D:\my-project\.env`), not in the skill folder. See [Where to save the `.env` file](#-where-to-save-the-env-file).
3. Start a **new** Claude Code session in your project folder. Skills load when a session starts.
4. Ask *"what skills do you have?"* and you should see **ai-visibility**. Then try:
   > Check AI visibility of example.com, a dental clinic in Pune

**Updating to a new version:** delete the `.claude\skills\ai-visibility` folder and repeat the steps with the new `.skill` file.

---

## API keys (optional)

| Platform | Key variable | Where to get it | Cost |
|---|---|---|---|
| Claude (built-in web search) | *none* | Works automatically | Free with your Claude plan |
| Gemini / Google | `GEMINI_API_KEY` | https://aistudio.google.com/apikey | Free tier (limited daily requests; Google Search grounding may need billing) |
| ChatGPT | `OPENAI_API_KEY` | https://platform.openai.com/api-keys | Pay as you go (~USD 0.02 per question) |
| Claude API | `ANTHROPIC_API_KEY` | https://console.anthropic.com | Pay as you go. **Not included in Claude Pro.** |
| Perplexity | `PERPLEXITY_API_KEY` | https://www.perplexity.ai/settings/api | Pay as you go (Perplexity Pro includes monthly credit) |

### 📍 Where to save the `.env` file

The `.env` file holds your API keys. It's **separate from the skill**, and where it goes depends on how you use Claude:

| You use… | Save `.env` here | How the skill gets it |
|---|---|---|
| **Claude app / claude.ai** | **Anywhere on your computer**, e.g. `Documents\.env` | **Attach it to your chat message** (📎 / + button) each time you ask for a report |
| **Claude Code (one project)** | **Your project folder**, the same folder you open in Claude Code, e.g. `D:\my-project\.env` | Read automatically, nothing to attach |
| **Claude Code (all projects)** | Your user folder, named **`.ai-visibility.env`**: Windows `C:\Users\<you>\.ai-visibility.env`, macOS/Linux `~/.ai-visibility.env` | Read automatically in every project |

❌ **Don't** save it inside the `ai-visibility` skill folder, don't put it in the `.skill` file, and don't upload it to Settings → Skills.
❌ **Don't** paste your keys as text in a chat.

Example for Claude Code (one project):
```
D:\my-project\
├── .env                     ← your API keys go here
└── .claude\
    └── skills\
        └── ai-visibility\   ← the skill (no keys in here)
```

#### How to create the `.env` file (Windows, Notepad)

1. Open **Notepad**. You can also download the template **[`.env.example`](.env.example)** (click it → **Download raw file**) and open it in Notepad.
2. Type or paste your keys, one per line, right after the `=` sign, with no spaces or quotes. Skip the platforms you don't use:
   ```
   GEMINI_API_KEY=AIzaSy...your-key
   OPENAI_API_KEY=sk-...your-key
   ANTHROPIC_API_KEY=
   PERPLEXITY_API_KEY=
   ```
3. Click **File → Save As**.
4. Go to the folder from the table above.
5. In **Save as type**, choose **All files (\*.\*)**.
6. In **File name**, type **`.env`** (or `.ai-visibility.env` for the all-projects option) and click **Save**.

Check it's right: in File Explorer, turn on **View → Show → File name extensions**. The file must be named exactly `.env`, **not** `.env.txt`.

**macOS:** in TextEdit choose **Format → Make Plain Text**, then save as `.env`.

**Using it in the Claude app / claude.ai:** in a new chat, click **📎 / +**, attach your `.env` file, and type e.g. *"Check AI visibility of example.com, a dental clinic in Pune. My API keys are in the attached .env file."*

A typical 20-question report costs about **USD 0.50–8** depending on platforms.

---

## Usage

Just ask in plain language:
- *"Check AI visibility of mybusiness.com, a bakery in Delhi. Competitors are X and Y."*
- *"Does ChatGPT recommend acmedental.in? Run the AI visibility report."*
- *"Check the AI readiness of example.com"* (free website audit only)

Claude will show you the competitors, buyer questions and estimated cost **once**. Reply **go**, and it runs everything and sends you the report (HTML + PDF).

**Your agency branding:** tell Claude your agency name, colours and contact, for example:
> Brand the report for my agency "Bright Growth", contact hello@brightgrowth.com, colours #5b21b6 and #db2777.

**Monthly tracking:** ask Claude to re-run the same check next month and it shows trend arrows against the previous report.

---

## Limitations (be honest with clients)

- AI answers vary between runs. Treat each report as a snapshot, and ask for 2–3 runs per question for important decisions.
- API answers can differ slightly from the consumer apps (personalisation, location, model version).
- Google AI Overviews, Microsoft Copilot, Meta AI and Grok have no public answer API. Google is approximated with Gemini + Google Search, and Copilot via Bing crawler access.
- The keyless Claude result is collected in-session and is indicative.

## Privacy & security

- API keys stay in your own `.env` file (or a file you attach to your own Claude chat). They're never written into configs or reports.
- Reports are saved on your computer (Claude Code) or in your chat (claude.ai). Nothing is sent to the author.

## Troubleshooting

| Problem | Fix |
|---|---|
| Upload rejected: *"SKILL.md file must be in the top-level folder"* | You uploaded GitHub's Download ZIP. Upload **`ai-visibility.skill`** instead ([download](https://github.com/ayushi-gupta-04/ai-visibility-skill/raw/main/ai-visibility.skill)) |
| Skill doesn't start | Start a **new** chat/session; check it's on in Skills (Claude app) or the path ends in `skills/ai-visibility/SKILL.md` (Claude Code) |
| "No platform API keys found" | Fine. Keyless Claude mode + audit still run. Add keys to `.env` for more platforms. |
| `HTTP 404 model not found` | A model was retired. Add e.g. `GEMINI_MODEL=gemini-flash-latest` to your `.env` |
| `HTTP 429 quota exceeded` (Gemini) | Free daily limit reached. Wait a day or enable billing; the skill falls back to a lighter model automatically |
| Can't reach websites (Claude app) | Allow the domains under Settings → Capabilities → network access |

---

## License

© 2026 **Ayushi Gupta**. Licensed under **Creative Commons Attribution-NoDerivatives 4.0** ([CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0/)).

- ✅ Free to use, including for client work, and to share **unmodified** copies
- ✅ Must keep the copyright notice and the "Skill by Ayushi Gupta" credit
- ❌ No distributing modified versions

See [LICENSE](LICENSE) for details.
