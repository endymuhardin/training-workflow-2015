# Penggunaan Git sehari-hari #

## Istilah ##

* Working Folder : folder tempat file-file kita berada
* Staging Area : wilayah (virtual) untuk perubahan yang **akan** dicommit
* Commit Area / Local Repository : penyimpanan history di local
* Local Repository : database di local

## Membuat Repository Baru di Local ##

* Perintah : `git init <nama-folder>`
* Contoh : `git init blog-endy`
* Hasil : membuat folder baru dengan nama `blog-endy` di lokasi tempat command dijalankan.

## Melihat perbedaan dengan versi sebelumnya ##

* Perintah : `git diff`
* Contoh : `git diff`
* Output : 

    ```
    C:\Users\winvbox\Documents\blog-endy>git diff
    diff --git a/tutorial-git.md b/tutorial-git.md
    index 1a0769e..b5662de 100644
    --- a/tutorial-git.md
    +++ b/tutorial-git.md
    @@ -13,3 +13,6 @@
     * Contoh : `git init blog-endy`
     * Hasil : membuat folder baru dengan nama `blog-endy` di lokasi tempat command
    +## Melihat perbedaan dengan versi sebelumnya ##
    +
    +* Perintah : `git diff`
    \ No newline at end of file
    ```
