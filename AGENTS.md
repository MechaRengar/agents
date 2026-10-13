\# 🤖 AI AGENT INSTRUCTIONS \& OPERATIONAL RULES



> \*\*Mục tiêu:\*\* Xây dựng quy trình làm việc thống nhất cho mọi AI Agent trong dự án, tối thiểu hóa mã nguồn mới, bảo vệ dữ liệu và bảo đảm mọi thay đổi đều có thể kiểm chứng.

>

> \*\*Triết lý cốt lõi:\*\* Giải pháp tốt nhất là giải pháp đơn giản nhất giải quyết đúng bài toán, với lượng mã mới ít nhất có thể mà không đánh đổi tính đúng đắn, bảo mật hoặc khả năng bảo trì.



\---



\## 0. NGUYÊN TẮC ƯU TIÊN \& PHẠM VI ÁP DỤNG



\### 0.1. Thứ tự ưu tiên



Khi các chỉ dẫn xung đột, tuân thủ theo thứ tự:



1\. Các chính sách an toàn, bảo mật và giới hạn của nền tảng, công cụ đang sử dụng.

2\. Yêu cầu trực tiếp và các xác nhận cụ thể của người dùng.

3\. Các quy tắc bảo vệ dữ liệu, Git và production trong tài liệu này.

4\. Kế hoạch triển khai đã được người dùng phê duyệt.

5\. Các quy tắc kiến trúc, phong cách lập trình và tư duy Ponytail.

6\. Quy ước hiện có của codebase và các mặc định của công cụ.



Các quy tắc bảo vệ dữ liệu và production không được tự ý nới lỏng chỉ vì việc đó giúp hoàn thành công việc nhanh hơn.



Nếu không thể đồng thời đáp ứng các yêu cầu, hãy dừng tại ranh giới an toàn, giải thích mâu thuẫn và hỏi người dùng.



\### 0.2. Phạm vi



\- Áp dụng cho mọi tác vụ phân tích, lập kế hoạch, viết mã, sửa lỗi, kiểm thử, đánh giá và bảo trì repository.

\- Không tự mở rộng phạm vi hoặc tự thêm tính năng ngoài yêu cầu.

\- Không mặc định rằng một công cụ, MCP, plugin, kỹ năng hoặc lệnh CLI luôn khả dụng.

\- Không tuyên bố đã đọc, sửa, chạy, kiểm thử hoặc xác minh điều gì nếu chưa thực sự thực hiện.

\- Tệp này là chỉ dẫn vận hành, không thay thế cơ chế phân quyền của hệ điều hành, Git, cơ sở dữ liệu hoặc nền tảng triển khai.



\---



\## 1. QUY TẮC NGÔN NGỮ \& BÁO CÁO



\### 1.1. Ngôn ngữ bắt buộc



\- Toàn bộ trao đổi, kế hoạch, thiết kế, đánh giá, báo cáo và nội dung giải thích phải sử dụng tiếng Việt.

\- Không sử dụng tiếng Anh để trình bày kế hoạch hoặc giải thích cho người dùng.

\- Giữ nguyên các định danh kỹ thuật cần thiết như tên biến, hàm, API, class, package, lệnh CLI và thông báo lỗi gốc.

\- Nội dung trong mã nguồn tuân thủ quy ước hiện có của dự án; không dịch tên định danh kỹ thuật hoặc phá vỡ giao thức chỉ để đáp ứng quy tắc ngôn ngữ.



\### 1.2. Minh bạch phạm vi theo Ponytail



Mỗi báo cáo kết quả cuối cùng phải nêu ngắn gọn:



\- \*\*Đã thực hiện:\*\* Những thay đổi chính và kết quả kiểm chứng.

\- \*\*Đã bỏ qua hoặc chưa xác minh:\*\* Những phần không nằm trong phạm vi hoặc chưa thể kiểm tra.

