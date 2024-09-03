---
title: "More questions"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: "<b>3.3</b>"
---

## More Question In Project `Hotel Booking App`

#### Question 1 : Tại sao trong setter của phương thứ `setNumberOfAdults` và `setNumberOfChildren` lại truyền `caculateTotolNumberOfGuests`
```java
 public void setNumberOfAdults(int numberOfAdults) {
        this.numberOfAdults = numberOfAdults;
        caculateTotolNumberOfGuests();
    }
    
    public void setNumberOfChildren(int numberOfChildren) {
        this.numberOfChildren = numberOfChildren;
        caculateTotolNumberOfGuests();
    }
```
##### giải thích :
 Khi Số Lượng Người Lớn Thay Đổi:
+ Phương thức setNumberOfAdults(int numberOfAdults) được gọi với giá trị mới.
+ Trong phương thức setter, numberOfAdults được cập nhật.
+ Gọi calculateTotalNumberOfGuests() để tính lại tổng số khách, bao gồm số người lớn mới cộng với số trẻ em hiện tại.

 Khi Số Lượng Trẻ Em Thay Đổi:
+ Phương thức setNumberOfChildren(int numberOfChildren) được gọi với giá trị mới.
+ Trong phương thức setter, numberOfChildren được cập nhật.
+ Gọi calculateTotalNumberOfGuests() để tính lại tổng số khách, bao gồm số trẻ em mới cộng với số người lớn hiện tại.

##### Ví dụ
```java 
  public static void main(String[] args) {
    // Tạo một đối tượng Booking
    Booking booking = new Booking();

    // Thiết lập số lượng người lớn và trẻ em
    booking.setNumberOfAdults(2); // Đặt số lượng người lớn là 2
    booking.setNumberOfChildren(3); // Đặt số lượng trẻ em là 3

    // In ra tổng số khách
    System.out.println("Total number of guests: " + booking.getTotalNumberOfGuests()); // Kết quả: 5

    // Thay đổi số lượng người lớn và trẻ em
    booking.setNumberOfAdults(3); // Thay đổi số lượng người lớn thành 3
    booking.setNumberOfChildren(4); // Thay đổi số lượng trẻ em thành 4

    // In ra tổng số khách sau khi thay đổi
    System.out.println("Updated total number of guests: " + booking.getTotalNumberOfGuests()); // Kết quả: 7
}
```
