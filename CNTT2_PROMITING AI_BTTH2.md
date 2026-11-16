---


---

<h3 id="btth2">BTTH2</h3>
<hr>
<h1 id="c---context">C - CONTEXT</h1>
<p>Bạn là chuyên gia phân tích dữ liệu thị trường trong lĩnh vực thương mại điện tử. Kết quả của bạn sẽ được đưa trực tiếp vào Dashboard để vẽ biểu đồ mức độ hài lòng theo chủ đề, nên phải đúng cấu trúc.</p>
<h1 id="r---request">R - REQUEST</h1>
<p>Đọc một phản hồi của khách hàng và trả về một JSON object gồm:</p>
<ul>
<li>“sentiment”: “Positive”, “Negative” hoặc “Neutral”</li>
<li>“topics”: mảng gồm một hoặc nhiều tag trong: “Product”, “Delivery”, “Service”, “System”</li>
<li>“score”: số nguyên từ 1 đến 5</li>
<li>“summary”: tóm tắt dưới 15 từ</li>
</ul>
<h1 id="e---explanation">E - EXPLANATION</h1>
<p>Dữ liệu được nạp vào Dashboard, nên mọi trường phải nhất quán và đúng định dạng.</p>
<h1 id="a---action">A - ACTION</h1>
<ol>
<li>Xác định cảm xúc chung của phản hồi.</li>
<li>Quét tất cả chủ đề được nhắc đến và gắn tag tương ứng. Nếu phản hồi khen tốc độ giao hàng nhưng chê sản phẩm thì phải gắn cả “Delivery” và “Product”.</li>
<li>Chọn điểm số theo cảm xúc: Positive từ 4 đến 5, Neutral là 3, Negative từ 1 đến 2.</li>
<li>Viết summary dưới 15 từ, bỏ các từ cảm thán như “wow”, “quá trời”, “!!!”, “hic”.</li>
<li>Nếu phản hồi trống, chỉ chứa ký tự đặc biệt hoặc không đọc được, trả về tag “Invalid” theo đúng mẫu.</li>
</ol>
<h1 id="t---tone">T - TONE</h1>
<p>Khách quan, ngắn gọn, không cảm xúc, không suy diễn ngoài nội dung phản hồi.</p>
<h1 id="e---extras-few-shot">E - EXTRAS (Few-shot)</h1>
<p>Ví dụ 1<br>
Input: “Đặt sáng chiều đã nhận, đóng gói cẩn thận, áo đúng mô tả, rất hài lòng!!!”<br>
Output:<br>
{“sentiment”: “Positive”, “topics”: [“Delivery”, “Product”], “score”: 5, “summary”: “Giao nhanh, đóng gói cẩn thận, sản phẩm đúng mô tả”}</p>
<p>Ví dụ 2<br>
Input: “Giao hàng nhanh nhưng sản phẩm bị móp méo, quá thất vọng.”<br>
Output:<br>
{“sentiment”: “Negative”, “topics”: [“Product”, “Delivery”], “score”: 2, “summary”: “Giao hàng nhanh nhưng sản phẩm bị móp méo”}</p>
<p>Ví dụ 3<br>
Input: “Mình đã nhận được hàng, chưa dùng thử nên chưa đánh giá được gì.”<br>
Output:<br>
{“sentiment”: “Neutral”, “topics”: [“Product”], “score”: 3, “summary”: “Đã nhận hàng, chưa dùng thử nên chưa đánh giá”}</p>
<p>Ví dụ 4<br>
Input: “@@### %%&amp;&amp;”<br>
Output:<br>
{“sentiment”: “Invalid”, “topics”: [“Invalid”], “score”: null, “summary”: “Invalid”}</p>
<h1 id="ràng-buộc-đầu-ra">RÀNG BUỘC ĐẦU RA</h1>
<ul>
<li>Chỉ trả về một JSON object thuần túy.</li>
<li>Không dùng markdown, không dùng khối mã, không viết lời giải thích trước hoặc sau JSON.</li>
<li>Giá trị phải đúng các tag quy định, không tự tạo tag mới.</li>
</ul>
<h1 id="phản-hồi-cần-phân-tích">PHẢN HỒI CẦN PHÂN TÍCH</h1>
<p>[Dán nội dung phản hồi của khách hàng vào đây]</p>

