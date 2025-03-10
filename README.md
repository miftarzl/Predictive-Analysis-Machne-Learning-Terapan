# Laporan Proyek Machine Learning - Mifta Rizaldirahmat
## Domain Proyek
Setiap wilayah tentunya memiliki minimal satu pasien yang dirawat di rumah sakit. Namun, ada beberapa orang yang memilih untuk tidak pergi ke rumah sakit meskipun mereka sakit. Alasan mereka sangat bervariasi, mulai dari ketidakpercayaan terhadap dunia medis, lebih memilih beristirahat di rumah, hingga ketakutan terhadap biaya pengobatan yang tinggi. Oleh karena itu, diperlukan penelitian untuk memprediksi besaran biaya perawatan di rumah sakit. Proyek ini bertujuan untuk memperkirakan biaya yang harus dikeluarkan oleh masyarakat yang ingin berobat ke rumah sakit.

## Business Understanding
Orang-orang cenderung berpikir mereka perlu pergi ke rumah sakit ketika penyakitnya sudah menjadi sangat menyakitkan. Dengan meremehkan gejala yang mereka anggap biasa, penyakit tersebut semakin parah. Begitu pula dengan tagihan rumah sakit. Jika penyakitnya masih tergolong ringan, biayanya lebih murah dibandingkan dengan biaya untuk penyakit yang sudah parah.

### Problem Statement
Berdasarkan masalah yang telah disebutkan sebelumnya, dapat disimpulkan bahwa tantangan yang dihadapi adalah:
- Bagaimana cara memprediksi biaya pengobatan di rumah sakit secara akurat?

### Goal
Berdasarkan masalah yang telah disebutkan sebelumnya, tujuan dari proyek ini adalah:
- Memahami cara memprediksi biaya pengobatan di rumah sakit.

### Solution statements
- Melakukan proses Exploratory Data Analysis (EDA) untuk memahami data lebih dalam, mengidentifikasi pola, dan menemukan anomali yang mungkin ada. 
- Membuat model Machine Learning dengan menggunakan beberapa metode, yaitu:
  1. K-Nearest Neighbors (KNN): Metode ini mengelompokkan data berdasarkan kedekatannya dengan tetangga terdekat.
  2. Random Forest (RF): Algoritma ini menggunakan beberapa pohon keputusan untuk meningkatkan akurasi prediksi.
  3. Boosting Algorithm: Teknik ini meningkatkan kinerja model dengan menggabungkan beberapa model lemah menjadi satu model kuat.

## Data Understanding

