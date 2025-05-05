# Laporan Proyek Machine Learning - Mifta Rizaldirahmat
## Domain Proyek
Setiap wilayah tentunya memiliki minimal satu pasien yang dirawat di rumah sakit. Namun, ada beberapa orang yang memilih untuk tidak pergi ke rumah sakit meskipun mereka sakit. Alasan mereka sangat bervariasi, mulai dari ketidakpercayaan terhadap dunia medis, lebih memilih beristirahat di rumah, hingga ketakutan terhadap biaya pengobatan yang tinggi. Oleh karena itu, diperlukan penelitian untuk memprediksi besaran biaya perawatan di rumah sakit. Proyek ini bertujuan untuk memperkirakan biaya yang harus dikeluarkan oleh masyarakat yang ingin berobat ke rumah sakit.

## Business Understanding

Orang-orang cenderung berpikir mereka perlu pergi ke rumah sakit ketika penyakitnya sudah menjadi sangat menyakitkan. Dengan meremehkan gejala yang mereka anggap biasa, penyakit tersebut semakin parah. Begitu pula dengan tagihan rumah sakit. Jika penyakitnya masih tergolong ringan, biayanya lebih murah dibandingkan dengan biaya untuk penyakit yang sudah parah.

Situasi ini menciptakan tantangan bagi pasien maupun rumah sakit dalam hal pengambilan keputusan, perencanaan keuangan, dan pelayanan kesehatan secara efisien. Oleh karena itu, diperlukan sistem yang mampu memberikan estimasi biaya pengobatan secara akurat berdasarkan data pasien. Dengan adanya prediksi ini, pasien dapat lebih sadar akan pentingnya penanganan medis sejak dini dan rumah sakit dapat meningkatkan efisiensi manajemen pelayanan.


## Problem Statements

Berdasarkan pemahaman terhadap masalah bisnis di atas, berikut adalah pernyataan masalah utama yang ingin diselesaikan:

1. **Bagaimana cara memprediksi biaya pengobatan di rumah sakit secara akurat?**  
   Prediksi yang tepat dapat membantu pasien dalam merencanakan biaya serta mendorong tindakan medis lebih awal, sekaligus membantu rumah sakit mengelola sumber daya dan pelayanan secara optimal.


## Goals

Menjelaskan tujuan yang ingin dicapai dari permasalahan yang telah dirumuskan:

1. **Membangun model prediksi biaya pengobatan di rumah sakit** dengan memanfaatkan data historis pasien, yang dapat digunakan untuk memperkirakan kisaran biaya berdasarkan karakteristik pasien.  
2. **Mendukung pengambilan keputusan medis dan keuangan** bagi pasien maupun penyedia layanan kesehatan melalui informasi prediksi biaya yang lebih transparan dan terukur.


## Solution Statements

Untuk mencapai tujuan tersebut, berikut adalah solusi yang direncanakan:

1. **Exploratory Data Analysis (EDA):**  
   - Melakukan analisis data untuk memahami pola umum, distribusi variabel, hubungan antar fitur, serta mendeteksi outlier atau anomali yang dapat memengaruhi hasil prediksi.

2. **Pengembangan Model Machine Learning:**  
   - Menggunakan beberapa algoritma machine learning untuk membandingkan performa dan memilih model terbaik:
     - **K-Nearest Neighbors (KNN):** Mengelompokkan data berdasarkan kemiripan dengan pasien lain untuk memprediksi biaya.
     - **Random Forest (RF):** Menggunakan kumpulan pohon keputusan untuk meningkatkan stabilitas dan akurasi prediksi.
     - **Boosting Algorithm (seperti XGBoost):** Menggabungkan model-model sederhana secara iteratif untuk menghasilkan prediksi yang lebih akurat.

3. **Evaluasi Model dengan Metrik Regresi:**  
   - Mengukur kinerja model menggunakan metrik seperti **Mean Absolute Error (MAE)**, **Root Mean Squared Error (RMSE)**, dan **R² Score**.
   - Melakukan **cross-validation** dan **hyperparameter tuning** untuk mengoptimalkan performa model dan mencegah overfitting.


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

