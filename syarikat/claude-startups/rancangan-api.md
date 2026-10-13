# Rancangan Penggunaan Claude API — Permohonan Claude for Startups

Draf untuk borang <https://platform.claude.com/offers/startups-application>.
Disediakan: 13 Okt 2026. Status: **DRAF — perlu disemak sebelum hantar.**

> Hanya hantar perkara yang betul-betul akan dibuat. Bahagian bertanda `[sahkan]`
> mesti diisi atau dibuang. Jangan besarkan angka — pengulas boleh semak.

---

## 1. Jawapan sedia tampal (Bahasa Inggeris)

### Versi pendek (~120 patah perkataan) — untuk medan "What are you building with Claude?"

HitDigital is a Malaysian digital marketing agency serving 20+ fundraising clients
(Islamic schools, mosques, NGOs) and several commercial brands. We built HIT Digital
Operation, our internal operations app, and connected it to Claude through our own
MCP server, so our team already uses Claude to pull client data, analyse Meta Ads
performance and write Malay-language fundraising copy.

Next, we are moving these workflows onto the Claude API: (1) automated weekly and
monthly client performance reports generated from Meta Ads and app data, reviewed by
a strategist before sending; (2) a copywriting and creative-analysis assistant built
into our app, with guardrails for responsible religious fundraising; (3) automatic
triage of client requests. Later we plan a donor-enquiry assistant for our
fundraising clients.

### Versi panjang — kalau ada medan "Tell us more" / "Use case details"

**Today.** HIT Digital Operation stores client profiles, campaigns and service
requests for our two divisions (crowdfunding and commercial). We exposed it through
an MCP server, and our team uses Claude with it, plus the Meta Ads connector, to
produce client reports, ad-creative analysis and campaign copy in Bahasa Melayu.

**Phase 1 — Automated client reporting (months 1–2).** A scheduled job pulls Meta Ads
insights (Marketing API) and campaign data from our app, and sends them to Claude to
draft a weekly or monthly report plus a short WhatsApp summary for each client. We
will use the Message Batches API for the weekly run and prompt caching for our shared
report template and style guide. A strategist approves every report before it goes
out.

**Phase 2 — Copy and creative assistant in our app (months 2–4).** Staff generate ad
copy variations (hook, primary text, headline, CTA) in Malay, and Claude reviews ad
creatives (images) against their performance to explain what worked. Structured
outputs keep results in our app's format. Guardrails: no exaggerated or false claims,
and Quran/hadith references only with verified sources.

**Phase 3 — Request triage (months 4–6).** Incoming client requests are classified by
type and urgency, routed to the right team member, and given a draft reply.

**Exploratory — Donor-enquiry assistant (6–12 months).** A WhatsApp assistant that
answers common donor questions (how to donate, receipts, campaign updates) for our
fundraising clients, with human handoff and no storage of donors' personal data.

**Why the credits matter.** We are a bootstrapped agency. Credits let us build and
test these workflows across real client accounts before charging clients for them.

---

## 2. Penerangan dalaman (Bahasa Melayu)

### Fasa 1 — Laporan automatik (bulan 1–2) ← mula di sini

- **Masalah:** laporan mingguan Al-Sidiqi dan laporan bulanan klien ambil masa lama
  untuk disediakan secara manual.
- **Penyelesaian:** skrip tarik data Meta Ads + HITDIGITAL_MCP → Claude API tulis draf
  laporan + ringkasan WhatsApp → strategist semak → hantar.
- **Ciri API:** Message Batches (separuh harga, sesuai untuk kerja tak segera), prompt
  caching (template laporan & gaya bahasa yang sama setiap kali).
- **Ukuran kejayaan:** masa sediakan satu laporan, dari `[sahkan: X jam]` ke
  `[sasaran: Y minit]`.
- **Klien perintis:** Al-Sidiqi Kebajikan (ad account 782453695798839) sebab skill dan
  format laporannya dah ada.

### Fasa 2 — Pembantu copywriting & analisis kreatif (bulan 2–4)

- Dalam app HIT Digital Operation: pilih klien → jana variasi copy iklan BM.
- Claude baca gambar kreatif + data prestasi, terangkan kenapa satu kreatif menjadi.
- Guardrail ikut CLAUDE.md: hormat, tiada dakwaan palsu, ayat/hadis dengan sumber sahaja.

### Fasa 3 — Triage permintaan klien (bulan 4–6)

- Permintaan baru dalam app → dikelaskan (jenis, keutamaan) → diagih ke staf → draf
  balasan. Model kecil (Haiku) cukup untuk tugas ni, jadi kos rendah.

### Penerokaan — Pembantu WhatsApp penderma (6–12 bulan)

- Jawab soalan lazim penderma untuk klien CF. Ada serahan kepada manusia.
- **Jangan simpan data peribadi penderma.** Perlu persetujuan klien.
- Ini idea, bukan komitmen. Boleh buang dari borang kalau tak pasti.

---

## 3. Perkara perlu disahkan sebelum hantar

- [ ] Tarikh tubuh syarikat (SSM) dan bilangan staf.
- [ ] App HIT Digital Operation dibina guna apa (Laravel? Node? lain-lain) dan siapa
      yang bangunkan — pengulas mungkin tanya.
- [ ] Siapa akan bina Fasa 1 (staf dalaman / freelancer) dan bila boleh mula.
- [ ] Bilangan klien aktif sebenar (CLAUDE.md senaraikan 22 klien CF selain 2 servis, + 12 projek PMD
      setakat Okt 2026 — termasuk projek dalaman).
- [ ] Laman web https://hitdigital.my/ boleh dibuka dari luar (13 Okt 2026: Claude tak dapat
      buka — domain tak resolve dari pelayan semakan Claude. Semak DNS / hosting).
- [ ] Email `@hitdigital.my` aktif (MX, SPF, DKIM, DMARC) dan dipakai untuk login Console.
- [ ] Login Claude Console guna akaun organisasi syarikat.
