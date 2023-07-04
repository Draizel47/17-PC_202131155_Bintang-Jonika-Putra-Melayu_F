
# Segmentasi Kalimat Menggunakan OpenCV


## 1. Teori Mengenai Projek Terkait

### A.Thresholding

Thresholding merupakan salah satu teknik
segmentasi yang baik digunakan untuk citra
dengan perbedaan nilai intensitas yang
signifikan antara latar belakang dan objek
utama (Katz,2000).
Parameter kunci di dalam Thresholding
merupakan pilihan dalam melakukan
Threshold . Terdapat berbagai metode dalam
memilih Threshold. Metode paling sederhana
dilakukan dengan cara memilih nilai mean
atau median. Pada dasanya jika piksel objek
lebih terang dibandingkan dengan
background maka piksel objek tersebut juga
lebih terang dari rata-ratanya. Pada gambar
yang masih memiliki noise dengan
background dan nilai objek, mean dan
median akan bekerja maksimal dalam
threshold. Dalam pendekatan yang lebih
dalam, dapat pula dilakukan dengan cara
membuat sebuah histogram dari intensitas
citra piksel dan menggunakan valley point
sebagai nilai threshold. Dengan melakukan
pendekatan histogram memungkinkan
adanya beberapa nilai rata – rata pada piksel
background dan objek, tetapi nilai piksel
tersebut mempunyai beberapa variasi nilai
yang masih berada pada sekitar nilai rata –
rata itu. Akan tetapi biasanya tidak selalu
sesederhana itu dan banyak histogram dari
citra yang mempunyai valley point yang tidak
jelas . Persamaan untuk menentukan nilai
thresholding dapat dirumuskan sebagai
berikut :
𝑇 =
𝑓𝑚𝑎𝑘𝑠 + 𝑓𝑚𝑖𝑛/2

### B. Deteksi Garis

Deteksi garis pada citra dapat diperoleh melalui penggunaan “cadar” 
(mask) dengan contoh tercantum pada Gambar 10.4 (Gonzalez & Woods, 2002). 
Cadar (a) berguna untuk memperoleh garis horizontal,cadar (b) untuk mendapatkan garis yang berorientasi 45o, cadar (c) untuk memperoleh garis tegak, dan cadar (d) untuk mendapatkan garis yang berorientasi -45 derajat.

### C. OpenCV

OpenCV adalah open source C++ library untuk image processing dan
computer vision. Secara teori OpenCV digunakan seperti meniru cara kerja sistem
visual manusia yaitu dengan melihat objek melalui "penglihatan/mata" dan citra
pada objek tersebut diteruskan ke otak untuk memproses sehingga mengerti objek
apa yang tampak pada pandangan mata manusia. OpenCV merupakan salah satu
cabang Artificial intellegent (kecerdasan buatan) yang digunakan untuk
pengembangan atau analisis isi suatu gambar.
Menghitung jumlah obyek dalam sebuah wadah menggunakan cara yang
manual membuang waktu cukup lama, terutama jika obyek tersebut bergerak atau
makhluk hidup. Kesalahan dalam menghitung akan sering terjadi dan dapat
merugikan salah satu pihak, maka dibutuhkan aplikasi yang dapat menghitung
jumlah obyek bergerak lebih mudah dan menghemat waktu. Dengan
memanfaatkan teknologi Android, user dapat menggunakan aplikasi dimana saja.
Program ini ditunjukan pada penjual ikan atau nelayan yang menjual ikan
dalam jumlah yang besar dan menghitung ikan satu persatu bukanlah pilihan,
mereka pun menjualnya dengan mempertimbangkan berat dan memperkirakan
perkilonya berisi sekian ikan hingga tidak adanya kepastian berapa jumlah ikan
yang dibeli. Kesalahan dalam menghitung dapat merugikan salah satu pihak dari
penjual maupun pembeli. Oleh karena itu dilakukan penelitian untuk membantu
masalah tersebut dengan merancang suatu aplikasi counting objek bergerak
dengan menggunakan OpenCV pada Smartphone

### D. Word Detection (Contours)

cv2.findContours() digunakan untuk menemukan kontur pada gambar yang melebar. Ada tiga argumen di cv.findContours(): gambar sumber, mode pengambilan kontur, dan metode perkiraan kontur. 
Fungsi ini mengembalikan kontur dan hierarki. Kontur adalah daftar python dari semua kontur pada gambar. Setiap kontur adalah larik Numpy dari (x, y) koordinat titik batas dalam objek. Kontur biasanya digunakan untuk menemukan objek putih dari latar belakang hitam. Semua teknik pemrosesan gambar di atas diterapkan agar Kontur dapat mendeteksi batas tepi blok teks gambar. File teks dibuka dalam mode tulis dan memerah. File teks ini dibuka untuk menyimpan teks dari keluaran OCR.

## 2. Penjelasan Mengenai Langkah Pembuatan Gambar

1. Membaca dan Mengubah Ukuran Gambar: Fungsi "cv.imread('nama.jpg')" membaca gambar dan mengambil dimensinya dengan variabel "tinggi" dan "lebar". Jika lebar gambar lebih dari 1000 piksel, ukurannya diubah menjadi 1000 piksel dengan mempertahankan aspek rasio. Ukuran gambar dapat diubah menggunakan fungsi "cv.resize(gambar, (lebar, tinggi))".

2. Thresholding: Fungsi "cv.cvtColor(img, cv.COLOR_BGR2GRAY)" mengubah gambar menjadi citra grayscale. Fungsi "cv.threshold(img_gray, 80, 255, cv.THRESH_BINARY_INV)" melakukan thresholding pada citra grayscale. Hasil thresholding ditampilkan menggunakan "plt.imshow(thresh, cmap='gray").

3. Dilatasi: Menggunakan fungsi "cv.dilate(thresh_img, kernel, iterations=1)" untuk menerapkan operasi dilatasi pada gambar hasil thresholding. Hasil dilatasi ditampilkan menggunakan "plt.imshow(dilate, cmap='gray')".

4. Deteksi Garis (Deteksi Garis): Menggunakan fungsi "cv.findContours(dilated.copy(), cv.RETR_EXTERNAL, cv.CHAIN_APPROX_NONE)" untuk mendapatkan kontur-kontur pada citra hasil dilatasi. Kemudian, urutkan kontur-kontur berdasarkan koordinat y dari atas ke bawah menggunakan "sorted_contours_line". Kemudian, buat salinan gambar ("gambar2") untuk menampilkan kotak persegi

5. Deteksi Teks (Deteksi Teks): Menampilkan kotak persegi panjang (bounding box) pada setiap kata yang terdeteksi dengan menggunakan salinan gambar awal (gambar3). Mengambil setiap garis yang terdeteksi pada langkah sebelumnya dan mengambil gambar bagian yang sesuai dengan kotak persegi panjang. Kemudian menerapkan operasi dilatasi pada gambar kata menggunakan "cv.dilate(roi_line, kernel, iterations=1)" dan menggunakan "cv.findContours()".
  

## 3. Daftar Pustaka

https://core.ac.uk/download/pdf/35380536.pdf

https://eprints.umm.ac.id/34169/2/jiptummpp-gdl-rendradwiw-43950-2-bab1.pdf

https://www.geeksforgeeks.org/text-detection-and-extraction-using-opencv-and-ocr/

PCD-10.pdf