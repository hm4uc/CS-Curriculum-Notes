# :bookmark: GIẢI THUẬT
## :PENCIL: Sort
:dart: Sắp xếp dãy bất kỳ

| TÊN            | TỐT NHẤT | TRUNG BÌNH | TỆ NHẤT | BỘ NHỚ | ỔN ĐỊNH | PHƯƠNG THỨC | NHƯỢC/ƯU ĐIỂM
| -------------- | -------- | ---------- | ------- | ------ | ------- | ----------- | ------------
| Bubble sort    | O(n)     |   O(n^2)   | O(n^2)  | O(n)   | Có      | Exchanging
| Selection sort | O(n^2)   |   O(n^2)   | O(n^2)  | O(n)   | Không   | Selection
| Insertion sort | O(n)     |   O(n^2)   | O(n^2)  | O(n)   | Có      | Insertion
| Merge sort     | O(nlogn) |   O(nlogn) | O(nlogn)| O(2n)  | Có      | Chia để trị 
| Quick sort     | O(nlogn) |   O(nlogn) | O(n^2)  | O(n)   | Không   | Chia để trị | Xem là hiệu quả nhất
| Heap sort      | O(nlogn) |   O(nlogn) | O(nlogn)| O(n)   | Không   | Selection
| Counting sort  | O(n)     |   O(n)     | O(n)    |        |         |             |không thể với số thập phân
| Radix sort     | O(n)     |   O(n)     | O(n)    |        |         |             |không thể với số thập phân
- Quick Sort có khả năng sắp xếp trong chính nó, tức là không cần sử dụng một mảng phụ để lưu trữ các giá trị trung gian trong quá trình sắp xếp. Điều này giúp giảm thiểu việc sử dụng bộ nhớ và tăng hiệu suất.

## :PENCIL: Chia để trị
:dart: *Tìm kiếm nhị phân*
- Hình thành cách tiếp cận đệ qui
    - Chia dãy
    - Sắp xếp các dãy con (bằng cách lặp lại việc chia dãy nếu số phần tử > 1)
    - Ghép kết quả
- Các thuật toán thông dụng
    - Tìm kiếm nhị phân
    - Merge sort
    - Quick sort

:no_entry: Không phải bài toán nào cũng dùng chia để trị (ví dụ tính tổng các số trong dãy, cách nào cũng có độ phức tạp là O(n)). 
##  :pencil: Vét cạn
- Có thể giải hầu hết các bài toán
- Dễ thực thi, luôn cho đáp án chính xác
- Độ phức tạp lớn do phải vét hết các trường hợp
## :pencil: Tham lam
:dart: *Knapsack problem*
- Phổ biến trong thực tế
- Chưa chắc tìm được đáp án tối ưu
- Giải thuật tham lam quyết định sớm và thay đổi đường đi thuật toán theo quyết định đó, không bao giờ xét lại các quyết định cũ. 
- Dễ nghĩ ra, dễ cài đặt và chạy nhanh (độ phức tạp thấp)
## :pencil: Quy hoạch động
:dart: *Fibonacci và Đồng xu kinh điển*
- QHĐ là kĩ thuật được được dùng khi có một công thức và một (hoặc một vài) trạng thái bắt đầu. Một bài toán được tính bởi các bài toán nhỏ hơn đã tìm ra trước đó.
- Khi nào áp dụng quy hoạch động
    - Bài toán có các bài toán con gối nhau
        - Quy hoạch động cũng chia bài toán lớn thành các bài toán con nhỏ hơn như chia để trị. Được sử dụng khi các bài toán con này được gọi đi gọi lại. Phương pháp quy hoạch động sẽ lưu kết quả của bài toán con này, và khi được gọi, nó sẽ không cần phải tính lại, do đó làm giảm thời gian tính toán.
    - Bài toán có cấu trúc con tối ưu
        - Cấu trúc con tối ưu là một tính chất mà lời giải của bài toán lớn sẽ là tập hợp lời giải từ các bài toán nhỏ hơn.
            - Ví dụ: Trong bài toán tìm đường đi ngắn nhất trong đồ thị, nếu một node x nằm trên đường đi ngắn nhất giữa hai node u, v thì đường đi ngắn nhất từ u đến v sẽ là tổng hợp của đường đi ngắn nhất từ u đến x và đường đi ngắn nhất từ x đến v.