\- \*\*Đánh đổi và rủi ro:\*\* Những hệ quả tiềm ẩn cần người dùng biết.



Không được ghi “không có rủi ro” nếu chưa có đủ căn cứ để kết luận.



\---



\## 2. TRIẾT LÝ THIẾT KẾ \& PONYTAIL



\### 2.1. Thang quyết định Ponytail



Trước khi thêm mã, lần lượt đặt các câu hỏi sau và dừng ngay khi tìm được giải pháp phù hợp:



1\. \*\*Có thực sự cần thay đổi không?\*\* Nếu không cần thiết, không thêm mã. Nếu yêu cầu mơ hồ, hỏi lại.

2\. \*\*Codebase đã có giải pháp chưa?\*\* Ưu tiên tái sử dụng helper, service, component, module và pattern hiện có.

3\. \*\*Nền tảng có hỗ trợ sẵn không?\*\* Ưu tiên API chuẩn của ngôn ngữ, runtime, framework hoặc trình duyệt.

4\. \*\*Dependency hiện có có đáp ứng được không?\*\* Không cài thêm thư viện nếu giải pháp hiện tại đáp ứng đầy đủ yêu cầu.

5\. \*\*Có thể đơn giản hóa không?\*\* Chọn cách triển khai dễ đọc, dễ kiểm thử và ít nhánh logic nhất.

6\. \*\*Viết lượng mã tối thiểu cần thiết.\*\* Không tạo mã dự phòng cho những nhu cầu chưa được xác nhận.



Mục tiêu không phải là giảm số dòng bằng mọi giá, mà là giảm tổng độ phức tạp của hệ thống.



\### 2.2. Các nguyên tắc bắt buộc



\- \*\*KISS:\*\* Ưu tiên giải pháp đơn giản.

\- \*\*YAGNI:\*\* Không triển khai nhu cầu chưa được yêu cầu hoặc chưa có căn cứ thực tế.

\- \*\*DRY có chọn lọc:\*\* Tránh lặp logic thực sự giống nhau, nhưng không tạo abstraction chỉ để loại bỏ vài dòng trùng lặp.

\- \*\*Single Responsibility:\*\* Mỗi hàm hoặc module có trách nhiệm rõ ràng.

\- \*\*Backend-first:\*\* Ưu tiên tính đúng đắn nghiệp vụ, toàn vẹn dữ liệu, bảo mật và hiệu năng truy vấn.

\- \*\*Sửa nguyên nhân gốc:\*\* Truy vết luồng xử lý và các nơi gọi trước khi sửa bug.

\- \*\*Xóa code có kiểm soát:\*\* Loại bỏ mã thừa khi đã xác minh không có người dùng, caller hoặc phụ thuộc nào bị ảnh hưởng.

\- \*\*Giữ nguyên hành vi ngoài phạm vi:\*\* Không thay đổi API contract, cấu trúc dữ liệu, hành vi nghiệp vụ hoặc giao diện công khai nếu không cần thiết cho yêu cầu đã duyệt.



\### 2.3. Quy tắc abstraction



Không tạo abstraction chỉ vì dự đoán có thể cần mở rộng trong tương lai.



Chỉ tạo interface, factory, adapter, generic wrapper hoặc lớp cấu hình khi có nhu cầu thực tế, chẳng hạn:



\- Tách biệt ranh giới với nhà cung cấp bên ngoài.

\- Có nhiều implementation thực sự hoặc cần thay thế implementation.

\- Cô lập phụ thuộc để kiểm thử.

\- Giảm coupling hoặc xử lý độ phức tạp hiện hữu.



Không áp dụng quy tắc “một dòng code” như tiêu chí bắt buộc. Ưu tiên khả năng đọc, tính đúng đắn và khả năng bảo trì.



\### 2.4. Quy tắc dữ liệu



\- Giữ nguyên định dạng dữ liệu tự nhiên của nền tảng khi phù hợp.

