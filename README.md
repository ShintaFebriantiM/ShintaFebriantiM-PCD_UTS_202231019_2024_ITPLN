# Laporan UTS


Terdapat beberapa proses yang dilakukan terhadap citra yang telah saya buat:

#### 1. Analisis Citra

- Load Gambar: memuat gambar dari file 'nama.jpg' menggunakan matplotlib.image.imread() untuk digunakan dalam analisis.
- Ekstraksi Channel Warna:  untuk memisahkan saluran warna merah, hijau, dan biru (RGB) dari gambar tersebut menggunakan slicing pada array numpy.
- Visualisasi Channel Warna:  untuk menampilkan gambar asli serta saluran warna merah, hijau, dan biru secara terpisah menggunakan matplotlib.pyplot.imshow().
- Konversi Format Gambar:  memuat gambar lagi menggunakan cv2.imread() untuk menggunakan OpenCV. Kemudian, Anda mengonversi format gambar dari BGR (format default OpenCV) ke RGB menggunakan cv2.cvtColor().
- Perhitungan Histogram: bertujuan menghitung histogram untuk masing-masing saluran warna (merah, hijau, biru) menggunakan cv2.calcHist(). Histogram adalah distribusi frekuensi intensitas piksel di dalam gambar.
- Visualisasi Histogram: memplot histogram untuk setiap saluran warna secara terpisah, serta histogram untuk keseluruhan warna, menggunakan matplotlib.pyplot.plot().
 

1.Pemisahan Saluran Warna: Citra dimuat dan dipisahkan menjadi saluran warna merah, hijau, dan biru (RGB) menggunakan slicing pada array numpy. Hal ini memungkinkan untuk memperoleh informasi tentang kontribusi masing-masing warna terhadap citra.

2.Visualisasi Saluran Warna: Citra asli dan saluran warna merah, hijau, dan biru dipresentasikan secara terpisah. Berguna memberikan pemahaman visual tentang distribusi warna dalam citra.

3.Konversi Format Gambar: Citra dimuat menggunakan OpenCV untuk kemudian dikonversi dari format defaultnya (BGR) ke format RGB. Hal ini memastikan konsistensi format dalam analisis selanjutnya.

4.Perhitungan dan Visualisasi Histogram: Histogram dihitung untuk masing-masing saluran warna (merah, hijau, biru) dan untuk seluruh citra. Histogram merepresentasikan distribusi frekuensi intensitas piksel dalam citra. Plot histogram memberikan informasi tentang sebaran nilai-nilai piksel dalam citra, yang dapat memberikan wawasan tentang kontras, kecerahan, dan distribusi warna.
Dengan analisis ini, kita dapat memahami kontribusi masing-masing saluran warna terhadap citra tersebut, serta mendapatkan wawasan tentang distribusi intensitas piksel dalam citra tersebut

#### Histogramuntuk Setiap Gambar
•	perhitungan dan visualisasi histogram untuk citra yang dimuat menggunakan OpenCV.saya akan jelaskan setiap langkahnya:

Memuat Citra : 
Citra dimuat menggunakan cv2.imread() dari file 'nama.jpg'. Ini menghasilkan citra dalam format BGR (Blue-Green-Red) yang merupakan format default yang digunakan oleh OpenCV.

Konversi Format Citra : 
Citra kemudian dikonversi dari format BGR ke format RGB menggunakan cv2.cvtColor(). Ini penting karena format RGB lebih umum digunakan dalam berbagai operasi pemrosesan citra dan analisis.

Perhitungan Histogram untuk Saluran Warna : 
Histogram dihitung untuk masing-masing saluran warna (biru, hijau, merah) menggunakan cv2.calcHist(). Fungsi ini menghitung jumlah piksel dengan intensitas tertentu dalam setiap saluran warna. Parameter yang digunakan adalah [b], [g], dan [r], yang merupakan saluran warna masing-masing dalam citra.

