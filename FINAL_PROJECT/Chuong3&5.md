<h1> Chương 3. Xây dựng bộ dữ liệu </h1>

<h2> 1. Các tiêu chí khi thu thập dữ liệu </h2>
<ul>
  <li> Vị trí của camera đặt cách sản phẩm từ 5 – 15cm (tính từ bề mặt hướng vào của sản phẩm đến camera). </li>
  <li> Background sản phẩm là nền sáng. </li>
  <li> Đảm bảo độ sáng hình chụp ISO > 100. </li>
  <li> Góc máy ảnh đặt từ trên xuống dưới trực diện sản phẩm và góc nghiêng. </li>
  <li> Các mặt hàng có nhiều hình dạng khác nhau nên để thuận lợi cho việc thu thập data và tăng khả năng nhận diện thì cách đặt mỗi loại hình dáng là phải khác nhau. </li>
  <li> Hình trụ: Đặt thẳng đứng hoặc nằm ngang và phải thấy logo hoặc tên. </li>
  <li> Hình hộp: Đặt nằm ngang, ưu tiên mặt có logo hoặc tên ở phía trên. </li>
  <li> Dạng gói: Đặt nằm ngang, ưu tiên mặt có logo hoặc tên ở phía trên. </li>
</ul>
![Logo TechMaster!](https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Sp_01.jpg)


<h2> 2. Tổng quan về bộ dữ liệu </h2>
<ul>
  <li> Bộ dữ liệu dùng để training và testing model: gồm <strong>18995 tấm ảnh</strong>, chụp <strong>199 classes</strong> khác nhau, mỗi class có sự chênh lệnh không đồng đều về số lượng ảnh. </li>
  <li> Bộ dữ liệu test mà model hoàn toàn chưa từng “tiếp xúc” bao giờ: gồm <strong>10 – 15 videos</strong> được quay với điều kiện ràng buộc Input vừa mới đề cập. </li>
  <li> <strong>Một tập dataset csv</strong> do nhóm tự đi thu thập trên mạng về, được cập nhật giá cụ thể và gần nhất, chủ yếu lấy từ Bách Hóa Xanh. </li>
  <li> <strong>Hoàn toàn do nhóm tự chụp, tự quay.</strong> </li>
</ul>

<h3> Hình ảnh một số sản phẩm </h3>

<h3> Nhận xét: </h3>
<ol> 
  <li> Data nhóm hoàn toàn do thủ công tự chụp, thành viên trong nhóm đã thống nhất với nhau từ trước sẽ tạo nên một bộ dữ liệu “sạch” (clean data). </li>
  <ul> => Nhóm chúng em không có bước tiền xử lý dữ liệu. </ul>
  
  <li> Data nhóm có kích thước khá lớn (17.3GB), và do trong quá trình chuẩn bị dữ liệu, đường truyền mùa dịch không ổn định và quá trình train hay bị tràn, crash trên colab.</li>
  <ul> => Nhóm chúng em quyết định không có bước tăng cường dữ liệu, chấp nhận việc model có thể bị overfitting – sẽ demo sau, nhưng chúng em vẫn đảm bảo model sẽ detect tốt trong các video test được quay với điều kiệu đã ràng buộc từ trước. </ul>
</ol>


<h2> 3. Mô tả thông số bộ dữ liệu </h2>

<h3> Nhận xét thông số: </h3>
<ul>
  <li> Bộ dữ liệu có sự chênh lệch lớn về giữa các class, dự đoán mô hình training sẽ khó xử lý trên nhưng bởi lí do đã nêu trên, nhóm chúng em quyết định sẽ không tiền xử lý dữ liệu. => <strong>unbalanced data</strong> </li>
  
  <li> Nếu đem model training từ tập dữ liệu trên nhưng không có tiền xử lý dữ liệu thì độ chính xác khi áp dụng vào thực tế có thể sẽ thấp hơn => <strong>dự đoán model bị overfitting</strong> </li>
</ul>

