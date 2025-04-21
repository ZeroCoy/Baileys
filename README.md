# Baileys
# 🚀 Baileys WhatsApp API - By IQBALRMDI

![Node.js](https://img.shields.io/badge/node-%3E%3D14.0-green)
![Contributors](https://img.shields.io/github/contributors/ZeroCoy/Baileys)

Baileys WhatsApp API adalah **library berbasis Node.js** untuk berkomunikasi dengan WhatsApp Web tanpa perlu WebSocket tambahan.  
Dikembangkan dengan performa tinggi untuk kebutuhan bot, otomatisasi pesan, dan integrasi aplikasi WhatsApp lainnya.  

## 📌 Tentang Proyek Ini
Repositori ini dikembangkan dan dikelola oleh **RyzenOfc** bersama para kontributor open-source lainnya.  
Dukungan dan kontribusi dari komunitas sangat diapresiasi! 💖  
Thank you RyzenOfc For You baileys 💖

---

## ✨ Fitur Utama

✅ **Autentikasi tanpa QR** menggunakan session authentication  
✅ **Dukungan Multi-Device (MD)** terbaru dari WhatsApp  
✅ **Kirim & terima pesan** dalam berbagai format  
✅ **Mengelola grup** (buat grup, tambahkan/kick anggota, atur deskripsi, dll.)  
✅ **Integrasi event** seperti masuk/keluar grup, pesan diterima, pesan terbaca  
✅ **Mendukung TypeScript** untuk pengembangan yang lebih aman  

---

## 📦 Instalasi

Pastikan **Node.js ≥ 14.0** sudah terpasang.  
Kemudian jalankan perintah berikut di terminal:

```sh
npm install @iqbalrmdi/baileys
```

Atau dengan **Yarn**:

```sh
yarn add @iqbalrmdi/baileys
```

---

## 🚀 Penggunaan Dasar

```javascript
const makeWASocket = require('@iqbalrmdi/baileys').default;

const sock = makeWASocket({
    auth: state,
    printQRInTerminal: true 
});

sock.ev.on('messages.upsert', async (m) => {
    const msg = m.messages[0];
    if (!msg.key.fromMe) {
        await sock.sendMessage(msg.key.remoteJid, { text: "Hello, I'm a bot 🤖!" });
    }
});
```

---

## 📜 Dokumentasi API

| Fitur               | Deskripsi |
|---------------------|----------|
| `sendMessage()`    | Mengirim pesan teks, gambar, video, dll. |
| `updateProfile()`  | Mengubah foto profil dan nama pengguna |
| `getChats()`       | Mendapatkan daftar chat pengguna |
| `groupParticipantsUpdate()` | Menambahkan/menghapus anggota grup |

📖 **Dokumentasi lengkap:** [Baileys API Docs](https://github.com/adiwajshing/Baileys/wiki)

---

## 📩 Contoh Kode Tambahan

### 📢 Mengirim Pesan Toko  
```ts
sock.sendMessage(msg.key.remoteJid, {
    text: "Isi Pesan",
    title: "Judul",
    subtitle: "Subjudul",
    footer: "Footer",
    viewOnce: true,
    shop: 3,
    id: "199872865193",
}, { quoted: m })
```

### 📊 Hasil Polling dari Newsletter  
```ts
await sock.sendMessage(msg.key.remoteJid, {
    pollResult: {
        name: "Judul Polling",
        votes: [
            ["Opsi 1", 10], 
            ["Opsi 2", 10]
        ],
    }
}, { quoted: m })
```

### 🏷️ Mention di Status  
```ts
await sock.StatusMentions({ text: "Halo!" }, [
    "123456789123456789@g.us",
    "123456789@s.whatsapp.net",
])
```

### 🃏 Pesan dengan Kartu  
```ts
await sock.sendMessage(msg.key.remoteJid, {
    text: "Halo!",
    footer: "Pesan Footer",
    cards: [
        {
            image: { url: 'https://example.jpg' }, 
            title: 'Judul Kartu',
            caption: 'Keterangan Kartu',
            footer: 'Footer Kartu',
            buttons: [
                { name: "quick_reply", buttonParamsJson: JSON.stringify({ display_text: "Tombol Cepat", id: "ID" }) },
                { name: "cta_url", buttonParamsJson: JSON.stringify({ display_text: "Buka Link", url: "https://www.example.com" }) }
            ]
        }
    ]
}, { quoted: m })
```

### 📷 Pesan Album  
```ts
await sock.sendAlbumMessage(msg.key.remoteJid, [
    { image: { url: "https://example.jpg" }, caption: "Halo Dunia" },
    { video: { url: "https://example.mp4" }, caption: "Halo Dunia" }
], { quoted: m, delay: 2000 })
```

### 📌 Menyimpan & Menyematkan Pesan  
```ts
await sock.sendMessage(msg.key.remoteJid, { keep: message.key, type: 1, time: 86400 })
await sock.sendMessage(msg.key.remoteJid, { pin: message.key, type: 1, time: 86400 })
```

### 📨 Pesan Undangan Grup  
```ts
await sock.sendMessage(msg.key.remoteJid, { 
    groupInvite: { 
        subject: "Nama Grup",
        jid: "1234@g.us",
        text: "Undangan Grup",
        inviteCode: "KODE",
        inviteExpiration: 86400 * 3,
    } 
}, { quoted: m })
```

---

## 🤝 Kontribusi

Kami menyambut kontribusi dari siapa saja! Jika ingin membantu:  
1. **Fork** repositori ini  
2. **Buat branch baru**  
3. **Buat Pull Request (PR)**  
---

## 👥 Kontributor

Terima kasih kepada semua yang telah berkontribusi! 🌟  

💖 **Nama Kamu Bisa Ada di Sini!**  

---

🚀 **Selamat ngoding & buat bot WhatsApp yang keren!** 🎉
