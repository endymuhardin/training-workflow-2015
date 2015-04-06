# Penggunaan Git sehari-hari #

## Istilah ##

* Working Folder : folder tempat file-file kita berada
* Staging Area : wilayah (virtual) untuk perubahan yang **akan** dicommit
* Commit Area / Local Repository : penyimpanan history di local
* Local Repository : database di local
* Remote Repository : database di server lain

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

## Melihat isi staging area ##

* Perintah : `git diff --staged`

## Melihat history perubahan

* Perintah : `git log`
* Opsi :

    * `--oneline` : menampilkan satu commit per baris (lebih ringkas)
    * `--graph` : menampilkan rantai perubahan

* Output :

    ```
    C:\Users\winvbox\Documents\blog-endy>git log --oneline --graph
    * 7dc4511 cara melihat staging area
    * f393673 penjelasan local repo
    * 60b0679 perintah git
    * db8d961 penjelasan staging area
    * 256111b commit pertama
    ```


# Mendaftarkan remote repository

* Command : ```git remote add <nama-remote> <url-remote>```
* Contoh : ```git remote add github https://github.com/endymuhardin/training-workflow-2015.git```

## Mengganti URL remote repository

* Command : ```git remote set-url <nama-remote> <url-baru>```
* Contoh : ```git remote set-url github git@github.com:endymuhardin/training-workflow-2015.git```

## Mengupload commit local ke remote 

* Command : ```git push <nama-remote> <branch-yang-mau-diupload>
* Contoh : ```git push github master```
