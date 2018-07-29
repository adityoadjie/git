## Git work flow Single Developer

Untuk melakukan development secara solo, workflow dibagi menjadi 3 bagian utama:
* Master dan origin (remote)
* Development
* Feature

Branch master dan origin merepresentasikan repositori kode publik. Branch tersebut berisi source code dari file aplikasi. Sedangkan development branch adalah dimana kita melakukan sebagian besar pekerjaan, dan juga merupakan asal dari banyak commit kita. Setelah perubahan disiapkan, kita menambahkan file, commit, dan akhirnya menggabungkan (merge) perubahan ke branch master dan push ke remote:

**![alt text](gambar1.jpg)**

berikut ini adalah tampilan di console:

**![alt text](gambar2.jpg)**

branch feature merepresentasikan penambahan major dalam project, seperti revamp dari CSS suatu situs atau penambahan fungsi pada aplikasi. Branch feature dibuat dari branch development tama untuk melakukan maintenance diluar pekerjaan pada fitur itu sendiri. Bekerja pada suatu fitur membutuhkan checkout pada branch yang tepat. Apabila kita ingin pindah ke branch development untuk maintenance, kita dapat commit dan langsung berpindah.

**![alt text](gambar3.jpg)**

Berikut ini adalah gambaran proses dimana semua segmen dikombinasikan

**![alt text](gambar4.jpg)**
