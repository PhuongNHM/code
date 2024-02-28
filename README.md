# code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Trang Chính</title>
</head>
<body>
    <div class="container">
        <h1>Danh sách kỳ thi</h1>
        
        <div>
            <label for="searchInput">Tìm kiếm:</label>
            <input type="text" id="searchInput" oninput="searchExams()">
        </div>

        <div>
            <label for="statusFilter">Lọc theo trạng thái:</label>
            <select id="statusFilter" onchange="filterExams()">
                <option value="all">Tất cả</option>
                <option value="open">Có thể truy cập tự do</option>
                <option value="scheduled">Yêu cầu thời gian cụ thể</option>
            </select>
        </div>

        <ul id="examList">
            <!-- Danh sách kỳ thi sẽ được hiển thị ở đây -->
        </ul>
    </div>

    <script src="script.js"></script>
</body>
</html>
