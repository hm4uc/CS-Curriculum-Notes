# Phạm vi truy cập

| Phạm vi truy cập |Public | Protected| Default | Private
| -------- | -------- | -------- |-------| --------
| **Trong class**   | Có    | Có|Có| Có
| **Trong package**  | Có|Có    |Có|Không
|**Ngoài package bởi lớp con**| Có|Có|Không|Không
| **Ngoài package** | Có    | Không|Không  | Không
# Constructor

| Constructor | Phương thức |
| -------- | -------- | 
| Constructor được sử dụng để khởi tạo trạng thái của một đối tượng |Phương thức được sử dụng để trưng bày hành vi của một đối tượng
| Constructor phải **không có** kiểu trả về |Phương thức phải **có** kiểu trả về
| Constructor được triệu hồi một cách ngầm định |Phương thức phải được triệu hồi một cách tường minh
| Compiler cung cấp một Constructor mặc định nếu bạn không có bất cứ Constructor nào |Phương thức không được cung cấp bởi Compiler trong bất cứ trường hợp nào
| Tên Constructor phải giống tên lớp |Tên phương thức có thể hoặc không giống như tên lớp
- Constructor có thể thực hiện các tác vụ khác ngoài khởi tạo như những phương thức khác

# Từ khóa
## :pencil: new
- Cấp phát vùng nhớ động
- Được tạo trong bộ nhớ Heap
## :pencil: this
- Tham chiếu tường minh đến thuộc tính và phương thức đối tượng (hay gặp)
- Làm tham số
```
public class Example {
    void display(Example obj) {
        System.out.println("Hello Java");
    }
    void p() {
        display(this);
    }
 
    public static void main(String args[]) {
        Example o1 = new Example();
        o1.p();
    }
}
```
- Là giá trị trả về
```
class Date { 
     private int year, month, day; 
     
     public Date(int y, int m, int d) { ... } 
 
     Date(Date d) { 
         this(d.year, d.month, d.day); 
         System.out.println("copy constructor called"); 
     }
}
 ```
## :pencil: super
- Tham chiếu trực tiếp đến đối tượng của lớp cha *gần nhất*
    - Tham chiếu trực tiếp đến biến instance của lớp cha
    ```
    class Vehicle {
        int x = 50;
    }
    
    public class Bike extends Vehicle {
        int x = 100;
        
        void display() {
            System.out.println(super.x); //In x của lớp Vehicle
        }
    }
    ```
    - super(): gọi Constructor của lớp cha, có thể có tham số (hay gặp)
    - Gọi trực tiếp phương thức của lớp cha
## :pencil: static
- Tiết kiệm bộ nhớ
- Không thể ghi đè phương thức static

Ví dụ: Ta tạo biến college là static, trường này sẽ chỉ sử dụng bộ nhớ một lần để lưu tên biến
```
public class Student {
    int id;
    String name;
    static String college = "UET";
 
    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
 
    void display() {
        System.out.println(rollno + " - " + name + " - " + college);
    }
 
    public static void main(String args[]) {
        Student s1 = new Student(111, "Thông");
        Student s2 = new Student(222, "Minh");
 
        s1.display();
        s2.display();
    }
}
```
Output:
```
111 - Thông - UET
222 - Minh - UET
```
- Hạn chế
    - Phương thức static không thể sử dụng thành viên dữ liệu non-static hoặc gọi trực tiếp phương thức non-static
    ```
    class A{  
         int a=40; //non static  

         public static void main(String args[]){  
              System.out.println(a); //Compile Time Error 
         }  
    } 
    ```
    - Từ khóa this và super không thể được sử dụng trong ngữ cảnh static
