
DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tạo Link Affiliate</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; padding: 30px; }
    input, button { padding: 10px; font-size: 16px; margin: 5px; width: 80%; }
    .result { margin-top: 20px; font-weight: bold; color: green; }
  </style>
</head>
<body>
  <h2>Nhập link sản phẩm</h2>
  <input type="text" id="linkInput" placeholder="Dán link Shopee/TikTok">
  <br>
  <button onclick="convertLink()">Tạo link mua hàng</button>
  <div class="result" id="result"></div>

  <script>
    function convertLink() {
      let link = document.getElementById("linkInput").value.trim();
      let result = document.getElementById("result");

      if (!link) {
        result.innerHTML = "⚠️ Bạn chưa nhập link!";
        return;
      }

      let affLink = "";

      if (link.includes("shopee.vn")) {
        affLink = link + (link.includes("?") ? "&" : "?") + "aff_id=YOUR_SHOPEE_AFF_ID";
      } else if (link.includes("tiktok")) {
        affLink = link + (link.includes("?") ? "&" : "?") + "af_id=YOUR_TIKTOK_AFF_ID";
      } else {
        result.innerHTML = "❌ Link không hợp lệ!";
        return;
      }

      result.innerHTML = `✅ Link mua hàng của bạn:<br><a href="${affLink}" target="_blank">${affLink}</a>`;
    }
  </script>
</body>
</html>
