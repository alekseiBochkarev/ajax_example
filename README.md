# ajax_example

Пример кода:

HTML:
```HTML
<!DOCTYPE html>
<html>
<head>
    <title>AJAX Пример</title>
</head>
<body>
    <h1>Введите ваше имя:</h1>
    <input type="text" id="nameInput">
    <button onclick="sendRequest()">Отправить</button>
    <p id="response"></p>

    <script src="ajax.js"></script>
</body>
</html>
```

JavaScript (ajax.js):
```JavaScript
function sendRequest() {
    var name = document.getElementById("nameInput").value;
    var xhr = new XMLHttpRequest();
    xhr.open("GET", `server.php?name=${name}`, true);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("response").innerText = xhr.responseText;
        }
    };
    xhr.send();
}
```
PHP (server.php):
```PHP
<?php
if (isset($_GET['name'])) {
    $name = htmlspecialchars($_GET['name']);
    echo "Привет, $name!";
}
?>
```
