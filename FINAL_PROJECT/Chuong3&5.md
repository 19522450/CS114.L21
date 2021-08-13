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

<h2> 2. Tổng quan về bộ dữ liệu </h2>
<ul>
  <li> Bộ dữ liệu dùng để training và testing model: gồm <strong>18995 tấm ảnh</strong>, chụp <strong>199 classes</strong> khác nhau, mỗi class có sự chênh lệnh không đồng đều về số lượng ảnh. </li>
  <li> Bộ dữ liệu test mà model hoàn toàn chưa từng “tiếp xúc” bao giờ: gồm <strong>10 – 15 videos</strong> được quay với điều kiện ràng buộc Input vừa mới đề cập. </li>
  <li> <strong>Một tập dataset csv</strong> do nhóm tự đi thu thập trên mạng về, được cập nhật giá cụ thể và gần nhất, chủ yếu lấy từ Bách Hóa Xanh. </li>
  <li> <strong>Hoàn toàn do nhóm tự chụp, tự quay.</strong> </li>
</ul>

<h3> Hình ảnh một số sản phẩm </h3>
<p align="middle">
  <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Sp_01.jpg" style="width:25%;"/>
  <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Sp_02.jpg" style="width:25%;"/>
  <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Sp_03.jpg" style="width:25%;"/>
  <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Sp_04.jpg" style="width:25%;"/>
</p>

<h3> Nhận xét: </h3>
<ol> 
  <li> Data nhóm hoàn toàn do thủ công tự chụp, thành viên trong nhóm đã thống nhất với nhau từ trước sẽ tạo nên một bộ dữ liệu “sạch” (clean data). </li>
  <ul> => Nhóm chúng em không có bước tiền xử lý dữ liệu. </ul>
  
  <li> Data nhóm có kích thước khá lớn (17.3GB), và do trong quá trình chuẩn bị dữ liệu, đường truyền mùa dịch không ổn định và quá trình train hay bị tràn, crash trên colab.</li>
  <ul> => Nhóm chúng em quyết định không có bước tăng cường dữ liệu, chấp nhận việc model có thể bị overfitting – sẽ demo sau, nhưng chúng em vẫn đảm bảo model sẽ detect tốt trong các video test được quay với điều kiệu đã ràng buộc từ trước. </ul>
</ol>


<h2> 3. Mô tả thông số bộ dữ liệu </h2>
<div align="middle"> <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/ThongSo01.png" /> </div>
<div align="middle"> <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/ThongSo02.png" /> </div>
<div align="middle"> <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/ThongSo03.png" /> </div>
<h3> Nhận xét thông số: </h3>
<ul>
  <li> Bộ dữ liệu có sự chênh lệch lớn về giữa các class, dự đoán mô hình training sẽ khó xử lý trên nhưng bởi lí do đã nêu trên, nhóm chúng em quyết định sẽ không tiền xử lý dữ liệu. => <strong>unbalanced data</strong> </li>
  
  <li> Nếu đem model training từ tập dữ liệu trên nhưng không có tiền xử lý dữ liệu thì độ chính xác khi áp dụng vào thực tế có thể sẽ thấp hơn => <strong>dự đoán model bị overfitting</strong> </li>
</ul>

<h3> Bộ dữ liệu cho mỗi model </h3>
<p> Hai tập dữ liệu dùng để train hai model đều có kích thước 17.3GB, tập dữ liệu sẽ bao gồm files ảnh chụp định dạng *.jpg các sản phẩm và files label (gán nhãn cho từng ảnh). </p>

<table border="1" style="width:100%;">
  <tr>
    <th> YOLO </th>
    <th> DETECRON2 </th>
  </tr>
  
  <tr>
    <td align="middle" style="width:50%;"> Định dạng files annotaions dưới dạng <strong>*.txt</strong> <br> (Tương ứng với một files ảnh sẽ có files labels trùng tên tương đương) </td>
    <td align="middle"> Định dạng files annotations dưới dạng <strong>*.json</strong>. </td>
  </tr>
  
  <tr>
    <td align="middle" colspan="2"> Bộ dữ liệu dùng để train model yolov4 được chia theo tỉ lệ <strong>80/20</strong> tương đương <strong>train/valid</strong>. </td>
  </tr>
</table>


<h3> Một số trường hợp khó xử lý: </h3>
<ul>
  <li> <strong>Khoảng các giữa các sản phẩm nhỏ hơn nhiều so với khoảng cách từ sản phẩm tới biên màn hình:</strong> </li>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/NhieuSp01.png" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/NhieuSp02.png" style="width:30%;"/>
  </div>
  <ul> => Giải pháp: trong một khung hình chỉ nên xuất hiện một sản phẩm. </ul>

  <li> <strong>Các sản phẩm có đặc điểm cùng màu sắc, cùng hình dáng:</strong> </li>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopDo01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopDo02.jpg" style="width:30%;"/>
  </div>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopTron01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopTron02.jpg" style="width:30%;"/>
  </div>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopVang01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopVang02.jpg" style="width:30%;"/>
  </div>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/LonXanh01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/LonXanh02.jpg" style="width:30%;"/>
  </div>

  <li> <strong>Các sản phẩm có cùng hình dáng khác tông màu:</strong> </li>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Tru01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Tru02.jpg" style="width:30%;"/>
  </div>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopTron01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/HopTron02.jpg" style="width:30%;"/>
  </div>
                                                                                                                                   
  <li> <strong>Các sản phẩm có tông màu khác hình dạng:</strong> </li>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Do01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Do02.jpg" style="width:30%;"/>
  </div>
  <div align="middle">
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Xanh01.jpg" style="width:30%;"/>
    <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/Xanh02.jpg" style="width:30%;"/>
  </div>
