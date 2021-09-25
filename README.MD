# Jarkom Modul 1
Nama Kelompok :  
1. Ian Felix Jonathan Simanjuntak  
2. Muhammad Zakky Ghufron  
3. Muhammad Naufal Imantyasto

## Nomor 1
### 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!  
Mengisi display filter dengan : ```http.host contains "ichimarumaru.tech"```  
<img src="Screenshot Praktikum Jarkom 1/no1 1.png">   
Setelah itu memilih salah satu paket dan melakukan follow tcp stream. Setelah itu kami menemukan bahwa server yang digunakan adalah nginx/1.18.0 (Ubuntu)   
<img src="Screenshot Praktikum Jarkom 1/no1 2.png">   
### 2. Temukan paket dari web-web yang menggunakan basic authentication method!  
Mengisi display filter dengan : ```http.authbasic```  
<img src="Screenshot Praktikum Jarkom 1/no2.png">   
### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!  
Mengisi display filter dengan : ```http.host contains "basic.ichimarumaru.tech"```  
<img src="Screenshot Praktikum Jarkom 1/no3 1.png">   
Setelah melihat pada bagian Authorization, kami menemukan sebuah credensial ```kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN ```
Menggunakan kredensial ini kami dapat masuk ke dalam website   
<img src="Screenshot Praktikum Jarkom 1/no3 2.png">   
### 4. Temukan paket mysql yang mengandung perintah query select!
Mengisi display filter dengan : ```mysql && frame contains "select"```  
<img src="Screenshot Praktikum Jarkom 1/no4.png">   
### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Mengisi display filter dengan : ```mysql && frame contains "INSERT"```  
<img src="Screenshot Praktikum Jarkom 1/no5 1.png">   
pada hasil filter kami menemukan satu buah data, setelah kami melihat pada request command query kami menemukan sebuah statement
```sql
INSERT INTO users (username,password) VALUES ("akakanomi",md5("pemisah4lautan"))
```
setelah mendapatkan username dan password, kami berhasil masuk kedalam website
<img src="Screenshot Praktikum Jarkom 1/no5 2.png">   
### 6. Cari username dan password ketika melakukan login ke FTP Server!
Mengisi display filter dengan : ```ftp.request.command == PASS || ftp.request.command == USER```   
Lalu kami menemukan data : USERNAME : secretuser | PASSWORD : aku.pengen.pw.aja   
<img src="Screenshot Praktikum Jarkom 1/no6.png">    
### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
Menggunakan display filter dengan : ```frame contains "Real.pdf"```  
<img src="Screenshot Praktikum Jarkom 1/no7 1.png">   
lalu kami melakukan follow tcp stream dan melakukan save as raw dan mendownload file tersebut
<img src="Screenshot Praktikum Jarkom 1/no7 2.png">   
Berikut isi dari file tersebut   
<img src="Screenshot Praktikum Jarkom 1/no7 3.png">   
### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
Menggunakan display filter dengan : ```ftp.request.command == RETR```
dan menemukan tidak ada paket yang didownload dari FTP server   
<img src="Screenshot Praktikum Jarkom 1/no8.png">   
### 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
Karna key “Indikasi penyimpanan” saya memasukkan ```ftp-data.command == "STOR secret.zip"```  
<img src="Screenshot Praktikum Jarkom 1/no9 1.png">
Melihat file data tersebut, kami menemukan secret.zip. Setelah itu kami melakukan follow tcp stream. Lalu mengganti tipe file ke RAW lalu di save as zip.   
<img src="Screenshot Praktikum Jarkom 1/no9 2.png">
Dan file tersebut rupanya membutuhkan password 
<img src="Screenshot Praktikum Jarkom 1/no9 3.png">
### 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
Menggunakan display filter dengan : ```ftp-data.command == "STOR history.txt"  ```   
<img src="Screenshot Praktikum Jarkom 1/no10 1.png">
dari data tersebut, bisa dilihat bahwa file tersebut dikunci dengan file bukanapaapa.txt. Lallu kami mencari file bukanapaapa.txt dengan perintah : ```ftp-data.command == "STOR bukanapaapa.txt"```   
<img src="Screenshot Praktikum Jarkom 1/no10 2.png">
setelah itu kami menemukan password yang digunakan adalah : Password : d1b1langbukanapaapajugagapercaya  
<img src="Screenshot Praktikum Jarkom 1/no10 3.png">
### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!\
menggunakan capture filter : ```src port 80```  
<img src="Screenshot Praktikum Jarkom 1/no11.png">
### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
Mengisi Capture Filter dengan : ```Port 21```   
<img src="Screenshot Praktikum Jarkom 1/no12 1.png">
<img src="Screenshot Praktikum Jarkom 1/no12 2.png">
### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
Mengisi Capture Filter dengan : ```tcp.port == 80```  
<img src="Screenshot Praktikum Jarkom 1/no13.png">
### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!  
Pertama kami mencari IP dari kemenag dengan perintah ```PING kemenag.go.id``` pada terminal. 
<img src="Screenshot Praktikum Jarkom 1/no14 1.png">
Setelah itu kami menemukan IP nya adalah 103.7.13.247. Lalu kami melakukan capture filter dengan perintah : ```dst host 103.7.13.247 ```
<img src="Screenshot Praktikum Jarkom 1/no14 2.png">
### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Mengisi capture filter dengan : ```rc host 192.168.100.7```
<img src="Screenshot Praktikum Jarkom 1/no15 1.png">
<img src="Screenshot Praktikum Jarkom 1/no14 2.png">

## Kendala yang dialami
- Tidak ada kendala dalam pengerjaan modul ini
