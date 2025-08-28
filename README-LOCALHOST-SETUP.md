# Setup untuk Development di Localhost

## Masalah yang Diperbaiki
- Error "Unauthorized" saat membuat laporan di localhost
- Masalah CORS antara frontend dan backend
- Konfigurasi environment variables yang tidak konsisten

## Langkah Setup

### 1. Environment Variables
Pastikan file `.env.local` ada di root project dengan konfigurasi berikut:

\`\`\`env
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=https://tfpleowwysvuaijbxmsl.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InRmcGxlb3d3eXN2dWFpamJ4bXNsIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTYyMjM1NjAsImV4cCI6MjA3MTc5OTU2MH0._42yCm4fr-1KS2Ud1-bYuYSrrPBEt0Uo4ekomI17dto

# Vercel Blob Storage
BLOB_READ_WRITE_TOKEN=vercel_blob_rw_Px7XNMnyd4xVvZHX_OgsYRQtS1TAgii8NH4Gmlg1GNhzjBo

# Development Configuration
NODE_ENV=development
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_API_BASE_URL=http://localhost:3000/api
\`\`\`

### 2. Restart Development Server
Setelah menambahkan `.env.local`, restart development server:

\`\`\`bash
npm run dev
# atau
yarn dev
\`\`\`

### 3. Test Login dan Buat Laporan
1. Buka http://localhost:3000
2. Login sebagai TU (username: `tu1`, password: `password123`)
3. Coba buat laporan baru
4. Seharusnya tidak ada error "Unauthorized" lagi

## Perubahan yang Dilakukan

### 1. Middleware Authentication
- Menambahkan `middleware.ts` di root level
- Menambahkan CORS headers untuk localhost
- Menggunakan environment variables

### 2. API Routes
- Menambahkan CORS headers di semua API responses
- Menambahkan OPTIONS handler untuk preflight requests
- Menggunakan environment variables untuk Supabase

### 3. Supabase Configuration
- Menggunakan environment variables di semua Supabase clients
- Fallback ke hardcoded values jika env vars tidak ada

### 4. Next.js Configuration
- Menambahkan CORS headers di `next.config.mjs`
- Konfigurasi khusus untuk development environment

## Troubleshooting

Jika masih ada masalah:

1. **Clear browser cookies dan localStorage**
2. **Restart development server**
3. **Check browser console untuk error messages**
4. **Pastikan Supabase service berjalan normal**

## Testing
- Login sebagai TU: `tu1` / `password123`
- Login sebagai Admin: `admin1` / `admin123`
- Login sebagai Koordinator: `coord1` / `coord123`