Perhitungan Histogram untuk Keseluruhan Warna: 
Histogram juga dihitung untuk keseluruhan citra (semua saluran warna) dengan menggunakan cv2.calcHist() dengan parameter [color_image]. Ini menghasilkan histogram untuk intensitas warna keseluruhan dalam citra.

Visualisasi Histogram: 
Setelah histogram dihitung, mereka kemudian divisualisasikan menggunakan matplotlib.pyplot.plot(). Empat subplot dibuat dalam satu figur untuk menampilkan histogram untuk setiap saluran warna (biru, hijau, merah) dan histogram untuk keseluruhan warna dalam citra. Plot histogram memberikan wawasan tentang distribusi intensitas piksel dalam citra dan saluran warnanya.
Dengan cara ini, kita dapat menganalisis distribusi intensitas piksel dalam citra baik secara keseluruhan maupun pada saluran warna individu. Hal ini penting dalam banyak aplikasi pemrosesan citra, seperti segmentasi, deteksi fitur, dan klasifikasi.

#### Nilai Ambang Batas Citra 
Untuk menemukan nilai ambang batas yang optimal, pertama-tama kita perlu memahami cara kerja ruang warna HSV (Hue, Saturation, Value). Dalam kode ini, ambang batas ditentukan dalam ruang warna HSV untuk mendeteksi warna tertentu.

Berikut adalah penjelasan nilai ambang batas yang digunakan dalam citra ini:

- Ambang Batas Biru:

Lower Blue: [100, 50, 50]
Upper Blue: [130, 255, 255]
Penjelasan:

Nilai H (Hue) berkisar antara 100 hingga 130, yang mewakili rentang warna biru dalam ruang warna HSV.
Nilai S (Saturation) mulai dari 50 ke atas, menunjukkan saturasi warna biru.
Nilai V (Value) mulai dari 50 ke atas, menunjukkan kecerahan warna biru.

- Ambang Batas Merah (untuk deteksi merah dan ungu):

Lower Red 1: [0, 50, 50]
Upper Red 1: [10, 255, 255]
Lower Red 2: [170, 50, 50]
Upper Red 2: [180, 255, 255]
Penjelasan:

Karena warna merah terletak di kedua ujung spektrum H (Hue), kita memerlukan dua rentang untuk menangkap merah secara keseluruhan.
Nilai H mendefinisikan kedua rentang, dengan rentang pertama dari 0 hingga 10 dan rentang kedua dari 170 hingga 180.
Nilai S dan V diatur untuk memastikan hanya warna dengan saturasi dan kecerahan yang memadai yang dideteksi sebagai merah.

- Ambang Batas Hijau:

Lower Green: [40, 50, 50]
Upper Green: [80, 255, 255]
Penjelasan:

Rentang H diatur untuk mencakup warna hijau.
Nilai S dan V diatur untuk memastikan hanya warna dengan saturasi dan kecerahan yang memadai yang dideteksi sebagai hijau.
Nilai-nilai ini telah dipilih berdasarkan pemahaman tentang spektrum warna dan ruang warna HSV. 

#### Tahapan Cara Menyelesaikan Projek
Terdapat beberapa tahapan dalam menyelesaikan projek ini, berikut penjelasanya :

1. Pemrosesan Gambar Asli:

- Gambar asli dimuat menggunakan matplotlib.image.imread.
- Komponen warna RGB (Red, Green, Blue) dipisahkan untuk analisis lebih lanjut.

2. Visualisasi Komponen Warna:

- Komponen warna (merah, hijau, biru) dipisahkan dan divisualisasikan menggunakan matplotlib.pyplot.imshow.
- Subplot digunakan untuk menampilkan gambar asli dan komponen warna secara bersamaan.

3. Penghitungan Histogram:

- Histogram untuk setiap komponen warna (merah, hijau, biru) dihitung menggunakan cv2.calcHist.
- Histogram ini menunjukkan distribusi intensitas piksel untuk masing-masing komponen warna.

