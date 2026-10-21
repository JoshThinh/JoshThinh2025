# Joshua Thinh — portfolio

Live site: **https://joshthinh.github.io/JoshThinh2025/**

I'm a computer science student at San Diego State University (B.S. CS, minor in AI & Human Responsibility, expected May 2029). This repo hosts my portfolio site and my older class work.

## Highlights

| Project | What it is | Built with |
| --- | --- | --- |
| **Brevvie** (internship, 2026) | Trained a computer vision model that classifies tanks in propane-exchange lockers as steel, composite, or no tank. Rolling out to hundreds of lockers across the US. | Computer vision, Python, Rust, AWS |
| **Church Rides** | Ride sign-up site: riders pick a pickup spot and driver, drivers get an organized list, and a Messenger group chat is created with automated pickup messages. | JavaScript, Supabase |
| **[Wedding Photo Booth](https://github.com/JoshThinh/WeddingPhoto)** | Guests take photos in the browser, which appear in a shared polaroid gallery. QR join, admin panel, slideshow video export. | JavaScript, Canvas, Supabase, GitHub Pages |
| **Smart Waste Sorter** (SDSU AI Club) | YOLO model that tells you whether an item goes in recycling or trash, trained partly on our own dataset. | YOLO, Python |
| **Coding Society** | Student peer-teaching platform. Worked on the frontend and backend, and led the frontend for the review page. | JavaScript, Spring Boot, Flask |
| **MIPS games** | Tic-tac-toe and Blackjack on the MARS bitmap display. | MIPS assembly |

## What's in this repo

- `index.html` — the portfolio homepage (standalone page, no theme)
- `navigation/`, `_posts/`, `_notebooks/` — AP CSA coursework and class blogs from Del Norte High School (2023–2025)
- `navigation/game.md`, `navigation/cargame.md` — early browser games

## Running locally

```bash
bundle install
bundle exec jekyll serve
```

The site deploys to GitHub Pages through `.github/workflows/jekyll-gh-pages.yml` on every push to `main`.

To add a résumé download button, drop a PDF at `assets/Joshua_Thinh_Resume.pdf`; the homepage shows the button automatically when that file exists.

Built on the Nighthawk Pages template ([original template README](NIGHTHAWK_PAGES.md)).