\- Không tạo DTO, mapper hoặc wrapper trung gian nếu không mang lại giá trị thực tế.

\- Không bỏ qua validation tại ranh giới dữ liệu không đáng tin cậy.

\- Không thay đổi schema, migration hoặc API contract chỉ để làm code gọn hơn.

\- Không đánh đổi tính nhất quán giao dịch hoặc xử lý lỗi để giảm số dòng mã.



\---



\## 3. QUY TẮC AN TOÀN NGHIÊM NGẶT



\### 3.1. Vùng bảo vệ tuyệt đối



Không tự ý trực tiếp tạo, sửa, di chuyển hoặc xóa bất kỳ tệp hay thư mục nào thuộc các nhóm sau:



\- `database/`

\- `dist/`

\- `node\_modules/`

\- Tệp log.

\- Tệp tạm thời.

\- Tệp backup.

\- Dữ liệu giao dịch, dữ liệu thực tế và các tài nguyên lưu trữ có nguy cơ gây mất dữ liệu.



Chỉ được thao tác trong vùng bảo vệ khi có chỉ thị riêng bằng văn bản, xác định cụ thể đường dẫn và thao tác được phép.



Việc người dùng phê duyệt kế hoạch tổng thể không tự động thay thế sự cho phép riêng này.



Không được tự ý chạy lệnh dọn dẹp, ghi đè, tái tạo hoặc xóa dữ liệu trong các vùng trên.



\### 3.2. Lệnh có tác động phụ



Trước khi chạy một lệnh có thể thay đổi dữ liệu hoặc môi trường, phải xác định:



\- Phạm vi tệp và tài nguyên bị tác động.

\- Khả năng ghi đè hoặc xóa dữ liệu hiện hữu.

\- Khả năng thay đổi cơ sở dữ liệu, dependency, cấu hình hoặc môi trường dùng chung.

\- Khả năng tác động đến production.

\- Khả năng sinh tệp trong vùng bảo vệ.



Nếu tác động chưa rõ, không chạy lệnh theo kiểu thử và sai. Hãy kiểm tra tài liệu hoặc dùng phương pháp chỉ đọc trước.



Các thao tác migration, reset database, xóa dữ liệu, thay đổi quyền, triển khai production và các hành động khó đảo ngược phải được đánh giá riêng. Nếu chưa có sự cho phép cụ thể, phải dừng lại và hỏi người dùng.



\### 3.3. Bảo vệ bí mật



\- Không đưa API key, token, mật khẩu, private key hoặc thông tin xác thực vào mã nguồn, log, báo cáo hay commit.

\- Không tự ý đọc hoặc xuất dữ liệu nhạy cảm khi không cần thiết.

\- Không ghi thông tin xác thực vào tệp kế hoạch.

\- Khi phát hiện bí mật bị lộ, báo cáo vị trí và mức độ ảnh hưởng mà không sao chép giá trị bí mật vào phản hồi.

\- Không tự ý gửi mã nguồn, dữ liệu hoặc thông tin nội bộ đến dịch vụ bên ngoài nếu chưa được cho phép.



\### 3.4. An toàn Git



Trước khi sửa mã:



\- Kiểm tra trạng thái repository bằng `git status`.

\- Xác định nhánh hiện tại và các thay đổi chưa commit.

\- Bảo toàn mọi thay đổi có sẵn của người dùng.

\- Không tự ý checkout, reset, stash, revert, rebase hoặc ghi đè các thay đổi chưa được xác nhận.

\- Không mặc định rằng working tree sạch.



Tuyệt đối không tự ý thực hiện:



\- `git push` lên bất kỳ remote nào.

\- Merge hoặc đưa mã vào nhánh dùng chung.

\- Tạo tag phát hành.

\- Triển khai mã lên production.



Phải có xác nhận rõ ràng của người dùng trước khi thực hiện thao tác tương ứng trên remote hoặc môi trường dùng chung.



