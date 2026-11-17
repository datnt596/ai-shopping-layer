# AI Shopping Layer: Phone Finder Prototype

**AI Shopping Layer** is a shopping assistant that understands what a buyer needs in plain Vietnamese. It recommends a short list of phones, compares them side by side and sends the buyer to the seller to complete the purchase.

This repository holds an **interactive prototype** of the product, built as a startup project for an Entrepreneurship course.

🔗 **Live demo:** https://YOUR-USERNAME.github.io/YOUR-REPO/ <!-- replace with your GitHub Pages URL -->

> ⚠️ **Demo data only.** All prices, stock levels, sellers ("Nhà bán A", "Nhà bán B", "Sàn C") and check times are simulated. Nothing is pulled from real marketplaces, and every seller link points to `example.com`.

---

## The problem

Buying a phone in Vietnam means comparing dozens of near-identical models across several marketplaces, each with different prices and sometimes conflicting specs. Most shoppers, and especially parents buying for family members, don't know which specs matter for their needs.

## What the prototype does

1. **Understands a request in everyday language**: budget, who the phone is for, brand preferences and needs.
2. **Shows what it understood** as tags, so the user can check the assistant read the request correctly.
3. **Recommends a ranked shortlist** that matches those needs, with the best available offer for each phone.
4. **Handles follow-up questions** that refine the current results, such as "rẻ hơn" (cheaper), "pin trâu hơn" (longer battery) or "ngoài Xiaomi" (not Xiaomi).
5. **Compares phones side by side** in a detailed spec table, with an option to show only the rows that differ.
6. **Suggests alternatives when nothing matches**: keep the budget and drop the brand, or keep the brand and raise the budget.
7. **Sends the user to the seller** after a confirmation dialog. The purchase happens on the seller's own site.

### Design principles shown in the prototype

- **Transparent ranking.** Sponsored placements are labelled *"Tài trợ"*, shown apart from the recommendations, and don't affect the ranking.
- **Honest data.** When marketplaces disagree on a spec, such as RAM or screen brightness, it is marked *"Chưa xác minh"* (unverified) instead of guessed.
- **No lock-in.** The assistant doesn't sell anything itself. It helps users decide and links them to sellers through affiliate links.

## Try these searches

The prototype understands **Vietnamese** requests. For example:

| Query | What it tests |
|---|---|
| `Tìm điện thoại cho mẹ ở quê, khoảng 5 triệu` | Phone for a parent: big screen, long battery, loud speaker, 5M VND budget |
| `Máy chơi game tầm 7 củ` | Gaming needs (RAM, 120Hz screen) with slang for millions ("củ") |
| `Điện thoại chụp ảnh đẹp dưới 6tr` | Camera-focused ranking |
| `Tìm iPhone 15 Pro Max giá rẻ nhất` | A specific model and its cheapest offer |
| `iPhone dưới 3 triệu` | No match, so it suggests alternatives |

After a search, try a follow-up such as `rẻ hơn`, `pin trâu hơn`, `ngoài Xiaomi` or `màn AMOLED`.

## How it works

The whole prototype is one self-contained file, `index.html`.

| Part | Implementation |
|---|---|
| UI | HTML + [Tailwind CSS](https://tailwindcss.com/) (CDN) + Inter font (Google Fonts) |
| Logic | Plain JavaScript, no framework or build step |
| Catalogue | 15 phones (Samsung, Xiaomi, Apple, OPPO, Honor, Tecno, realme) with offers from 3 simulated sellers |
| Request understanding | Keyword and pattern rules that **simulate** the AI understanding step (budget, user profile, needs, brands, models) |
| Ranking | Weighted scoring across display, battery, performance, camera and features, based on the detected needs |
| Images | Phone illustrations generated as inline SVG, with no image files |

There is **no backend, tracking or data storage**. The page makes no network requests apart from loading Tailwind and the font. In the full product, the rule-based parser would be replaced by a language model and the catalogue by live data from marketplaces.

## Run it locally

No installation is needed. Download `index.html` and open it in a browser.

To serve it locally instead:

```bash
npx serve .
```

## Deploy

It's deployed with **GitHub Pages**: **Settings → Pages → Deploy from a branch → `main` / root**. Any static host also works, including Vercel, Netlify and Cloudflare Pages.


*Course project, prototype only. Not a commercial service. Product names and brands belong to their respective owners.*
