# AI Assistant (TypeScript)

Proyek ini adalah contoh aplikasi chat AI sederhana berbasis TypeScript yang memisahkan backend (Hono + Google Generative AI) dan frontend (Vite + React). Dokumen ini ditulis dalam Bahasa Indonesia.

**Perhatian (Privacy)**: Jangan meng-commit file yang berisi API key atau data sensitif (mis. `backend/.env`). Gunakan `backend/.env.example` untuk menunjukkan variabel lingkungan yang diperlukan.

**Fitur**:
- Ringkas: Frontend React + komponen UI sederhana.
- Backend ringan menggunakan Hono dan Google Generative AI.

## Struktur Proyek

- `backend/` — server Hono, endpoint API
- `frontend/` — aplikasi React (Vite)

## Prasyarat

- Node.js (disarankan v18 atau lebih baru)
- npm atau yarn
- Kunci API Google Generative AI (Gemini) — simpan sebagai `GEMINI_API_KEY`

## Instalasi & Menjalankan

1. Clone repository ini.

### Backend

```
cd backend
npm install
cp .env.example .env    # lalu isi GEMINI_API_KEY di backend/.env
npm run dev             # development (watch)
# atau untuk production: npm run start
```

Server backend berjalan di `http://localhost:3000` (port dikonfigurasi di `backend/src/index.ts`).

### Frontend

```
cd frontend
npm install
npm run dev
```

Frontend menggunakan Vite; default akan tersedia di `http://localhost:5173` (atau port yang ditentukan Vite).

## API

- Endpoint: `POST /api/chat`
- Conten-Type: `application/json`
- Request body contoh:

```json
{ "message": "Halo, bantu jelaskan tentang ..." }
```

- Response sukses contoh:

```json
{ "reply": "... jawaban AI ..." }
```

- Response error mengandung properti `error` dan `message`.

## Environment variables

- `GEMINI_API_KEY` — kunci API Google Generative AI yang diperlukan oleh backend.

Gunakan file `backend/.env.example` sebagai template. Jangan commit file `backend/.env` yang berisi nilai nyata.

## Keamanan & Open Source

- Pastikan file `backend/.env` ditambahkan ke `.gitignore` sebelum mem-push ke remote publik.
- Jika repo sudah terlanjur berisi API key di commit sebelumnya, pertimbangkan untuk mengganti kunci dan membersihkan riwayat git (contoh: `git rm --cached backend/.env` lalu commit dan push). Hati-hati saat menghapus kunci dari history — itu membutuhkan langkah tambahan.

## Kontribusi

- Fork repo, buat branch baru, lakukan perubahan, lalu buka Pull Request.