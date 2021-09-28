---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://images.unsplash.com/photo-1460925895917-afdab827c52f?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MXwxfDB8MXxhbGx8fHx8fHx8fA&ixlib=rb-1.2.1&q=80&w=1080&utm_source=unsplash_source&utm_medium=referral&utm_campaign=api-credit
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

# Mockup Dashboard

Monitor and Evaluate P2P Lending Product Performance

<br>
<br>

Created by: Thowwafi Alfiansyah

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: full

---
<img border="rounded" src="/images/mockup-image.png">

---

# Dashboard

- Dashboard bisa menampilkan data berdasarkan range tanggal (from, to)
- Menampilkan jumlah transaksi pendanaan/pinjaman dan total nilainya
<img border="rounded" src="/images/pendanaan.png">

---

# Performance

- Menampilkann nilai akumulasi Return of Investment oleh semua transaksi
<img border="rounded" src="/images/roi.png">

- Menampilkan data performa pinjaman
<img border="rounded" src="/images/telat-bayar.png">

---

# Overall Transactions

- Bisa ditampilkan berdasarkan product atau user type
- X-axis adalah bulan dan tahun
- Y-axis adalah Jumlah uang dalam rupiah
<img border="rounded" src="/images/overall.png">

---

# Users Section

- Menampilkan jumlah user:
  1. Registered (terdaftar)
  2. Registered and Active (sudah melakukan pendanaan/pinjaman minimal 1 kali)
  3. New User data user baru harian

<img border="rounded" src="/images/users.png" width="500">

---

# Products

- Menampilkan performa pada tiap product
<img border="rounded" src="/images/products.png" width="200">
- Jumlah Pendana dan Peminjam berdasarkan individuals/institutional
- Total transaksi dan ROI
- Listing success rate, berapa user yang ditolak untuk pengajuan pinjaman

---

# Daftar Pinjaman Aktif

- Live Data harian, progress pinjaman yang sedang berlangsung
- Agar manajemen bisa memantau UKM mana yang potential untuk dilakukan campaign
<img border="rounded" src="/images/list-pinjaman.png" width="400">

---

# Idea

1. Dengan adanya dashboard ROI, kita bisa melihat berapa keuntungan yang didapat dengan membandingkan antara peminjam individu/institutional
    Misal: Pinjaman yang diberikan kepada UKM mendapatkan ROI lebih besar 50% dibandingkan ke individu.
    Campaign: Berikan promo atau tawaran menarik pada UKM.

2. Dari data 3 produk yang ada, bisa dilihat berapa presentasi telat/gagal bayar dan berada di Grade resiko tingkat apa.
    Pihak manajemen bisa menggunakan data ini untuk evaluasi seleksi user/UKM yang mengajukan pinjaman
    Eksperimen berikan pendanaan resiko tinggi pada beberapa borrower, dan hitung tingkat berhasil bayar

3. Pada dashboard user section, bisa ditinjau tingkat kenaikan user harian/mingguan sebelum dan sesudah dilakukan campaign.
    Apakah lebih banyak user baru yang mendaftar sebagai Lender atau Borrower.

---
preload: false

---
<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div 
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 1000, duration: 500 } }">
    Terima Kasih
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 1
  }
}
</script>