\### 3.5. Pull Request



\- Chuẩn bị nội dung PR gồm mục tiêu, thay đổi chính, kết quả kiểm thử, phần đã tối giản và rủi ro còn lại.

\- Chỉ tạo PR trên nền tảng bên ngoài khi có đủ quyền và sự cho phép thực hiện các thao tác remote cần thiết.

\- Nếu chưa được phép push hoặc tạo PR, chỉ cung cấp nội dung PR để người dùng xem xét.

\- Không tuyên bố PR đã được tạo nếu chưa nhận được xác nhận thành công từ công cụ.



\---



\## 4. QUY TRÌNH THỰC THI 5 BƯỚC



Mọi tác vụ thay đổi mã nguồn phải tuân thủ tuần tự:



`PLANNING → ACTING → TESTING → VERIFYING → REFLECTING`



Không được bỏ qua bước phê duyệt hoặc tuyên bố hoàn thành khi chưa thực hiện đủ các bước cần thiết.



\### BƯỚC 1 — PLANNING



Đây là bước bắt buộc trước mọi thay đổi mã nguồn.



\#### 1.1. Khảo sát



\- Đọc yêu cầu và xác định kết quả mong muốn.

\- Kiểm tra hướng dẫn dự án và quy tắc của công cụ đang sử dụng.

\- Khảo sát codebase theo quy tắc CodeGraph tại Phần 7.

\- Kiểm tra trạng thái Git và các thay đổi có sẵn.

\- Truy vết luồng xử lý từ đầu đến cuối, bao gồm caller, service, repository, API và các thành phần liên quan khi cần thiết.

\- Xác định rủi ro dữ liệu, bảo mật, hiệu năng và tương thích.



Không đọc hoặc sửa hàng loạt tệp một cách thiếu định hướng khi chưa xác định được phạm vi.



\#### 1.2. Khi nào phải hỏi lại?



Hỏi người dùng nếu:



\- Thiếu thông tin có thể làm thay đổi đáng kể cách triển khai.

\- Có nhiều cách hiểu dẫn đến hành vi nghiệp vụ khác nhau.

\- Có nguy cơ mất dữ liệu hoặc ảnh hưởng production.

\- Cần mở rộng phạm vi, thay đổi API contract hoặc schema ngoài yêu cầu.

\- Không thể xác định phương án an toàn từ thông tin hiện có.



Không hỏi lại những chi tiết nhỏ mà codebase đã xác định rõ và không ảnh hưởng đến kết quả hoặc phạm vi.



\#### 1.3. Lập kế hoạch



Ghi kế hoạch vào:



`.agents/implementation\_plan.md`



Kế hoạch phải bao gồm:



1\. Mục tiêu và phạm vi.

2\. Các tệp dự kiến tạo mới hoặc chỉnh sửa.

3\. Các tệp hoặc khu vực không được tác động.

4\. Luồng logic và các caller cần kiểm tra.

5\. Giải pháp tối giản được chọn và các phương án bị loại bỏ nếu cần giải thích.

6\. Tác động đến API, database, migration, dependency và cấu hình.

7\. Kế hoạch kiểm thử.

8\. Kế hoạch xác minh và tiêu chí hoàn thành.

9\. Rủi ro, đánh đổi và những phần không nằm trong phạm vi.



Nếu thư mục `.agents/` chưa tồn tại, chỉ tạo tệp kế hoạch trong bước này khi được phép tạo thư mục phục vụ công việc; không sửa các tệp mã nguồn khác.



\#### 1.4. Chờ phê duyệt



Sau khi hoàn tất kế hoạch:



\- Tóm tắt kế hoạch bằng tiếng Việt.

\- Chờ người dùng xác nhận chính xác bằng `Approved` hoặc xác nhận tương đương có ý nghĩa rõ ràng.

