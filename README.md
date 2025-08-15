# Infrastructure & Automation Cheat Sheets

A curated, copy-ready collection of cheat sheets for Infrastructure & Automation & DevOps & Platform engineering

---

## ✨ Highlights

- **Copy-ready**: short, battle-tested commands & snippets.
- **mdBook-powered**: browsable docs + printable HTML.

---

## 📦 Repository Info

- **Title**: `Infrastructure & Automation Cheat Sheets`
- **Author**: `Duong Van Thanh`
- **Language**: `en`
- **Docs Source**: root folder (`src="."`)
- **Build output**: `book/`
- **Repository**: https://github.com/duongvanthanh1992/cheat-sheets

> The mdBook config is in `book.toml`. If you use the snippet below, you’re good to go.

```toml
[book]
title = "Infrastructure & Automation Cheat Sheets"
authors = ["Duong Van Thanh"]
language = "en"
src = "."

[build]
build-dir = "book"
create-missing = false

[output.html]
default-theme = "ayu"
preferred-dark-theme = "ayu"
git-repository-url = "https://github.com/duongvanthanh1992/cheat-sheets"
git-repository-icon = "fa-github"
copy-font = true
