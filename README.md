## Analisis Sentimen Tweet Terhadap **Kilang Minyak**

Proyek ini merupakan bagian dari penugasan mata kuliah yang berfokus pada teknik pemrosesan teks dan implementasi analisis sentimen menggunakan pustaka populer Python. Analisis ini bertujuan untuk mengukur sentimen publik (positif, negatif, atau netral) terhadap isu-isu seputar kilang minyak di media sosial X (Twitter).

---

## Informasi Penugasan

| Keterangan      | Detail                                                                |
| :-------------- | :-------------------------------------------------------------------- |
| **Nama** | **Muhammad Rizki Ananda** |
| **NIM** | **5220411019** |
| **Tugas Wajib** | Scraping data dari internet dan Melakukan **Case Folding** pada teks. |
| **Topik Data** | Sentimen publik terhadap kata kunci **"Kilang Minyak"** dalam bahasa **Indonesia**. |
| **Jumlah Data** | Minimal **"2000"** baris data.                                        |

---

## Alat dan Pustaka yang Digunakan

Proyek ini memanfaatkan beberapa alat utama untuk setiap tahapan proses:

| Tahapan Proyek                  | Alat/Pustaka Utama                                          |
| :------------------------------ | :---------------------------------------------------------- |
| **Pengambilan Data (Scraping)** | `tweet-harvest` (versi 2.6.1)                               |
| **Pemrosesan Data** | `Pandas`                                                    |
| **Visualisasi Hasil** | `Seaborn` dan `Matplotlib`                                  |

---

## Detail Pengambilan Data (Scraping)

Data tweet diambil menggunakan `tweet-harvest` dengan konfigurasi yang spesifik untuk mendapatkan data yang relevan dan terbatas.

| Parameter              | Nilai / Deskripsi                                                                                                                                |
| :--------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nama File Output** | `kilang_minyak_data.csv`                                                                                                                         |
| **Batas Data (Limit)** | **2000** tweet                                                                                                                                   |
| **Keyword Pencarian** | `(kilang minyak OR #KilangMinyak OR Pertamina) -filter:retweets -filter:replies -promo -loker since:2025-05-01 until:2025-10-09 min_faves:5 lang:id` |
| **Tanggal Pencarian** | Dari **2025-05-01** hingga **2025-10-09** |
| **Bahasa** | Bahasa Indonesia (`lang:id`)                                                                                                                     |

### Perintah Scraping yang Digunakan

```bash
# Crawl Data (versi optimal)

filename = 'kilang_minyak_data.csv'
keyword = '(kilang minyak OR #KilangMinyak OR Pertamina) -filter:retweets -filter:replies -promo -loker since:2025-05-01 until:2025-10-09 min_faves:5 lang:id'
limit = 2000

!npx -y tweet-harvest@2.6.1 -o "{filename}" -s "{keyword}" --tab "LATEST" -l {limit} --token {twitter_auth_token}
