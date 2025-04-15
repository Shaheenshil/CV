<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Billionaire Fun Store</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #2e003e;
      color: #ffd700;
    }
    header {
      background-color: #4b0082;
      padding: 20px;
      text-align: center;
      font-size: 2rem;
      color: gold;
      border-bottom: 3px solid gold;
    }
    .balance {
      text-align: center;
      font-size: 1.2rem;
      margin: 10px 0;
    }
    .store {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .item {
      background-color: #3b005e;
      border: 2px solid gold;
      border-radius: 15px;
      padding: 15px;
      text-align: center;
    }
    .item h3 {
      margin-bottom: 10px;
    }
    button {
      padding: 10px;
      background-color: gold;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      font-weight: bold;
    }
    button:hover {
      background-color: #ffdf00;
    }
    .receipt, .inventory {
      background-color: #3b005e;
      margin: 20px;
      padding: 15px;
      border-radius: 10px;
      border: 2px solid gold;
    }
    .receipt h2, .inventory h2 {
      margin-top: 0;
      border-bottom: 1px solid gold;
    }
  </style>
</head>
<body>
  <header>Billionaire Fun Store</header>
  <div class="balance">Your Fake Balance: $<span id="balance">1000000000</span></div>
  <div class="store" id="store"></div>  <div class="inventory">
    <h2>Your Inventory / Aap ki Cheezen</h2>
    <ul id="inventory"></ul>
  </div>  <div class="receipt">
    <h2>Recent Purchases / Aakhri Khareedari</h2>
    <ul id="receipt"></ul>
  </div>  <script>
    const items = [
      { name: 'Flying Lamborghini', price: 120000000 },
      { name: 'Private Moon', price: 800000000 },
      { name: 'Time Machine', price: 250000000 },
      { name: 'Invisible Jet', price: 150000000 },
      { name: 'Diamond Mansion', price: 400000000 },
      { name: 'Talking Dragon', price: 99999999 },
      { name: 'Robot Army', price: 300000000 },
      { name: 'Underwater Castle', price: 200000000 },
      { name: 'Gold Pizza', price: 150000 },
      { name: 'Weather Control Remote', price: 350000000 }
    ];

    let balance = 1000000000;
    const storeDiv = document.getElementById('store');
    const balanceSpan = document.getElementById('balance');
    const receiptList = document.getElementById('receipt');
    const inventoryList = document.getElementById('inventory');

    function updateBalance() {
      balanceSpan.textContent = balance.toLocaleString();
    }

    function buyItem(item) {
      if (balance >= item.price) {
        balance -= item.price;
        updateBalance();
        const li = document.createElement('li');
        li.textContent = `You bought ${item.name} for $${item.price.toLocaleString()}`;
        receiptList.prepend(li);

        const inv = document.createElement('li');
        inv.textContent = item.name;
        inventoryList.appendChild(inv);
      } else {
        alert('Insufficient fake balance! / Paise khatam hogaye bhai!');
      }
    }

    function showItems() {
      storeDiv.innerHTML = '';
      items.forEach(item => {
        const div = document.createElement('div');
        div.className = 'item';
        div.innerHTML = `
          <h3>${item.name}</h3>
          <p>Price: $${item.price.toLocaleString()}</p>
          <button onclick='buyItem(${JSON.stringify(item)})'>Buy / Kharido</button>
        `;
        storeDiv.appendChild(div);
      });
    }

    updateBalance();
    showItems();
  </script></body>
</html>
