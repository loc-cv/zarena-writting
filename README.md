# TODO: Title here

TODO: Opening paragraph here

## Path finding cơ bản

Mình sẽ bắt đầu với tình huống đơn giản nhất, một con bot <s>ngu</s> và một cái rương vàng.

TODO: insert image here

Nhìn vào hình thì có vẻ như mọi thứ rất đơn giản, và đúng là như vậy. Có rất nhiều con đường con bot có thể đi để lấy được rương vàng, và chúng ta sẽ chỉ quan tâm đến đường đi ngắn nhất. Ở đây mình không cần đến một thuật toán cao siêu phức tạp nào cả, chỉ cần tịnh tiến con bot theo chiều dọc và ngang (một cách hợp lý) cho tới khi vị trí của bot chính là vị trí của rương.

Bởi vì bot chỉ có thể di chuyển dọc và ngang, mình dễ dàng có được một đường đi ngắn nhất:

TODO: insert image here

Mọi thứ đều ổn, nhưng mình lại nhớ ra một điều, đó là trên bản đồ không chỉ có mỗi một rương vàng như vậy, mà ngoài ra sẽ có nhiều xu vàng và túi vàng nằm rải rác. Nghe có vẻ không liên quan lắm nhỉ, bởi vì mục tiêu của con bot của mình vẫn là cái rương vàng to sụ kia cơ mà. Hãy kiểm tra xem nếu như vậy thì có ảnh hưởng gì đến con bot của mình không nhé.

TODO: insert image here

Lúc này chắc chắn nhiều bạn đọc đã thấy được vấn đề, trên con đường đến với thùng rương 4 vàng, con bot của mình đã "vô tình" bỏ túi một cái túi vàng với giá trị là 2 vàng. Bởi vì kho đồ của mỗi con bot chỉ có thể chứa tối đa 5 vàng nên giờ đây, cho dù có đến được cái rương đang lấp lánh kia, con bot ngu của mình cũng không thể vác cái rương đấy về nhà được. Vậy mình có một vấn đề cần phải giải quyết: tránh những vị trí có thể làm cho kho đồ của bot bị đầy trước khi đến được rương vàng.

Giả sử như sau những giờ code siêu căng thẳng, bot của mình đã bớt ngu hơn một chút và có thể tự tin đi đến rương vàng mà không làm cho kho đồ bị quá tải. 

TODO: insert image here

Nhưng lúc này mình lại nhớ ra thêm một điều, trên bản đồ không chỉ có vàng, nó còn có những cánh cửa dịch chuyển. Là một fan của Doraemon, mình không thể bỏ qua những cánh cửa này được.

TODO: insert image here

Nhìn bằng mắt thường thì có thể thấy rõ ràng là việc đi qua 2 cánh cửa sẽ cho mình một đường đi ngắn hơn rất nhiều so với việc chạy bộ trước đó. Tất nhiên, bot của mình sẽ cắm đầu chạy ngay qua cánh cửa này mà không cần suy nghĩ quá nhiều.

TODO: insert image here

Mà khoan đã, cần phải biết là vị trí của những cánh cửa là ngẫu nhiên, nên không phải lúc nào việc đi qua cửa cũng đem lại cho con bot của mình một đường đi hiệu quả hơn là đường đi truyền thống.

TODO: insert image here

Như trong hình trên, nếu đi qua cánh cửa, con bot của mình sẽ ở một vị trí rất xa. Và trừ khi nó biết cách sử dụng cánh cửa để quay lại vị trí cũ, có thể con bot của mình sẽ có một hành trình vĩ đại hơn cả Colombo trước khi nó đến được với rương vàng.

Vậy mình lại có thêm một vấn đề nữa cần giải quyết: chỉ đi qua những cánh cổng nếu chúng cho mình một con đường ngắn hơn con đường truyền thống.

Lại giả sử sau những giờ code siêu căng thẳng, con bot của mình tiếp tục thông minh hơn một chút, không bị cám dỗ bởi những cánh cửa mà sẽ đưa nó tới miền cực lạc. Nhưng lúc này mình lại nhớ ra thêm một điều nữa, ngoài con bot ngu của mình, còn có những con bot siêu thông minh của đối thủ.

TODO: insert image here

Có thể thấy, trên con đường đi tới rương vàng, có một con bot khác của đối thủ đang chờ sẵn. Và để cho tình huống này thực tế hơn thì mình sẽ giả sử như con bot này hiện đang có nhiều hơn 2 vàng, kho đồ của con bot này sẽ không đủ chỗ cho cái rương vàng kia, và thay vì đi lấy những xu vàng còn lại trên bản đồ , con bot xấu xa này quyết định sẽ mai phục với mong muốn "ăn" được con bot của mình.

Và lúc này mọi thứ bắt đầu phức tạp hơn khá nhiều.

Khi có đối thủ thì đương nhiên sẽ có đối kháng, và khi có đối kháng, sẽ có tấn công và phòng thủ. Và việc lựa chọn giữa tấn công và phòng thủ sẽ là yếu tố quyết định ảnh hưởng tới chiến thuật và phong cách chơi của mỗi con bot. Lúc này mình có 3 lựa chọn cho con bot của mình, hoặc chơi kiểu tấn công, hoặc kiểu phòng thủ, hoặc cả hai. Thực tế khi chạy, mỗi con bot bắt buộc phải dừng ít nhất 800 ms trước khi thực hiện một lượt đi mới, nên sẽ rất khó cho con bot của mình nếu chơi kiểu tấn công trong tình huống này, bởi ngay khi bot của mình tiến đến bên cạnh con bot của đối phương, sẽ không có cơ hội nào để con bot của mình sống sót được cả. Do đó, một vấn đề nữa lại được sinh ra: trên đường đi đến rương vàng, bot của mình cần phải thoát được sự mai phục của bot đối phương.