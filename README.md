
## 📘 `logrpm` — Rails Log Analyzer for RPM, Slow Queries, and N+1 Detection

**`logrpm`** is a CLI tool for analyzing Ruby on Rails logs (e.g., `production.log`, `development.log`, and `.gz` archives).  
It calculates Requests Per Minute (RPM), finds slow requests, detects possible N+1 queries, outputs CSV, and renders ASCII graphs in terminal.

---

## 🚀 Quick Start

```bash
logrpm path/to/logfile.log [options]
```

Example:

```bash
logrpm log/production.log --csv --out=rpm.csv --graph
```

---

## 🧠 Features

- 📊 RPM (requests per minute or hour)
- 🐢 Slow request detection (e.g., over 1s)
- 🕵️ N+1 `SELECT` detection
- 📈 ASCII graph output in terminal
- 📤 CSV export
- ✅ Supports `.log` and `.log.gz`
- 🧠 Auto-detects OS (Linux/macOS) and uses proper `awk` or `gawk`

---

## ⚙️ Options

### 🔍 Filtering

| Option | Description |
|--------|-------------|
| `--after=YYYY-MM-DD` | Only include requests **after** this date |
| `--before=YYYY-MM-DD` | Only include requests **before** this date |
| `--path=/endpoint` | Only include requests to this route (e.g., `/graphql`) |
| `--by=minute` _(default)_ | Group RPM by minute |
| `--by=hour` | Group RPM by hour |

---

### 📤 Output

| Option | Description |
|--------|-------------|
| `--csv` | Output as CSV |
| `--out=filename.csv` | Save RPM data to a CSV file |
| `--graph` | Render an ASCII chart in the terminal |

---

### 🐢 Slow Request Detection

| Option | Description |
|--------|-------------|
| `--slow=seconds` | Show requests taking longer than N seconds |
| `--slow-out=logfile.log` | Save raw log entries to file |
| `--slow-csv=filename.csv` | Export slow requests as CSV: `timestamp,duration_ms,method,path` |

---

### 🕵️ N+1 Query Detection

| Option | Description |
|--------|-------------|
| `--nplus1` | Look for repeated `SELECT` queries (possible N+1 patterns) |

---

## 📂 Examples

### ➤ Basic RPM Count (per minute)

```bash
logrpm log/production.log
```

---

### ➤ Filter by Path and Export RPM to CSV

```bash
logrpm log/production.log.2.gz --path=/graphql --csv --out=graphql_rpm.csv
```

---

### ➤ Graph & Slow Requests (> 2 seconds)

```bash
logrpm log/production.log --graph --slow=2
```

---

### ➤ Save Slow Requests to CSV

```bash
logrpm log/production.log --slow=1.5 --slow-csv=slow_requests.csv
```

---

### ➤ N+1 Detection

```bash
logrpm log/production.log --nplus1
```

---

## 💻 System Requirements

- Linux or macOS
- `awk` (GNU awk preferred)
- On **macOS**, install `gawk` via Homebrew:

```bash
brew install gawk
```

---

## 🛠 Installation

1. Copy the script to `~/bin/logrpm`
2. Make it executable:

```bash
chmod +x ~/bin/logrpm
```

3. Add `~/bin` to your `$PATH` if needed:

```bash
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

---

## 🧪 Coming Soon

- `--debug` mode
- Export to JSON
- Real-time `watch` mode
- `cron`-ready summaries

---

## 📎 License

MIT License (feel free to modify, improve, or contribute)

