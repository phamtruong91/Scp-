Scp-
====
#Câu lệnh Scp trong linux

**SCP** là lệnh dùng để sao chép tập tin giữa các host trên mạng. Nó sử dụng ssh để truyền dữ liệu, cung cấp bảo mật tương tự ssh

###Cú pháp cơ bản

```
scp source_file_name username@destination_host:destination_folder
```
Copy file nguồn *source_file_name* đến thư mục đích *destination_folder* tại máy đích có ip là *destination_host* với tài khoản *username*


Sau đó các tập tin sẽ được sao chép và truy cập trên thư mục người nhận. Mặc định bạn không có quyền để ghi hoặc thực thi nó, tuy nhiên nếu muốn bạn có thể sử dụng lệnh dưới đây để có toàn quyền:

```
sudo chmod 777 source_file_name
```

###Cài đặt

```
sudo apt-get install -y openssh-server

```

###Các trường hợp

* Copy một file từ remotehost về localhost

```	
scp username@remotehost:file_name /some/local/directory
```
* Copy một file từ localhost lên remotehost:

```  
scp file_name username@remotehost:/some/remote/directory
```  
* Copy thư mục foo vào thư mục bar:

```  
scp -r foo username@remotehost:/some/remote/directory/bar
```  
* Copy nhiều file:

```
scp foo.txt bar.txt username@remotehost:/path/directory/
```

* Copy file từ remotehost1 sang remotehost2:

```
scp username@rh1.edu:/some/remote/directory/file_name username@rh2.edu:/some/remote/directory/
```

* Copy file "source_file_name" từ remote host đến localhost

```
scp your_username@remotehost:source_file_name /some/local/directory
```

###Cú pháp nâng cao

```
scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file] [-l limit] [-o ssh_option] [-P port]
    [-S program] [[user@]host1:]file1 ... [[user@]host2:]file2
```

####Các tham số

-v  :để hiển thị thông tin của quá trình truyền file với SCP:
Có thể sử dụng tham số **-v** để in ra thông tin debug. Những thông tin này có thể giúp người dùng kiểm tra, sửa lỗi kết nối, xác thực và giải quyết vấn đề.

```
scp -v Label.pdf mrarianto@202.x.x.x:.
```

-p  :Hiện thị thời gian dự kiến, tốc độ kết nối

```
scp -p Label.pdf mrarianto@202.x.x.x:.
```
-C  :Nén file trước khi truyền

Có thể thực hiện điều này với tham số **-C**. Nén file trước khi truyền sẽ giúp chuyển file nhanh hơn, đặc biệt với các file có dung lượng cao. Khi file đến đích sẽ tự động được giải nén để trở lại trạng thái ban đầu.

```	
scp -Cpv messages.log mrarianto@202.x.x.x:.
```

-c  :Lựa chọn mã khác để mã hóa cho file:

Ở chế độ mặc định SCP sử dụng mã AES-128 để mã hóa file. Ta có thể chọn loại mã hóa khác (3DES) như sau:

```
scp -c 3des Label.pdf mrarianto@202.x.x.x:.
```

Chú ý: **-C** và **-c**

-l  :Hạn chế băng thông sử dụng:
Thực hiện điều này với tham số **-l**. Đơn vị của băng thông đường truyền là kilobit/giây. Như vậy, muốn hạn chế đường truyền là 50KB/s (Kil0byte/giây) thì phải đặt: 50 x 8 = 400 (kb/s)

```
scp -l 400 Label.pdf mrarianto@202.x.x.x:.
```

-p  :Đặt cổng kết nối
Ở chế độ mặc định, SCP sử dụng cổng 22, ta có thể thay đổi cổng này với tham số **-P** như sau:

```	
scp -P 2249 Label.pdf mrarianto@202.x.x.x:.
```

Chú ý: **-P** chứ không phải **-p**

-r  :Copy tất cả file và thư mục trong thư mục chỉ định
Ta có thể dùng tham số **-r** để làm điều đó:
	scp -r documents mrarianto@202.x.x.x:.
	
Sau khi lệnh này chạy xong, ta sẽ tìm thấy thư mục *document* với toàn bộ file ở trong nó tại thư mục đích.

-q  :Tắt thông báo và đo lường trạng thái
Bình thường khi sử dụng SCP sẽ có những thông báo và đo lường mạng như băng thông, thời gian còn lại...<br>
Để tắt nó đi, ta sử dụng tham số **-q**

```
	scp -q Label.pdf mrarianto@202.x.x.x:.
```













	
	
	
	
	
	
	
	
	
	
	



