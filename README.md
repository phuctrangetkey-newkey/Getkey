<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>Lấy Key – PhucNguyen</title>
<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: linear-gradient(135deg, #4a00e0, #8e2de2);
        background-size: 400% 400%;
        animation: bgmove 6s infinite alternate;
        font-family: Arial, sans-serif;
        color: white;
        overflow: hidden;
    }

    @keyframes bgmove {
        0% { background-position: 0% 50%; }
        100% { background-position: 100% 50%; }
    }

    #container { text-align: center; }

    #bigButton {
        padding: 40px 70px;
        font-size: 35px;
        font-weight: bold;
        background: #ffffff;
        color: #4a00e0;
        border: none;
        border-radius: 20px;
        cursor: pointer;
        box-shadow: 0px 0px 20px #fff;
    }

    #keysPage { display: none; }

    .keyBox {
        background: rgba(0,0,0,0.4);
        padding: 20px;
        margin: 10px;
        border-radius: 14px;
        font-size: 22px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    button.copyBtn {
        padding: 10px 20px;
        background: #fff;
        border-radius: 10px;
        color: #4a00e0;
        border: none;
        cursor: pointer;
        font-weight: bold;
    }
</style>
</head>
<body>

<div id="container">
    <button id="bigButton">ẤN 20 LẦN ĐỂ LẤY KEY</button>
</div>

<div id="keysPage">
    <h1>7 KEY CỦA BẠN</h1>
    <div id="keyList"></div>
</div>

<script>
let clickCount = 0;

let keys = [];
for (let i = 1; i <= 7; i++) {
    let randomKey = "Phuc_" + Math.random().toString(36).substring(2, 7);
    keys.push(randomKey);
}

document.getElementById("bigButton").onclick = () => {
    clickCount++;

    if (clickCount === 20) {
        document.getElementById("container").innerHTML =
            "<h1>ĐỢI 10 GIÂY ĐỂ LẤY KEY...</h1>";

        setTimeout(() => {
            document.getElementById("container").style.display = "none";
            document.getElementById("keysPage").style.display = "block";

            let html = "";
            keys.forEach(k => {
                html += `
                    <div class='keyBox'>
                        <span>${k}</span>
                        <button class='copyBtn' onclick='navigator.clipboard.writeText("${k}")'>COPY</button>
                    </div>`;
            });

            document.getElementById("keyList").innerHTML = html;
        }, 10000);
    }
};
</script>

</body>
</html>
