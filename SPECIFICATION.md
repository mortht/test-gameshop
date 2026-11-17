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
