<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hoye Restaurant</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f7f7f7; margin: 0; padding: 0; }
    .container { max-width: 600px; margin: 40px auto; background: #fff; padding: 24px; border-radius: 8px; box-shadow: 0 2px 10px #ccc; }
    h1 { text-align: center; color: #d35400; }
    .menu-list { list-style: none; padding: 0; }
    .menu-item { padding: 12px; border-bottom: 1px solid #eee; display: flex; justify-content: space-between; align-items: center; }
    .menu-item:last-child { border-bottom: none; }
    .menu-img { width: 60px; height: 60px; border-radius: 8px; object-fit: cover; margin-right: 16px; }
    button { padding: 8px 18px; background: #d35400; color: #fff; border: none; border-radius: 4px; cursor: pointer; }
    button:hover { background: #e67e22; }
    .details { margin-top: 32px; }
    .back-btn { margin-top: 20px; display: block; }
    .price { color: #27ae60; font-weight: bold; margin-bottom: 12px; }
    .details-img { width: 220px; height: 180px; border-radius: 12px; object-fit: cover; margin-bottom: 18px; display: block; margin-left: auto; margin-right: auto; }
  </style>
</head>
<body>
  <div class="container">
    <h1>Hoye Restaurant</h1>
    <ul class="menu-list" id="menuList"></ul>
    <div class="details" id="details" style="display:none;">
      <img id="detailsImg" class="details-img" src="" alt="Dish Image" />
      <h2 id="itemTitle"></h2>
      <div class="price" id="itemPrice"></div>
      <div id="itemDetail"></div>
      <button class="back-btn" onclick="goBack()">Go to Back</button>
    </div>
  </div>
  <script>
    // Sample menu data with images
    const menu = [
      {
        title: "Chicken Biryani",
        price: "Rs. 450",
        detail: "Spicy rice dish with marinated chicken, served with raita.",
        image: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&w=400&q=80"
      },
      {
        title: "Paneer Tikka",
        price: "Rs. 350",
        detail: "Grilled paneer cubes marinated in spices, served with mint chutney.",
        image: "https://images.unsplash.com/photo-1604908177222-74b60c6ba7ce?auto=format&fit=crop&w=400&q=80"
      },
      {
        title: "Beef Burger",
        price: "Rs. 300",
        detail: "Juicy beef patty with fresh lettuce, tomato and house sauce.",
        image: "https://images.unsplash.com/photo-1550317138-10000687a72b?auto=format&fit=crop&w=400&q=80"
      },
      {
        title: "Zinger Burger",
        price: "Rs. 270",
        detail: "Crispy chicken fillet, spicy mayo, lettuce in a soft bun.",
        image: "https://images.unsplash.com/photo-1568901346375-23c9450c58cd?auto=format&fit=crop&w=400&q=80"
      },
      {
        title: "French Fries",
        price: "Rs. 120",
        detail: "Golden fried potato fries, served with ketchup.",
        image: "https://images.unsplash.com/photo-1542444459-db68c9b3d8b6?auto=format&fit=crop&w=400&q=80"
      }
    ];

    const menuList = document.getElementById('menuList');
    const detailsDiv = document.getElementById('details');
    const itemTitle = document.getElementById('itemTitle');
    const itemPrice = document.getElementById('itemPrice');
    const itemDetail = document.getElementById('itemDetail');
    const detailsImg = document.getElementById('detailsImg');

    // Show menu
    function showMenu() {
      menuList.innerHTML = '';
      menu.forEach((item, idx) => {
        const li = document.createElement('li');
        li.className = 'menu-item';
        li.innerHTML = `
          <img src="${item.image}" class="menu-img" alt="${item.title}" />
          <span>${item.title}</span>
          <button onclick="showDetails(${idx})">Click karen</button>
        `;
        menuList.appendChild(li);
      });
      menuList.style.display = '';
      detailsDiv.style.display = 'none';
    }

    // Show details
    window.showDetails = function(idx) {
      const item = menu[idx];
      itemTitle.textContent = item.title;
      itemPrice.textContent = "Price: " + item.price;
      itemDetail.textContent = item.detail;
      detailsImg.src = item.image;
      detailsImg.alt = item.title;
      menuList.style.display = 'none';
      detailsDiv.style.display = '';
    }

    // Go to Back
    window.goBack = function() {
      showMenu();
    }

    // Initial show
    showMenu();
  </script>
</body>
</html>
