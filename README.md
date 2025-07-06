<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Alamin’s Link Income</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #f0f2f5;
      margin: 0;
      padding: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .container {
      background: white;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 400px;
      width: 90%;
      text-align: center;
    }
    input[type="text"] {
      width: 100%;
      padding: 10px;
      margin: 15px 0;
      border-radius: 6px;
      border: 1px solid #ccc;
      font-size: 16px;
    }
    button {
      background: #0084ff;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s ease;
    }
    button:hover {
      background: #005fcc;
    }
    .result {
      margin-top: 20px;
      font-weight: bold;
      word-break: break-word;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Alamin’s Link Income</h2>
    <p>তোমার লিংক নিচে দাও, শর্ট করে ইনকাম করো</p>
    <input type="text" id="longUrl" placeholder="যেমন: https://youtube.com..." />
    <button onclick="shortenLink()">শর্ট করো</button>
    <div class="result" id="shortenedUrl"></div>
  </div>

  <script>
    async function shortenLink() {
      const longUrl = document.getElementById('longUrl').value.trim();
      if (!longUrl) {
        alert('দয়া করে লিংকটি দিন!');
        return;
      }

      const apiUrl = 'https://shrinkearn.com/api?api=3be62abf4bc0a608ee9c0e63aa121852eb662dee&url=' + encodeURIComponent(longUrl);

      try {
        const response = await fetch(apiUrl);
        const data = await response.json();
        if (data.status === 'success' || data.ok) {
          const shortLink = data.result ? data.result.full_short_link : data.shortenedUrl;
          document.getElementById('shortenedUrl').innerHTML = '✅ শর্ট লিংক: <a href="' + shortLink + '" target="_blank" rel="noopener noreferrer">' + shortLink + '</a>';
        } else {
          document.getElementById('shortenedUrl').innerText = '❌ লিংক শর্ট করা যায়নি, আবার চেষ্টা করুন।';
        }
      } catch (error) {
        document.getElementById('shortenedUrl').innerText = '⚠️ সমস্যা হয়েছে, ইন্টারনেট চেক করুন।';
      }
    }
  </script>
</body>
</html>
