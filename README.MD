# Jarkom Modul 1
Nama Kelompok :  
1. Ian Felix Jonathan Simanjuntak  
2. Muhammad Zakky Ghufron  
3. Muhammad Naufal Imantyasto

## Nomor 1
### 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!  
Mengisi display filter dengan : ```http.host contains "ichimarumaru.tech"```  
Setelah itu memilih salah satu paket dan melakukan follow tcp stream. Setelah itu kami menemukan bahwa server yang digunakan adalah nginx/1.18.0 (Ubuntu)
### 2. Temukan paket dari web-web yang menggunakan basic authentication method!  
Mengisi display filter dengan : ```http.authbasic```  
### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!  
Mengisi display filter dengan : ```http.host contains "basic.ichimarumaru.tech"```  
Setelah melihat pada bagian Authorization, kami menemukan sebuah credensial ```kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN ```
Menggunakan kredensial ini kami dapat masuk ke dalam website
### 4. Temukan paket mysql yang mengandung perintah query select!
Mengisi display filter dengan : ```mysql && frame contains "select"```  
### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Mengisi display filter dengan : ```mysql && frame contains "INSERT"```  
pada hasil filter kami menemukan satu buah data, setelah kami melihat pada request command query kami menemukan sebuah statement
```sql
INSERT INTO users (username,password) VALUES ("akakanomi",md5("pemisah4lautan"))
```
### 6. Cari username dan password ketika melakukan login ke FTP Server!
### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
### 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
### 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!