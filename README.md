# Tutorial Dasar Git & GitHub untuk Siswa RPL

Selamat datang di dunia Git dan GitHub! 👩‍💻👨‍💻 Git adalah *Version Control System* yang wajib dikuasai oleh seorang programmer untuk melacak perubahan pada kode, sementara GitHub adalah platform untuk menyimpan kode tersebut secara online dan berkolaborasi dengan orang lain.

Mari kita mulai langkah demi langkah!

---

## 1. Konfigurasi Awal Git

Pertama, kita perlu memperkenalkan diri kita ke Git. Buka **Git Bash** (cari di Start Menu) dan ketikkan perintah berikut.

> **Penting:** Konfigurasi ini hanya perlu dilakukan sekali saja di komputermu.

1.  **Buka Git Bash**
    
    Tampilan awalnya akan seperti terminal.

2.  **Atur Nama Pengguna**
    Ganti `"Nama Lengkap Kamu"` dengan nama aslimu.
    ```bash
    git config --global user.name "Nama Lengkap Kamu"
    ```

3.  **Atur Email**
    Ganti `"emailkamu@example.com"` dengan email yang akan kamu daftarkan di GitHub.
    ```bash
    git config --global user.email "emailkamu@example.com"
    ```

4.  **Cek Konfigurasi**
    Pastikan nama dan email kamu sudah tersimpan dengan benar.
    ```bash
    git config --list
    ```
    Carilah baris `user.name` dan `user.email` pada hasil yang muncul. Jika sudah ada, berarti konfigurasi berhasil!
    

---

## 2. Membuat Proyek (Repository Lokal)

Sekarang, kita akan membuat folder proyek pertama kita yang akan dilacak oleh Git.

1.  **Masuk ke Folder Dokumen**
    Kita akan membuat folder proyek di dalam direktori `Documents`. Gunakan perintah `cd` (*change directory*).
    ```bash
    cd Documents
    ```

2.  **Buat Folder Proyek Baru**
    Gunakan perintah `mkdir` (*make directory*) untuk membuat folder bernama `belajar-git`.
    ```bash
    mkdir belajar-git
    ```

3.  **Masuk ke Folder Proyek**
    Pindah ke dalam folder yang baru saja kita buat.
    ```bash
    cd belajar-git
    ```

4.  **Inisialisasi Git**
    Ini adalah langkah kuncinya. Perintah ini akan membuat sebuah "repository" atau "repo" lokal di dalam folder `belajar-git`. Folder ini sekarang resmi diawasi oleh Git.
    ```bash
    git init
    ```
    Kamu akan melihat pesan seperti `Initialized empty Git repository in .../Documents/belajar-git/.git/`.

---

## 3. Membuat Commit Pertama

*Commit* bisa diartikan sebagai "menyimpan" atau "merekam" perubahan pada proyek kita.

1.  **Buka Folder di Visual Studio Code**
    Ketik perintah berikut di Git Bash untuk membuka folder proyek di VS Code (atau teks editor favoritmu).
    ```bash
    code .
    ```
    > Tanda titik `.` artinya "folder saat ini".

2.  **Buat File README.md**
    Di VS Code, buat file baru dengan nama `README.md`. File ini biasanya berisi deskripsi tentang proyek.
    

3.  **Isi File README.md**
    Ketik atau salin teks di bawah ini ke dalam file `README.md` yang baru kamu buat. Ganti isinya dengan datamu sendiri.
    ```markdown
    # Biodata Saya

    - **Nama:** Budiono Siregar Kapal Lawud
    - **Kelas:** XI RPL
    - **Alamat:** Baleendah, Bandung
    ```

4.  **Simpan File** (`Ctrl + S`).

5.  **Cek Status Perubahan**
    Kembali ke Git Bash, lalu jalankan perintah `git status`.
    ```bash
    git status
    ```
    Git akan memberitahu bahwa ada file `README.md` yang belum dilacak (*untracked files*).

6.  **Tambahkan File ke "Staging Area"**
    Kita perlu memberitahu Git file mana yang ingin kita simpan perubahannya. Perintah `git add` memindahkan file ke "area pementasan" (*staging area*).
    ```bash
    git add README.md
    ```
    > **Tips:** Jika ingin menambahkan semua file yang berubah, gunakan `git add .`

7.  **Cek Status Lagi**
    Jalankan `git status` lagi. Sekarang, file `README.md` akan berwarna hijau dengan status *Changes to be committed*.

8.  **Lakukan Commit**
    Sekarang kita simpan perubahan ini secara permanen di riwayat Git dengan sebuah pesan yang jelas.
    ```bash
    git commit -m "feat: membuat file readme dengan biodata awal"
    ```
    > `-m` artinya *message*. Pesan commit yang baik menjelaskan perubahan yang kamu buat.

