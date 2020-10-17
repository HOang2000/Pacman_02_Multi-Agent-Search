# Pacman_02_Multi-Agent-Search
# Q1: viết một hàm đánh giá evaluationFunction trả về số điểm nếu pacman đi vào vị trí cần đánh giá, điểm đánh giá càng cao thì lựa chọn của pacman càng tốt

Tìm đường đi ngắn nhất từ pacman đên thức ăn và đường đi ngắn nhất đên con ma khi scareTimer của nó khác 0.
Giá trị trả về là một số được tính theo successorGameState.getScore() + 5.0 / (nearestFoodDistance + 1) - 15.0 / (nearestGhostDistance + 1), trong đó, càng gần thức ăn thì càng tốt (lựa chọn càng tốt) và càng gần con ma thì càng xấu (lựa chọn xấu dần). Tỷ lệ đầu ra như trên là khá tốt.

# Q2: Triển khai thuật toán minimax để tìm lựa chọn hướng đi tốt nhất cho pacman

Hàm minimax(agentIndex, depth, gameState) trong đó agentIndex = 0 là pacman và là ghost khi >= 1, depth là số bước đi cho pacman và gameState ghi lại trạng thái của trò chơi.
Trạng thái kết thúc khi gameState.isWin() hoặc gameState.isLose() hoặc depth đạt độ sâu giới hạn của trò chơi
Khi agentIndex = 0 (pacman), ta sẽ tim max khoảng cách từ pacman đến các con ma. Vì panman càng xa các con ma càng tốt
Khi agentIndex != 0 (ghost), ta sẽ tim min khoảng cách từ ghost đến pacman vì càng gần pacman càng có lợi cho ghost
Giá trị trả về là lựa chọn tốt nhất trong các lựa chọn có thể có của pacman

# Q3: Triển khai thuật toán Alplha-Beta pruning để cải thiện thuật toán Minimax với alpha là giá trị max tốt nhất và beta là giá trị min tốt nhất

Thuật toán tương tự như thuật toán minimax ở câu trước nhưng để dễ hình dung với những gì đã học ta sẽ chia thành các hàm minValue() cho ghost và maxValue() cho pacman. Các tham số tương tự như hàm minimax() ở câu trước nhưng có thêm 2 tham số là alpha và beta.
Giá trị trả về là lựa chọn hướng đi tốt nhất cho pacman

# Q4: Triển khai ExpectimaxAgent, rất hữu ích để mô hình hóa hành vi xác suất của các tác nhân có thể đưa ra lựa chọn dưới mức tối ưu.

Làm tương tự như thuật toán minimax trong q2 nhưng thay vì tìm min khi agentIndex != 0 thì ta sẽ tính trung bình điểm số đạt được của các hành động (vì các con ghost xuất hiện ngẫu nhiên nên xác suất sẽ có giá trị như nhau).
Giá trị trả về là lựa chọn hướng đi tốt nhất cho pacman

# Q5: Viết một hàm đánh giá tốt hơn cho pacman trong hàm betterEvaluationFunction. Trong trường hợp này thay vì đánh giá trạng thái tiếp theo sau khi pacman hành động như q1 thì ta sẽ đánh giá trạng thái hiện tại.

Vì là hàm đánh giá nên có thể sử dụng lại cách giải đã dùng ở q1 và lược bỏ các phần không cần thiết như