- Độ phức tạp đa thức, nhanh hơn quay lui và vét cạn nhưng chậm hơn tham lam
## :pencil: Quay lui
- Dựa trên đệ quy
- Giải bài toán liệt kê các cấu hình. Mỗi cấu hình được xây dựng bằng từng phần tử. Mỗi phần tử lại được chọn bằng cách thử tất cả các khả năng.
- Các bước trong việc liệt kê cấu hình dạng X[1...n]:
    - Xét tất cả các giá trị X[1] có thể nhận, thử X[1] nhận các giá trị đó. Với mỗi giá trị của X[1] ta sẽ:
    - Xét tất cả giá trị X[2] có thể nhận, lại thử X[2] cho các giá trị đó. Với mỗi giá trị X[2] lại xét khả năng giá trị của X[3]...tiếp tục như vậy
    - ...
    - Xét tất cả giá trị X[n] có thể nhận, thử cho X[n] nhận lần lượt giá trị đó.
    - Thông báo cấu hình tìm được.
- Bản chất là quá trình tìm kiếm theo chiều sâu (DFS)
- Nhược điểm: Quay lui không có cơ chế nhìn về tương lai để nhận biết đc nhánh tìm kiếm sẽ đi vào bế tắc.
- Độ phức tạp cấp số mũ
# :bookmark: CẤU TRÚC DỮ LIỆU
## :pencil: Linked list
- Có 2 loại: 
    - Dslk đơn (gồm cả dslk vòng)
    - Dslk đôi
- Cài đặt: Tự định nghĩa Node (dùng struct/class)
- Độ phức tạp (:+1:tự biết)
## :pencil: Stack & Queue
- Cài đặt 
    - Bằng Dslk: độ phức tạp khi truy vấn là $O(1)$
    - Bằng mảng: độ phức tạp khi truy vấn là $O(1)$ hoặc $O(n)$
- Ứng dụng
    - Stack: khử đệ quy, chuẩn hóa xâu
    - Queue: BFS
## :pencil: Hash, Map, Set
1. Hash
- Bảng băm là một cấu trúc dữ liệu sử dụng hàm băm để ánh xạ từ khóa đến giá trị tương ứng
- Lợi ích
    - Tính toán nhanh
    - Phân bố đồng đều, ít va chạm (ít giá trị được ánh xạ từ một khóa)
- Có 2 cách phổ biến xử lý va chạm:
    - Chaining (phổ biến nhất): cài đặt bằng danh sách liên kết. Để lưu giữ một phần tử trong bảng băm, thêm nó vào một dslk ứng với chỉ mục của nó. Nếu có va chạm xảy ra, các phần tử đó sẽ nằm cùng trong 1 dslk.
        - Độ phức tạp:
            - Tối ưu: $O(1)$
            - Xấu nhất: $O(n)$ (tất cả giá trị cùng nằm trong 1 dslk)
    - Linear probing: Khi thêm vào bảng băm, nếu chỉ mục đó đã có phần tử rồi, giá trị chỉ mục sẽ được tính toán lại theo cơ chế tuần tự (chuỗi Hasing bị trùng chỉ mục nào đó thì giá trị sẽ được đẩy xuống chỉ mục trống gần nhất phía sau)
        - Độ phức tạp:
            - Tối ưu: $O(1)$ (không có chỉ mục nào bị trùng)
            - Xấu nhất: $O(n)$
2. Map
- Mỗi phần tử đại diện cho 1 cặp khóa-giá trị (key-value), trong đó *mỗi khóa là duy nhất*
- Các key được sử dụng để sắp xếp và xác định value tương ứng được liên kết với nó
- Độ phức tạp khi tìm kiếm: $O(logn)$
- Truy cập: 
    ```
    mp[key] = value
    mp.at[key]
    ```
3. Set
- Set thuộc dạng *Cây đỏ đen*, là một tập hợp các phần tử duy nhất được sắp xếp theo thứ tự cụ thể (các phần tử là *khác nhau* và *được sắp xếp*)
- Nếu thêm các phần tử mới không theo thứ tự cụ thể vào một set, chúng sẽ tự động sắp xếp lại theo giá trị trước khi lưu trữ nội bộ.
- Độ phức tạp khi thêm, xóa, tìm kiếm: $O(logn)$
## :pencil: Tree
- Cây là một tập hữu hạn các node có cùng kiểu dữ liệu và các cạnh liên kết các node theo quan hệ phân tầng (cha-con)
    - Không có chu trình
