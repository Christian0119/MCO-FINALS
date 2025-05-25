let user_name = prompt("Register your Username:");
let password = prompt("Register your password:");
let re_password = prompt("Re-enter your passcode:");

if (password === re_password) {       // Check if the password is equal to re_password
    alert("You are already registered!");

    let LogIn = prompt("Username:");     // After registration the user is ask to log in

    if (LogIn === user_name) {
        let encode_password = prompt("Password:");
        while (encode_password !== password) {       
            alert("Incorrect Password, Re-run the code!");   // it will display if the password is incorrect 
            encode_password = prompt("Password:");
        }
        alert(`WELCOME, ${user_name}!`);       // Display if the log in is successful

        let cart = [];
        let continueShopping = true;

        function addToCart(category, Name, qty, price) {
            cart.push({ category, item: Name, qty, price, total: qty * price });
        }

// Prints the cart, handles payment,and show the receipt
        function showReceipt() {
            let receipt = "Receipt:\n";
            let totalAmount = 0;
            cart.forEach((entry, index) => {
                receipt += `${index + 1}. Category: ${entry.category}, Item: ${entry.item}, Qty: ${entry.qty}, Price: Php ${entry.price}, Total: Php ${entry.total}\n`;
                totalAmount += entry.total;
            });
            receipt += `Total Amount: Php ${totalAmount}`;
            alert(receipt);

            let payment = parseFloat(prompt("Enter your payment amount:"));
            while (payment < totalAmount || isNaN(payment)) {
                alert("Insufficient payment.");
                payment = parseFloat(prompt("Enter your payment amount:"));
            }

            let change = payment - totalAmount;
            alert(`Your Change is: Php ${change}`);
            alert(`${receipt}\nPayment: Php ${payment}\nChange: Php ${change}`);
        }

        function chooseCategory() {

// Ask the user to select a category
            let choice_category = prompt(`Choose Category:    
A. Fruits
B. Drinks
C. Hygiene
D. Sweets
Select the letter:`).toUpperCase();

// Category A (Fruits)
            if (choice_category === "A") {
                let chooseItem = prompt(`Choose Item:     
A. Apple (Php 200)
B. Banana (Php 150)
C. Mango (Php 200)
D. Avocado (Php 120)
E. JackFruit (Php 170)
Select the letter:`).toUpperCase();
                  let qty = parseInt(prompt("How many items:"));
                let price = 0;
                let Name = "";

                switch (chooseItem) {
                    case "A": Name = "Apple"; price = 200; 
                    break;

                    case "B": Name = "Banana"; price = 150; 
                    break;

                    case "C": Name = "Mango"; price = 200; 
                    break;

                    case "D": Name = "Avocado"; price = 120; 
                    break;

                    case "E": Name = "JackFruit"; price = 170; 
                    break;

                    default: alert("Invalid item."); 
                    return;
                }
                alert(`The total price: Php ${qty * price}`);
                addToCart("Fruits", Name, qty, price);
// Category B (Drinks)

            } else if (choice_category === "B") {
                let chooseItem = prompt(`Choose Item:
A. Water (Php 20)
B. Fresh Milk (Php 145)
C. Coca-Cola (Php 45)
D. Energy Drink (Php 60)
E. Red Wine (Php 550)
Select the letter:`).toUpperCase();
                let qty = parseInt(prompt("How many items:"));
                let price = 0;
                let Name = "";

                switch (chooseItem) {
                    case "A": Name = "Water"; price = 20; 
                    break;

                    case "B": Name = "Fresh Milk"; price = 145; 
                    break;

                    case "C": Name = "Coca-Cola"; price = 45; 
                    break;

                    case "D": Name = "Energy Drink"; price = 60; 
                    break;

                    case "E": Name = "Red Wine"; price = 550; 
                    break;

                    default: alert("Invalid item."); 
                    return;
                }
                alert(`The total price: Php ${qty * price}`);
                addToCart("Drinks", Name, qty, price);
// Category C (Hygiene)
            } else if (choice_category === "C") {
                let chooseItem = prompt(`Choose Item:
A. Shampoo (Php 80)
B. Soap (Php 60)
C. Cologne (Php 120)
D. Deodorant (Php 185)
E. Cotton Buds (Php 22)
Select the letter:`).toUpperCase();
                let qty = parseInt(prompt("How many items:"));
                let price = 0;
                let Name = "";

                switch (chooseItem) {
                    case "A": Name = "Shampoo"; price = 80; 
                    break;

                    case "B": Name = "Soap"; price = 60; 
                    break;case "C": Name = "Cologne"; price = 120; 
                    break;

                    case "D": Name = "Deodorant"; price = 185; 
                    break;

                    case "E": Name = "Cotton Buds"; price = 22; 
                    break;

                    default: alert("Invalid item."); 
                    return;
                }
                alert(`The total price: Php ${qty * price}`);
                addToCart("Hygiene", Name, qty, price);
// Category D (Sweets)
            } else if (choice_category === "D") {
                let chooseItem = prompt(`Choose Item:
A. Candies (Php 65)
B. Chocolate (Php 145)
C. Cookies (Php 135)
D. Ice Cream (Php 35)
E. Gummies (Php 55)
Select the letter:`).toUpperCase();
                let qty = parseInt(prompt("How many items:"));
                let price = 0;
                let Name = "";

                switch (chooseItem) {
                    case "A": Name = "Candies"; price = 65; 
                    break;

                    case "B": Name = "Chocolate"; price = 145; b
                    reak;

                    case "C": Name = "Cookies"; price = 135; 
                    break;

                    case "D": Name = "Ice Cream"; price = 35; 
                    break;

                    case "E": Name = "Gummies"; price = 55; 
                    break;

                    default: alert("Invalid item."); 
                    return;
                }
                alert(`The total price: Php ${qty * price}`);
                addToCart("Sweet", Name, qty, price);
            } else {
                alert("Invalid category.");
            }
        }
// ask the user if thery wanted to,add more, remove item, or check out
        while (continueShopping) {
            chooseCategory();

            let choosing = true;
            while (choosing) {
                let user_choice = prompt(`Do you want to:
A. Add more
B. Remove Item
C. Check Out
Select your choice:`).toUpperCase();

                if (user_choice === "A") {
                    choosing = false;
                } else if (user_choice === "B") {
                    if (cart.length === 0) {
                        alert("Your cart is empty.");
                        continue;
                    }
// If the user chooses to remove an item, it will display the cart
                    let modifying = true;
                    while (modifying) {
                        let cartList = "Your Cart:\n";
                        let totalAmount = 0;
                        cart.forEach((entry, index) => {
                            cartList += `${index + 1}. Category: ${entry.category}, Item: ${entry.item}, Qty: ${entry.qty}, Total: Php ${entry.total}\n`;
                            totalAmount += entry.total;
                        });
                        cartList += `Total Amount: Php ${totalAmount}`;
                        alert(cartList);

                        let removeIndex = parseInt(prompt("Enter item number to modify (0 to go back):")) - 1;
                        if (removeIndex === -1) {
                            modifying = false;
                            continue;
                        }
// if the user chooses to remove an item, this will diplay and the user should type its choice
                        if (cart[removeIndex]) {
                            let action = prompt(`Type:
                                D: to delete 
                                C: to change quantity 
                                B: to go back`).toUpperCase();

                            if (action === "D") {
                                cart.splice(removeIndex, 1);
                                alert("Item removed.");
                                
                            } else if (action === "C") {
                                let newQty = parseInt(prompt(`Enter new quantity (current: ${cart[removeIndex].qty}):`));
                                if (isNaN(newQty) || newQty < 0) {
                                    alert("Invalid quantity.");
                                } else if (newQty === 0) {
                                    cart.splice(removeIndex, 1);
                                    alert("Quantity is 0. Item removed.");
                                } else {
                                    cart[removeIndex].qty = newQty;
                                    cart[removeIndex].total = newQty * cart[removeIndex].price;
                                    alert("Quantity updated.");
                                }
                            } else if (action === "B") {
                                modifying = false;
                            } else {
                                alert("Invalid action.");
                            }
                        } else {
                            alert("Invalid item number.");
                        }
                    }
                } else if (user_choice === "C") {
                    if (cart.length === 0) {
                        alert("Cart is empty. Cannot checkout.");
                    } else {
                        showReceipt();
                        continueShopping = false;
                        choosing = false;
                    }
                } else {
                    alert("Invalid choice.");
                }
            }
        }
    }
}
