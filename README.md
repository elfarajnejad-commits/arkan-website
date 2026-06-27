# وب‌سایت آرکان

وب‌سایت رسمی **آرکان** — مشاور استراتژی و رشد کسب‌وکار. یک صفحه‌ی تک‌اسکرولی با
هدف واحد: رساندن بازدیدکننده به **فرم درخواست مشاوره**.

## استک

- **Next.js 14** (App Router) + **TypeScript**
- **Tailwind CSS** با توکن‌های برند آرکان
- RTL کامل (فارسی) — فونت **استعداد** (عناوین) و **وزیرمتن** (بدنه) به‌صورت لوکال
- فرم با **Server Action** + اعتبارسنجی **zod** + ذخیره در **Supabase**
- آماده‌ی استقرار روی **Vercel**

## راه‌اندازی

```bash
npm install
cp .env.local.example .env.local   # سپس کلیدهای Supabase را وارد کنید
npm run dev
```

سایت روی http://localhost:3000 بالا می‌آید.

> تا زمانی که کلیدهای Supabase تنظیم نشده باشند، فرم در حالت **فالبک** کار می‌کند و
> درخواست‌ها در کنسول سرور لاگ می‌شوند — توسعه بدون پایگاه داده هم ممکن است.

## اتصال Supabase

1. در پروژه‌ی Supabase، فایل [`supabase/schema.sql`](supabase/schema.sql) را در
   **SQL Editor** اجرا کنید (ساخت جدول `leads`).
2. از `Settings → API` مقادیر زیر را در `.env.local` قرار دهید:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `SUPABASE_SERVICE_ROLE_KEY` (فقط سمت سرور؛ هرگز در کلاینت افشا نمی‌شود)
3. درخواست‌ها از سمت سرور با کلید SERVICE_ROLE درج می‌شوند و RLS امن می‌ماند.

## اطلاع‌رسانی ایمیل (اختیاری)

قلاب آماده‌ی Resend در [`src/app/actions.ts`](src/app/actions.ts) کامنت‌گذاری شده است؛
با تنظیم `RESEND_API_KEY` و خارج‌کردن از کامنت فعال می‌شود.

## ساختار

```
src/
  app/        layout (RTL/SEO) · page · actions (server) · globals.css
  components/  Header · Hero · Services · Pillars · Process · Credibility
               ConsultationForm · Footer · ui/*
  lib/         supabase · validation (zod) · utils
public/
  fonts/  images/  favicon.svg
supabase/schema.sql
```

## استقرار روی Vercel

پروژه را به Vercel متصل کنید و همان متغیرهای محیطی `.env.local` را در
`Project Settings → Environment Variables` وارد کنید.

---

© آرکان — مشاور استراتژی و رشد کسب‌وکار
