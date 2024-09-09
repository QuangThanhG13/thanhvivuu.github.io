---
title: "Java Spring Boot backend (p2)"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: "<b>3.3</b>"
---

## UserRepository và UserControlller 
#### 1.Giải thích logic chưa hiểu. 
##### Trong api `creatUser`
Để convert tu User DTO sang User ta làm 
```java
       
        User newUser =countId(userDTO.getFacebookAccountId())
                .googleAccountId(userDTO.getGoogleAccountId())
                .build();
        //1 role thi se cos nhieu user bây giờ ta sẽ tại role cho user
        Role role = roleRepository.findById(userDTO.getRoleId())
                .orElseThrow(() -> new DataNotFoundException("Role not found: " + userDTO.getRoleId()));
        newUser.setRole(role);
```

##### Có 1 product có sẵn các thông tin ở trong và `muốn thêm ảnh vào`
```shell 
  

            List<MultipartFile> files = productDTO.getFiles();
            files = files == null ? new ArrayList<MultipartFile>() : files;
            for (MultipartFile file : files) {
                if (file.getSize() == 0) {
                    continue;
                }
                //Kiem tra kich thuoc file va dinh dang.
                if (file.getSize() > 10 * 1024 * 1024) { //kich thuoc file lon hon 10Mb
                    // throw new ResponseStatusException(HttpStatus.PAYLOAD_TOO_LARGE, "File is too large! Maximum size is 10Mb");
                    return ResponseEntity.status(HttpStatus.PAYLOAD_TOO_LARGE).body("File is too large! Maximum size is 10Mb");
                }
                String contentType = file.getContentType();
                if (contentType == null || !contentType.startsWith("image/")) {
                    return ResponseEntity.status(HttpStatus.UNSUPPORTED_MEDIA_TYPE).body("File must be an image");
                }
                //luu file vao thu muc
                String fileName = storeFile(file);
                //sau do luu vao doi tuong product trong db
                //luu vao bang product images
             ProductImage productImage = productService.createProductImage(newProduct.getId(),
                        ProductImageDTO.builder()
                                .imageUrl(fileName)
                                .build());

            }
```
##### 1. Tạo sản phẩm mới : 
```java
 Product newProduct =  productService.craetProduct(productDTO);
```
- tạo 1 newProduct trong đây nó đẫ chứa đầy thông tin 
##### 2. Xử lí các tệp tin 
```shell
List<MultipartFile> files = productDTO.getFiles();
files = files == null ? new ArrayList<MultipartFile>() : files;
```
> tương đương 
```shell 
if (files == null) {
    files = new ArrayList<MultipartFile>();
} else {
    files = files;
}

```
- Tiếp theo, đoạn code lấy danh sách các tệp tin (`MultipartFile`) từ `productDTO.`
- Nếu không có tệp tin nào tức là `file` là null, 

##### 3. Duyệt qua các tệp tin 
```shell
for (MultipartFile file : files) {
    if (file.getSize() == 0) {
        continue;
    }
}
```

##### 4. Kiểm tra kichs thước 
```shell
if (file.getSize() > 10 * 1024 * 1024) {
    return ResponseEntity.status(HttpStatus.PAYLOAD_TOO_LARGE).body("File is too large! Maximum size is 10Mb");
}

```
##### 5. Kiểm tra loại tệp tin 
```shell 
String contentType = file.getContentType();
if (contentType == null || !contentType.startsWith("image/")) {
    return ResponseEntity.status(HttpStatus.UNSUPPORTED_MEDIA_TYPE).body("File must be an image");
}
```
- `(content type)` được kiểm tra để đảm bảo rằng đó là tệp tin hình ảnh.

##### 6. Lưu trữ tệp tin:
```shell 
String fileName = storeFile(file);
```
-  Nó sẽ được lưu trữ vào một vị trí cụ thể bằng phương thức storeFile(file)
##### 7. Lưu thông tin hình ảnh vào cơ sở dữ liệu: 
```java
ProductImage productImage = productService.createProductImage(newProduct.getId(),
        ProductImageDTO.builder()
                .imageUrl(fileName)
                .build());
```
- `Buider pattern` : làm việc với đối tượng có nhiều thuộc tính phưucs tạp 




##### 2. Luồng chạy của 2 class và các `anotation` liên quan.
Luồng chạy : từ class Service ta có anotation `@RequiredArgsConstructor` `@Service` để : Khi bạn sử dụng `@Service` và `@RequiredArgsConstructor`, Spring sẽ tự động quản lý lớp `Service` này, và tất cả các `dependency` (như repository hoặc các service khác) sẽ được tự động tiêm vào thông qua constructor mà @RequiredArgsConstructor tạo ra.

Còn class Controller có `@RequiredArgsConstructor` : sẽ tạo ra constructor và cho phép Spring tự động tiêm các `dependency,`mà không cần `@Autowire` chẳng hạn như các service mà Controller sử dụng.


