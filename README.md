<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shopee Affiliate Link Generator</title>
  <script>
    async function generateLink() {
      const input = document.getElementById("productLink").value.trim();
      const resultBox = document.getElementById("result");
      resultBox.innerText = "Đang tạo link...";try {
    const response = await fetch("https://your-backend.vercel.app/create-affiliate-link", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ originalLink: input })
    });

    const data = await response.json();
    if (data.affiliateLink) {
      resultBox.innerHTML = `<p>✅ Link Affiliate:</p><a href="${data.affiliateLink}" target="_blank">${data.affiliateLink}</a>`;
    } else {
      resultBox.innerText = "Không tạo được link affiliate. Kiểm tra lại link hoặc server.";
    }
  } catch (error) {
    resultBox.innerText = "Lỗi kết nối server.";
  }
}

  </script>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; margin: 30px; }
    input { width: 80%; padding: 10px; border: 1px solid #ccc; border-radius: 8px; }
    button { padding: 10px 20px; margin-top: 10px; background: orange; color: white; border: none; border-radius: 8px; cursor: pointer; }
    #result { margin-top: 20px; font-weight: bold; }
  </style>
</head>
<body>
  <h2>🔗 Tạo Link Affiliate Shopee</h2>
  <input type="text" id="productLink" placeholder="Dán link sản phẩm Shopee..." />
  <br>
  <button onclick="generateLink()">Tạo Link</button>
  <div id="result"></div>
  
</body>
</html>
