# Supply Chain

## Week 2
### EOQ
Deterministic EOQ (Economic Order Quantity) models are continious-review models.
The model assumes constant demand with no lead time. Because demand is
deterministic (and ther is also no lead time) and thus there can't
be stock outs. We get ZIO (Zero Inventory Order), that is, when inventory level
reaches 0, only then do we make an order. The order size is always the same,
again this is because we have constant demand.

#### Costs
The yearly cost for a certain order quantity ($Q$) is given by:
$\frac{K\lambda}{Q} + \frac{hQ}{2}$
Deconstructing this formula the first part represents the the fixed costs
times the number of times we have to reorder per year. The second part
represents the holding cost. This is the triangle of the inventory level curve.

#### Non-Zero Lead Time
When we have a lead time, that is it takes some time for the order to arrive,
we have to change the model a bit. The change is not significant, because we
have the constant demand, which leads to the same order size, but at a time
period that is earlier than when IL reaches 0.

The re-order point is $r = \lambda \cdot L$, where $L$ is the lead time.
That is when IL reaches r, we make a new order.

#### Power of Two Policy
We cannot order whenever we want, instead we have some base period that
we have to account for. This could (in the example of power-of-two) be 2
and we can only order every $2^n$ where $n\in\mathbb{Z}$.

### EOQ with Discounts
In reality it often occurs that you recieve discounts if you place larger
orders. These types of discount often comes in one of two types of forms:
* All-units discount
* Incremental discount

Both forms uses break points to determine when a new price is given.

#### All-Units Discount
The all-units discount has one price up until a certain point, after that the
price changes for *all* products (that have already been) orderd.

#### Incremental Discount
The incremental discount changes the price for all orders after reaching
the breaking point. That means you do _not_ recieve a discount on the
orderds that are below the break point.