---

## 4. Menghubungkan ke GitHub

Saatnya meng-upload proyek kita ke GitHub agar bisa diakses online.

1.  **Daftar atau Login ke GitHub**
    Jika belum punya akun, buka [github.com](https://github.com) dan daftar. Jika sudah, langsung login saja.

2.  **Buat Repository Baru**
    - Klik ikon `+` di pojok kanan atas, lalu pilih **New repository**.
    - Beri nama repository: `belajar-git`.
    - Biarkan yang lain sebagai default (Public, tanpa inisialisasi README, .gitignore, atau license).
    - Klik **Create repository**.
    

3.  **Membuat Personal Access Token (PAT)**
    Untuk keamanan, GitHub sekarang mewajibkan penggunaan Token sebagai pengganti password saat melakukan *push* dari terminal.
    - Buka halaman **Settings** di GitHub (klik foto profilmu > Settings).
    - Gulir ke bawah, cari dan klik **Developer settings**.
    - Klik **Personal access tokens** > **Tokens (classic)**.
    - Klik **Generate new token** > **Generate new token (classic)**.
    - **Note:** Beri nama token, contoh: `git-bash-token`.
    - **Expiration:** Pilih durasi token, misalnya 30 hari.
    - **Select scopes:** Centang kotak `repo`.
    - Gulir ke bawah dan klik **Generate token**.
    - **PENTING:** Salin token yang muncul. Token ini hanya akan ditampilkan sekali. Simpan di tempat yang aman!
    

4.  **Hubungkan Repo Lokal ke GitHub**
    Kembali ke halaman repository GitHub yang tadi kamu buat. Di sana ada beberapa baris perintah di bawah judul "...or push an existing repository from the command line". Kita akan menggunakan itu.

    Salin perintah `git remote add origin ...` yang diberikan oleh GitHub.
    ```bash
    git remote add origin [https://github.com/USERNAME/belajar-git.git](https://github.com/USERNAME/belajar-git.git)
    ```
    > Ganti `USERNAME` dengan username GitHub kamu. Perintah ini memberitahu Git lokal di mana alamat "remote" atau "pusat" dari proyek ini berada.

5.  **(Opsional) Ganti Nama Branch ke `main`**
    Secara default, Git versi baru menggunakan nama branch `main`. Jika di komputermu masih menggunakan `master`, ganti dengan perintah ini agar seragam.
    ```bash
    git branch -M main
    ```

6.  **Push ke GitHub!** 🎉
    Saatnya mengirim *commit* pertama kita dari lokal ke server GitHub.
    ```bash
    git push -u origin main
    ```
    - Terminal akan meminta **Username** kamu. Masukkan username GitHub-mu, tekan Enter.
    - Kemudian akan meminta **Password**. **JANGAN masukkan password GitHub-mu**. Masukkan **Personal Access Token (PAT)** yang sudah kamu salin tadi.
    - Tekan Enter.

7.  **Cek Hasilnya**
    Refresh halaman repository `belajar-git` di browser. File `README.md` kamu sekarang seharusnya sudah muncul di sana!

---

## 5. Membuat Perubahan dan Push Kembali

Bagaimana jika kita ingin mengubah sesuatu? Prosesnya sama!

1.  **Update File `README.md`**
    Buka kembali VS Code. Tambahkan baris baru di bawah biodatamu.
    ```markdown
    # Biodata Saya

    - **Nama:** Budiono Siregar Kapal Lawud
    - **Kelas:** XI RPL
    - **Alamat:** Baleendah, Bandung
    - **Cita-cita:** Menjadi Software Engineer handal
    ```
    Simpan file (`Ctrl + S`).

2.  **Ulangi Proses Add & Commit**
    Kembali ke Git Bash.
    - Cek status: `git status` (akan terlihat `README.md` termodifikasi).
    - Tambahkan ke staging: `git add README.md`
    - Buat commit baru: `git commit -m "docs: menambahkan cita-cita di readme"`

3.  **Push Perubahan**
    Karena kita sudah menghubungkan remote sebelumnya, sekarang prosesnya lebih singkat.
    ```bash
    git push
    ```
    > Karena sebelumnya kita menggunakan `-u`, Git sudah ingat ke mana harus mengirim perubahan untuk branch `main`.

4.  **Selesai!**
    Refresh lagi halaman repository GitHub-mu. Kamu akan melihat baris "Cita-cita" sudah ditambahkan.

**Selamat! Kamu sudah berhasil melalui siklus dasar penggunaan Git dan GitHub. Teruslah berlatih, karena ini adalah skill fundamental bagi seorang developer.** 👍