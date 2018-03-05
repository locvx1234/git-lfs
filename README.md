# git-lfs

Git Large File Storage là một extension cho Git dùng để làm việc với các file lớn.

Nội dung những file audio, video, DB, graphics được thay thế bằng file text trỏ tới vị trí lưu file trên LFS server. 


Cài đặt : 

Downloal gói cài đặt tại :

https://git-lfs.github.com/

Cài đặt lfs lần đầu trên mỗi môi trường : 

```
git lfs install 
```

Để đánh dấu những file lớn, ta dùng khái niệm `track`

Ví dụ, track những file `.gz`

```
git lfs track "*.gz"
git lfs track "*.jpg"
```
Liệt kệ các track 

```
git lfs track
```

Sau khi thực hiện lệnh này, nội dung file `.gitattributes` tự động cập nhật. Do đó, ta phải commit cả file này

```
git add .gitattributes
```

Thực hiện add các file khác và commit 

```
git add file.tar.gz 
git add text.txt 
git add cat.jpg

git commit -m "add files"
```

Liệt kê các file được track: 

```
git lfs ls-files
```

Push lên github như thông thường:

```
git push origin master
```

Nội dung file track sẽ có dạng:

```
➜  git-lfs git:(master) ✗ git ls-files -s cat.jpg
100644 d7fe8c80d1c1f25e8c1bd11911c219ff5fbeb7a5 0	cat.jpg
➜  git-lfs git:(master) ✗ git cat-file -p d7fe8c80d1c1f25e8c1bd11911c219ff5fbeb7a5
version https://git-lfs.github.com/spec/v1
oid sha256:4da39c7b77870039ac8152c03cdbb4d6dc77f04c1c167e19b2c36a2a1c00c87a
size 47687
```

Để clone repository mà không tải về các file track, trước khi thực hiện git clone như thông thường, ta cần:

```
export GIT_LFS_SKIP_SMUDGE=1
```