Dataset yang digunakan untuk proyek ini diperoleh dari [Kaggle](https://www.kaggle.com/datasets/rajgupta2019/medical-insurance-dataset). 
Dataset ini mencakup 1338 data dan memiliki 7 fitur. Fitur-fitur tersebut dibagi menjadi dua kategori, yaitu *Numerical Features* (age, bmi, children, dan expenses) dan *Categorical Features* (sex, smoker, dan region).
Berikut adalah penjelasan detailnya:
- age: Umur pasien
- bmi: _Body Mass Index_ 
- children: Jumlah anak yang ditanggung asuransi
- expenses: Biaya medis individu
- sex: Jenis kelamin pasien
- smoker: Perokok atau bukan
- region: Tempat asal

### EDA-Univariate
Berikut merupakan *EDA-Univariate Analysis*:

- Grafik sex, grafik di bawah ini menunjukkan bahwa laki-laki mendominasi dalam dataset yang digunakan. Hal ini dapat memberikan wawasan lebih lanjut tentang distribusi jenis kelamin dalam data medis yang dianalisis.

![grafik sex](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/sex.png)
Gambar 1. Grafik Sex

- Grafik smoker, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset adalah non-perokok. Informasi ini dapat memberikan wawasan lebih lanjut tentang distribusi kebiasaan merokok di antara pasien yang dianalisis.
![grafik smoker](https://github.com/miftarzl/Predictive-Analysis-Learning-Terapan/blob/main/Image/smoker.png)
Gambar 2. Grafik Smoker

- Grafik region, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset berasal dari wilayah Southeast. Informasi ini memberikan gambaran mengenai distribusi regional pasien yang dianalisis, yang dapat digunakan untuk memahami lebih lanjut pola kesehatan dan demografi di wilayah tersebut.
![grafik region](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/region.png)
Gambar 3. Grafik Region

### EDA-Multivariate
Berikut merupakan *EDA-Multivariate Analysis*:
- Grafik rata-rata expenses relatif terhadap sex, grafik di bawah ini menunjukkan bahwa rata-rata biaya medis relatif terhadap jenis kelamin didominasi oleh pasien laki-laki. Informasi ini memberikan gambaran mengenai perbedaan pengeluaran medis berdasarkan jenis kelamin dalam dataset yang dianalisis.
![multivariate-sex](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/multivariate%20sex.png)
Gambar 4. Grafik Rata-rata Expenses Relatif Terhadap Sex

- Grafik rata-rata expenses relatif terhadap smoker, grafik di bawah ini menunjukkan bahwa rata-rata biaya medis yang dikeluarkan lebih tinggi bagi pasien yang merokok dibandingkan dengan pasien yang tidak merokok. Informasi ini memberikan gambaran mengenai dampak kebiasaan merokok terhadap pengeluaran medis, yang tentunya penting untuk memahami faktor-faktor yang mempengaruhi biaya pengobatan.
![multivariate-smoker](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/multivariate%20smoker.png)
Gambar 5. Grafik Rata-rata Expenses Relatif Terhadap Smoker

- Grafik rata-rata expenses relatif terhadap region, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset berasal dari wilayah Southeast dan rata-rata biaya medis relatif terhadap region tersebut. Informasi ini memberikan gambaran mengenai distribusi regional pasien serta biaya pengobatan yang mungkin terkait dengan wilayah mereka.
![multivariate-region](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/multivariate%20region.png)
Gambar 6. Grafik Rata-rata Expenses Relatif Terhadap Region

Berdasarkan analisis dari ketiga grafik tersebut, dapat disimpulkan bahwa biaya pengobatan di rumah sakit cenderung lebih tinggi bagi pasien yang merokok dibandingkan dengan pasien yang tidak merokok. Hal ini menunjukkan bahwa kebiasaan merokok memiliki dampak signifikan terhadap biaya medis, yang kemungkinan besar disebabkan oleh berbagai masalah kesehatan yang terkait dengan merokok. Memahami pola ini dapat membantu dalam merencanakan biaya kesehatan dan mengedukasi masyarakat mengenai risiko kesehatan dan finansial akibat merokok.

#### Korelasi Matriks
Berdasarkan matriks dibawah, *Numerical Features* memiliki korelasi yang rendah terhadap expenses.
![korelasi matriks fitur numerik](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/korelasi%20fitur%20numerik.png)
Gambar 7. Korelasi Matriks *Numerical Features*

## Data Preparation
### Encoding
Beberapa cara untuk melakukan Encoding sebagai berikut:
1. Melakukan one-hot-encoding pada *categorical features* menggunakan get_dummies.
```sh
hospital = pd.concat([hospital, pd.get_dummies(hospital['sex'], prefix='sex')], axis=1)
hospital = pd.concat([hospital, pd.get_dummies(hospital['smoker'], prefix='smoker')], axis=1)
hospital = pd.concat([hospital, pd.get_dummies(hospital['region'], prefix='region')], axis=1)
```
Korelasi matriks untuk seluruh fitur
Berdasarkan matriks dibawah, maka dapat disimpulkan bahwa smoker berkorelasi kuat terhadap expense
![korelasi matriks seluruh fitur](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/korelasi%20matriks%20seluruh%20fitur.png)
Gambar 8. Korelasi Matriks untuk Seluruh Fitur

2. Label Data
Kita akan menghapus fitur sex, smoker, dan region terlebih dahulu karena ketiga fitur tersebut telah melewati proses one-hot-encoding menggunakan fungsi drop.

Lalu membuat dataframe x yang menampung variabel
```sh
x = hospital.drop(['expenses'], axis=1)
x
```

Kemudian, membuat dataframe y untuk menampung variabel expenses

3. Train-Test-Split
Membagi data sampel menjadi data train dan data test dengan ukuran 80% data train dan 20% data test.
```sh
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=200)
```
Total dari panjang x, data train, dan data test sebagai berikut:
```sh
Total # of sample in whole dataset: 1338
Total # of sample in train dataset: 1070
Total # of sample in test dataset: 268
```

4. Standarisasi
Melakukan standarisasi pada data menggunakan StandardScaler untuk mengubah nilai rata-rata (mean) menjadi 0 dan nilai standar deviasi menjadi 1.
```sh
scaler = StandardScaler()
scaler.fit(x_train[numerical_features])
x_train[numerical_features] = scaler.transform(x_train.loc[:, numerical_features])
x_train[numerical_features].head()
```

Melakukan pengecekan nilai mean dan standar deviasi pada setelah proses standarisasi
```sh
x_train[numerical_features].describe().round(4)
```

## Modeling
Model-model yang digunakan padal proyek ini adalah:
- **KNN** adalah algoritma yang relatif sederhana dibandingkan dengan algoritma lainnya. Algoritma ini menggunakan 'kesamaan fitur' untuk memprediksi nilai dari data baru. Dengan kata lain, setiap data baru diberikan nilai berdasarkan seberapa mirip titik tersebut dengan data dalam set pelatihan. Hal ini memungkinkan KNN untuk melakukan prediksi dengan membandingkan fitur-fitur yang ada.
```sh
knn = KNeighborsRegressor(n_neighbors=10)
```
Pada implementasi ini, digunakan parameter n_neighbors dengan nilai 10. Parameter tersebut akan memilih 10 tetangga terdekat berdasarkan jarak. Selanjutnya, data dari 10 tetangga terdekat tersebut akan digunakan untuk menentukan nilai data baru yang dimasukkan.

- **Random forest** adalah salah satu model machine learning yang termasuk dalam kategori ensemble (group) learning. Ensemble merupakan model prediksi yang terdiri dari beberapa model yang bekerja secara bersama-sama. Ide di balik model ensemble adalah sekelompok model yang bekerja bersama untuk menyelesaikan masalah. Dengan demikian, tingkat keberhasilan cenderung lebih tinggi dibandingkan dengan model yang bekerja sendirian.
```sh
RF = RandomForestRegressor(n_estimators=50, max_depth=16, random_state=55, n_jobs=-1)
```
Pada implementasi ini, digunakan parameter n_estimators dengan nilai 50. Parameter ini akan membuat 50 cabang pohon, dengan kedalaman maksimal 16. Hal ini memungkinkan Random Forest untuk membuat beberapa pohon keputusan dan menggabungkannya untuk memberikan prediksi yang lebih akurat dan handal.


- **Algoritma Boosting** bertujuan untuk meningkatkan performa atau akurasi prediksi dengan cara menggabungkan beberapa model sederhana yang dianggap lemah (weak learners), sehingga membentuk satu model yang kuat (strong ensemble learner). Algoritma boosting muncul dari gagasan bahwa model-model sederhana seperti linear regression dan decision tree dapat dimodifikasi dan digabungkan untuk meningkatkan kinerja prediksi secara signifikan.
```sh
boosting = AdaBoostRegressor(learning_rate=0.05, random_state=55)
```
Pada implementasi ini, digunakan parameter learning_rate dengan nilai 0.05. Model akan dilatih dengan nilai ini untuk menentukan seberapa besar penyesuaian yang dilakukan pada setiap iterasi. Selain itu, digunakan parameter random_state dengan nilai 55 untuk memastikan reprodusibilitas hasil yang konsisten.

Tabel 1. Nilai *Train* dan *Test* dari KNN, RF, dan Boosting
** | **train** | **test**|
:-----:|:-----:|:-----:|
**KNN** | 30064.576543 | 39220.122427|
**RF** | 3791.412142 | 22034.478805 |
**Boosting** | 21482.520677 | 22608.716112|

Karena Mean Squared Error (MSE) pada model Random Forest (RF) lebih rendah dibandingkan dengan model K-Nearest Neighbors (KNN) dan Boosting, maka kita akan menggunakan model RF untuk prediksi biaya pengobatan di rumah sakit. Model RF memberikan hasil yang lebih akurat dan andal berdasarkan evaluasi kinerja yang dilakukan.

## Evaluasi
Matriks evaluasi yang akan digunakan adalah Mean Squared Error (MSE) dan R-squared (R²).

Mean Squared Error (MSE): MSE menghitung jumlah selisih kuadrat rata-rata antara nilai sebenarnya dan nilai prediksi. MSE didefinisikan dalam persamaan berikut:
![mse](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/rumus%20mse.png)
Gambar 9. MSE

Berdasarkan hasil evaluasi menggunakan matriks Mean Squared Error (MSE), dapat disimpulkan bahwa model Random Forest memiliki MSE yang lebih kecil dibandingkan dengan model K-Nearest Neighbors (KNN) dan Boosting. Hal ini menunjukkan bahwa model Random Forest memberikan prediksi yang lebih akurat dalam memprediksi biaya pengobatan di rumah sakit.

Tabel 2. Nilai *Train* dan *Test* dari KNN, RF, dan Boosting
** | **train** | **test**|
:-----:|:-----:|:-----:|
**KNN** | 30064.576543 | 39220.122427|
**RF** | 3791.412142 | 22034.478805 |
**Boosting** | 21482.520677 | 22608.716112|

![grafik mse](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/mse.png)
Gambar 10. Grafik MSE

R-squared (R²) merupakan angka yang berkisar antara 0 sampai 1, yang menunjukkan seberapa besar kombinasi variabel independen secara bersama-sama mempengaruhi nilai variabel dependen. Nilai R² yang lebih tinggi menunjukkan bahwa model mampu menjelaskan sebagian besar variasi dalam data, sementara nilai R² yang lebih rendah menunjukkan sebaliknya.

![r2](https://github.com/miftarzl/Predictive-Analysis-Machne-Learning-Terapan/blob/main/Image/r2.png)
Gambar 11. *R2 Squared*

Tabel 3. Nilai prediksi
** | y_true |	prediksi_KNN | prediksi_RF | prediksi_Boosting |
:-----:|:-----:|:-----:|:-----:|:-----:|
992 | 10118.42 | 12328.2 | 10616.4 | 13157.5 |

Dari tabel yang ada, dapat terlihat bahwa prediksi menggunakan model Random Forest lebih mendekati nilai aktual 
𝑦.

Nilai R-squared (R²) dari model Random Forest lebih besar dibandingkan dengan model K-Nearest Neighbors (KNN) dan Boosting, menunjukkan bahwa Random Forest sangat efektif dalam memprediksi nilai. Hal ini memperlihatkan kemampuan model Random Forest dalam menjelaskan variasi dalam data secara lebih akurat dan andal.
```sh
R2 score KNN :  0.7494154894917251
R2 score RF :  0.8592176988797552
R2 score Boosting :  0.7494154894917251
```
