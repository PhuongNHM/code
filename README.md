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




const exams = [
    { name: "Luyện tập", status: "open" },
    { name: "Giữa kỳ", status: "scheduled" },
    { name: "Cuối kỳ", status: "scheduled" },
    // Thêm các kỳ thi khác
];

document.addEventListener("DOMContentLoaded", function () {
    displayExams();
    document.getElementById("searchInput").addEventListener("input", searchExams);
    document.getElementById("statusFilter").addEventListener("change", filterExams);

    
    const examItems = document.querySelectorAll("#examList li");
    examItems.forEach(item => {
        item.addEventListener("click", startOrRegisterExam);
    });
});

function displayExams() {
    const examList = document.getElementById("examList");
    examList.innerHTML = "";

    exams.forEach(exam => {
        const listItem = document.createElement("li");
        listItem.textContent = exam.name;

        const scheduleButton = document.createElement("button");
        scheduleButton.textContent = "Hẹn Lịch";
        scheduleButton.addEventListener("click", function(event) {
            scheduleExam(event, exam.name);
        });
        
        const startButton = document.createElement("button");
        startButton.textContent = "Bắt Đầu Kỳ Thi";
        startButton.addEventListener("click", function(event) {
            startExam(event, exam.name);
        });

        listItem.appendChild(scheduleButton);
        listItem.appendChild(startButton);
        examList.appendChild(listItem);
    });
}

function searchExams() {
    const searchInput = document.getElementById("searchInput");
    const searchTerm = searchInput.value.toLowerCase();

    const filteredExams = exams.filter(exam => exam.name.toLowerCase().includes(searchTerm));
    displayFilteredExams(filteredExams);
}

function filterExams() {
    const statusFilter = document.getElementById("statusFilter");
    const selectedStatus = statusFilter.value;

    let filteredExams = exams;

    if (selectedStatus !== "all") {
        filteredExams = exams.filter(exam => exam.status === selectedStatus);
    }

    displayFilteredExams(filteredExams);
}

function displayFilteredExams(filteredExams) {
    const examList = document.getElementById("examList");
    examList.innerHTML = "";

    filteredExams.forEach(exam => {
        const listItem = document.createElement("li");
        listItem.textContent = exam.name;

        const scheduleButton = document.createElement("button");
        scheduleButton.textContent = "Hẹn Lịch";
        scheduleButton.addEventListener("click", function(event) {
            scheduleExam(event, exam.name);
        });
        
        const startButton = document.createElement("button");
        startButton.textContent = "Bắt Đầu Kỳ Thi";
        startButton.addEventListener("click", function(event) {
            startExam(event, exam.name);
        });

        listItem.appendChild(scheduleButton);
        listItem.appendChild(startButton);
        examList.appendChild(listItem);
    });
}

function startOrRegisterExam(event) {
    const selectedExamName = event.target.textContent;
    const confirmation = confirm("Bạn muốn bắt đầu làm kỳ thi " + selectedExamName + " hay đăng ký lịch trình?");
    
    if (confirmation) {
        startExam(event, selectedExamName);
    } else {
        scheduleExam(event, selectedExamName);
    }
}

function startExam(event, examName) {
    alert("Bắt đầu làm kỳ thi: " + examName);
    // Thêm mã để xử lý bắt đầu làm kỳ thi ở đây
}

function scheduleExam(event, examName) {
    alert("Hẹn lịch cho kỳ thi: " + examName);
    // Thêm mã để xử l
}


CSS:

/* Thêm code CSS vào file style.css */
body {
    font-family: Arial, sans-serif;
    background-color: #f8f8f8;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

label {
    margin-top: 10px;
}

input, select {
    margin-bottom: 10px;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    padding: 10px;
    margin: 5px;
    background-color: #fff;
    border-radius: 5px;
    cursor: pointer;
}

li:hover {
    background-color: #f0f0f0;
}


