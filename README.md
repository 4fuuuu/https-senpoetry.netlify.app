from zipfile import ZipFile
import os

# 定義網站檔案目錄與壓縮檔輸出位置
output_path = "/mnt/data/senpoetry_site.zip"

# 模擬一個簡單的網站結構來壓縮（實際內容會是完整網站檔案）
site_files = {
    "index.html": """
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>泉的花園詩歌</title>
</head>
<body>
    <h1>歡迎來到泉的詩歌花園</h1>
    <p>「我寫詩，是因為情感太深，語言太窄。」</p>
</body>
</html>
    """,
    "style.css": """
body {
    font-family: "Noto Serif TC", serif;
    background-color: lavender;
    color: #333;
    padding: 20px;
}
    """
}

# 建立壓縮檔
with ZipFile(output_path, 'w') as zipf:
    for filename, content in site_files.items():
        filepath = f"/mnt/data/{filename}"
        with open(filepath, 'w', encoding='utf-8') as f:
            f.write(content)
        zipf.write(filepath, arcname=filename)
        os.remove(filepath)

output_path
