# Nintendo Switch Softmod CFW Setup (Atmosphere dan/atau SX OS)
## Created by ChaotiCipher

## Pre Caution
```
- Do it with your own risk!!!
- Mohon agar dokumen ini dapat digunakan dengan bijak
- Apabila terdapat update Firmware Nintendo jangan serta merta langsung didownload!!!
- Apabila terdapat rilis Atmosphere juga jangan serta merta langsung didownload!!! Tunggu hingga Sigpatches keluar dari GBATemp atau GitHub eXhumer
- Dokumen ini dibuat dengan seluruh komponen terbaru per tanggal 7 Oktober 2020, dokumen akan saya perbarui jika dan hanya jika saya senggang dan punya cukup niat
- NSW Firmware Version 10.2.0
- Atmosphere Firmware Version 0.14.4
- Latest Sigpatches dari GitHub eXhumer https://github.com/eXhumer/patches
- Latest Hekate https://github.com/CTCaer/hekate/releases
- Latest HBGShop Tinfoil
```

## Tools Needed
```
- Windows 10 PC/Laptop
- TegraRCM GUI https://github.com/eliboa/TegraRcmGUI/releases
- USB-C to USB-A Cable
- PC/Laptop bisa diganti dengan HP Android atau Dongle RCM Injector kalau punya
- RCM Jig (nanti bisa tidak digunakan apabila sudah mengaktifkan AutoRCM, tidak direkomendasikan karena AutoRCM cukup menguras baterai NSW meskipun keadaan Power Off)
- MicroSD Card Minimum 64 GB untuk backup NAND dan create emuNAND/emuMMC
```

## Pre Requisite Setup
```
1. Cek serial number support softmod atau tidak (NSW first gen only (2017 - Juli 2018)), dapat menggunakan https://damota.me/ssnc/checker/ atau https://ismyswitchpatched.com
2. Aktifkan Airplane Mode di NSW OFW mode, kemudian Power Off (bukan Sleep Mode!!)
3. Format MicroSD Card dengan FAT32 (jangan exFAT karena nanti akan problem)
```

## Create Backup NAND/eMMC
```
Tujuannya untuk jaga-jaga apabila terjadi hal tidak diinginkan di kemudian hari, kita punya Backup Firmware NSW sebelum di CFW
```
```
1. Download latest Hekate melalui https://github.com/CTCaer/hekate/releases
2. Ekstrak hekate_ctcaer_X.X.X_Nyx_X.X.X.zip kemudian copy direktori "bootloader" ke root direktori MicroSD Card
3. Masukkan MicroSD Card kembali ke NSW
4. Buka aplikasi TegraRCM GUI (dapat didownload melalui https://github.com/eliboa/TegraRcmGUI/releases)
5. Nyalakan NSW ke mode RCM dengan langkah berikut:
   - Lepas joycon kanan, kemudian masukkan RCM Jig
   - Tekan tombol volume up dan power bersamaan selama kurang lebih 3 detik
6. Colokkan kabel USB ke PC/laptop yang digunakan untuk menjalankan TegraRCM GUI
7. Inject payload hekate_X.X.X.bin ke NSW
8. Setelah boot ke hekate, pilih "Tools" -> "Backup eMMC" -> "eMMC BOOT 0 & BOOT 1" (proses memakan waktu 1-2 menit), seteleh selesai pilih "Close"
9. Pilih "eMMC RAW GPP" (proses memakan waktu 40-90 menit tergantung kualitas MicroSD Card), seteleh selesai pilih "Close"
10. Power Off NSW -> masukkan MicroSD Card ke PC/laptop -> pindahkan direktori "backup" ke HD PC/Laptop -> kompres dengan ZIP atau TAR
```

## Create emuNAND/emuMMC
```
Tujuannya agar CFW tidak berjalan di sysNAND (memori internal NSW), CFW akan kita jalankan secara virtual dengan emuNAND dari MicroSD sehingga memori internal NSW tetap bersih
```
```
1. Jalankan langkah 3-7 di step "Create Backup NAND/eMMC"
2. Setelah boot ke hekate, pilih "Tools" -> "Archive bit * AutoRCM * Touch Tuning" -> "Partition SD Card" -> akan muncul tampilan "Your SD Card files will be backed up automatically!"
3. Drag "emuMMC (RAW)" menjadi 29 GB -> pilih "Next Step" -> "Start", setelah selesai pilih "OK" -> "Close"
4. Pilih "Home" -> "emuMMC" -> "Create emuMMC" -> "SD Partition" -> "Part 1" (proses memakan waktu 10-30 menit), seteleh selesai pilih "Close"
5. Verifikasi emuMMC berhasil dibuat dengan melihat tanda "Enabled!" di halaman "emuMMC Manage"
```

