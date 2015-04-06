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


## Mendaftarkan remote repository

* Command : ```git remote add <nama-remote> <url-remote>```
* Contoh : ```git remote add github https://github.com/endymuhardin/training-workflow-2015.git```

## Mengganti URL remote repository

* Command : ```git remote set-url <nama-remote> <url-baru>```
* Contoh : ```git remote set-url github git@github.com:endymuhardin/training-workflow-2015.git```

## Mengupload commit local ke remote 

* Command : ```git push <nama-remote> <branch-yang-mau-diupload>```
* Contoh : ```git push github master```
* Output :

    ```
    Counting objects: 5, done.
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 582 bytes | 0 bytes/s, done.
    Total 3 (delta 1), reused 0 (delta 0)
    To git@github.com:endymuhardin/training-workflow-2015.git
       f42d98e..0bec9fc  master -> master
    ```

# Undo #

Berbagai skenario undo:

* Sudah commit, mau commit ulang (misalnya ganti commit message) tanpa mengubah changeset

    `git reset --soft HEAD~1`

* Sudah commit, mau commit ulang dengan changeset yang berbeda

    `git reset --mixed HEAD~1` atau `git reset HEAD~1`

* Sudah commit, mau kembalikan ke kondisi commit sebelumnya

    `git reset --hard HEAD~1`


# Branch dan Merge

## Membuat branch

* Command : `git branch <nama-branch>`
* Contoh : `git branch fix125`


## Pindah branch

* Command : `git checkout <nama-branch>`
* Contoh : `git checkout fix125`


## Ambil commit dari upstream

* Command : 

    * Satu upstream saja : `git fetch <nama-upstream>`
    * Semua upstream : `git fetch --all`


## Merge commit dari upstream ke master di local

1. Pindah dulu ke master

    ```git checkout master```

2. Fetch upstream

    ```git fetch upstream```

3. Merge upstream ke master lokal

    ```git merge upstream/master```

4. Push ke remote kita

    ```git push origin master```

## Merge commit dari remote branch

Ini digunakan bila tidak mau mendaftarkan remote dulu, tapi langsung merge

* Remote repo url : `git@github.com:mkdika/blog.git`
* Remote branch : `tambahan`

1. Buat dulu branch untuk integrasi

    ```
    git branch integrasi-maikel
    git checkout integrasi-maikel
    ```

2. Pull dari remote repo

    ```
    git pull git@github.com:mkdika/blog.git tambahan
    ```

3. Review dan fix bila perlu
4. Merge ke master

    ```
    git checkout master
    git merge integrasi-maikel
    ```

5. Push master yang sudah merged

    ```git push origin master```

6. Hapus branch integrasi yang sudah selesai

    ```git branch -d integrasi-maikel```