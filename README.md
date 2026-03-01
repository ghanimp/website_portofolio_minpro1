# Website Portofolio


## Teknologi yang Digunakan
- HTML Struktur halaman web
- CSS Custom styling dan animasi
- Bootstrap Framework CSS untuk layout responsif
- Vue.js Framework JavaScript untuk reactive data binding
- Google Fonts (Poppins) Tipografi modern

## Tampilan Website
<img width="1824" height="934" alt="image" src="https://github.com/user-attachments/assets/e51e956a-9a6e-4e64-a84f-592c5f419a51" />
<img width="1823" height="937" alt="image" src="https://github.com/user-attachments/assets/93249ed7-0432-4510-92ac-d66f7f44fe22" />
<img width="1827" height="963" alt="image" src="https://github.com/user-attachments/assets/981db177-968c-45ba-8021-d95aa1244efb" />

## Tampilan Setiap Section / Fitur
1. Navbar

Navigasi tetap (fixed-top) dengan efek blur transparan di bagian atas halaman. Berisi link ke setiap section: Home, About, dan Certificates. Responsif dengan hamburger menu di layar kecil.
<img width="1824" height="934" alt="image" src="https://github.com/user-attachments/assets/e51e956a-9a6e-4e64-a84f-592c5f419a51" />

2. About Me Section

Terdiri dari dua kartu (glass-card) berdampingan:
- Kartu kiri: Deskripsi diri dan daftar pengalaman (Experience)
- Kartu kanan: Daftar skill dengan progress bar animasi yang menunjukkan level kemampuan dalam persen
<img width="1823" height="937" alt="image" src="https://github.com/user-attachments/assets/93249ed7-0432-4510-92ac-d66f7f44fe22" />

3. Certificates Section

Menampilkan kartu-kartu sertifikat dalam grid 3 kolom. Setiap kartu berisi gambar sertifikat, judul, dan deskripsi singkat. 
<img width="1827" height="963" alt="image" src="https://github.com/user-attachments/assets/981db177-968c-45ba-8021-d95aa1244efb" />


## Penjelasan Code Setiap Section / Fitur
1. Navbar
```
    <nav class="navbar navbar-expand-lg fixed-top navbar-dark custom-nav">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">Ghani</a>

            <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#navMenu">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navMenu">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item"><a class="nav-link" href="#home">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                    <li class="nav-item"><a class="nav-link" href="#certificates">Certificates</a></li>
                </ul>
            </div>
        </div>
    </nav>
```
Menggunakan class Bootstrap fixed-top agar navbar selalu terlihat saat scroll. Class custom-nav dari style.css menambahkan efek backdrop blur dan border bawah hijau transparan.

2. Hero Section

```
<section id="home" class="hero">
    <h1 class="fw-bold display-4">{{ name }}</h1>
    <p class="lead">{{ tagline }}</p>
    <img :src="profileImage" class="hero-img">
</section>
```
- {{ name }} dan {{ tagline }} adalah Vue.js text interpolation — nilainya diambil dari data().
- :src="profileImage" adalah Vue.js v-bind — mengikat atribut src ke variabel data profileImage.

3. About Me — Experience List
```
<li v-for="exp in experiences" :key="exp">{{ exp }}</li>
```
Menggunakan Vue v-for directive untuk me-render daftar pengalaman secara dinamis dari array experiences di data().

4. About Me — Skills Progress Bar
```
<div v-for="skill in skills" :key="skill.name" class="mb-3">
    <span>{{ skill.name }}</span>
    <span>{{ skill.level }}%</span>
    <div class="progress-bar" :style="{ width: skill.level + '%' }"></div>
</div>
```
Iterasi array skills menggunakan v-for. Lebar progress bar diatur secara dinamis dengan :style binding berdasarkan nilai skill.level.

6. Certificates Section

```
<div class="col-md-4" v-for="cert in certificates" :key="cert.title">
   <div class="card modern-card h-100">
   <img :src="cert.image" class="card-img-top">
      <div class="card-body">
         <h5 class="card-title">{{ cert.title }}</h5>
         <p class="card-text">{{ cert.description }}</p>
         </div>
   </div>
</div>
```
Kartu sertifikat di-render secara dinamis dari array certificates menggunakan v-for. Gambar dimuat via :src binding.

6. Vue.js Data
```
createApp({
    data() {
        return {
            name: "Ghani Mandala Putra",
            tagline: "Mahasiswa Sistem Informasi 2024",
            profileImage: "ghani.jpeg",

            about: "Saya merupakan mahasiswa Sistem Informasi yang memiliki ketertarikan pada UI/UX Design dan pengembangan website modern. Selain itu, saya aktif dalam organisasi dan kepanitiaan yang membantu saya mengembangkan kemampuan komunikasi, kerja tim, dan kepemimpinan.",

            experiences: [
                "UI/UX Design",
                "Organisasi",
                "Kepanitiaan"
            ],

            skills: [
                { name: "Teamwork", level: 90 },
                { name: "Komunikasi", level: 85 },
                { name: "UI/UX Design", level: 90 },
                { name: "HTML", level: 80 },
                { name: "CSS", level: 75 }
            ],

            certificates: [
                {
                    title: "UI/UX Design",
                    description: "Mengikuti Study club UI/UX Design.",
                    image: "sertif uiux.jpeg"
                },
                {
                    title: "Organisasi",
                    description: "Anggota Department Relations and Community Services Inforsa 2025.",
                    image: "sertif inforsa.jpeg"
                },
                {
                    title: "Kepanitiaan",
                    description: "Anggota panitia pada event ulang tahun prodi Sistem Informasi (Insevent) 2025.",
                    image: "sertif insevent.jpeg"
                }
            ]
        }
    }
}).mount('#app')
```
Semua konten website dikelola di dalam objek data() Vue.js. Dengan ini, perubahan data cukup dilakukan di satu tempat dan tampilan akan otomatis terupdate (reactive).

7. style.css — Custom Styling
   - Dark Theme & Color Palette
```
body {
    background: #0F1A16;
    color: #E8F5E9;
}
.section-title { color: #34D399; }
```
   - Glass Card
```
.glass-card {
    background: #16241E;
    border-radius: 18px;
    border: 1px solid rgba(52, 211, 153, 0.15);
    box-shadow: 0 6px 18px rgba(0, 0, 0, 0.4);
    transition: 0.3s ease;
}
```
Menciptakan efek kartu semi-transparan dengan border hijau tipis dan shadow gelap.

   - Hover Effect
```
.modern-card:hover {
    transform: translateY(-6px);
    border: 1px solid rgba(52, 211, 153, 0.35);
}
```
Kartu terangkat ke atas saat di-hover dengan transisi halus 0.3s, dan border menjadi lebih terang.

   - Progress Bar
```
.progress-bar {
    background: linear-gradient(90deg, #10B981, #34D399);
    border-radius: 50px;
    transition: 1s ease;
}
```
Gradient dari hijau tua ke hijau muda dengan animasi transisi 1 detik saat lebar bar berubah.

   - Navbar Blur Effect
```
.custom-nav {
    background: rgba(15, 26, 22, 0.95);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(0, 200, 150, 0.2);
}
```
Navbar menggunakan backdrop-filter: blur() untuk efek kaca buram di atas konten halaman.
