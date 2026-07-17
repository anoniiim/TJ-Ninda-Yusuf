# RSVP Tingjing Day - Tema Chinese

Proyek ini adalah halaman RSVP sederhana namun elegan dengan nuansa budaya Tionghoa untuk acara **Tingjing Day** (tradisi lamaran Tionghoa).

## Fitur
- Desain elegan dengan latar belakang Chinese (merah keemasan, red envelope)
- Form RSVP: Nama, Kehadiran, Jumlah tamu, Pesan
- Terhubung langsung ke Google Spreadsheet
- Siap di-host gratis di GitHub Pages

## Cara Setup

### 1. Google Sheets + Apps Script (untuk simpan data)
1. Buka [Google Sheets](https://sheets.google.com) → Buat spreadsheet baru.
2. Ganti nama sheet menjadi `RSVP`.
3. Tambahkan header di baris 1:
   - Timestamp
   - Name
   - Attendance
   - Guests
   - Message
4. Buka **Extensions → Apps Script**
5. Hapus kode default, paste kode berikut:

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('RSVP');
  const data = JSON.parse(e.postData.contents);
  
  sheet.appendRow([
    data.timestamp,
    data.name,
    data.attendance,
    data.guests,
    data.message
  ]);
  
  return ContentService.createTextOutput(JSON.stringify({status: "success"}))
    .setMimeType(ContentService.MimeType.JSON);
}
```

6. Klik **Deploy → New deployment** → Type: Web app
   - Execute as: Me
   - Who has access: Anyone
7. Deploy dan copy **Web app URL**.

### 2. Update HTML
- Edit `index.html`
- Ganti `YOUR_SCRIPT_URL` dengan URL dari Apps Script.

### 3. Upload ke GitHub
1. Buat repository baru di GitHub.
2. Upload file `index.html` dan `README.md`.
3. Aktifkan GitHub Pages (Settings → Pages → Source: Deploy from a branch → main).

Akses situs di: `https://username.github.io/repo-name`

## Customisasi
- Ganti background image di CSS (baris background url)
- Tambah gambar, musik, atau detail acara sesuai kebutuhan.

Selamat merayakan Tingjing Day! 🧧✨
Semoga acara berjalan lancar dan penuh berkah.