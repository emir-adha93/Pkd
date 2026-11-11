# e-Sijil Pro

Aplikasi penjana sijil individu dan pukal. Teknologi: React + Vite, Supabase Auth/Database/Storage, jsPDF, SheetJS, JSZip dan QRCode.

## Setup tempatan
1. Pasang Node.js 20.19+ atau 22.12+.
2. Jalankan `npm install`.
3. Salin `.env.example` kepada `.env.local` dan masukkan URL Supabase serta anon/publishable key.
4. Jalankan `npm run dev`.

## Setup Supabase
1. Cipta projek di Supabase.
2. Buka SQL Editor dan jalankan keseluruhan `supabase/schema.sql`.
3. Authentication → Providers → aktifkan Email.
4. Authentication → Users → tambah akaun admin. Untuk akses private, matikan public signups selepas akaun admin diwujudkan.
5. Simpan Project URL dan anon/publishable key. Jangan gunakan service-role key dalam frontend.

## Deploy GitHub + Vercel
1. Buka repo GitHub `emir-adha93/Pkd`.
2. Log masuk Vercel → Add New → Project → Import Git Repository → pilih `Pkd`.
3. Framework preset: Vite. Build command: `npm run build`. Output directory: `dist`.
4. Tambah Environment Variables: `VITE_SUPABASE_URL`, `VITE_SUPABASE_ANON_KEY`, `VITE_PUBLIC_APP_URL`.
5. Deploy. Selepas dapat domain, masukkan domain tersebut dalam Supabase → Authentication → URL Configuration → Site URL dan Redirect URLs.

## Format Excel
Gunakan kolum `nama` (wajib) dan `emel` (pilihan). Alias `name` dan `email` turut diterima. Setiap baris ialah seorang peserta.

## Keselamatan
Jangan commit `.env.local` atau service-role key. Polisi RLS mengasingkan rekod mengikut pemilik. Bucket sijil adalah private. QR verification mendedahkan nama peserta, program, nombor sijil dan tarikh keluaran sahaja. Elakkan menyimpan nombor IC atau data sensitif peserta.

## Nota versi awal
Sistem menjana PDF individu dan ZIP untuk batch, menyimpan rekod serta PDF ke Supabase. Upload template imej sebagai latar; teks sijil dijana oleh sistem. Penghantaran email dan pengurusan multi-admin belum disertakan.