</ul>


<h1> Chương 5. Ứng Dụng và Hướng Phát Triển </h1>

<h2> 1. Bài toán đặt ra </h2>
<p> Bài Toán “Nhận Diện Sản Phẩm Thương Mại” mà nhóm em hướng đến để giải quyết là bài toán có hướng phát triển và ứng dụng cao, đặc biệt là trong thời đại công nghệ ngày càng phát triển và “xâm nhập” vào thị trường mua sắm. Nếu model được cải tiến để giải quyết bài toán với model có độ chính xác cao, thì bài toán của chúng em sẽ góp phần quan trọng trong việc xây dựng mô hình mua sắm công nghệ cao, điển hình với dự án của một số công ty lớn sau: </p>

<ul>
  <li> Chuỗi của hàng Amazon Go của công ty Amazon với slogan “Just Walk Out”. </li>
  <li> Dự án quầy thanh toán không thu ngân của công ty Abto Software (Abto Cashierless Checkout). </li>
  <li> .... </li>
</ul>
 
 
<h2> 2. Hướng cải tiến </h2>
<p> Bài toán Nhận Diện Sản Phẩm Thương Mại là một bài toán có hướng phát triển và ứng dụng cao, tuy nhiên để có thể phát triển và đưa bài toán này vào ứng dụng thực tế như “Chuỗi cửa hàng Amazon Go của công ty Amazon” hay “Dự án quầy thanh toán không thu ngân của công ty Abto software” thì trước hết chúng em cần khắc phục một vài nhược điểm: </p>

<ul>
  <li> <strong>Về Data</strong> </li>
  <ul> 
    <li> Bộ dữ liệu không cân bằng, có class chứa tới hơn 400 bức ảnh (Kem Đánh Răng PS Tra Xanh 100g) trong khi có class chỉ chứa gần 30 bức ảnh (Bột chiên giòn Meizan 150g) </li>
      <ul> => <strong>Giải pháp:</strong> Chụp thêm nhiều ảnh đồng thời lựa chọn và sử dụng các kỹ thuật như tăng cường dữ liệu (blur, gray scale, cutout, cutmix, rotate,...) một cách hợp lý. </ul>
    
    <li> Bộ dữ liệu vẫn chưa đa dạng (chỉ có 199 sản phẩm so với hơn 10k sản phẩm trên Bách Hóa Xanh) </li>
      <ul> => <strong>Giải pháp:</strong> Tăng sự đa dạng về số loại sản phẩm, ngoài ra thường xuyên cập nhật data vì mẫu mã và giá cả thay đổi liên tục. </ul>
    
    <li> Độ sáng, phông nền, góc quay chụp vẫn chưa thể hoàn toàn thống nhất do chụp ảnh thủ công. </li>
      <ul> => <strong>Giải pháp:</strong> Quy trình thu thập data phải diễn ra chặt chẽ, có sự đầu tư về phần cứng thiết bị, ví dụ như set up một phòng lab riêng biệt chỉ dành cho việc chụp hình các sản phẩm, các camera set up có giá đỡ cố định ở các góc, ánh sáng điều kiện, phù hợp với bối cảnh thực tế, chú ý đến vấn đề tạo nên một balanced data,... => Clean Data </ul>
  </ul>
  
  <li> <strong>Về Model</strong> </li>
  <ul>
    <p> Vì chưa đủ kiến thức để hiểu một cách rõ ràng được ý nghĩa và phương thức hoạt động bên trong model nên hiện tại chúng em đang phải sử dụng pretrained model. Tuy nhiên việc sử dụng pretrain model cũng gây ảnh hương đến kết quả detect. Vậy nên sau khi đã có kiến thức sâu hơn về Machine learning và Deep learning, thì chúng em sẽ thay đổi model để phù hợp với bộ dữ liệu. </p>
  </ul>
  
  <li> <strong>Vấn đề model khó khăn khi nhận diện một bức ảnh chứa nhiều đối tượng</strong> </li>
  <p>Theo gợi ý của thầy, để cải thiện vấn đề này chúng em dự định:</p>
  <ul>
    <li>Tạo ra ảnh mới bằng cách ghép những ảnh có sẵn trong data.</li>
    <li>Label tất cả các đối tượng xuất hiện trong ảnh.</li>
    <li>Sau đó tiến hành training như các bước ở Chương 4.</li>
  </ul>
  <p>Ví dụ minh họa:</p>
  <p align="middle">
  <img src="https://raw.githubusercontent.com/19522450/CS114.L21/main/FINAL_PROJECT/image/nObject.png" style="width:80%;"/>
  </p>
</ul>

<h2> 3. Hướng phát triển </h2>
<p> Nếu như có thể khắc phục được các vấn đề trên thì chúng em sẽ phát triển thêm một số tính năng để tương tác người dùng đồng thời hướng đến phát triển ứng dụng trên điện thoại để người dùng thuận tiện sử dụng: </p>
  <ul>
    <li> Sử dụng bảng điện tử trực truyết để người dùng có thể theo dõi tình trạng đơn hàng ở quầy thanh toán, tăng tương tác giữa người dùng với hệ thống,... </li>
    <li> Phát triển một ứng dụng điện thoại kết nối với dữ liệu mua sắm của người dùng, để người dùng tiện tra cứu thông tin, giá hóa đơn, sản phẩm,.. Tuy nhiên cũng đảm bảo bảo mật thông tin người dùng. </li>
  </ul>