\- Không bắt đầu sửa mã nguồn trước khi được duyệt.

\- Không tự hiểu sự im lặng là đồng ý.

\- Không coi yêu cầu chung như “xem giúp”, “phân tích” hoặc “lập kế hoạch” là quyền thực thi.



Nếu kế hoạch thay đổi đáng kể sau khi duyệt, phải cập nhật kế hoạch và chờ phê duyệt lại.



\*\*Lưu ý:\*\* Phê duyệt kế hoạch không tự động cho phép thao tác trong vùng bảo vệ, push, merge hoặc triển khai production.



\### BƯỚC 2 — ACTING



Chỉ bắt đầu khi kế hoạch đã được duyệt.



\- Thực hiện đúng phạm vi và thứ tự trong kế hoạch.

\- Ưu tiên sửa ít tệp nhất có thể.

\- Tái sử dụng thành phần sẵn có.

\- Không thêm dependency nếu chưa chứng minh được sự cần thiết.

\- Không thay đổi hành vi ngoài phạm vi.

\- Không sửa tệp không liên quan chỉ để làm đẹp hoặc refactor.

\- Không tự ý sửa dữ liệu, cấu hình hoặc tài nguyên bị bảo vệ.

\- Không tự ý commit, push, merge hoặc triển khai.



Nếu phát hiện yêu cầu mới hoặc cần thay đổi phạm vi:



1\. Dừng phần công việc bị ảnh hưởng.

2\. Giải thích vấn đề và tác động.

3\. Cập nhật kế hoạch đề xuất.

4\. Chờ người dùng phê duyệt lại trước khi thực hiện thay đổi bổ sung.



\### BƯỚC 3 — TESTING



Kiểm thử phải thực dụng, tập trung vào rủi ro thực tế.



\#### 3.1. Ưu tiên kiểm thử



Bắt buộc ưu tiên các luồng:



\- Xử lý tiền tệ, thanh toán, số dư và giao dịch.

\- Xác thực, phân quyền và ranh giới bảo mật.

\- Validation dữ liệu đầu vào.

\- Logic phân nhánh, parser và xử lý trạng thái.

\- Xử lý lỗi, timeout, retry và idempotency.

\- Đặt hàng đồng thời, tính nhất quán dữ liệu và transaction.

\- Các luồng nghiệp vụ trực tiếp bị ảnh hưởng bởi thay đổi.



Không cần tạo test riêng cho getter/setter hoặc đoạn mã thuần túy, không có rủi ro đáng kể và đã được bao phủ đầy đủ ở tầng phù hợp.



Không đánh giá mức độ cần test chỉ dựa trên số dòng code.



\#### 3.2. Thực thi kiểm thử



\- Tìm hiểu lệnh test chính thức của dự án trước khi chạy.

\- Ưu tiên test mục tiêu trước, sau đó chạy các bộ test liên quan rộng hơn.

\- Chạy bộ kiểm thử theo yêu cầu dự án và khả năng của môi trường.

\- Kiểm tra kết quả thực tế, mã thoát và báo cáo lỗi.

\- Không tự tạo kết quả test giả hoặc tuyên bố đã chạy test khi chưa chạy.



\#### 3.3. Xử lý test thất bại



Khi test thất bại:



1\. Xác định lỗi có liên quan đến thay đổi mới hay đã tồn tại từ trước.

2\. Tìm nguyên nhân gốc.

3\. Chỉ sửa trong phạm vi kế hoạch đã duyệt.

4\. Chạy lại test liên quan sau khi sửa.

5\. Nếu lỗi nằm ngoài phạm vi, môi trường không khả dụng hoặc cần quyền bổ sung, báo cáo và xin phê duyệt thay vì tự mở rộng công việc.



Không được bỏ qua test thất bại bằng cách xóa test, nới lỏng assertion, vô hiệu hóa validation hoặc làm yếu kiểm tra bảo mật chỉ để đạt kết quả xanh.



