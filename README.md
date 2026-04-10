# StrukturData-Q1-2501010071-GunturErza-C
UAS

1. Array (Kontinu): Elemen disimpan dalam blok memori yang berurutan secara fisik. Karena alamatnya berurutan, sistem menggunakan offset calculation. Untuk mengakses indeks ke-i, CPU cukup menghitung Alamat=BaseAddress+(i×elementSize). Karena hanya melibatkan satu operasi aritmatika, kompleksitas waktunya adalah O(1).

Singly Linked List (Non-kontinu): Node tersimpan secara acak di dalam heap. Hubungan antar elemen hanya dijaga oleh pointer next. Komputer tidak bisa memprediksi alamat node ke-i tanpa mengunjungi node 0,1,...,i−1. Proses penelusuran (traversal) ini menyebabkan akses data memiliki kompleksitas O(n).

2. Linked List lebih efisien daripada Array dalam kondisi:

Penyisipan/Penghapusan di Awal (Head): Pada Linked List, operasi ini hanya memerlukan pembaruan pointer (O(1)). Pada Array, semua elemen yang ada harus digeser satu slot ke kanan atau ke kiri untuk menjaga kontinuitas, sehingga memakan waktu O(n).

Manipulasi di Tengah (setelah pointer diketahui): Jika kita sudah memiliki referensi ke node tertentu, proses link/unlink node hanya membutuhkan waktu konstan O(1) tanpa perlu memindahkan data lain secara fisik di memori.

3. Konsep Doubly Linked List
Anatomi Node: Terdiri dari tiga komponen utama:

Data Field: Menyimpan nilai/objek.
Next Pointer: Alamat memori node berikutnya.
Prev Pointer: Alamat memori node sebelumnya.
Dampak Memori: Penggunaan memori meningkat secara linear terhadap jumlah node (n) karena setiap node harus menyimpan satu pointer tambahan (biasanya 4 atau 8 byte tergantung arsitektur sistem).

Fleksibilitas: Memungkinkan Bidirectional Traversal. Hal ini sangat berguna untuk algoritma yang membutuhkan navigasi mundur (seperti undo functionality atau LRU Cache) dan mempermudah penghapusan node jika hanya alamat node tersebut yang diketahui (tanpa perlu mencari node sebelumnya dari Head).

4. Mekanisme Circular Linked List
Secara teoritis, perbedaannya terletak pada nilai pointer node terakhir (tail). Pada Linked List biasa, pointer terakhir bernilai NULL. Pada Circular Linked List, pointer next dari node terakhir menunjuk kembali ke alamat node pertama (head).

Skenario Penggunaan: Sistem Penjadwalan Round-Robin. Dalam sistem operasi, proses-proses diberikan slot waktu CPU secara bergiliran. Struktur sirkular memungkinkan algoritma untuk kembali ke proses pertama secara otomatis setelah proses terakhir selesai diproses tanpa perlu melakukan reset pointer secara manual ke awal list.

5. Array Dinamis di Python (List)
Ketika list di Python mencapai batas kapasitasnya (full capacity) saat operasi append, terjadi mekanisme yang disebut Dynamic Resizing:

Allocation: Python mengalokasikan blok memori baru yang lebih besar (biasanya mengikuti pola pertumbuhan tertentu untuk meminimalkan frekuensi resizing).
Migration: Semua referensi objek dari array lama disalin ke array baru. Secara teknis, ini adalah operasi O(n).
Deallocation: Memori lama dibebaskan (di-release).
Pointer Update: Internal pointer dari list mengarah ke lokasi memori baru.
Meskipun proses ini O(n), ia terjadi cukup jarang sehingga secara amortized cost, operasi append tetap dihitung sebagai O(1).
