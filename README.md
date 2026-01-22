# Bank Soal TOEFL

Repositori ini berisi kumpulan bank soal TOEFL dalam format JSON yang dikategorikan berdasarkan jenis section: Listening, Structure, Written Expression, dan Reading.

## Aturan Versi

Untuk menjaga konsistensi dan melacak perubahan data:
- Setiap kali terdapat **perubahan pada bank soal** (tambah soal, hapus soal, atau perbaikan konten), maka versi harus **naik sebesar 0.1**.
- Versi data soal tercatat di file `version.json`.
- Versi file audio tercatat di file `audio/audi_version.json`.
- Field `count` pada `audio/audi_version.json` **wajib sesuai** dengan jumlah total file audio (`.mp3`) yang ada di dalam folder `/audio`.
- Pastikan untuk memperbarui field `lastUpdated` pada kedua file version saat melakukan perubahan.

## Format Soal (Template)

### 1. Listening Comprehension (`listening_questions.json`)
Section ini terbagi menjadi dua struktur utama:

#### a. Short Questions (Part A)
```json
{
  "id": "L001",
  "sectionType": "listening",
  "audioFile": "audio_l001.mp3",
  "questionText": "What does the woman imply?",
  "options": [
    "Option 1",
    "Option 2",
    "Option 3",
    "Option 4"
  ],
  "answerIndex": 2, // Index dimulai dari 0
  "explanation": "Penjelasan mengapa jawaban tersebut benar."
}
```

#### b. Long Sets (Part B & C)
```json
{
  "setId": "LS001",
  "title": "Discussion: Campus Initiative",
  "audioFile": "audio_ls001.mp3",
  "questions": [
    {
      "id": "L021",
      "questionText": "What is the main purpose?",
      "options": ["A", "B", "C", "D"],
      "answerIndex": 1,
      "explanation": "..."
    }
  ]
}
```

### 2. Structure (`structure_questions.json`)
Digunakan untuk soal melengkapi kalimat.
```json
{
  "id": "S001",
  "sectionType": "structure",
  "questionText": "The North Platte River ______ from Wyoming into Nebraska.",
  "options": [
    "it flowed",
    "flows",
    "flowing",
    "with flowing water"
  ],
  "answerIndex": 1,
  "explanation": "Kalimat membutuhkan main verb 'flows'."
}
```

### 3. Written Expression (`written_expression_questions.json`)
Digunakan untuk soal mengidentifikasi error (bagian yang digarisbawahi).
```json
{
  "id": "WE001",
  "sectionType": "written_expression",
  "questionText": "The (A) decisions made by the committee (B) was based on (C) inaccurate data and (D) biased opinions.",
  "underlinedParts": ["decisions", "was", "inaccurate", "opinions"],
  "options": ["decisions", "was", "inaccurate", "opinions"],
  "answerIndex": 1,
  "explanation": "Subjek 'decisions' jamak, seharusnya menggunakan 'were'."
}
```

### 4. Reading Comprehension (`reading_questions.json`)
Section berdasarkan teks bacaan.
```json
{
  "passageId": 1,
  "title": "The History of Coffee",
  "content": "Isi teks bacaan panjang di sini...",
  "questions": [
    {
      "id": "R001",
      "questionText": "Where did coffee originate?",
      "options": ["A", "B", "C", "D"],
      "answerIndex": 0,
      "explanation": "..."
    }
  ]
}
```

## Cara Penggunaan

### Menambah Soal
1. Buka file JSON yang sesuai dengan kategori soal yang ingin ditambah.
2. Tambahkan objek baru di dalam array yang sesuai (misal: array `short_questions` pada `listening_questions.json`).
3. Pastikan `id` mengikuti urutan yang ada (misal: `L093`, `S051`, `R101`).
4. Jika menambah soal Listening, letakkan file audio `.mp3` di folder `/audio`.
5. Simpan file.

### Memperbarui Versi
Setiap kali selesai melakukan perubahan pada file soal atau audio:
1. Buka `version.json` dan/atau `audio/audi_version.json`.
2. Naikkan angka `version` (misal dari `1.0` ke `1.1`).
3. Jika terdapat perubahan pada file audio, perbarui field `count` di `audio/audi_version.json` agar sesuai dengan jumlah file `.mp3` terbaru.
4. Update `lastUpdated` dengan waktu sekarang (ISO format).

### Integrasi
Aplikasi dapat memuat file JSON ini secara langsung atau melalui API untuk menampilkan soal secara dinamis kepada pengguna.