\### BƯỚC 4 — VERIFYING



Xác minh độc lập các thay đổi đã thực hiện.



\#### 4.1. Các kiểm tra cần thiết



Tùy phạm vi và công cụ của dự án, kiểm tra:



\- Cú pháp và khả năng biên dịch.

\- Lint và quy chuẩn mã nguồn.

\- Kiểu dữ liệu và type safety.

\- Các test liên quan.

\- Tương thích API và dữ liệu.

\- Xử lý ngoại lệ và tài nguyên.

\- Ảnh hưởng đến các caller.

\- Các thay đổi ngoài dự kiến trong `git diff`.



Không tự ý chạy lệnh có thể ghi vào vùng bảo vệ nếu chưa có sự cho phép tương ứng.



\#### 4.2. Vòng lặp tự sửa lỗi



Chỉ tự sửa lỗi khi đáp ứng đồng thời các điều kiện:



\- Lỗi thuộc phạm vi kế hoạch đã duyệt.

\- Phương án sửa không vi phạm quy tắc an toàn.

\- Không cần thêm quyền hoặc thay đổi kiến trúc chưa được duyệt.

\- Có thể xác minh lại kết quả.



Nếu không đáp ứng các điều kiện trên, dừng và hỏi người dùng.



Không lặp vô hạn. Khi không tìm được nguyên nhân hoặc đã thử các phương án hợp lý mà lỗi vẫn tồn tại, báo cáo bằng chứng và hướng xử lý tiếp theo.



\#### 4.3. Điều kiện báo hoàn thành



Chỉ báo `✅ DONE` khi đã xác minh đầy đủ các tiêu chí bắt buộc trong phạm vi.



Nếu còn test thất bại, kiểm tra chưa chạy, môi trường bị giới hạn hoặc lỗi tồn tại từ trước chưa được giải quyết, phải nêu rõ trạng thái thực tế. Không tuyên bố sạch lỗi hoặc hoàn thành tuyệt đối khi thiếu bằng chứng.



\### BƯỚC 5 — REFLECTING \& AUDITING



Rà soát lần cuối trước khi kết thúc.



\#### 5.1. Kiểm toán Ponytail



Tự hỏi:



\- Có đoạn code nào không cần tồn tại không?

\- Có thể tái sử dụng giải pháp hiện có không?

\- Có abstraction hoặc dependency thừa không?

\- Có thể xóa logic cũ thay vì chồng thêm logic mới không?

\- Có nhánh xử lý, wrapper hoặc cấu hình không cần thiết không?

\- Có làm thay đổi hành vi ngoài yêu cầu không?



Chỉ thực hiện refactor bổ sung nếu nằm trong phạm vi đã duyệt và không tạo rủi ro mới.



\#### 5.2. Đánh giá kỹ thuật



Đánh giá theo mức độ liên quan:



\- Hiệu năng và độ phức tạp.

\- Khả năng đọc và bảo trì.

\- Khả năng mở rộng cần thiết.

\- Tính nhất quán và an toàn dữ liệu.

\- Chỉ mục DB hoặc caching khi có bằng chứng về nhu cầu.

\- Khả năng tương thích với codebase hiện tại.



Không tự ý thêm index, cache hoặc hệ thống mới chỉ vì chúng có thể hữu ích trong tương lai.



\#### 5.3. CodeGraph



Nếu repository sử dụng CodeGraph, cập nhật chỉ mục khi có thay đổi mã nguồn và công cụ hỗ trợ. Không tuyên bố đã cập nhật nếu chưa thực hiện thành công.



\#### 5.4. Báo cáo cuối cùng



Báo cáo ngắn gọn bằng tiếng Việt, gồm:



1\. Những gì đã thay đổi.

2\. Các tệp bị ảnh hưởng.

3\. Test, lint, build và các bước xác minh đã thực sự chạy.

4\. Kết quả thành công hoặc thất bại.

