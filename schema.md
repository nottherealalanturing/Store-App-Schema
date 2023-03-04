# Store APP

## User story

As a shopper, I want to be able to browse a catalog of products and add items to my shopping cart. I also want to be able to view the contents of my cart and adjust the quantity of items in my cart. Finally, I want to be able to place an order and receive confirmation of my order.

## Requirements Analysis

### Entities

- Users: A user has a unique identifier, name, email, password, balance, list of orders, and cart
- Product: A product is a single item in the store and it has unique identifier, name, description, and a price
- Cart: The cart stores all the products selected for purchase, it has a unique identifier, an list of items, and the total cost.
- Order: An order has a unique identifier, a customer id, a list of item (cart), status of the order, delivery address and the order date.

## NoSQL Schema Design

Based on the requirements analysis, the following schema can be designed:

### Users Collection:

```
{
   _id: ObjectId,
   name: string,
   email: string,
   password: string,
   balance: number,
   cart: ObjectId,
   orders: [ObjectId]
}

```

### Products Collection:

```
{
   _id: ObjectId,
   name: string,
   description: string,
   price: number
}

```

### Cart Collection:

```

{
    id: ObjectId,
    items: [{
        productId: ObjectId,
        quantity: number
    }],
    totalCost: number
}

```

### Orders Collection:

```

{
    id: ObjectId,
    customerId: ObjectId,
    cartId: ObjectId,
    orderDate: date,
    deliveryAddress: string,
    success: boolean
}

```

```
## API Endpoints

```

- GET /products - Get a list of all products in store.
- GET /products/:{productId} - Get details of a specific product.
- POST /custormer/cart/:{productId} - Add an item to the customer cart.
- DELETE /custormer/cart/:{productId} - Remove an item to the customer cart.
- GET /custormer/cart - Get the list of items currently in the cart.
- POST customer/order - place an order with the items currently in the cart
- GET customer/order - return a list of all orders placed by customer
- GET customer/order/:{orderId} - return the specified order
