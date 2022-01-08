<h1 align="center">Kiến thức cơ bản về hướng đối tượng</h1>

Ta đã biết về lập trình hướng đối tượng (OOP) là một hình mẫu lập trình tập trung vào việc sử dụng các đối tượng để xây dựng ứng dụng, trái ngược với lập trình hướng thủ tục được thiết kế bằng những khối lệnh để quản lý dữ liệu, OOP tổ chức chương trình và gom dữ liệu, hàm và các logic khác vào trong một "đối tượng" chứa.

Các khái niệm cơ bản trong OOP:

* **Objects**: đối tượng (object) biểu diễn một thực thể ở thế giới thực và là thành phần cơ bản của OOP. Ví dụ một trang bán hàng điện tử sẽ có các đối tượng như khách hàng, đơn hàng, sản phẩm,...
* **Class**: lớp (class) là bản mẫu của một đối tượng. Nó là bản mẫu với các định nghĩa các thuộc tính và phương thức cho đối tượng. Ví dụ, trang bán hàng điện tử, đối tượng khác hàng có thuộc tính như địa chỉ, thẻ tín dụng,.. và phương thức là thêm vào giỏ hàng, huỷ đơn,...

**Code mẫu về lớp và đối tượng**

**Lớp**

```python
class ShoppingCart(object):

    def __init__(self):
      self.total = 0
      self.items = {}

    def add_item(self, item_name, quantity, price):
        self.total += (quantity * price)
        self.items.update({item_name : quantity})


    def remove_item(self, item_name, quantity, price):
        self.total -= (quantity * price)
        if quantity > self.items[item_name]:
          del self.items[item_name]
        self.items[item_name] -= quantity


    def checkout(self, cash_paid):
        balance = 0
        if cash_paid < self.total:
          return "You paid {} but cart amount is {}".format(cash_paid, self.total)
        balance = cash_paid - self.total
        return "Exchange amount: {}".format(balance)
```

**Đối tượng**

```python
# Driver code
cart = ShoppingCart()

cart.add_item('A', 10, 50)
cart.add_item('B', 5, 20)

cart.remove_item('B', 1, 20)

cart_res = cart.checkout(600)

print('Total cart amount:', cart.total)
print('Cart items:', cart.items)

print(cart_res)
```

**Kết quả:**
```
Total cart amount: 580
Cart items: {'B': 4, 'A': 10}
Exchange amount: 20
``` 

<p align="center">
    <img src="/media-files/oop-principles.svg" alt="OOP Principles">
</p>

Trong lập trình OOP có bốn tính chất là tính đóng gói, tính kế thừa, tính đa hình và tính trừu tượng.

1. **Tính đóng gói:** Đóng gói là phương thức liên kết dữ liệu với nhau và ẩn nó khỏi các truy cập từ bên ngoài. Sau khi đóng gói, mỗi đối tượng sẽ giữ được sự riêng tư cho các trạng thái, các đối tượng khác không thể truy cập trực tiếp đến trạng thái của nó, thay vào đó, chúng có thể truy cập gián tiếp qua các hàm công khai của đối tượng.

**Code**

```python
class Product:
    def __init__(self):
        self.__maxprice = 900
    
    def sell(self):
        print("Selling Price: {}".format(self.__maxprice))

    def set_max_price(self, price):
        self.__maxprice = price

product = Product()
product.sell()

# change the price
product.__maxprice = 1000
product.sell()

# using setter function
product.set_max_price(1000)
product.sell()
```

**Kết quả:**
```
Selling Price: 900
Selling Price: 900
Selling Price: 1000
```

2. **Tính trừu tượng** Tính trừu tượng có thể hiểu là mở rộng tự nhiên của tính đa hình. Có nghĩa là nó ẩn tất cả những dữ liệu có liên quan đến một đối tượng theo thứ tự để giảm độ phức tạp cho hệ thống. Ở những hệ thống lớn, các đối tượng tương tác với nhau, làm cho việc bảo trì rất khó khăn. Tính trừu tượng giúp ẩn các chi tiết triển khai nội bộ của đối tượng và chỉ cung cấp các tính năng có liên quan đến các đối tượng khác.

**Code :**

```python
from abc import ABC, abstractmethod

class Parent(ABC):
  def common(self):
    print('In common method of Parent')

  @abstractmethod
  def vary(self):
    pass

class Child1(Parent):
  def vary(self):
    print('In vary method of Child1')

class Child2(Parent):
  def vary(self):
    print('In vary method of Child2')

# object of Child1 class
child1 = Child1()
child1.common()
child1.vary()

# object of Child2 class
child2 = Child2()
child2.common()
child2.vary()
```


**Kết quả:**
```
In common method of Parent
In vary method of Child1
In common method of Parent
In vary method of Child2
```

3. **Tính kế thừa**: là tính năng tạo ra một lớp mới dựa trên đối tượng đã có.


**Code :**

```python
class Person(object): 

    def __init__(self, name):
        self.name = name

    def get_name(self):
        return self.name

    def is_employee(self):
        return False
   

class Employee(Person):

    def is_employee(self): 
        return True
   
# Driver code
emp = Person("Person 1")
print("{} is employee: {}".format(emp.get_name(), emp.is_employee()))

emp = Employee("Employee 1")
print("{} is employee: {}".format(emp.get_name(), emp.is_employee()))
```


**Kết quả:**
```
Person 1 is employee: False
Employee 1 is employee: True
```

4. **Tính đa hình**: là khả năng một đối tượng có thể có nhiều biểu diễn khác nhau, phụ thuộc vào ngữ cảnh mà phản hồi cùng một thông điệp theo nhiều cách. Ví dụ như ở cờ vua, các con cờ có nhiều loại, quân hậu, mã hay xe sẽ phản hồi thông điệp "move" khác nhau.

**Code :**

```python
class Bishops:

    def move(self):
        print("Bishops can move diagonally")

class Knights:

    def move(self):
        print("Knights can move two squares vertically and one square horizontally, or two squares horizontally and one square vertically")

# common interface
def move_test(chess_piece):
    chess_piece.move()
# Driver code

#instantiate objects
bishop = Bishops()
knight = Knights()

# passing the object
move_test(bishop)
move_test(knight)
```


**Kết quả:**
```
Bishops can move diagonally
Knights can move two squares vertically and one square horizontally, or two squares horizontally and one square vertically
```