5\. Phần đã chủ động bỏ qua hoặc chưa xác minh.

6\. Rủi ro và đánh đổi còn lại.

7\. Trạng thái Git và PR nếu có liên quan.



\---



\## 5. QUY CHUẨN LẬP TRÌNH



\### 5.1. Clean Code



\- Viết mã rõ nghĩa, dễ đọc và dễ bảo trì.

\- Tên biến, hàm và class phản ánh đúng mục đích.

\- Hàm ngắn gọn nhưng không chia nhỏ một cách máy móc.

\- Tuân thủ quy ước định danh của ngôn ngữ và codebase.

\- Không lặp lại logic nghiệp vụ quan trọng.

\- Không thêm comment mô tả điều hiển nhiên; ưu tiên giải thích lý do và các quyết định không hiển nhiên.

\- Không chỉnh sửa định dạng hàng loạt ở các tệp ngoài phạm vi.



\### 5.2. API, Database và Network



\- Xử lý lỗi có chủ đích tại tầng phù hợp.

\- Dùng `try-catch` khi cần chuyển đổi lỗi, bổ sung ngữ cảnh, phục hồi, cleanup hoặc bảo đảm tài nguyên được giải phóng.

\- Không bắt lỗi chỉ để ném lại nguyên trạng nếu không mang lại giá trị.

\- Không nuốt lỗi hoặc trả kết quả thành công giả.

\- Không để Promise rejection bị bỏ quên.

\- Tuân thủ cơ chế xử lý exception hiện có của framework.

\- Bảo đảm transaction, rollback và tính nhất quán dữ liệu theo yêu cầu nghiệp vụ.

\- Không tự ý retry các thao tác không an toàn hoặc không có cơ chế idempotency phù hợp.



\### 5.3. Bảo mật và validation



\- Xác thực dữ liệu tại ranh giới tin cậy.

\- Kiểm tra quyền trước khi thực hiện thao tác được bảo vệ.

\- Không tin dữ liệu từ client, provider hoặc dịch vụ bên ngoài một cách mặc định.

\- Không làm lộ thông tin nhạy cảm trong phản hồi lỗi hoặc log.

\- Không hạ thấp kiểm tra bảo mật để làm test pass.

\- Tuân thủ các cơ chế xác thực, phân quyền và quản lý bí mật hiện có của dự án.



\### 5.4. Dependency



Trước khi thêm thư viện:



1\. Kiểm tra nền tảng có hỗ trợ sẵn không.

2\. Kiểm tra dependency hiện có.

3\. Xác định lợi ích thực tế và chi phí bảo trì.

4\. Xác định ảnh hưởng đến lockfile, môi trường triển khai và bảo mật.

5\. Đưa vào kế hoạch và chờ phê duyệt.



Không tự ý cập nhật hàng loạt dependency hoặc thay đổi phiên bản framework ngoài phạm vi.



\---



\## 6. QUY TẮC LÀM VIỆC VỚI CÔNG CỤ AI



\### 6.1. Tương thích đa Agent



Các công cụ như Codex, Cline và Antigravity có thể có cơ chế nạp hướng dẫn, quyền thực thi và khả năng tích hợp khác nhau.



\- Không mặc định mọi Agent đều tự động nạp toàn bộ tệp hướng dẫn.

\- Kiểm tra quy tắc của công cụ khi có nghi ngờ.

\- Không giả định một MCP, plugin hoặc CLI luôn tồn tại.

\- Không tự cài công cụ hoặc thay đổi cấu hình toàn hệ thống nếu chưa được phép.

\- Không tạo thêm tệp hướng dẫn trùng lặp nếu không có nhu cầu thực tế.

\- Khi phát hiện xung đột giữa hướng dẫn dự án và hành vi của công cụ, báo cáo rõ thay vì âm thầm bỏ qua.



\### 6.2. Tính trung thực khi sử dụng công cụ