## :pencil: final
- Biến final: bạn không thể thay đổi giá trị của biến final (nó sẽ là hằng số)
- Phương thức final: bạn không thể ghi đè phương thức final
- Lớp final: bạn không thể kế thừa lớp final
- Biến static final trống: Một biến final mà không được khởi tạo tại thời điểm khai báo được gọi là biến final trống
```
static final int data;
```
## :pencil: instanceof
- Kiểm tra kiểu Wrapper (String, Integer, ...)
- Kiểm tra xem đối tượng có là instance của kiểu cụ thể: lớp hoặc lớp con hoặc interface hay không
- Nếu áp dụng toán tử instanceof với biến có giá trị null thì nó trả về false
- Downcasting với toán tử instanceof
# Nạp chồng phương thức
- Là một ví dụ về đa hình tại compile time
:pencil: Thay đổi số lượng tham số
```
void sum(int a, int b)
void sum(int a, int b, int c)
```
:pencil: Thay đổi kiểu dữ liệu của tham số
```
void sum(int a, int b)
void sum(double a, double b)
```
- *Không có thay đổi kiểu trả về của phương thức, vì việc này sẽ gây ra tính lưỡng nghĩa (ambiguity)*
- *Có thể nạp chồng phương thức main*
```
public static void main(int a) {}
```
# :dart: Tính kế thừa (IS-A)
- Một lớp không thể kế thừa nhiều lớp
# :dart: Tính đa hình (HAS-A)
# Ghi đè phương thức
- Là ví dụ về đa hình tại runtime
- Quy tắc
    - Phương thức phải có cùng tên như trong lớp cha
    - Phương thức phải có cùng tham số như trong lớp cha
    - Phải là quan hệ IS-A (kế thừa)
```
class Animal {  
    void eat() {
        System.out.println("animal");
    }  
}  

class Dog extends Animal {   
    void eat(){
        System.out.println("dog");
    }  
}  

class BabyDog extends Dog {  
    public static void main(String args[]) {  
        Animal a = new BabyDog1();  
        a.eat();  
    }
} 
```
Output: (sẽ gọi phương thức ở lớp cha gần nhất trong kế thừa nhiều tầng)
```
dog
```
# Liên kết tĩnh và Liên kết động (Static Binding & Dynamic Binding)
|Liên kết tĩnh|Liên kết động
|-----------|-------------
|Lời gọi phương thức được quyết định tại compile time|Lời gọi phương thức được quyết định tại run time
```
// class Student extends Person

Person p = new Student("Duc", 20); // Upcasting không tường minh

// Hàm constructor sẽ được gọi lần lượt từ lớp cha đến lớp con
// Phương thức sẽ lấy của lớp con Student nếu nó ghi đè phương thức ở lớp cha Person, 
nếu lớp con Student không có phương thức đó thì vẫn gọi phương thức từ lớp cha,
nếu lớp cha không có phương thức đó thì lỗi  
// Thuộc tính sẽ lấy của lớp cha Person
```
# Upcasting và Downcasting
```
class Animal {
    public void eat() {
        System.out.println("eat");
    }
}
 
public class Cat extends Animal {
    public void meow() {
        System.out.println("meow");
    }
}
```
- Upcasting là khi biến tham chiếu của lớp cha tham chiếu tới đối tượng của lớp con
```
public class Upcasting {
    public static void main(String[] args) {
        Cat cat = new Cat();
        Animal animal1 = cat; // Chuyển kiểu không tường minh
        Animal animal2 = (Animal) cat; // Chuyển kiểu tường minh
 
        cat.eat();
        cat.meow();
        animal1.eat();
        animal2.eat();
        // animal2.meow(); // Không thể gọi phương thức meow() vì lớp cha không có phương thức này
    }
}
```
- Downcasting là đạng chuyển kiểu đối tượng là thể hiện của lớp cha xuống thể hiện của lớp con trong quan hệ kế thừa
- Các lỗi:
```
Dog d = new Animal(); // gay ra loi tai thoi gian bien dich
```
```
Dog d = (Dog)new Animal();  
//Bien dich thanh cong nhung co the ClassCastException bi nem tai runtime 
```
- Thực hiện downcasting với toán tử instanceof
```
public class Dog extends Animal {
    static void method(Object obj) {
        if (obj instanceof Dog) {
            Dog dog = (Dog) obj; // downcasting
            System.out.println("downcasting successfully");
        } else {
            System.out.println("obj is not instance of Dog");
        }
    }
 
    public static void main(String[] args) {
        Animal dog = new Dog();
        Dog.method(dog);
         
        Object obj = new Rectangle();
        Dog.method(obj);
    }
}    
```
Output:
```
downcasting successfully
obj is not instance of Dog
```
# :dart: Trừu tượng
```
public abstract class Employee
{
   private String name;
   private String address;
   private int number;

   public abstract double computePay();

   //Phan con lai cua dinh nghia class
}
```
- Nếu một lớp chứa một phương thức abstract, thì lớp đó cũng phải là abstract
- Bất kỳ lớp con nào phải hoặc override phương thức abstract hoặc khai báo abstract chính nó
# Interface
- Một lớp có thể triển khai một hoặc nhiều interface tại một thời điểm
- Một lớp chỉ có thể kế thừa một lớp khác, nhưng được triển khai nhiều interface
- Một interface có thể kế thừa từ một interface khác, tương tự cách một lớp có thể kế thừa lớp khác
## :pencil: Đa kế thừa
**Câu hỏi**: Đa kế thừa không được hỗ trợ thông qua lớp trong Java nhưng là có thể bởi Interface, tại sao?

