# Untuk Teman

Dashboard yayasan berbasis Next.js, Supabase, dan TypeScript.

## Menjalankan Lokal

Gunakan Node.js 20.9 atau lebih baru.

```bash
npm install
copy .env.example .env.local
npm run dev
```

Buka `http://localhost:3000`. Isi `.env.local` dengan nilai dari project Supabase Anda:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

Jalankan `supabase_schema.sql` di Supabase SQL Editor sebelum memakai fitur data dan autentikasi.

## Deploy ke Netlify dari GitHub

1. Push isi folder `temankita123-main` ini ke repository GitHub. Jangan push folder pembungkus di luarnya.
2. Di Netlify pilih **Add new site > Import an existing project > GitHub**, lalu pilih repository tersebut.
3. Gunakan pengaturan berikut:
	- Build command: `npm run build`
	- Publish directory: biarkan kosong
	- Node version: `20.9.0` (sudah diatur di `netlify.toml`)
4. Di **Site configuration > Environment variables**, tambahkan:
	- `NEXT_PUBLIC_SUPABASE_URL`
	- `NEXT_PUBLIC_SUPABASE_ANON_KEY`
5. Deploy site. Setiap push ke branch produksi akan memicu build Netlify.

`NEXT_PUBLIC_SUPABASE_ANON_KEY` aman digunakan di browser jika Row Level Security dan policy Supabase sudah dikonfigurasi. Jangan masukkan service role key atau secret lain ke GitHub.

## Validasi Sebelum Push

```bash
npm run build
npm run lint
```

`npm run build` adalah pemeriksaan wajib untuk memastikan aplikasi dapat dibangun di Netlify.