\- Chỉ mô tả thao tác đã thực sự thực hiện.

\- Phân biệt kết quả quan sát được với suy luận.

\- Không giả lập kết quả chạy lệnh hoặc kiểm thử.

\- Nếu công cụ lỗi, không khả dụng hoặc thiếu quyền, báo rõ.

\- Nếu không thể xác minh một kết luận, nêu giới hạn đó.



\---



<!-- CODEGRAPH\_START -->



\## 7. ĐIỀU TRA MÃ NGUỒN VỚI CODEGRAPH



Trong repository có thư mục `.codegraph/` ở root, ưu tiên CodeGraph trước khi dùng `grep`, `find` hoặc đọc từng tệp để định vị mã nguồn.



\### 7.1. Sử dụng MCP



\- Nếu có công cụ MCP CodeGraph phù hợp, ưu tiên `codegraph\_explore`.

\- Truy vấn bằng câu hỏi cụ thể, tên symbol, file hoặc luồng xử lý cần điều tra.

\- Ưu tiên kết quả thể hiện mã nguồn hiện tại, vị trí dòng và call path.

\- Theo dõi cả các điểm gọi gián tiếp hoặc dynamic dispatch nếu liên quan.

\- Nếu symbol bị hoãn nạp, tìm nạp theo hướng dẫn của công cụ.



\### 7.2. Sử dụng CLI



Nếu MCP không khả dụng nhưng CLI đã được cài đặt, có thể dùng:



```bash

codegraph explore "<tên symbol hoặc câu hỏi tra cứu>"

```



Chỉ sử dụng khi đã xác minh công cụ tồn tại và lệnh phù hợp với môi trường.



\### 7.3. Trường hợp không có CodeGraph



\- Nếu repository không có `.codegraph/`, bỏ qua CodeGraph.

\- Không tự ý khởi tạo hoặc đánh chỉ mục repository khi chưa có yêu cầu hoặc cho phép tương ứng.

\- Có thể sử dụng các phương pháp khảo sát khác theo phạm vi công việc.

\- Không tuyên bố đã truy vết toàn bộ call path nếu chỉ kiểm tra một phần.



\### 7.4. Cập nhật chỉ mục



Chỉ cập nhật hoặc tạo lại chỉ mục sau khi thay đổi mã nguồn khi repository thực sự sử dụng CodeGraph và có công cụ phù hợp.



Trước khi chạy lệnh cập nhật, xác định phạm vi tệp sẽ bị ghi. Không ghi đè dữ liệu hoặc tài nguyên được bảo vệ nếu chưa được cho phép.



<!-- CODEGRAPH\_END -->



\---



\## 8. TIÊU CHÍ HOÀN THÀNH CÔNG VIỆC



Một tác vụ chỉ được xem là hoàn thành khi:



\- Đã triển khai đúng kế hoạch được duyệt.

\- Không tự ý mở rộng phạm vi.

\- Không vi phạm vùng bảo vệ và quy tắc Git.

\- Đã thực hiện các bước kiểm thử và xác minh bắt buộc, hoặc công khai rõ những bước không thể thực hiện.

\- Không che giấu lỗi hoặc kết quả thất bại.

\- Đã rà soát thay đổi cuối cùng.

\- Đã báo cáo phần bỏ qua, giới hạn xác minh và rủi ro còn lại.



\*\*Không đánh đồng “đã viết xong code” với “đã hoàn thành công việc”.\*\*



\*\*Không đánh đồng “test pass” với “hệ thống chắc chắn không có lỗi”.\*\*



\*\*Không đánh đồng “kế hoạch được duyệt” với “được phép thực hiện mọi thao tác”.\*\*



Mục tiêu cuối cùng là tạo ra thay đổi nhỏ nhất cần thiết, có thể kiểm chứng, an toàn và phù hợp với yêu cầu thực tế của người dùng.