Vì không có tính lưỡng nghĩa khi trình triển khai được cung cấp bởi lớp Implementation. Ví dụ:
```
interface Printable {  
    void print();  
}  

interface Showable {  
    void print();  
}  

class Test implements Printable, Showable {  
    public void print() {System.out.println("Hello");}  
    
    public static void main(String args[]) {  
        Test obj = new Test();  
        obj.print();  
     }  
} 
```
Printable và Showable interface có cùng các phương thức nhưng trình triển khai của nó được cung cấp bởi lớp Test, vì thế không có tính lưỡng nghĩa
# Ngoại lệ
- Là một sự kiện xảy ra khi thực thi chương trình mà phá vỡ luồng hoạt động mong đợi
- Có 3 loại:
    - Ngoại lệ được kiểm tra (checked exception)
    - Lỗi (error)
    - Ngoại lệ runtime (runtime exception)
- Xử lý ngoại lệ: phân tách mã nguồn, sử dụng try-catch/try-catch-finally
1. Ngoại lệ được kiểm tra
- Là ngoại lệ chương trình có thể dự đoán được ngoại lệ và xử lý được ngoại lệ đó, kiểm tra tại compile time
- Ví dụ: người dùng mở tệp tên Data.txt để đọc nội dung nhưng tệp này không tồn tại trong hệ thống
    - Luồng hoạt động mong đợi: tệp tồn tại và dữ liệu được đọc từ tệp thành công
    - Thực tế: tệp không tồn tại => FileNotFoundException
2. Lỗi
- Là một ngoại lệ không được kiểm tra, ngoài phạm vi kiểm soát của chương trình
- Ví dụ: chương trình mở tệp thành công, sẵn sàng đọc dữ liệu từ tệp nhưng không thể đọc nội dung vì lỗi nào đó thuộc phần cứng hoặc thuộc hệ thống (IOError)
- Lỗi phổ biến: OutOfMemoryError (hết bộ nhớ RAM), VirtualMachineError (lỗi máy ảo),...
3. Ngoại lệ runtime
- Là một ngoại lệ không được kiểm tra, xuất phát từ bug lập trình như dùng sai API hoặc viết mã sai logic
- Ví dụ: ArithmaticException (lỗi số học như chia cho 0), NullPointException 
```
Object ref = null;
ref.toString();
// NullPointException
```
:pencil: Chương trình mẫu
```
public class Main {
    public static void main(String[] args) {
        try {
            int a = 50 / 0; // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }
}
```
Output:
```
Lỗi: / by zero
```
# Design Patterns
## Sigleton
- Đảm bảo chỉ duy nhất một thể hiện (instance) được tạo ra và có một method có thể truy xuất thể hiện duy nhất đó mọi lúc mọi nơi trong chương trình
- Ứng dụng: Quản lý cấu hình ứng dụng, truy cập tài nguyên chung như kết nối cơ sở dữ liệu, trình quản lý tập tin,...
```
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
## Adapter
- Adapter được sử dụng để kết nối hai hệ thống có giao diện không tương thích
- Ví dụ: không thể sạc điện thoại từ nguồn điện 220V mà cần một adapter chuyển 220V thành 5V để sạc

![Screenshot 2023-12-25 004706](https://hackmd.io/_uploads/rk5sAk8DT.png)
## Prototype
- Khởi tạo một đối tượng bằng cách clone một đối tượng đã tồn tại thay vì khởi tạo với từ khoá new. Đối tượng mới là một bản sao có thể giống 100% với đối tượng gốc, có thể thay đổi dữ liệu của nó mà không ảnh hưởng đến đối tượng gốc

![Screenshot 2023-12-25 005206](https://hackmd.io/_uploads/rkQ0kg8Da.png)
```
public class Computer implements Cloneable{
    private int id;
    private String name;

