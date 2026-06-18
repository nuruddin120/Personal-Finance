# অর্থসাথী (OrthoSathi)

ব্যক্তিগত আয়-ব্যয়, বাজেট, সঞ্চয়, বিনিয়োগ, ইমারজেন্সি ফান্ড, রিটায়ারমেন্ট ও ঋণ
ট্র্যাকিংয়ের একটি সিঙ্গেল-পেজ ওয়েব অ্যাপ। কোনো বিল্ড বা ব্যাকএন্ড লাগে না —
পুরোটাই একটা `index.html` ফাইল।

## ফাইল কাঠামো

```
orthosathi-site/
├── index.html      # পুরো অ্যাপ (HTML + CSS + JS এক ফাইলে)
├── vercel.json     # Vercel কনফিগ (ঐচ্ছিক, নিরাপদ ডিফল্ট)
├── .gitignore
└── README.md
```

## যেভাবে কাজ করে

- ডেটা ব্যবহারকারীর নিজের ব্রাউজারে **localStorage**-এ জমা থাকে — কোনো সার্ভার বা
  ডেটাবেস লাগে না। প্রতিটি ভিজিটরের ডেটা তার নিজের ব্রাউজারে আলাদা।
- Excel এক্সপোর্টের জন্য SheetJS লাইব্রেরি CDN থেকে লোড হয়; ইন্টারনেট থাকলেই কাজ করে।

> দ্রষ্টব্য: একাধিক ডিভাইস বা একাধিক ব্যবহারকারীর মধ্যে ডেটা শেয়ার করতে হলে
> ভবিষ্যতে একটি ব্যাকএন্ড (যেমন Supabase/Firebase) ও লগইন যোগ করতে হবে।

---

## ধাপ ১ — GitHub-এ কোড তোলা

### সহজ উপায় (ওয়েব ইন্টারফেস)
1. github.com-এ লগইন করে **New repository** বানান (নাম যেমন `orthosathi`)।
2. রিপো পেজে **Add file → Upload files** ক্লিক করুন।
3. এই ফোল্ডারের সব ফাইল (`index.html`, `vercel.json`, `README.md`, `.gitignore`) টেনে ছাড়ুন।
4. **Commit changes** চাপুন।

### অথবা Git CLI দিয়ে
```bash
cd orthosathi-site
git init
git add .
git commit -m "Initial commit: OrthoSathi"
git branch -M main
git remote add origin https://github.com/<your-username>/orthosathi.git
git push -u origin main
```

## ধাপ ২ — Vercel-এ ডিপ্লয়

1. [vercel.com](https://vercel.com) এ গিয়ে **GitHub দিয়ে Sign up / Login** করুন।
2. ড্যাশবোর্ডে **Add New… → Project** ক্লিক করুন।
3. আপনার `orthosathi` রিপোটি **Import** করুন।
4. সেটিংস (সাধারণত আপনাআপনি ঠিক থাকে):
   - **Framework Preset:** `Other`
   - **Build Command:** *(ফাঁকা রাখুন)*
   - **Output Directory:** *(ফাঁকা রাখুন)*
   - **Root Directory:** `./`
5. **Deploy** চাপুন। কয়েক সেকেন্ডের মধ্যে একটি লাইভ লিংক পাবেন, যেমন
   `https://orthosathi.vercel.app`।

## ধাপ ৩ — আপডেট

`index.html`-এ পরিবর্তন করে GitHub-এ push করলেই Vercel স্বয়ংক্রিয়ভাবে
নতুন ভার্সন ডিপ্লয় করবে।

---

## কাস্টম ডোমেইন (ঐচ্ছিক)

Vercel প্রজেক্ট → **Settings → Domains** → আপনার ডোমেইন যোগ করুন এবং
দেখানো DNS রেকর্ডগুলো আপনার ডোমেইন প্রোভাইডারে বসান।

## লোকাল প্রিভিউ (ঐচ্ছিক)

শুধু `index.html` ফাইলটি ব্রাউজারে খুললেই চলে। অথবা একটি লোকাল সার্ভার:
```bash
python3 -m http.server 8000
# তারপর ব্রাউজারে: http://localhost:8000
```
