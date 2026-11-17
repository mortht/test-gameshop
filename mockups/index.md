# Mockups: Card & Board Game Shop

_The approved screens of run 3649a2ef (2026-11-17), written by agent-platform: open the files in a browser. They change through a run's request or its ui checkpoint; edits made here are overwritten._

- Accent: `#1d4ed8`

## Catalog (`catalog.html`)

Browse, filter by category and search games

- Reached by: the start page, or the Shop link in the header
- Stories: US-1, US-2
- Elements:
  - textbox "Game name"
  - button "Search"
  - combobox "Category"
  - heading "Games"
  - link "Cart"

## Game detail (`product.html`)

Read details of a game and add it to the cart

- Reached by: a game name in the catalog
- Stories: US-3, US-4
- Elements:
  - heading "Catan"
  - button "Add to cart"
  - link "Cart"

## Cart (`cart.html`)

Review items, change quantities, remove items, proceed to checkout

- Reached by: the Cart link in the header
- Stories: US-4, US-5
- Elements:
  - heading "Your cart"
  - spinbutton "Quantity"
  - button "Remove"
  - link "Checkout"

## Checkout (`checkout.html`)

Enter shipping details and pay

- Reached by: the Checkout link in the cart
- Stories: US-5
- Elements:
  - heading "Checkout"
  - textbox "Name"
  - textbox "Email"
  - textbox "Shipping address"
  - button "Pay now"

## Order confirmation (`confirmation.html`)

See the order number and summary after paying

- Reached by: Pay now on a valid checkout
- Stories: US-5
- Elements:
  - heading "Thank you for your order"
  - link "Continue shopping"

## Admin login (`admin-login.html`)

Log in as admin

- Reached by: the Admin link in the shop header
- Stories: US-6
- Elements:
  - heading "Admin login"
  - textbox "Username"
  - textbox "Password"
  - button "Log in"

## Admin products (`admin-products.html`)

List, create, edit and delete products and see stock

- Reached by: logging in, or the Products link in the admin header
- Stories: US-6
- Elements:
  - heading "Products"
  - link "New product"
  - link "Orders"
  - button "Delete"

## Product form (`admin-product-form.html`)

Create or edit a product with validation

- Reached by: New product or Edit in the admin product list
- Stories: US-6
- Elements:
  - heading "Product"
  - textbox "Name"
  - textbox "Description"
  - textbox "Price"
  - combobox "Category"
  - spinbutton "Stock"
  - button "Save product"

## Admin orders (`admin-orders.html`)

View the list of orders

- Reached by: the Orders link in the admin header
- Stories: US-6
- Elements:
  - heading "Orders"

## Design choices

- Validation errors: each error is a block-level message directly under its field, inside a stacked field group with spacing (alternative: inline small text beside the field)
- Search and category filter: one form on the catalog page (alternative: search box in every header)
- Cart: a page of its own (alternative: a side panel on the catalog)
- Checkout: one page with shipping details and simulated payment, confirmation on a separate screen
- Admin product create/edit: a separate form page (alternative: inline dialog on the list)
- Delete product: button in the list row (alternative: confirm dialog)
- Admin area: own header with Products, Orders and Log out links, no shop navigation
