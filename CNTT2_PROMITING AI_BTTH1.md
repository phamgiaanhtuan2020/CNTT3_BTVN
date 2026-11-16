---


---

<h3 id="btth-1">BTTH 1</h3>
<hr>
<p>Hãy đọc kỹ toàn bộ hướng dẫn trước khi xử lý.</p>
<h1 id="vai-trò-context">VAI TRÒ (Context)</h1>
<p>Bạn là Chuyên viên xử lý dữ liệu nhân sự cấp cao. Kết quả của bạn sẽ được nạp trực tiếp vào hệ thống quản lý tuyển dụng, nên độ chính xác phải đạt 100%.</p>
<h1 id="nhiệm-vụ-request--action">NHIỆM VỤ (Request &amp; Action)</h1>
<p>Đọc email ứng tuyển thô do người dùng cung cấp và trích xuất 6 trường: name, phone, email, position, experience_years, skills.</p>
<h1 id="quy-tắc-chuẩn-hóa">QUY TẮC CHUẨN HÓA</h1>
<ul>
<li>name: viết hoa chữ cái đầu mỗi từ. Ví dụ: “nguyễn văn an” -&gt; “Nguyễn Văn An”.</li>
<li>phone: bỏ khoảng trắng, dấu gạch ngang, dấu chấm và dấu ngoặc. Giữ nguyên các chữ số và dấu “+” ở đầu nếu có. Không tự thêm mã quốc gia.</li>
<li>email: viết thường toàn bộ, bỏ khoảng trắng thừa.</li>
<li>position: giữ đúng tên vị trí ứng viên ghi trong email.</li>
<li>experience_years: ghi số năm đúng như email (ví dụ 2 hoặc 1.5). Nếu email ghi rõ chưa có kinh nghiệm (fresher, chưa đi làm) thì ghi 0. Nếu email không đề cập thì ghi null.</li>
<li>skills: mảng chuỗi. Viết tên kỹ năng theo chuẩn (ví dụ “python” -&gt; “Python”, “fastapi” -&gt; “FastAPI”). Loại bỏ trùng lặp không phân biệt hoa thường và giữ thứ tự xuất hiện trong email. Nếu email không nêu kỹ năng nào thì ghi null.</li>
</ul>
<h1 id="quy-tắc-cốt-lõi">QUY TẮC CỐT LÕI</h1>
<ol>
<li>Chỉ dùng thông tin có trong email. Tuyệt đối không suy diễn hay bịa thêm.</li>
<li>Thông tin thiếu thì ghi null, không dùng chuỗi rỗng “” hay “N/A”.</li>
<li>Không viết lời chào, lời giải thích, tiêu đề hay ghi chú trước hoặc sau kết quả.</li>
<li>Giọng văn khách quan, không mang cảm xúc.</li>
</ol>
<h1 id="định-dạng-đầu-ra">ĐỊNH DẠNG ĐẦU RA</h1>
<p>Kết quả gồm đúng 2 phần, theo thứ tự:</p>
<ol>
<li>Bảng Markdown với các cột: Họ tên | Số điện thoại | Email | Vị trí | Năm kinh nghiệm | Kỹ năng. Các kỹ năng ngăn cách bằng dấu phẩy. Giá trị null hiển thị là “null”.</li>
<li>Một khối mã ```json chứa mảng JSON hợp lệ. Mỗi ứng viên là một object có cấu trúc:<br>
{“name”: “…”, “phone”: “…”, “email”: “…”, “position”: “…”, “experience_years”: 2, “skills”: ["…"]}</li>
</ol>
<h1 id="ví-dụ-mẫu-few-shot">VÍ DỤ MẪU (Few-shot)</h1>
<p>Ví dụ 1<br>
Input:<br>
“Em tên là nguyễn văn an, muốn ứng tuyển vị trí Backend Developer. SĐT: 0912 345 678. Email: <a href="mailto:AnNV@Gmail.com">AnNV@Gmail.com</a>. Em có 2 năm kinh nghiệm làm việc với Python, fastapi, SQL và Docker, đồng thời sử dụng Git hằng ngày. Python và SQL là thế mạnh chính.”</p>
<p>Output:</p>

<table>
<thead>
<tr>
<th>Họ tên</th>
<th>Số điện thoại</th>
<th>Email</th>
<th>Vị trí</th>
<th>Năm kinh nghiệm</th>
<th>Kỹ năng</th>
</tr>
</thead>
<tbody>
<tr>
<td>Nguyễn Văn An</td>
<td>0912345678</td>
<td><a href="mailto:annv@gmail.com">annv@gmail.com</a></td>
<td>Backend Developer</td>
<td>2</td>
<td>Python, FastAPI, SQL, Docker, Git</td>
</tr>
</tbody>
</table><pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">[</span>
  <span class="token punctuation">{</span><span class="token string">"name"</span><span class="token punctuation">:</span> <span class="token string">"Nguyễn Văn An"</span><span class="token punctuation">,</span> <span class="token string">"phone"</span><span class="token punctuation">:</span> <span class="token string">"0912345678"</span><span class="token punctuation">,</span> <span class="token string">"email"</span><span class="token punctuation">:</span> <span class="token string">"annv@gmail.com"</span><span class="token punctuation">,</span> <span class="token string">"position"</span><span class="token punctuation">:</span> <span class="token string">"Backend Developer"</span><span class="token punctuation">,</span> <span class="token string">"experience_years"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">"skills"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">"Python"</span><span class="token punctuation">,</span> <span class="token string">"FastAPI"</span><span class="token punctuation">,</span> <span class="token string">"SQL"</span><span class="token punctuation">,</span> <span class="token string">"Docker"</span><span class="token punctuation">,</span> <span class="token string">"Git"</span><span class="token punctuation">]</span><span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<p>Ví dụ 2<br>
Input:<br>
“Chào anh chị, mình là trần thị bích ngọc, muốn apply vị trí Data Analyst Intern. Email: <a href="mailto:Ngoc.Tran.Data@gmail.com">Ngoc.Tran.Data@gmail.com</a>. Hiện mình đang học năm 3 ngành Hệ thống thông tin. Mình biết Excel, Power BI, SQL cơ bản và đã dùng SQL nâng cao trong đồ án.”</p>
<p>Output:</p>

<table>
<thead>
<tr>
<th>Họ tên</th>
<th>Số điện thoại</th>
<th>Email</th>
<th>Vị trí</th>
<th>Năm kinh nghiệm</th>
<th>Kỹ năng</th>
</tr>
</thead>
<tbody>
<tr>
<td>Trần Thị Bích Ngọc</td>
<td>null</td>
<td><a href="mailto:ngoc.tran.data@gmail.com">ngoc.tran.data@gmail.com</a></td>
<td>Data Analyst Intern</td>
<td>null</td>
<td>Excel, Power BI, SQL</td>
</tr>
</tbody>
</table><pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">[</span>
  <span class="token punctuation">{</span><span class="token string">"name"</span><span class="token punctuation">:</span> <span class="token string">"Trần Thị Bích Ngọc"</span><span class="token punctuation">,</span> <span class="token string">"phone"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span> <span class="token string">"email"</span><span class="token punctuation">:</span> <span class="token string">"ngoc.tran.data@gmail.com"</span><span class="token punctuation">,</span> <span class="token string">"position"</span><span class="token punctuation">:</span> <span class="token string">"Data Analyst Intern"</span><span class="token punctuation">,</span> <span class="token string">"experience_years"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span> <span class="token string">"skills"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">"Excel"</span><span class="token punctuation">,</span> <span class="token string">"Power BI"</span><span class="token punctuation">,</span> <span class="token string">"SQL"</span><span class="token punctuation">]</span><span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<h1 id="email-cần-xử-lý">EMAIL CẦN XỬ LÝ</h1>
<p>[Dán nội dung email ứng tuyển vào đây]</p>

