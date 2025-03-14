Nama    : Akhyar Rasyid Asy syifa

NPM     : 2306241682

Kelas    : Advance programming - A

# Module 5 - Java Profiling

> **1. What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?**

<p align="justify">
JMeter terutama digunakan untuk menguji performa sistem dengan mensimulasikan banyak pengguna dan mengukur responsnya di bawah tekanan. Alat ini membantu mendeteksi masalah seperti latensi, throughput, dan penggunaan sumber daya saat beban tinggi. Sementara itu, IntelliJ Profiler bedanya berfokus pada analisis internal aplikasi, termasuk penggunaan CPU, alokasi memori, dan waktu eksekusi metode. JMeter memberikan gambaran menyeluruh tentang kinerja sistem, sedangkan IntelliJ Profiler lebih mendalam dalam mengidentifikasi hambatan pada level kode.
</p>
<br>

> **2. How does the profiling process help you in identifying and understanding the weak points in your application?**

<p align="justify">
Profiling dapat membantu saya dalam menemukan metode yang berjalan lambat dan menjadi beban bagi program. Profiler dapat mengukur waktu eksekusi setiap method/fungsi dalam sebuah aplikasi dan dapat menunjukkan metode mana yang berjalan paling lambat sehingga dapat dioptimisasi. Lalu profiler juga membantu saya dalam mendeteksi penggunaan memori karena profiler dapat melacak alokasi dan penggunaan memori dalam aplikasi sehingga mencegah aplikasi mengalami kebocoran memori.
</p>
<br>

> **3. Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?**

<p align="justify">
Ya, IntelliJ Profiler sangat membantu saya dalam mengidentifikasi bottleneck, karena dapat menemukan metode yang paling lama dieksekusi, mendeteksi kebocoran memori, menganalisis performa thread, serta mengoptimalkan penggunaan CPU agar aplikasi berjalan lebih lancar dan responsif.
</p>
<br>

> **4. What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?**

<p align="justify">
Karena baru kali ini saya melakukan performance testing dan profiling terutama di IntellliJ, saya belum terbiasa terhadap informasi-informasi yang diberikan pada profiler. Banyaknya informasi teknis seperti stack trace, alokasi memori, grafik CPU/Memori dan lain-lain membuat saya menjadi bingung terhadap sebenarnya hal apa yang menjadi beban bagi program. Untuk mengatasi hal ini, saya berusaha untuk mengamati data dengan cermat sehingga mendapat kesimpulan yang tepat.
</p>
<br>

> **5. What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?**

<p align="justify">
Dengan menggunakan IntelliJ Profiler, saya dapat menemukan bottleneck dan inefisiensi dalam kdoe saya secara cepat berdasarkan waktu method/fungsi saya bekerja. Selain itu saya juga dapat memantau alokasi memori secara real-time, dan memantau thread. Profiling di IntelliJ juga intuitif dan mudah digunakan karena terintegrasi dengan IntelliJ IDEA.
</p>
<br>

> **6. How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?**

<p align="justify">
Jika saya menemukan perbedaan, pertama-tama saya akan mengecek bahwa pengujian di IntelliJ Profiler dilakukan dengan kondisi yang sama seperti apa yang ada di JMeter, contohnya jumlah thread memastikan penggunaan aplikasi dalam beban yang sama. Jumlah thread atau jumlah pengguna yang berbeda di tiap profiler dapat menyebabkan perbedaan hasil testing. Selain itu route ke URL localhost juga harus dicek kembali di JMeter sehingga sama dan akurat terhadap apa yang ingin dites.
</p>
<br>

> **7. What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?**

<p align="justify">
Setelah menganalisis hasil dari pengujian performa dan profiling, saya meningkatkan efisiensi metode dengan mengurangi operasi yang redundan, seperti yang saya lakukan pada getAllStudentWithCourse, findStudentWithHighestGpa, dan joinStudentNames. Saya memastikan bahwa setiap pemanggilan metode hanya dilakukan ketika benar-benar diperlukan dan menghindari looping yang tidak efisien untuk mempercepat eksekusi.

Selain itu, saya juga mengoptimalkan strategi pengambilan data agar lebih efisien dengan memanfaatkan fitur yang disediakan oleh Spring Data JPA. Dalam StudentRepository, saya mengganti query manual dengan Spring Data JPA derived queries, yang memungkinkan framework secara otomatis menghasilkan query yang lebih optimal. Di sisi lain, dalam StudentController, saya merefaktor metode highestGpa() agar langsung mengembalikan objek Student daripada Optional<Student>. 

Kemudian cara saya untuk memastikan tidak ada yang berubah dari segi fungsional adalah saya mencoba menjalankan method2 tersebut dan mengecek hasilnya apakah sama dengan yang lama atau berbeda. Namun, best practice nya sebenarnya adalah dengan melakukan testing di sebelum dan juga sesudah optimization agar memastikan tidak ada fungsionalitas yang berubah sama sekali.
</p>


# JMeter GUI Test Plan Results (Before profiling)
 
 **1. `/all-students` endpoint:**
    <img width="1012" alt="Image" src="https://github.com/user-attachments/assets/dc8e69eb-5f35-448e-868c-d296ac4c4f19" />
 
 **2. `/all-student-name` endpoint:**
    <img width="1010" alt="Image" src="https://github.com/user-attachments/assets/dd23e899-f4dd-4891-b72f-d3b41eceb74e" />
 
 **3. `/highest-gpa` endpoint:**
    <img width="1010" alt="Image" src="https://github.com/user-attachments/assets/bbd557dc-c15d-4a01-bc55-4d550e11e674" />
 
 # JMeter CLI Test Plan Results (Before profiling)
 
 **1. `/all-students` endpoint:**
    <img width="983" alt="Image" src="https://github.com/user-attachments/assets/8ffc874d-5b1a-47aa-b68d-85e179ad54e7" />
 
 **2. `/all-student-name` endpoint:**
    <img width="989" alt="Image" src="https://github.com/user-attachments/assets/9d1f98a2-d6f4-4993-93fd-3b0acaaaaf6d" />
 
 **3. `/highest-gpa` endpoint:**
    <img width="986" alt="Image" src="https://github.com/user-attachments/assets/901da72b-42b4-49c9-b796-aeaa50ecf71e" />
 
 # JMeter GUI Test Plan Results (After profiling)
 
 **1. `/all-students` endpoint:**
    <img width="1009" alt="Image" src="https://github.com/user-attachments/assets/bb65d10e-2dde-4d71-ae6b-efa13f9e2575" />
 
 **2. `/all-student-name` endpoint:**
    <img width="1010" alt="Image" src="https://github.com/user-attachments/assets/cf0f1864-eee9-4525-92fa-b0bab7417ec1" />
 
 **3. `/highest-gpa` endpoint:**
    <img width="1013" alt="Image" src="https://github.com/user-attachments/assets/912c355c-f456-4cba-a9aa-648defa378b7" />
 
 # JMeter CLI Test Plan Results (After profiling)
 
 **1. `/all-students` endpoint:**
    <img width="993" alt="Image" src="https://github.com/user-attachments/assets/a74d93e0-aa73-47a9-8d4c-e81362344c01" />
 
 **2. `/all-student-name` endpoint:**
    <img width="987" alt="Image" src="https://github.com/user-attachments/assets/ab7f04a9-2439-4168-9896-4d45cc24b5ea" />
 
 **3. `/highest-gpa` endpoint:**
    <img width="988" alt="Image" src="https://github.com/user-attachments/assets/9962a400-a97b-45cb-ba29-4125922473c3" />