- Mức của node: node gốc có mức là 0 và cứ thế tăng
- Bậc của node: số node con của nó
- Bậc của cây: bậc lớn nhất của các node trong cây. Cây bậc n là cây n-phân
- Độ sâu của node: là số cạnh từ node đến root
- Chiều cao của cây: số mức lớn nhất của node có trên cây

#### Duyệt cây
*Cây bình thường chỉ có 2 cách duyệt: pre-order và pos-order. Cây nhị phân có thêm in-order*
- Pre-order: 
    - Truy cập node gốc
    - Duyệt các cây con bên trái một cách đệ quy
    - Duyệt các cây con bên phải một cách đệ quy
- In-order:
    - Duyệt các cây con bên trái một cách đệ quy
    - Truy cập node gốc
    - Duyệt các cây con bên phải một cách đệ quy
- Pos-order:
    - Duyệt các cây con bên trái một cách đệ quy
    - Duyệt các cây con bên phải một cách đệ quy
    - Truy cập node gốc
### :star: Các thao tác
- Tạo cây
- Thêm nút / xóa nút
- Duyệt cây
- Tìm kiếm
### :one: Cây nhị phân
- Cây nhị phân là cây rỗng hoặc là cây mà mỗi node có tối đa 2 node con
- Cài đặt: dùng danh sách liên kết
#### :a: Tạo cây
```
struct node {
int data; 
node *left, *right;
};
```
#### :b: Duyệt cây
```
void preOrder(node* root) {
if (root == NULL) return;
cout << root->data << endl;
if (root->left) preOrder(root->left);
if (root->right) preOrder(root->right);
```
### :two: Cây nhị phân tìm kiếm
- Là cây nhị phân được sắp xếp. Giá trị node con trái nhỏ hơn giá trị node cha, giá trị node con phải lớn hơn giá trị node cha
- Khi duyệt in-order, ta sẽ được dãy tăng dần
#### :a: Tìm kiếm
```
Node* find(Node *node, int x) {
    if (node == NULL) return NULL;
    if (x > node->data) return find(node->right,x);
    if (x < node->data) return find(node->left,x);
    return node;
}
```
#### :b: Thêm
```
Node* insert(Node *node, int x) {
    if (node == NULL) return new Node(x);
    if (x < node->data) node->left = insert(node->left, x);
    else if (x > node->data) node->right = insert(node->right, x);
    return node;
}
```
#### :ab: Xóa 
- Xóa node lá: *Cút luôn không phải nghĩ*
- Xóa node có 1 node con: thay thế node cần xóa bằng node con của nó
- Xóa node có 2 node con:
    - Tìm node thế mạng (thường là node trái nhất của cây con phải hoặc node phải nhất của cây con trái)
    - Thay thế data node cần xóa bằng data node thế mạng, cập nhật node cha và node con của node thế mạng hiện tại
    - 