<h3> Bộ dữ liệu cho mỗi model </h3>
<p> Hai tập dữ liệu dùng để train hai model đều có kích thước 17.3GB, tập dữ liệu sẽ bao gồm files ảnh chụp định dạng *.jpg các sản phẩm và files label (gán nhãn cho từng ảnh). </p>
<ul>
  <li> YOLO </li>
  <ul>
    <li> Định dạng files annotaions dưới dạng <strong>*.txt</strong>. </li>
    <li> Tương ứng với một files ảnh sẽ có files labels trùng tên tương đương. </li>
    <li> Bộ dữ liệu dùng để train model yolov4 được chia theo tỉ lệ <strong>80/20</strong> tương đương <strong>train/valid</strong>. </li>
  </ul>
  
  <li> FASTER R-CNN sử dụng Framework Detectron2 </li>
  <ul>
    <li> Định dạng files annotations dưới dạng <strong>*.json</strong>. </li>
    <li> Bộ dữ liệu dùng để train model yolov4 được chia theo tỉ lệ <strong>80/20</strong> tương đương <strong>train/valid</strong>. </li>
  </ul>
</ul>

<h3> Một số trường hợp khó xử lý: </h3>





<h1> Chương 5. Ứng Dụng và Hướng Phát Triển </h1>

<h2> Bài toán đặt ra </h2>
<p> Bài Toán “Nhận Diện Sản Phẩm Thương Mại” mà nhóm em hướng đến để giải quyết là bài toán có hướng phát triển và ứng dụng cao, đặc biệt là trong thời đại công nghệ ngày càng phát triển và “xâm nhập” vào thị trường mua sắm. Nếu model được cải tiến để giải quyết bài toán với model có độ chính xác cao, thì bài toán của chúng em sẽ góp phần quan trọng trong việc xây dựng mô hình mua sắm công nghệ cao, điển hình với dự án của một số công ty lớn sau: </p>

<ul>
  <li> Chuỗi của hàng Amazon Go của công ty Amazon với slogan “Just Walk Out”. </li>
  <li> Dự án quầy thanh toán không thu ngân của công ty Abto Software (Abto Cashierless Checkout). </li>
  <li> .... </li>
</ul>
 
 
<h2> Hướng cải tiến </h2>
<p> Như đã nói ở trên, để có thể giải quyết bài toán “Nhận Diện Sản Phẩm Thương Mại” ở mức độ ứng dụng được vào trong các mô hình mua sắm công nghệ cao, thì với model như trên của chúng em cần phải có những hưỡng cải tiến như sau: </p>

<ul>
  <li> <strong>Về Data</strong> </li>
  <ul> 
    <li> Tăng sự đa dạng và số lượng, loại sản phẩm nhiều hơn, ngoài ra phải thường xuyên thu thập data vì mẫu mã sản phẩm, giá cả liên tục thay đổi, ngoài ra cũng phải đáp ứng được các chương trình khuyến mãi của các chuỗi cửa hàng,... </li>
    <li> Quy trình thu thập data phải diễn ra chặt chẽ, có sự đầu tư về phần cứng thiết bị, ví dụ như set up một phòng lab riêng biệt chỉ dành cho việc chụp hình các sản phẩm, các camera set up có giá đỡ cố định ở các góc, ánh sáng điều kiện, phù hợp với bối cảnh thực tế, chú ý đến vấn đề tạo nên một balanced data,... => Clean Data </li>
    <li> Tăng cường dữ liệu, sử dụng các kỹ thuật như Data Augmentation (blur, gray scale, cutout, cutmix, rotate,...),...việc lựa chọn các bước tăng cường dữ liệu rất quan trọng, không phải phương pháp nào cũng tốt cho tập dữ liệu. </li>
  </ul>
  
  <li> <strong>Về Model</strong> </li>
  <ul>
    <li> Model trên của chúng em bị overfitting, nên phần cải tiến data như trên có thể sẽ giúp model well generalize. </li>
    <li> Ngoài ra, cũng còn một số biện pháp cải thiện model như điều chỉnh độ phức tạp lại của networks, thay đổi các tham số, sử dụng kỹ thuật early stopping,... </li>
    <li> Việc sử dụng pretrained model cũng ảnh hưởng tới kết quả detect, nên cân nhắc việc sử dụng pretrained model. </li>
  </ul>
  
  <li> <strong>Để bài toán được mở rộng và phát triển, chúng em có ý tưởng thêm một số chức năng như sau:</strong> </li>
  <ul>
    <li> Sử dụng bảng điện tử trực truyết để người dùng có thể theo dõi tình trạng đơn hàng ở quầy thanh toán, tăng tương tác giữa người dùng với hệ thống,... </li>
    <li> Phát triển một ứng dụng điện thoại kết nối với dữ liệu mua sắm của người dùng, để người dùng tiện tra cứu thông tin, giá hóa đơn, sản phẩm,.. Tuy nhiên cũng đảm bảo bảo mật thông tin người dùng. </li>
  </ul>
</ul>
