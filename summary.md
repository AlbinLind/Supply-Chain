# Supply Chain

## Week 2
### EOQ
Deterministic EOQ (Economic Order Quantity) models are continuous-review models.
The model assumes constant demand with no lead time. Because demand is
deterministic (and there is also no lead time) and thus there can't
be stock outs. We get ZIO (Zero Inventory Order), that is, when inventory level
reaches 0, only then do we make an order. The order size is always the same,
again this is because we have constant demand.

#### Costs
The yearly cost for a certain order quantity ($Q$) is given by:
$\frac{K\lambda}{Q} + \frac{hQ}{2}$
Deconstructing this formula the first part represents the fixed costs
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
In reality it often occurs that you receive discounts if you place larger
orders. These types of discount often comes in one of two types of forms:
* All-units discount
* Incremental discount

Both forms uses break points to determine when a new price is given.

#### All-Units Discount
The all-units discount has one price up until a certain point, after that the
price changes for *all* products (that have already been) ordered.

Determine the order quantity by testing for all the types of prices,
and which ones has the lowest cost. The minimum cost is either one of the
$Q^*$ or at one of the breakpoints. You need to make sure that the $Q^*$
you test is realizable.

#### Incremental Discount
The incremental discount changes the price for all orders after reaching
the breaking point. That means you do _not_ receive a discount on the
order's that are below the break point.

To determine the order quantity here we simply needs to take the one
where the cost is the lowest among all the types of prices that could
be.

### EPQ - Economic Production Quantity
Instead of ordering items, we will now produce them. The production 
rate has to be greater than the consumption rate, otherwise there
will be backorders.

### Periodic-Review (Wagner-Within)
Instead of being able to look at the IL all the time, and order once the
IL falls under a certain level (base-stock model), the periodic review
has recurring periods for when we make new orders. For example, each week
we look at the IL and then order new items if we deem it necessary (what
W-W model does).

We do *not* assume constant demand, but rather _deterministic_ demand, which
may change. We may assume that, wlog, IL is 0 at time 0, since we can simply
change the demand in the following period(s), to use the IL at hand.

Wagner-Within uses dynamic programming to iteratively choose the best strategy
for each time period.

## Week 3
We are now no longer using deterministic demand, but rather _stochastic_ demand
rates. This means we cannot guarantee that a certain solution is optimal for
all possible outcomes. We can however use the _average_ demand rate, or take
the _expected_ costs. Again, there are two types of models:
* Periodic-review
* Continuous-review

The periodic review model are base-stock models, where we order if the IL
has fallen under a certain level, when we are checking the IL. The size of the
order depends on what our base-stock level is, and we then order until we reach
that point.
The continuous review model, is similar, and sets a reorder point. That means 
as soon as the IL goes under the reorder point we make a new order of size $Q$.

#### Safety Stock
Safety stock is the amount of stock we keep so that in case of higher demand
than expected (we have stochastic demand) we can (hopefully) still fulfill
the demand.

#### Cycle Stock
Cycle stock is the amount of stock we have to keep in order to fulfill the
expected demand.

#### Demand Process
The demand may differ in how it is modeled. We may have continuous demand or
discrete demand. The difference is the type of distribution.







