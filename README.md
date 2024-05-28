# API Google Drive

## Konfigurasi Google Drive API Library Melalui Google Console
1. Buka [Google Console](https://console.cloud.google.com/)
2. Buat atau Pilih ke Project 
![halaman pertama google console](docs/google_console.png)
3. Masuk ke APIs & Services yang berada di quick access ataupun di sidebar
![Quick Access APIs & Services](docs/api_menu.png)
![Sidebar APIs & Services](docs/api_menu_sd.png)
4. Setelah Masuk ke menu APIs & Services, Pilih Library
![Sidebar APIs & Services](docs/sidebar.png)
5. Cari Google Drive API, pilih yang google drive API, pada gambar dibawah ini letaknya berada di paling bawah
![Google Drive API](docs/gd_lib.png)
6. kemudian klik enabled
![Google Drive API](docs/enabled.png)
7. jika sudah maka tampilan akan seperti ini 
![Google Drive API enabled](docs/gd_enabled.png)

## Mendapatkan CredentialsRaw Dari Google Console 
1. Pada halaman APIs & Services, masuk ke menu Credentials
![Google Drive API enabled](docs/gd_enabled.png)
![Sidebar APIs & Services](docs/sidebar.png)
2. Kemudian Tambahkan Credetial Baru 
![New Credential](docs/create_creds.png)
3. Pilih OAuth Client ID
![OAuth Client ID](docs/cred_conf.png)
4. Jika, Oauth Consent Screen Belum DI buat maka buat dulu Oauth Consent screen
5. setelah seselai membuat Oauth Consent Screen maka tampilan akan seperti berikut 
![Tampilan Oauth Consent Screen](docs/oauth_cs.png)
6. klik publish app, kemudian akan muncul popup, maka tekan confirm 
![publish app](docs/publish_app.png)
7. kemudian kembali ke halaman credential, dab buar credential baru, dengan tipe oauth client id 
![OAuth Client ID](docs/cred_conf.png)
8. aplication type web applicaton, name nya bebas, kemudian pada Authorized redirect URIs isi kan link [https://developers.google.com/oauthplayground](https://developers.google.com/oauthplayground) kemudian klik create
![OAuth Options](docs/oauth_page.png)
9. setelah berhasil, maka akan muncul popup seperti berikut 
![pop up success](docs/popup_success.png)
10. Klik download JSON, kemudian arahkan file download ke directory utama
![ss png](docs/ss_json.png)
11. buka file tersebut, lalu copy kan seua conten nya, dengan 
```
ctrl + a -> ctrl + c
```
12. kemudian pergi ke folder config/tokenConfig.go dan temukan variabel CREDENTIALRAW
```
var CREDENTIALRAW = []byte(`======>>DATA CREDENTIAL DARI GOOGLE CONSOLE OAUTH CLIENT ID<<======`)
```
13. pastekan value dengan posisi di dalam kurung 
```
var CREDENTIALRAW = []byte(`Value Json From FILE`)
```

## Mendapatkan Access Token dan Refresh Token Dari Google Console 
1. untuk pertama kali, maka kunjungi [google plygorund](https://developers.google.com/oauthplayground) klik setting yang disebelah kanan 
![gp setting](docs/gp_setting.png)
2. checklist pada pilihan Use your own OAuth credentials
![check User](docs/check_use.png)
3. isikan client_id dan client secret yang ada pada oauth google console, (APIs & Services -> credentials -> pada table oauth client id klik edit atau yang gambar pensil)
![oauth page lupa](docs/oauth_page_lupa.png)
4. pada step satu, pilih **Drive API v3**, kemudian klik dan checklist semua scope dibawahnya, kemudian klik authorize APIs
![checklist drive api v3](docs/step1_gp.png)
5. kemudian akan di arahkan ke halaman login, dan login dengan akun google yang di inginkan 
![Login Akun Google](docs/step1_gp_log.png)
6. jika terdapat warning maka klik lanjutkan 
![Login akun google](docs/warning.png)
7. kemudian pada step dua checklist **Auto-refresh the token before it expires.** kemudan klik Exchange Authorization code for tokens 
![step 2](docs/step2.png)
8. kemudian pilih token json yang berada di paling bawah, kemudian copy 
![tokens](docs/token.png)
9. pergi ke directory config/tokenConfig.go cari variable TOKENRAW
```
var TOKENRAW = []byte(`=====>>DATA API TOKEN DARI GOOGLE PLAYGROUND<<=====`)
```
10. paste kan value di didalam kurung 
``` 
var TOKENRAW = []byte(`paste jason token disini`)
```
**NOTE**:
 - ketikan melakukan paste jangna menghilangkan `` (tanda petik nya)


## Install Local Machine
1. extract file -> buka terminal di directory api_google_drive
2. jalankan perintah 
```
go mod tidy
```
3. tunggu intalasi selesai
4. setelah instalasi selesai, jalankan perintah 
```
go run main.go
```

## Install Dengan Docker-Compose
1. extract file -> buka terminal di directory api_google_drive
2. jalankan perintah 
```
docker build -t nama_image:nama_tag .
```
3. setelah selesai, jalankan perintah 
```
docker-compose up -d
```

