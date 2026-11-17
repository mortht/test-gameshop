# Specification: Card & Board Game Shop

_The approved specification of run 3649a2ef (2026-11-17), kept up to date by agent-platform. Edit it freely and commit the edit: the next run reads it as it is._

A web shop where shoppers browse, search and buy card and board games using a cart and checkout. An admin manages products, stock and views orders.

## User stories

Stories marked _not implemented yet_ are specified but not built: their tasks haven't run or didn't get done. The next run on this project plans them again.

### US-1 (must) · not implemented yet

As **shopper**, I want **to browse the catalog of card and board games and filter by category**, so that I can discover games I like.

Acceptance criteria:

- Catalog lists products with name, image, price and category (card game or board game)
- Filtering by category shows only products of that category
- Empty result shows a 'no games found' message
- Out-of-stock products are marked as such

### US-2 (must) · not implemented yet

As **shopper**, I want **to search games by name**, so that I can quickly find a specific game.

Acceptance criteria:

- Search is case-insensitive and matches partial names
- No matches shows a 'no games found' message
- Empty search query shows the full catalog

### US-3 (must) · not implemented yet

As **shopper**, I want **to view a game's detail page**, so that I can decide whether to buy it.

Acceptance criteria:

- Page shows name, description, price, player count, play time, minimum age and stock status
- Unknown product id shows a 'not found' error

### US-4 (must) · not implemented yet

As **shopper**, I want **to add games to a cart and change quantities**, so that I can collect what I want to buy.

Acceptance criteria:

- Adding a product puts it in the cart with quantity 1; adding again increases the quantity
- Quantity can be changed or the item removed; quantity 0 removes it
- Quantity cannot exceed available stock; an error message is shown if tried
- Cart shows line totals and an overall total
- Out-of-stock products cannot be added
- Cart persists across page reloads in the same browser

### US-5 (must) · not implemented yet

As **shopper**, I want **to check out by entering shipping details and paying**, so that I receive my games.

Acceptance criteria:

- Checkout requires name, email, and shipping address; invalid or missing fields show errors and block submission
- Empty cart cannot be checked out
- Successful order shows a confirmation with an order number and summary
- Stock is reduced by the ordered quantities on success
- If stock became insufficient meanwhile, the order is rejected with a clear message and nothing is charged

### US-6 (must) · not implemented yet

As **shop admin**, I want **to log in and manage products and stock**, so that the catalog stays current.

Acceptance criteria:

- Admin area requires login; unauthenticated access is denied
- Admin can create, edit and delete products (name, description, price > 0, category, stock >= 0)
- Invalid values are rejected with errors
- Admin can view a list of orders

## User interface

Screens as approved with the mockups (`mockups/`); the elements each one must have are in `mockups/index.md`. This section is rendered from the mockups: change a screen through a run's request, not here.

### Catalog (`mockups/catalog.html`)

Browse, filter by category and search games Reached by the start page, or the Shop link in the header. Stories: US-1, US-2.

### Game detail (`mockups/product.html`)

Read details of a game and add it to the cart Reached by a game name in the catalog. Stories: US-3, US-4.

### Cart (`mockups/cart.html`)

Review items, change quantities, remove items, proceed to checkout Reached by the Cart link in the header. Stories: US-4, US-5.

### Checkout (`mockups/checkout.html`)

Enter shipping details and pay Reached by the Checkout link in the cart. Stories: US-5.

### Order confirmation (`mockups/confirmation.html`)

See the order number and summary after paying Reached by Pay now on a valid checkout. Stories: US-5.

### Admin login (`mockups/admin-login.html`)

Log in as admin Reached by the Admin link in the shop header. Stories: US-6.

### Admin products (`mockups/admin-products.html`)

List, create, edit and delete products and see stock Reached by logging in, or the Products link in the admin header. Stories: US-6.

### Product form (`mockups/admin-product-form.html`)

Create or edit a product with validation Reached by New product or Edit in the admin product list. Stories: US-6.

### Admin orders (`mockups/admin-orders.html`)

View the list of orders Reached by the Orders link in the admin header. Stories: US-6.

### Design choices

- Validation errors: each error is a block-level message directly under its field, inside a stacked field group with spacing (alternative: inline small text beside the field)
- Search and category filter: one form on the catalog page (alternative: search box in every header)
- Cart: a page of its own (alternative: a side panel on the catalog)
- Checkout: one page with shipping details and simulated payment, confirmation on a separate screen
- Admin product create/edit: a separate form page (alternative: inline dialog on the list)
- Delete product: button in the list row (alternative: confirm dialog)
- Admin area: own header with Products, Orders and Log out links, no shop navigation

## Non-functional requirements

- Usable on mobile and desktop browsers
- Admin passwords stored hashed; admin routes protected
- Catalog pages load in under 2 seconds for up to 1000 products
- Prices handled without floating-point rounding errors

## Out of scope

- Customer accounts and order history
- Reviews and ratings
- Discount codes and wishlists
- Multiple currencies and languages
- Shipping cost calculation and tax rules
- Email notifications

## Open questions and assumptions

- Which payment provider should be used? Assumed: payment is simulated/mocked behind an interface.
- Is guest checkout enough? Assumed: yes, no customer accounts.
- Single admin or multiple? Assumed: a single seeded admin account.
- Which currency? Assumed: EUR.