![grafik sex](https://github.com/user-attachments/assets/30a25ed2-df79-4c1c-bcbe-448e2992c1b7)
Gambar 1. Grafik Sex


- Grafik smoker, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset adalah non-perokok. Informasi ini dapat memberikan wawasan lebih lanjut tentang distribusi kebiasaan merokok di antara pasien yang dianalisis.
![Grafik Smoker](https://github.com/user-attachments/assets/cf670df7-cfa0-4744-8056-a3637ece14b1)
Gambar 2. Grafik Smoker


- Grafik region, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset berasal dari wilayah Southeast. Informasi ini memberikan gambaran mengenai distribusi regional pasien yang dianalisis, yang dapat digunakan untuk memahami lebih lanjut pola kesehatan dan demografi di wilayah tersebut.
![grafik region](https://github.com/user-attachments/assets/f4d60246-e304-49aa-91ad-bbdce796dd38)
Gambar 3. Grafik Region

### EDA-Multivariate
Berikut merupakan *EDA-Multivariate Analysis*:
- Grafik rata-rata expenses relatif terhadap sex, grafik di bawah ini menunjukkan bahwa rata-rata biaya medis relatif terhadap jenis kelamin didominasi
 oleh pasien laki-laki. Informasi ini memberikan gambaran mengenai perbedaan pengeluaran medis berdasarkan jenis kelamin dalam dataset yang dianalisis.
![multivariate sex](https://github.com/user-attachments/assets/ea6de072-c9af-475a-acb2-2d18d27ebed5)
Gambar 4. Grafik Rata-rata Expenses Relatif Terhadap Sex

- Grafik rata-rata expenses relatif terhadap smoker, grafik di bawah ini menunjukkan bahwa rata-rata biaya medis yang dikeluarkan lebih tinggi bagi pasien yang merokok dibandingkan dengan pasien yang tidak merokok. Informasi ini memberikan gambaran mengenai dampak kebiasaan merokok terhadap pengeluaran medis, yang tentunya penting untuk memahami faktor-faktor yang mempengaruhi biaya pengobatan.
![multivariate smoker](https://github.com/user-attachments/assets/92632201-f9a9-4544-95ec-a4bc2295e7b3)
Gambar 5. Grafik Rata-rata Expenses Relatif Terhadap Smoker

- Grafik rata-rata expenses relatif terhadap region, grafik di bawah ini menunjukkan bahwa mayoritas pasien dalam dataset berasal dari wilayah Southeast dan rata-rata biaya medis relatif terhadap region tersebut. Informasi ini memberikan gambaran mengenai distribusi regional pasien serta biaya pengobatan yang mungkin terkait dengan wilayah mereka.
![multivariate region](https://github.com/user-attachments/assets/89c50326-19a0-4f37-8458-cd66e8dfda43)
Gambar 6. Grafik Rata-rata Expenses Relatif Terhadap Region

Berdasarkan analisis dari ketiga grafik tersebut, dapat disimpulkan bahwa biaya pengobatan di rumah sakit cenderung lebih tinggi bagi pasien yang merokok dibandingkan dengan pasien yang tidak merokok. Hal ini menunjukkan bahwa kebiasaan merokok memiliki dampak signifikan terhadap biaya medis, yang kemungkinan besar disebabkan oleh berbagai masalah kesehatan yang terkait dengan merokok. Memahami pola ini dapat membantu dalam merencanakan biaya kesehatan dan mengedukasi masyarakat mengenai risiko kesehatan dan finansial akibat merokok.

#### Korelasi Matriks
Berdasarkan matriks dibawah, *Numerical Features* memiliki korelasi yang rendah terhadap expenses.
![korelasi fitur numerik](https://github.com/user-attachments/assets/b0276bfd-15d8-4987-ad39-9a081787a84c)
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
![korelasi matriks seluruh fitur](https://github.com/user-attachments/assets/11032f49-cb22-4574-beaa-62c8da5128d3)
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

## Evaluation

Dalam laporan ini, kita akan mengevaluasi dampak dari model yang telah dievaluasi terhadap **Business Understanding**. Evaluasi ini bertujuan untuk memastikan bahwa model yang telah dibangun mampu menjawab setiap pernyataan masalah (Problem Statement), mencapai tujuan (Goals), dan dampak dari solusi yang diimplementasikan dapat memenuhi harapan yang ditetapkan.

### 1. Apakah sudah menjawab setiap problem statement?

Problem Statement yang diajukan berkaitan dengan bagaimana memprediksi biaya pengobatan di rumah sakit secara akurat. Dalam proses evaluasi ini, kita menggunakan **Mean Squared Error (MSE)** dan **R-squared (R²)** untuk mengukur akurasi model yang telah dibangun, yakni **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting**. Berdasarkan hasil evaluasi:

- **MSE** menunjukkan bahwa **Random Forest** memiliki MSE yang lebih rendah dibandingkan dengan **KNN** dan **Boosting**, yang berarti **Random Forest** dapat memberikan prediksi biaya pengobatan yang lebih akurat.
- **R²** menunjukkan bahwa **Random Forest** juga memiliki nilai R² yang lebih tinggi, menunjukkan bahwa model ini dapat menjelaskan sebagian besar variasi dalam data dan memprediksi biaya pengobatan dengan lebih andal.

Dengan demikian, model yang dikembangkan telah menjawab **Problem Statement** terkait akurasi dalam memprediksi biaya pengobatan.

### 2. Apakah berhasil mencapai setiap goals yang diharapkan?

Tujuan dari proyek ini adalah untuk memahami dan memprediksi biaya pengobatan di rumah sakit. Berdasarkan evaluasi, model **Random Forest** berhasil mencapai tujuan ini dengan baik. **MSE** yang rendah dan **R²** yang tinggi menunjukkan bahwa model ini efektif dalam memprediksi biaya dengan akurasi yang lebih tinggi dibandingkan model lainnya.

Selain itu, **Exploratory Data Analysis (EDA)** yang dilakukan sebelumnya membantu dalam pemahaman data dan identifikasi pola yang mendalam, yang turut mendukung pembuatan model prediksi yang lebih akurat.

### 3. Apakah setiap solusi statement yang kamu rencanakan berdampak?

Solusi yang direncanakan dalam proyek ini meliputi proses **Exploratory Data Analysis (EDA)** untuk memahami data lebih dalam, serta penggunaan berbagai algoritma Machine Learning seperti **KNN**, **Random Forest**, dan **Boosting**. Evaluasi menunjukkan bahwa:

- **Random Forest** memberikan hasil terbaik dengan **MSE** yang lebih kecil dan **R²** yang lebih tinggi dibandingkan dengan model lainnya. Hal ini menunjukkan bahwa solusi yang diterapkan, terutama penggunaan **Random Forest**, berdampak signifikan dalam meningkatkan akurasi prediksi biaya pengobatan.
- Penggunaan **Boosting** dan **KNN** juga memberikan hasil yang cukup baik, namun tidak sebanding dengan **Random Forest** dalam hal akurasi prediksi, yang menunjukkan bahwa pemilihan algoritma yang tepat adalah kunci untuk mencapai hasil terbaik.

Dengan demikian, solusi yang diterapkan telah berdampak positif dalam mencapai tujuan yang diinginkan, yaitu memprediksi biaya pengobatan dengan akurat.

### 4. Tabel Evaluasi Model

**Tabel 2. Nilai *Train* dan *Test* dari KNN, RF, dan Boosting**

| Model        | Train MSE     | Test MSE      |
|--------------|---------------|---------------|
| **KNN**      | 30064.576543  | 39220.122427  |
| **RF**       | 3791.412142   | 22034.478805  |
| **Boosting** | 21482.520677  | 22608.716112  |

![mse](https://github.com/user-attachments/assets/f202d4cc-c85c-4291-88dc-727551d507f0)
Gambar 9. Grafik MSE


**Tabel 3. Nilai prediksi**

| ID  | y_true   | prediksi_KNN | prediksi_RF | prediksi_Boosting |
|-----|----------|--------------|-------------|-------------------|
| 992 | 10118.42 | 12328.2      | 10616.4     | 13157.5           |


![r2](https://github.com/user-attachments/assets/e20190f2-3e12-4d35-b07e-754a930ae93b)
Gambar 10. *R2 Squared*

**Nilai R² Model:**
```sh
R² score KNN       :  0.7494154894917251
R² score RF        :  0.8592176988797552
R² score Boosting  :  0.7494154894917251