4. Peningkatan Kecerahan Gambar:

- Fungsi increase_brightness digunakan untuk meningkatkan kecerahan gambar menggunakan operasi dalam ruang warna HSV.
- Proses ini membantu meningkatkan kontras gambar sehingga deteksi warna menjadi lebih baik.

5. Deteksi Warna:

- Terdapat tiga fungsi deteksi warna: detect_and_highlight_blue, detect_and_highlight_red_blue, dan detect_and_highlight_red_green_blue.
- Setiap fungsi menggunakan ruang warna HSV untuk menentukan masker (ambang batas) untuk warna yang ingin dideteksi.
- Masker ini kemudian diterapkan ke gambar asli menggunakan operasi bitwise untuk menyorot piksel yang sesuai dengan warna tertentu.

6. Visualisasi Hasil Deteksi Warna:

- Hasil deteksi warna ditampilkan menggunakan matplotlib.pyplot.imshow.
- Subplot digunakan untuk menampilkan gambar asli dan hasil deteksi warna untuk beberapa skenario (deteksi biru, deteksi merah-biru, deteksi merah-hijau-biru).

Dengan tahapan-tahapan ini, kita dapat memahami dan mengevaluasi bagaimana deteksi warna dilakukan pada gambar yang diberikan. Mulai dari pemrosesan gambar asli, pemisahan komponen warna, penghitungan histogram, hingga deteksi dan visualisasi hasilnya. 

#### Teori terkait

Berikut adalah beberapa teori yang mendukung:

- Model Warna RGB dan HSV:
Dalam model warna RGB, warna direpresentasikan sebagai kombinasi dari tiga komponen warna: merah (Red), hijau (Green), dan biru (Blue).
Model warna HSV (Hue, Saturation, Value) menggambarkan warna berdasarkan nuansa (Hue), saturasi (Saturation), dan kecerahan (Value).
Pemahaman tentang model warna ini penting untuk memahami cara kerja deteksi warna, di mana sering kali kita beroperasi dalam ruang warna HSV karena lebih sesuai untuk deteksi warna daripada RGB.

- Histogram Warna:
Histogram warna adalah representasi visual dari distribusi intensitas piksel dalam gambar untuk setiap komponen warna.
Analisis histogram dapat memberikan wawasan tentang distribusi warna dalam gambar dan digunakan dalam penyesuaian ambang batas untuk deteksi warna.

- Thresholding:
Thresholding adalah teknik yang umum digunakan dalam pengolahan citra untuk memisahkan objek dari latar belakang dengan membuat masker piksel berdasarkan nilai ambang batas.
Dalam konteks deteksi warna, thresholding digunakan untuk membuat masker yang menyoroti piksel yang sesuai dengan warna yang ingin dideteksi.

- Operasi Bitwise:
Operasi bitwise digunakan untuk menerapkan masker (hasil dari thresholding) ke gambar asli, di mana hanya piksel yang sesuai dengan masker yang dipertahankan, sedangkan piksel lainnya dihapus.
Dalam deteksi warna, operasi bitwise digunakan untuk menyoroti piksel yang cocok dengan warna yang ditentukan dalam masker.

- Peningkatan Kecerahan dan Kontras:
Peningkatan kecerahan dan kontras adalah teknik yang sering digunakan untuk meningkatkan kualitas gambar sebelum proses analisis lebih lanjut.
Dalam konteks deteksi warna, peningkatan kecerahan dapat membantu meningkatkan kontras antara objek yang ingin dideteksi dan latar belakang.
Dengan pemahaman teori-teori ini, kita dapat merancang dan menerapkan metode deteksi warna yang efektif menggunakan OpenCV dan Python. Teori-teori ini memberikan landasan yang kuat untuk memahami prinsip-prinsip dasar dalam pemrosesan citra dan analisis warna yang diperlukan dalam projek deteksi warna.

