# Git Workflow: Single Developer

Untuk melakukan development secara solo, workflow dibagi menjadi 3 bagian utama:
* Master dan origin (remote)
* Development
* Feature

Branch master dan origin merepresentasikan repositori kode publik. Branch tersebut berisi source code dari file aplikasi. Sedangkan development branch adalah dimana kita melakukan sebagian besar pekerjaan, dan juga merupakan asal dari banyak commit kita. Setelah perubahan disiapkan, kita menambahkan file, commit, dan akhirnya menggabungkan (merge) perubahan ke branch master dan push ke remote:

**![alt text](pictures/gambar1.jpg)**

berikut ini adalah tampilan di console:

**![alt text](pictures/gambar2.jpg)**

branch feature merepresentasikan penambahan major dalam project, seperti revamp dari CSS suatu situs atau penambahan fungsi pada aplikasi. Branch feature dibuat dari branch development tama untuk melakukan maintenance diluar pekerjaan pada fitur itu sendiri. Bekerja pada suatu fitur membutuhkan checkout pada branch yang tepat. Apabila kita ingin pindah ke branch development untuk maintenance, kita dapat commit dan langsung berpindah.

**![alt text](pictures/gambar3.jpg)**

Berikut ini adalah gambaran proses dimana semua segmen dikombinasikan

**![alt text](pictures/gambar4.jpg)**

# Git Workflow: Team Developer

Ketika mengevaluasi workflow pada tim, hal palinng penting adalah mempertimbangkan sifat tim. Kita ingin workflow meningkatkan efektifitas dan tidak membebani sehingga membatasi produktivitas. Beberapa hal untuk dipertimbangkan ketika mengevaluasi git workflow adalah:
* kesesuaian workflow dengan skala besarnya tim
* kemudahan memperbaiki kesalahan dan error pada workflow
* apakah workflow menambahkan cognitive overhead pada tim

## Centralized Workflow
adalah workflow yang bagus untuk tim transisi dari SVN. Seperti subversion, Centralized Workflow menggunakan repositori sentral yang berperan sebagai pintu masuk tunggal untuk semua perubahan pada proyek. Development branch disebut master dan semua perubahan di-commit-kan pada branch ini. Workflow ini tidak membutuhkan branch lain selain master.

gambar5

## Membuat Central Repository
Pertama, seseorang harus membuat repositori sentral pada server. Apabila project baru, maka dapat membuat repository kosong, bila tidak harus mengimport Git atau SVN repository yang sudah ada. Central repository harus selalu merupakan repository yang tidak memiliki working directory, yang bisa dibuat dengan:

'ssh user@host git init --bare /path/to/repo.git'

## Clone Central Repository
Selanjutnya, tiap developer membuat local copy dari keseluruhan project dengan menggunakan git clone command:

`git clone ssh://user@host/path/to/repo.git`

Ketika meng-clone repository, Git secara otomatis menambahkan shortcut yang disebut origin yang menunjuk ke repository "parent".

## Membuat Perubahan dan Commit
Setelah repository di-clone secara local, developer dapat membuat perubahan menggunakan proses Git standard: edit, stage, dan commit. Apabila tidak familiar dengan area staging, ini adalah cara untuk mempersiapkan commit tanpa memasukkan setiap perubahan ke dalam working directory. Cara ini membuat kita dapat membuat commit dengan fokus yang tinggi, walaupun membuat banyak perubahan.

`git status # View the state of the repo`<br/>
`git add <some-file> # Stage a file`<br/>
`git commit # Commit a file</some-file>`<br/>

## Push Commit Baru ke Central Repository
Setelah repository local sudah di-commit perubahannya, perubahan itu perlu di-push untuk dibagikan kepada developer lain yang terlibat dalam proyek.

`git push origin master`

perintah di atas akan mem-push perubahan yang telah dicommit ke central repository. Ketika mem-push perubahan ke central repository, ada kemungkinan update dari developer lain akan berkonflik dengan apa yang kita push. Dalam situasi ini, git pull perlu dieksekusi paling awal.

## Managing Conflicts
Central repository merepresentasikan project official, sehingga commit historinya adalah hal penting. Apabila local commit developer berbeda dengan central repository, Git akan menolah push karena akan meng-overwrite commit official.

gambar7
