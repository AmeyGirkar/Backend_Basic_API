# Simple express demo

> Express: fast, unopinionated, minimalist web framework for Node.js

This project shows a simple express server serving a single HTML page and using `express.static` to serve static files.

Check out the [express documentation](https://expressjs.com/) for more information.

# E-commerce API Documentation

This document outlines the endpoints available in the E-commerce API service.

## API Endpoints Overview

### 1. Cart Total Calculator
**Endpoint:** `/cart-total`  
**Method:** GET  
**Description:** Calculates the total price of items in the cart  

#### Query Parameters:
- `newItemPrice`: Price of the new item to be added (float)
- `cartTotal`: Current cart total (float)

#### Example:
```
GET http://localhost:3000/cart-total?newItemPrice=1200&cartTotal=0
```
#### Response:
```
1200
```

### 2. Membership Discount Calculator
**Endpoint:** `/membership-discount`  
**Method:** GET  
**Description:** Applies membership discount to cart total  

#### Query Parameters:
- `cartTotal`: Total amount in cart (float)
- `isMember`: Membership status (boolean)

#### Example:
```
GET http://localhost:3000/membership-discount?cartTotal=3600&isMember=true
```
#### Response:
```
3240
```

### 3. Tax Calculator
**Endpoint:** `/calculate-tax`  
**Method:** GET  
**Description:** Calculates tax on the cart total  

#### Query Parameters:
- `cartTotal`: Total amount in cart (float)

#### Example:
```
GET http://localhost:3000/calculate-tax?cartTotal=3600
```
#### Response:
```
180
```

### 4. Delivery Time Estimator
**Endpoint:** `/estimate-delivery`  
**Method:** GET  
**Description:** Estimates delivery time based on shipping method and distance  

#### Query Parameters:
- `shippingMethod`: Type of shipping ('standard' or 'express')
- `distance`: Distance in kilometers (float)

#### Business Rules:
- Standard shipping: 1 day per 50 km
- Express shipping: 1 day per 100 km

#### Example:
```
GET http://localhost:3000/estimate-delivery?shippingMethod=express&distance=600
```
#### Response:
```
6
```

### 5. Shipping Cost Calculator
**Endpoint:** `/shipping-cost`  
**Method:** GET  
**Description:** Calculates shipping cost based on weight and distance  

#### Query Parameters:
- `weight`: Package weight in kg (float)
- `distance`: Distance in kilometers (float)

#### Calculation Formula:
```
shipping_cost = weight * distance * 0.1
```

#### Example:
```
GET http://localhost:3000/shipping-cost?weight=2&distance=600
```
#### Response:
```
120
```

### 6. Loyalty Points Calculator
**Endpoint:** `/loyalty-points`  
**Method:** GET  
**Description:** Calculates loyalty points earned from a purchase  

#### Query Parameters:
- `purchaseAmount`: Total purchase amount (float)

#### Example:
```
GET http://localhost:3000/loyalty-points?purchaseAmount=3600
```
#### Response:
```
7200
```