    public int getId() {return id;}
    public void setId(int id) {this.id = id;}
    public String getName() {return name;}
    public void setName(String name) {this.name = name;}

    @Override
    protected Computer clone() throws CloneNotSupportedException {
        return (Computer) super.clone();
    }
}
```
## Composite
- Cần viết một công cụ quản lý hệ thống file. Các thành phần chính: file, shortcut, và folder. Folder có thể chứa folder, file, shortcut khác
 
![Screenshot 2023-12-25 010113](https://hackmd.io/_uploads/H1DlzgUP6.png)

# :1234: Bài tập
## :one: Định nghĩa một lớp ngoại lệ mới và ví dụ
```
public class MyException extends Exception {
    public MyException (String messege) {
        super(messege);
    }
}

public class Main {
    public static void check(int x) throws MyException {
        if (x < 0) {
            throw new MyException("So am");
        } else {
            System.out.println("So khong am");
        }
    }
    public static void main(String[] args) {
        try {
            check(5);
        } catch (MyException) {
            System.out.println(e.getMessage());
        }
    }
}
```
## :two: Định nghĩa lớp A có phương thức *int getNumber* trả về số đối tượng thuộc A đã được tạo ra
```
public class A {
    private static int cnt = 0;
    
    public A() {
        cnt++;
    }
    
    public static int getCnt() {
        return cnt;
    }
    
    public static void main(String[] args) {
        A obj1 = new A();
        A obj2 = new A();
        System.out.println(A.getCnt());
    }
}
```
Output:
```
2
```
## :three: Phân biệt ```a == b``` và ```a.equals(b)```. Ví dụ
- ``` a == b ``` là so sánh tham chiếu, xem hai biến a và b có đang trỏ đến cùng một vùng nhớ trong bộ nhớ heap hay không. 
```
String s1 = new String ("hi");
String s2 = s1;

System.out.println(s1 == s2); //Kết quả là true
```
- ```a.equals(b)``` so sánh giá trị nội dung của đối tượng mà a và b trỏ đến
```
String s1 = new String("hi");
String s2 = new String("hi");

System.out.println(s1.equals(s2)); //Kết quả là true
System.out.println(s1 == s2); //Kết quả là false
```
## :four: Ví dụ thể hiện cơ chế liên kết tĩnh và liên kết động. Giải thích
- Liên kết tĩnh
    - Lời gọi phương thức diễn ra tại compile time
    - Nếu có phương thức private, final hoặc static trong class thì đó là liên kết tĩnh, do đó không thể ghi đè trong liên kết tĩnh
```
class Animal {
    static void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    static void eat() {
        System.out.println("Dog is eating");
    }
}

public class Example {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.eat(); // Liên kết tĩnh: Gọi phương thức của lớp Animal
    }
}
```
Output:
```
Animal is eating
```
- Liên kết động
    - Lời gọi phương thức diễn ra tại run time
    - Các phương thức là public
```
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void eat() {
        System.out.println("Dog is eating");
    }
}

public class Example {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.eat(); // Liên kết động: Gọi phương thức của lớp Dog
    }
}
```
Output:
```
Dog is eating
```
## :five: Upcasting và Downcasting là gì. Lấy ví dụ. Khi nào thì downcasting thất bại? (đã nêu trên)
## :six: Ví dụ và giải thích về việc sử dụng tham chiếu this làm tham số của một phương thức
```
public class Example {
    void display(Example obj) {
        System.out.println("Hello Java");
    }
    void p() {
        display(this);
    }
 
