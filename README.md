<html>
<head>
  <title>Menu Calculator</title>
    <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 350vh;
      text-align: center;
    }
	.total-box {
		display: flex;
		justify-content: center; /* Center horizontally */
		align-items: center; /* Center vertically */
		margin-top: 20px;
	}}
	
	 .calculate-button {
      width: 150px; /* Adjust the desired width */
      height: 50px; /* Adjust the desired height */
    }
	
	.submit-button {
      width: 150px; /* Adjust the desired width */
      height: 40px; /* Adjust the desired height */
    }
	
	.reset-button {
      width: 150px; /* Adjust the desired width */
      height: 30px; /* Adjust the desired height */
    }
    
    h1 {
      margin-bottom: 20px;
    }
    
    h2 {
      margin-top: 20px;
    }
	
	h3 {
      border: 1px solid black; /* Adjust the border style as needed */
      padding: 5px; /* Add padding to create space around the heading */
    }
    
    .menu-items {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 10px;
    }
    
    .menu-items div {
      display: flex;
      align-items: center;
    }
    
    .total-box {
      display: flex;
      justify-content: flex-end;
      align-self: flex-end;
      margin-top: 20px;
    }
    
    .button-container {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
	
	.menu-items div img {
      width: 50px; /* Adjust the desired width */
      height: 50px; /* Adjust the desired height */
      margin-left: 10px; /* Add margin as per your preference */
    }
    {
    button {
      margin-top: 20px;
	}}}}}}
  </style>
  <script>
    function calculateTotal() {
    var total = 0;
    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');

    checkboxes.forEach(function(checkbox) {
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var price = parseFloat(checkbox.value);

      if (checkbox.value === '-25%') {
        var itemPrice = total * 0.25;
        total -= itemPrice;
      } else if (checkbox.value === '-30%') {
        var itemPrice = total * 0.3;
        total -= itemPrice;
      } else if (checkbox.value === '-50%') {
        var itemPrice = total * 0.5;
        total -= itemPrice;
      } else {
        total += price * quantity;
      }
    });

    var totalElement = document.getElementById('total');
    totalElement.textContent = total.toFixed(2);

    var discountTotalElement = document.getElementById('discount-total');
    var discount = total * 0.07;
    discountTotalElement.textContent = discount.toFixed(2);
  }


    
    function submitOrder() {
  var name = document.getElementById('name').value;
  
  // Check if the name field is empty
  if (name.trim() === '') {
    alert('Please enter a name.');
    return;
  }
  var total = parseFloat(document.getElementById('total').textContent);
  var commission = (total * 0.05).toFixed(2); // Calculate the commission (5%)
  
  alert('Order submitted!');
  
  var discordWebhookURL = '"insert"'; // Replace with your Discord webhook URL
  
  var xhr = new XMLHttpRequest();
  xhr.open('POST', discordWebhookURL, true);
  xhr.setRequestHeader('Content-Type', 'application/json');
  
  var message = {
    content: 'New order!',
    embeds: [{
      title: 'Order Details',
      fields: [
        {
          name: 'Name',
          value: name,
          inline: true
        },
        {
          name: 'Total',
          value: '$' + total.toFixed(2),
          inline: true
        },
        {
          name: 'Commission (5%)',
          value: '$' + commission,
          inline: true
        }
      ]
    }]
    
  };
  
  xhr.send(JSON.stringify(message));
}

function resetCalculator() {
  var checkboxes = document.querySelectorAll('input[type="checkbox"]');
  var quantityInputs = document.querySelectorAll('input[type="number"]');
  
  checkboxes.forEach(function(checkbox) {
    checkbox.checked = false;
  });
  
  quantityInputs.forEach(function(quantityInput) {
    quantityInput.value = 1;
  });
  
  document.getElementById('total').textContent = '0.00';
}
  </script>
</head>
<body>
	
<div style="margin-bottom: 250px;"></div>
 
<body style="background-color:deeppink;">
	<img src="BackGround.png" alt="Company Logo!">
  <h1>Menu Calculator</h1>
  
  <h2>Menu Items</h2>

  <div style="margin-bottom: 10px;"></div>
  
    <!--This is where you change the combos with prices-->
  
  
  <h3> Combos </h3>
  
  <div>
    <input type="checkbox" id="ColinChoice" value="1"><!--The price is the value, change that and then the name and itll change on the menu-->
    <label for="ColinChoice">Coming Soon</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="JudysChoice" value="1">
    <label for="JudysChoice">Coming Soon$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Velmachoice" value="1$">
    <label for="Velmachoice">Coming Soon</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Davechoice" value="1$">
    <label for="Davechoice">Coming Soon</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  
  
   <h3> Entree </h3>
  
  <div>
    <input type="checkbox" id="Salad" value="150">
    <label for="Salad">The Bleeder - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FruitExplosion" value="200">
    <label for="FruitExplosion">Double Shot - 200$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="TurkeySammie" value="150">
    <label for="TurkeySammie">Pickle - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="BeefSammie" value="150$">
    <label for="BeefSammie">Taco - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="BLTSammie" value="150">
    <label for="BLTSammie">Heart Stopper - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="175">
    <label for="choccypanckaes">Chicken Wrap - 175$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="175">
    <label for="choccypanckaes">Goat Cheese Wrap - 175$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="175">
    <label for="choccypanckaes">Fries - 175$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  
  
  <h3> Beverage </h3>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="125">
    <label for="FrozenYoghurt">Burger Shot Drink - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="125">
    <label for="FrozenYoghurt">Orangotang Ice Cream - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="125">
    <label for="FrozenYoghurt">Meteorite Ice Cream - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="125">
    <label for="FrozenYoghurt">Mocha Shake - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  
  <div style="margin-bottom: 10px;"></div>
  
   

<div style="margin-bottom: 100px;"></div>

<div>
    <label for="name">Employee's Name:</label>
    <input type="text" id="name">
  </div>
  <p><b> Include Kitchen and Front staff in names section </b></p>

<div style="margin-bottom: 60px;"></div>

 
<div class="total-box">
  <span>Total: $</span>
  <span id="total">0.00</span>
</div>

<div class="total-box">
  <span>Commision (5%): $</span>
  <span id="discount-total">0.00</span>
</div>



 
  
  
  <div style="margin-bottom: 10px;"></div>
  

  
  <div style="margin-bottom: 30px;"></div>

  <button class="calculate-button" onclick="calculateTotal()">Calculate Total</button>
  <button class="submit-button" onclick="submitOrder()">Submit Order</button>
  <button class="reset-button" onclick="resetCalculator()">Reset</button>

  
  
  
  <div style="margin-bottom: 100px;"></div>