## Setup Atmosphere + Sigpatches + Incognito
```
- Sigpatches diperlukan untuk menjalankan aplikasi Homebrew seperti HBGShop/Tinfoil
- Incognito bertujuan agar NSW CFW aman digunakan untuk download game secara online melalui HBGShop/Tinfoil dan mengurangi resiko banned konsol
- Serial Number menjadi tidak terlihat/blank sehingga konsol tidak akan dapat terkoneksi ke server Nintendo (OTA Firmware Update, akses eShop, dsb)
```
```
1. Pastikan langkah "Create Backup NAND/eMMC" dan "Create emuNAND/emuMMC" telah dijalankan dengan benar
2. Download latest Atmosphere melalui https://github.com/Atmosphere-NX/Atmosphere/releases, ekstrak file atmosphere-X.X.X-master-XXXXXXXX+hbmenu-X.X.X.zip kemudian copy isinya ke root direktori MicroSD Card
3. Download latest Sigpatches melalui https://github.com/eXhumer/patches, ekstrak file sigpatches.zip kemudian copy direktori "atmosphere" ke root direktori MicroSD Card (merge / copy and replace)
4. Download exosphere.ini melalui https://raw.githubusercontent.com/Atmosphere-NX/Atmosphere/master/config_templates/exosphere.ini
5. Edit file exosphere.ini -> blank_prodinfo_emummc=0 menjadi blank_prodinfo_emummc=1

# Key: debugmode, default: 1.
#  Desc: Controls whether kernel is debug mode.
#   Disabling this may break Atmosphere's debugger in a future release.

# Key: debugmode_user, default: 0.
#  Desc: Controls whether userland is debug mode.

# Key: disable_user_exception_handlers, default: 0.
#  Desc: Controls whether user exception handlers are executed on error.
#  NOTE: This will cause atmosphere to not fail gracefully.
#   Support may not be provided to users tho disable these.
#   If you do not know what you are doing, leave them on.

# Key: enable_user_pmu_access, default: 0.
#  Desc: Controls whether userland has access to the PMU registers.
#  NOTE: It is unknown what effects this has on official code.

# Key: blank_prodinfo_sysmmc, default: 0.
#  Desc: Controls whether PRODINFO should be blanked in sysmmc.
#   This will cause the system to see dummied out keys and
#   serial number information.
#  NOTE: This is not known to be safe, as data may be
#   cached elsewhere in the system. Usage is not encouraged.

# Key: blank_prodinfo_emummc, default: 0.
#  Desc: Controls whether PRODINFO should be blanked in emummc.
#  NOTE: This is not known to be safe, as data may be
#   cached elsewhere in the system. Usage is not encouraged.

# Key: allow_writing_to_cal_sysmmc, default: 0.
#  Desc: Controls whether PRODINFO can be written by homebrew in sysmmc.
#  NOTE: Usage of this setting is strongly discouraged without
#    a safe backup elsewhere. Turning this on will also cause Atmosphere
#    to ensure a safe backup of calibration data is stored in unused
#    mmc space, encrypted to prevent detection. This backup can be used
#    to prevent unrecoverable edits in emergencies.

[exosphere]
debugmode=1
debugmode_user=0
disable_user_exception_handlers=0
enable_user_pmu_access=0
blank_prodinfo_sysmmc=0
blank_prodinfo_emummc=1
allow_writing_to_cal_sysmmc=0

6. Simpan file exosphere.ini, kemudian copy ke root direktori MicroSD Card
7. Masukkan MicroSD Card kembali ke NSW
8. Buka aplikasi TegraRCM GUI
9. Nyalakan NSW ke mode RCM, kemudian colokkan kabel USB ke PC/laptop yang digunakan untuk menjalankan TegraRCM GUI
10. Inject payload fusee-primary.bin ke NSW
11. Verifikasi Atmosphere telah berjalan melalui "Settings -> System", akan muncul info "Current Version: X.X.X|AMS X.X.X|E"
12. Verifikasi Incognito telah aktif melalui "Settings -> System -> Serial Information", akan muncul info "XAW10000000000"
```

