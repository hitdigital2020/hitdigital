# HitDigital Marketing Sdn Bhd — Panduan untuk Claude

Fail ni dibaca setiap kali sesi Claude Code bermula. Kemas kini bila ada perubahan
pada klien, cara kerja atau gaya bahasa. Bahagian bertanda `TODO` perlu diisi.

## Tentang syarikat

- **Nama:** HitDigital Marketing Sdn Bhd (HIT Digital)
- **Jenis:** Agensi pemasaran digital, Malaysia
- **Mata wang:** Ringgit Malaysia (RM)
- **Bahasa kerja:** Bahasa Melayu (santai tapi profesional). Istilah pemasaran
  boleh kekal dalam Bahasa Inggeris (ROAS, CTR, CPM, CPC, LPV, hook, CTA).
- **Laman web:** https://hitdigital.my/ (domain email dirancang: `@hitdigital.my`)
- TODO: alamat, nombor WhatsApp rasmi, logo/warna jenama.

### Dua bahagian (division)

| Kod | Nama | Klien |
|-----|------|-------|
| `cf` | Crowdfunding | Sekolah/tahfiz, masjid/surau, NGO — kutipan dana, derma, wakaf, infak |
| `pmd` | Projek / jenama dalaman & klien komersial | AWWABIN, HD LENSA, HD TRAINING CENTRE, HD MARKETING, CHENTA ABAYA, dll. |

## Sumber data (connectors)

- **HITDIGITAL_MCP** — data klien daripada app HIT Digital Operation (baca sahaja).
  Aliran: `list-clients-tool` → dapatkan `project_id` → `get-client-profile-tool`,
  `get-client-campaigns-tool`, `get-client-requests-tool`.
  Jangan reka fakta — nyatakan jika maklumat kosong.
- **Meta Ads MCP** — prestasi iklan Facebook/Instagram.
- **Canva** — reka bentuk poster dan kreatif.
- **Google Drive** — fail klien, laporan lama.

## Klien aktif (setakat Okt 2026)

Nombor depan nama ialah kod dalaman klien. `project_id` ialah ID dalam HITDIGITAL_MCP.

### Crowdfunding (`cf`)

| project_id | Klien | Jenis |
|-----------:|-------|-------|
| 1 | 002 SRITI TOK GURU | sekolah |
| 33 | 007 Global Unity | ngo |
| 4 | 050 MTAQ AT-TANWIRIAH | sekolah |
| 5 | 055 TAHFIZ AN-MANHAL | sekolah |
| 6 | 081 PDK RAUDHAH MUHAMMADI | sekolah |
| 7 | 105 MAAHAD ASSOLEHAH KEDAH | sekolah |
| 53 | 105 MAAHAD ASSOLEHIN KEDAH | sekolah |
| 8 | 139 TAHFIZ QURAN GONG BAYOR | sekolah |
| 10 | 162 SMIDI YAN | sekolah |
| 49 | 164 PUSAT TAHFIZ ANAK YATIM AL SIDIQI (Kebajikan) | sekolah |
| 11 | 164 PUSAT TAHFIZ ANAK YATIM AL SIDIQI (Pembangunan) | sekolah |
| 14 | 196 NGO PAKAT - PERTUBUHAN KEBAJIKAN AT-TANWIRIAH | ngo |
| 16 | 197 DARUL IMTIYAZ SENDAYAN | sekolah |
| 17 | 200 TAHFIZ DARUL AMAN TAKBAI | sekolah |
| 18 | 201 PASTI KAWASAN KUBANG KERIAN | sekolah |
| 20 | 212 SRITI AL-FARABI KOK LANAS | sekolah |
| 39 | 215 PONDOK PENGAJIAN TURATH AMANULLAH | sekolah |
| 46 | 217 MASJID AN-NUR, MUKIM KOTA KUBANG LABU | masjid |
| 47 | 218 MASJID ASSALAM BANGGOL, KG PADANG SALIM | masjid |
| 51 | 219 DPDP - Madrasah Tahfiz Al-Ayyubi | sekolah |
| 52 | 220 DPDP - Muslimeen Care Academy | sekolah |
| 54 | 221 DPDP - Madrasah Darul Ansar | masjid |
| 22 | EMAIL & SMS MARKETING | servis |
| 34 | Social Media Management (SMM) | servis |

### PMD (`pmd`)

| project_id | Projek |
|-----------:|--------|
| 29 | AWWABIN |
| 24 | CHENTA ABAYA |
| 35 | GCC GLOBAL |
| 30 | HARTANAH |
| 28 | HD LENSA (wedding photographer, Kelantan) |
| 44 | HD MARKETING |
| 50 | HD TRAINING CENTRE |
| 25 | KEMBARA SERANTAU |
| 27 | MEDIA CF |
| 26 | MUSLIMCATION |
| 42 | Other Services |
| 37 | SISTEM YURAN |

### ID akaun iklan Meta

| Klien | Ad Account ID |
|-------|---------------|
| Al-Sidiqi (Kebajikan) | 782453695798839 |
| TODO: klien lain | |

## Format output default

- **Laporan bulanan klien (Meta Ads):** slide PowerPoint, fokus pada kreatif mana yang
  menjadi dan kenapa.
- **Laporan mingguan Al-Sidiqi:** Word/PDF.
- **Planning kandungan / KPI / tracker:** Excel (.xlsx).
- **Website / landing page:** satu fail HTML responsif dengan CTA WhatsApp, simpan
  dalam `websites/`.
- TODO: ringkasan untuk WhatsApp klien — panjang maksimum, emoji ok atau tidak?

## Gaya penulisan

- Copywriting kutipan dana: hormat, tidak melampau, tiada dakwaan palsu, rujuk ayat
  atau hadis dengan sumber yang betul sahaja.
- Elak jargon berlebihan bila menulis untuk klien (sekolah/masjid) — terangkan metrik
  dalam bahasa mudah.
- TODO: perkataan atau frasa yang wajib/elak guna.

## Struktur repo

```
CLAUDE.md            ← fail ini
klien/
  _template/         ← salin folder ini bila ada klien baru
  cf/<kod-nama>/     ← klien crowdfunding (cth. cf/164-al-sidiqi)
  pmd/<nama>/        ← projek PMD (cth. pmd/hd-lensa)
templates/           ← template laporan, copywriting, prompt
websites/            ← landing page HTML
```

Nama folder klien: huruf kecil, sempang, mula dengan kod klien jika ada
(cth. `klien/cf/218-masjid-assalam-banggol`).

## Peraturan kerja

- Simpan semua hasil kerja dalam repo dan commit — container cloud akan dipadam bila
  sesi tamat.
- Jangan simpan kata laluan, token atau data peribadi penderma dalam repo.
- Angka prestasi mesti datang daripada connector (Meta Ads / HITDIGITAL_MCP), bukan
  anggaran.