[Link code](https://freetuts.net/xoa-node-khoi-cay-nhi-phan-tim-kiem-3034.html)
- Độ phức tạp 
    - Trung bình: O(logn)
    - Xấu nhất: O(n) (full node trái hoặc phải)
### :three: Cây nhị phân đầy đủ
- Là cây nhị phân mà mỗi node có 0 hoặc 2 node con
### :four: Cây nhị phân hoàn hảo
- Là cây nhị phân mà các node trong có đủ 2 node con và các node lá ở cùng 1 mức
### :five: Cây AVL
- Là cây tìm kiếm nhị phân, mức của các node lá chênh lệch lớn nhất là 1
- Thêm vào mỗi node một field balance, diễn tả trạng thái cân bằng của node đó:
    - balance = -1: node lệch trái 
    - balance = 0: node cân bằng 
    - balance = +1: node lệch phải
- Các thao tác
    - Thêm
    - Xóa
    - Cân bằng lại cây
#### :a: Thêm
- Duyệt từ node vừa thêm ngược về node gốc
- Nếu tìm thấy node P bị mất cân bằng thì tiến hành xoay cây tại nút P (chỉ cần điều chỉnh 1 lần duy nhất)
#### :b: Xóa
- Duyệt từ node vừa xóa ngược về node gốc
- Nếu tìm thấy node P bị mất cân bằng thì tiến hành xoay cây tại node P (Thao tác điều chỉnh có thể làm cho những node phía trên của node P bị mất cân bằng ⇒ cần điều chỉnh cho đến khi không còn node nào bị mất cân bằng nữa (lùi dần về node gốc))
#### :ab: Cân bằng
- Kỹ thuật quay trái
- Kỹ thuật quay phải
- Kỹ thuật quay trái-phải
- Kỹ thuật quay phải-trái

[Tham khảo](https://hoclaptrinh.vn/tutorial/cau-truc-du-lieu-amp-giai-thuat-55-bai/cay-avl-trong-cau-truc-du-lieu-va-giai-thuat)
- **Độ phức tạp**: Phép chèn, xóa, điều chỉnh: $O(logn)$
### :six: Cây đỏ đen 
- Là cây nhị phân tìm kiếm tự cân bằng có tính chất:
    - Mọi node trong cây phải là đỏ hoặc đen
    - Node gốc là đen
    - Tất cả các lá (NULL) là đen
    - Mọi node đỏ đều có node con là đen
    - Tất cả các đường đi từ một nút bất kỳ tới các lá phải đi qua số nút đen bằng nhau
- Phép chèn: [Tham khảo](https://blog.luyencode.net/cay-do-den-red-black-tree-phan-2-insert/)
- Phép xóa: [Tham khảo](https://blog.luyencode.net/cay-do-den-red-black-tree-phan-3/)
    - Nếu xóa một nút đỏ thì chiều cao đen của cây không đổi
    - Nếu xóa một nút đen thì phải cân bằng lại cây
- **Độ phức tạp**: 
    - Độ sâu của cây: tệ nhất: ~$O(2.logn)$, trung bình: $O(logn)$
    - Tìm kiếm, chèn, xóa: $O(logn)$
### :seven: Heap tree
- Là cây nhị phân cân bằng
- Phân loại:
    - Max heap: giá trị node cha lớn hơn giá trị node con
    - Min heap: giá trị node cha nhỏ hơn giá trị node con
- Xây dựng (Max heap)
    - B1: Tạo một nút mới tại vị trí cuối cùng của Heap
    - B2: Gán giá trị mới cho nút này
    - B3: So sánh giá trị của nút con với giá trị cha
    - B4: Nếu giá trị của cha là nhỏ hơn con thì tráo đổi chúng
    - B5: Lặp lại bước 3 và 4 cho tới khi vẫn duy trì thuộc tính của Heap
- Xóa max (Max heap)
    - B1: Xóa nút gốc
    - B2: Di chuyển phần tử cuối cùng có bậc thấp nhất lên nút gốc
    - B3: So sánh giá trị của nút con này với giá trị của cha
    - B4: Nếu giá trị của cha là nhỏ hơn của con thì tráo đổi chúng
    - B5: Lặp lại bước 3 và 4 cho tới khi vẫn duy trì thuộc tính của Heap
- **Độ phức tạp**:
    - Tìm max, min: $O(1)$
    - Xóa max, min: $O(logn)$
    - Thay đổi giá trị: $O(logn)$
    - Chèn: $O(logn)$
    - Hợp 2 heap: $O(n)$
## :pencil: Graph
### 1. Định nghĩa
- Là một cấu trúc rời rạc: G = <V,E>
    - V là tập các đỉnh ( vertices)
    - E là tập các cạnh ( Edges) _ tập các cặp (u,v) mà u,v là hai đỉnh thuộc V
### 2. Phân loại
- Có hướng và vô hướng
- Có trọng số và không có trọng số
### 3. Biểu diễn đồ thị
- Ma trận kề
    - Ma trận kề của đồ thị vô hướng luôn luôn là mà trận đối xứng a[i][j] = a[j][i]
    - Dễ cài đặt
    - Ưu điểm: So sánh hai đỉnh bất kỳ trong đồ thị có kề nhau hay không chỉ bằng một phép so sánh
    - Nhược điểm: Kích thước luôn là **V^2** dẫn đến tốn bộ nhớ
- Danh sách cạnh
    - Mỗi cạnh E = <x,y> sẽ tương ứng với hai biến: Dau[E] và Cuoi[E]. Lưu trữ dạng mảng hoặc dslk
    - **Bộ nhớ: E (không trọng số), 2E (có trọng số)**
    - Thường dùng khi ma trận là thưa
    - Nhược điểm: Để xác định những đỉnh nào là kề của một đỉnh cho trước ta phải làm cỡ E phép so sánh (duyệt qua tất cả các cạnh của đồ thị)
    
- Danh sách kề
    - Ta sẽ lưu một mảng các đỉnh, mỗi đỉnh chứa một danh sách các đỉnh khác mà nó nối tới
    - **Bộ nhớ: E + V**
    - Ưu điểm:
        - Không tốn dung lượng biểu diễn cạnh không tồn tại như ma trận kề, có thể biểu diễn và lưu trữ hàng triệu đỉnh
        - Duyệt tất cả các đỉnh kề của một đỉnh là hết sức dễ dàng
        - Biểu diễn được cạnh song song
    - Nhược điểm:
        - Việc remove cạnh sẽ tốn chi phí để duyệt danh sách
        - Chi phí kiểm tra 2 cạnh có kết nối nhau không sẽ lớn hơn ma trận kề do phải duyệt danh sách
### 4. Duyệt đồ thị
- DFS
    - Stack
    - Ứng dụng: Tìm thành phần liên thông mạnh, sắp xếp Topo
- BFS
    - Queue 
    - Ứng dụng: Tìm đường đi ngắn nhất trên đồ thị không trọng số
- **Độ phức tạp của 2 cách duyệt: $O(E + V)$**
### 5. Sắp xếp Topo trong DAG(đồ thị có hướng và không chu trình) sử dụng DFS
- Thứ tự Tô-pô là một thứ tự sắp xếp của các đỉnh sao cho với mọi cung từ đỉnh uđến đỉnh v, u luôn nằm trước v
- Ý tưởng: Chọn 1 đỉnh nguồn, gọi DFS, đỉnh thăm xong đầu tiên là đỉnh cuối cùng trong thứ tự Topo, cứ thể đẩy dần đỉnh lên phía trước 
    - Sử dụng danh sách kề
- **Độ phức tạp: $O(E + V)$**
### 6. Tìm số thành phần liên thông mạnh trong đồ thị có hướng (Thuật toán Kosaraju)
- B1: DFS trên G (các đỉnh lưu trong danh sách kề), lưu các đỉnh vào Stack
- B2: Đồ thị TG là đồ thị G đảo chiều tất cả các cạnh
- B3: Pop các đỉnh trong Stack và gọi DFS trên TG, từ đó thu được thành phần liên thông mạnh
- **Độ phức tạp: $O(E + V)$**
### 7. Đường đi ngắn nhất
#### :one: Dijkstra
- Ý tưởng
    - B1. Đánh dấu đỉnh ban đầu (đỉnh nguồn) là $0$ và các đỉnh còn lại là vô cùng
    - B2. Gọi đỉnh chưa xét với giá trị đánh dấu nhỏ nhất là $C$ (current node)
    - B3. Với mỗi đỉnh kề $N$ (neighbour) với đỉnh $C$: Cộng giá trị đang đánh dấu của đỉnh $C$ với trọng số của cạnh nối đỉnh $C$ với đỉnh $N$. Nếu được kết quả nhỏ hơn giá trị đang đánh dấu ở đỉnh $N$ ta cập nhật giá trị đánh dấu cho đỉnh $N$ mới:
    *d(N) = min (d(N), d(C, N) + d(C ))*
    - B4. Đánh dấu đỉnh $C$ đã xét xong
    - B5. Nếu vẫn còn đỉnh chưa xét, lặp lại bước $2$
- *Chỉ áp dụng với đồ thị có trọng số không âm*
- **Độ phức tạp** (khi cài đặt bằng hàng đợi ưu tiên (Binary heap) và danh sách kề): **$O((E + V)logV)$**

[Link code](https://viblo.asia/p/thuat-toan-dijkstra-va-ung-dung-aWj53zgQl6m)
#### :two: Bellman-Ford
- *Chậm hơn Dijkstra nhưng áp dụng cả đồ thị có trọng số âm. Tuy nhiên với chu trình âm thì không thể do thuật toán sẽ thực hiện vòng lặp vô tận*
- Cài đặt: Sử dụng danh sách cạnh
- **Độ phức tạp:** 
    - **Tốt nhất: O(E)**
    - **Trung bình và xấu nhất: O(EV)**
- Ý tưởng: Thuật toán lưu vết khoảng cách từ đỉnh bắt đầu đến tất các đỉnh của đồ thị. Khởi đầu, khoảng cách đến đỉnh bắt đầu là 0 và khoảng cách đến tất cả các đỉnh khác là vô cùng. Thuật toán giảm khoảng cách bằng cách tìm các cạnh mà có đường ngắn nhất cho đến khi nó không thể giảm thêm bất kỳ khoảng cách nào nữa.
[Ví dụ](https://vallicon.com/post/%C4%91%C6%B0%E1%BB%9Dng-%C4%91i-ng%E1%BA%AFn-nh%E1%BA%A5t-(shortest-paths)-1rZNpgDYkAV)
- Nhận xét: ở trên một đỉnh chỉ cập nhật tối đa n-1 lầ, nên tại lần cập nhật thứ n, nếu như vẫn có đỉnh được cập nhật nghĩa là đỉnh đó thuộc chu trình âm
#### :three: Floyd-Warshall
- Ý tưởng: Thuật toán duy trì một mảng 2 chiều chứa khoảng cách giữa các đỉnh. Thuật toán giảm thiểu khoảng cách bằng cách sử dụng lần lượt các đỉnh làm đỉnh trung gian 
    - B1: Các khoảng cách được tính toán chỉ sử dụng trực tiếp các cạnh giữa các đỉnh. 
    - B2: Chọn lần lượt các đỉnh trong đồ thị làm đỉnh trung gian $C$
    - B3: Chọn 1 cặp đỉnh không trùng với đỉnh trung gian $A$ và $B$
    - B3: $d(A, B) = min (d(A,B), d(A,C) + d(C,B))$

[Link code](https://vallicon.com/post/%C4%91%C6%B0%E1%BB%9Dng-%C4%91i-ng%E1%BA%AFn-nh%E1%BA%A5t-(shortest-paths)-1rZNpgDYkAV)

:Star: Tổng hợp
| Đặc điểm| BFS | Dijkstra (Binary Heap)|Bellman-Ford | Floyd-Warshall
| -----  | -----| ------- | ------- | ------
|Độ phức tạp|$O(E + V)$|$O((V+E)logV)$|$O(VE)$ | $O(V^3)$
|Kích thước đồ thị áp dụng | $V, E ≤ 10M$ | $V,E ≤ 300K$ | $V, E ≤ 10M$ | $V ≤ 400$
|Không trọng số | Tốt nhất | Ổn | Tệ | Tệ
|Có trọng số| N/A | Tốt nhất | Ổn | Tệ
|Trọng số âm  | N/A | Ổn | Ổn |Tệ 
|Phát hiện chu trình âm | Không |Không | Có | Không 
|Mục đích|Đường đi ngắn nhất từ đỉnh nguồn |Đường đi ngắn nhất từ đỉnh nguồn |Đường đi ngắn nhất từ đỉnh nguồn |Đường đi ngắn nhất giữa mọi cặp đỉnh
### 8. Cây khung nhỏ nhất
#### :one: Prim
- Ý tưởng:
    - B1: Khởi tạo tập hợp đỉnh V rỗng, tập hợp cạnh E rỗng
    - B2: Chọn ngẫu nhiên 1 đỉnh và thêm vào tập hợp các đỉnh V
    - B3; Chọn 1 đỉnh chưa có trong tập V mà có kết nối với 1 đỉnh trong V, cạnh tạo từ 2 đỉnh đó phải là cạnh có trọng số nhỏ nhất và thêm vào tập hợp các cạnh E
    - B4: Lặp lại bước 3 cho đến khi cây khung hoàn thành (tất cả các đỉnh của cây khung đều đã xuất hiện trong V), cây khung nhỏ nhất là cây khung được tạo từ tập các cạnh trong E
- **Độ phức tạp**: $O((E + V)logV)$
    
#### :two: Krusal
- Ý tưởng: (Giải thuật tham lam)
    - B1:Sắp xếp các cạnh từ bé đến lớn theo trọng số. 
    - B2: Lần lượt chọn các cạnh theo thứ tự từ bé đến lớn trong danh sách sao cho không tạo thành chu trình. 
    - Thuật toán sẽ dừng lại khi đã có đủ V−1 cạnh trong cây khung
- **Độ phức tạp**: $O(E.logE)$