    public static void main(String args[]) {
        Example o1 = new Example();
        o1.p();
    }
}
```
## :seven: Finally trong xử lý ngoại lệ
- Được sử dụng để tạo một khối mã mà sẽ được thực thi sau khi thực hiện xong khối try và khối catch. Câu lệnh trong khối finally luôn được thực thi bất chấp code có rơi vào exception hay không
- Nhiệm vụ: dọn dẹp tài nguyên (đóng file, đóng kết nối cơ sở dữ liệu,...)
```
public class FinallyExample {
    public static void main(String[] args) {
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("example.txt"));
            String line = reader.readLine();
            System.out.println(line);
        } catch (IOException e) {
            System.err.println(e.getMessage());
        } finally {
            try {
                // Đảm bảo rằng tài nguyên (BufferedReader) sẽ được giải phóng ngay cả khi có ngoại lệ
                if (reader != null) {
                    reader.close();
                }
            } catch (IOException e) {
                System.err.println(e.getMessage());
            }
        }
    }
}
```
## :eight: Trong Java, chuyện gì sẽ xảy ra nếu có nhiều hơn 1 khối catch có thể bắt đối tượng ngoại lệ bị ném
- Khi có nhiều khối catch trong một câu lệnh try-catch và một đối tượng ngoại lệ được ném, JVM sẽ kiểm tra từng khối catch theo thứ tự và thực thi khối catch đầu tiên phù hợp với kiểu của đối tượng ngoại lệ
Ví dụ:
```
public class Example {
    public static void main(String[] args) {
        int res = 10 / 0; //ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        } catch (NullPointerException e) {
            System.out.println(e.getMessage());
        } 
    }
}
```
Output:
```/ by zero```
## :nine: Phân biệt checked exception và unchecked exception
- Checked là exception được kiểm tra tại compile time, còn unchecked chỉ được kiểm tra tại run time
- Ví dụ
    - Checked exception (FileNotFoundException)
    ```
    public class Main {
        public static void main(String[] args) {
            try {
                FileReader file = new FileReader("example.txt"); 
            } catch (FileNotFoundException e) {
                System.out.println(e.getMessage());
            } finally {
                file.close();
            }
        }
    }
    ```
    - Unchecked exception (ArithmeticException)
    ```
    public class Main {
        public static void main(String[] args) {
            try {
                int a = 50 / 0; 
            } catch (ArithmeticException e) {
                System.out.println(e.getMessage());
            }
        }
    }
    ```
## :keycap_ten: Cho một ví dụ và giải thích về việc sử dụng interface làm kiểu của tham số phương thức
```
interface Shape {
    double calculateArea();
}

class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

// Lớp sử dụng interface làm kiểu của tham số phương thức
class AreaCalculator {
    public static double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}

public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle(5);
        Rectangle rectangle = new Rectangle(4, 6);

        double circleArea = AreaCalculator.calculateArea(circle);
        double rectangleArea = AreaCalculator.calculateArea(rectangle);

        System.out.println("Circle Area: " + circleArea);
        System.out.println("Rectangle Area: " + rectangleArea);
    }
}
```
AreaCalculator là một lớp chứa phương thức calculateArea, và nó có thể nhận bất kỳ đối tượng nào implement interface Shape. Điều này giúp ta tính diện tích của hình tròn và hình chữ nhật bằng cách sử dụng cùng một phương thức, tận dụng tính đa hình trong Java
## :exclamation: 
```
abstract class FS {
    String name;
    abstract int getSize();
}

class File extends FS {
    int size;
    String type;

    @Override
    int getSize() {
        return size;
    }
}

class Shortcut extends FS {
    FS source;
    int size = 1; // 1KB

    @Override
    int getSize() {
        return size;
    }
}

class Folder extends FS {
    List<FS> contents = new ArrayList<>();

    void add(FS fs) {
        contents.add(fs);
    }

    @Override
    int getSize() {
        int totalSize = 0;
        for (FS item : contents) {
            totalSize += item.getSize();
        }
        return totalSize;
    }
}

class Disk extends FS {
    int capacity;
    List<FS> contents = new ArrayList<>();

    void add(FS fs) {
        contents.add(fs);
    }

    @Override
    int getSize() {
        int totalSize = 0;
        for (FS item : contents) {
            totalSize += item.getSize();
        }
        return totalSize;
    }

    int getFreeSpace() {
        return capacity - totalSize();
    }
}
```