## Setup Booting Atmosphere via Hekate
```
Bertujuan agar bisa memilih mode boot melalui Hekate (dual OS seperti PC Windows dengan Linux)
```
```
1. Buat file hekate_ipl.ini dengan isi seperti di bawah, kemudian copy ke direktori "bootloader"

[config]
autoboot=0
autoboot_list=0
bootwait=3
backlight=100
autohosoff=0
autonogc=1
updater2p=0

[CFW (sysMMC)]
emummc_force_disable=1
fss0=atmosphere/fusee-secondary.bin
icon=bootloader/res/icon_payload.bmp

[CFW (emuMMC)]
emummcforce=1
payload=bootloader/payloads/fusee-primary.bin
icon=bootloader/res/icon_payload.bmp

[Stock]
emummc_force_disable=1
fss0=atmosphere/fusee-secondary.bin
icon=bootloader/res/icon_switch.bmp
stock=1

[Fusee]
icon=bootloader/res/icon_payload.bmp
payload=bootloader/payloads/fusee-primary.bin

2. Copy fusee-primary.bin ke direktori "/bootloader/payloads/"
3. Rename hekate_ctcaer_X.X.X.bin menjadi reboot_payload.bin, kemudian copy ke direktori "atmosphere"
4. Masukkan MicroSD Card kembali ke NSW
5. Buka aplikasi TegraRCM GUI
6. Nyalakan NSW ke mode RCM, kemudian colokkan kabel USB ke PC/laptop yang digunakan untuk menjalankan TegraRCM GUI
7. Inject payload hekate_ctcaer_X.X.X.bin ke NSW
8. Pilih "Launch" -> "CFW (emuMMC)"
```

## Setup HBGShop/Tinfoil by Homebrew Gang
```
Bertujuan agar bisa download game langsung dari HBGShop secara online. Kondisi saat ini HBGShop sudah ditutup kecuali kita donate dan mendapatkan akses ke HBG Drive. Alternatif lain adalah menggunakan JITS tetapi masih sedang maintenance juga.
```
```
1. Download latest HBGShop/Tinfoil melalui https://thehbg.shop/main.html
2. Ekstrak file zip nya, kemudian copy ke root direktori MicroSD Card
3. Buka album Homebrew kemudian instal Tinfoil (hanya dilakukan sekali ketika akan menggunakan Tinfoil)
4. Edit DNS menjadi 8.8.8.8 dan 8.8.4.4 agar speed download meningkat
5. Tambahkan repository di HBGShop/Tinfoil
   - https://jits.cc

```

## Setup AIO Atmosphere Updater by JITS (JustInsertTheStuff)
```
Bertujuan untuk memudahkan update Atmosphere, Sigpatches dan Hekate ketika ada rilis baru
```
```
1. Download latest AIO updater melalui https://github.com/JackInTheShop/AIO-atmosphere-updater/releases
2. Copy file .nro ke direktori "/switch/AIO-atmosphere-updater/" di dalam MicroSD Card
```

## Setup RCM Loader
```
Setelah proses setup Atmosphere di atas selesai dilakukan, RCM loader dapat digunakan untuk menggantikan aplikasi TegraRCM GUI yang harus dijalankan menggunakan PC/Laptop Windows 10. Fungsi utamanya adalah sebagai alat untuk melakukan inject payload ke NSW tanpa PC/Laptop, sehingga lebih fleksibel dan mudah dibawa. Step setupnya dapat mengikuti video YouTube berikut : https://www.youtube.com/watch?v=G2nig_Sj2dw&list=WL&index=24
```

## Setup SX OS
```
Coming soon
```

## FAQ
```
1. Bagaimana mematikan NSW ketika dalam keadaan RCM mode?
   Tekan tombol power selama kurang lebih 10 detik kemudian tekan tombol power lagi seperti biasa untuk menyalakan NSW
2. Apa itu aplikasi Homebrew?
   Aplikasi yang dikembangkan oleh komunitas Homebrew untuk menjalankan software bajakan di NSW
3. Apa saja aplikasi Homebrew yang berguna?
   Ada banyak, 2 yang saya gunakan adalah Tinfoil dan AIO Atmosphere Updater
```

## Referensi Utama
```
https://birbchirp.gitbook.io/switchguide/
https://www.youtube.com/watch?v=G2nig_Sj2dw&list=WL&index=24
https://switch.homebrew.guide
https://www.sdsetup.com
https://www.kaskus.co.id/thread/5b6d0e09d9d77010608b4567/sharing-nintendo-switch---panduan-instalasi-cfw-to-play-xci-amp-nsp---sx-os-amp-hekate
https://thehbg.shop/main.html
https://jits.cc/aio
```
