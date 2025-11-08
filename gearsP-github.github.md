<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>gearsP</title>
    <style>

        .container {
            text-align: center;
            margin-top: 20vh;
        }

        .centered-image {
            max-width: 80%;
            height: auto;
      }
        </style>
    <div class="container">
        <img src="因特尔2.jpg" alt="Logo" class="centered-image">
    </div>

    <div class="container">
        <input type="text" id="searchInput" placeholder="输入网站名或网址搜索..." class="search-input">
        <button onclick="search()" class="search-button">搜索</button>
    </div>

    <script>
        const siteDirect = {
            '百度': 'https://www.baidu.com',
            }

        function search() {
            const input = document.getElementById('searchInput').value.trim();
            if (!input) {
                alert('请输入内容！'); 
                return;
            }

            const lowerInput = input.toLowerCase();
            for (const [key, url] of Object.entries(siteDirect)) {
                if (key.toLowerCase() === lowerInput) {
                    window.open(url, '_blank');
                    document.getElementById('searchInput').value = '';
                    return;
                }
            }

            if (input.startsWith('http://') || input.startsWith('https://')) {
                window.open(input, '_blank');
                document.getElementById('searchInput').value = '';
                return;
            }

            const searchUrl = `https://www.baidu.com/?wd=${encodeURIComponent(input)}`;
            window.open(searchUrl, '_blank');
            document.getElementById('searchInput').value = '';
        }

        document.getElementById('searchInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                search();
            }
        });
    </script>

</body>
</html>
